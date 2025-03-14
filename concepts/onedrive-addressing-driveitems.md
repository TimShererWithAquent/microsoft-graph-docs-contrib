---
title: "Address resources in a drive on OneDrive"
description: "Learn how to access items within a drive on OneDrive with ID-based and path-based addressing, and how to properly encode paths for Microsoft Graph."
ms.localizationpriority: high
ms.subservice: "sharepoint"
author: "spgraph-docs-team"
doc_type: conceptualPageType
ms.date: 11/07/2024
---

# Address resources in a drive on OneDrive

Learn how to access items within a drive on OneDrive with ID-based and path-based addressing, and how to properly encode paths for Microsoft Graph.

## ID-based addressing
OneDrive supports ID-based addressing of items. Items are assigned a unique
identifier when they are created and the ID persists across the actions a user
performs on the item. Renaming or moving the item will not change the item's ID.

ID-based addressing is a useful way to track items that might be moved by the user
to different locations on OneDrive. As long as you have the item's ID and the item exists, you'll be
able to find it.

## Path-based addressing
OneDrive also supports path-based addressing. This allows you to use a friendly
URL syntax to address items relative to the hierarchy of items visible in
OneDrive. If you know the hierarchy to an item, you can directly address that
item, without spending any time making repeated calls to discover each level of the
hierarchy.

However, since path-based addressing is based on the name of the item, renaming
or moving the item to a new location will cause the path of the item to change.

You can use path-based addressing relative to any item in OneDrive.
For example, when working with shared folders, you
can use a path-based URL relative to the shared folder's item ID to address
something in the shared folder by path.

## Examples
The following examples show the different URL formats available to access data.
All of these URLs are logically equivalent and return the content of MyFile.xlsx.

| URL example                                       | Description                                              |
|:--------------------------------------------------|:---------------------------------------------------------|
| `/drive/root:/Documents/MyFile.xlsx:/content`     | Specified by path relative to the root of a drive.       |
| `/drive/special/documents:/MyFile.xlsx:/content`  | Specified by filename in the `documents` special folder. |
| `/drive/items/0123456789AB/content`               | Specified by item-id.                                    |
| `/drives/AB0987654321/items/0123456789AB/content` | Specified by drive-id and item-id.                       |


## Path encoding

OneDrive supports addressing files and folders using the path of the item in the
user's OneDrive. However, because the path contains user specified content, which
can potentially contain characters that are not URL safe, you should ensure proper
encoding of any path segments.

Microsoft Graph expects that URLs conform to [RFC 3986](http://tools.ietf.org/html/rfc3986).
The following is a summary of how to properly encode paths for Microsoft Graph.

### OneDrive reserved characters
The following characters are OneDrive reserved characters and can't be used in OneDrive folder and file names.

```
  onedrive-reserved  = "/" / "\" / "*" / "<" / ">" / "?" / ":" / "|"
  onedrive-business-reserved
                     = "/" / "\" / "*" / "<" / ">" / "?" / ":" / "|" / "#" / "%"
```

> [!NOTE]
> - Folder names can't end with a period (`.`).
> - File or folder names cannot begin with a tilde ('~').
>
> For more information, see [Restrictions and limitations when you sync SharePoint libraries to your computer through OneDrive for work or school](https://support.microsoft.com/en-us/kb/2933738).

### URI path characters

When constructing the path segment of a URL for the Microsoft Graph API, the following characters are allowed for path names, based on the URI RFC.

```
  pchar       = unreserved / pct-encoded / sub-delims / ":" / "@"
  pct-encoded = "%" HEXDIG HEXDIG
  unreserved  = ALPHA / DIGIT / "-" / "." / "_" / "~"
  sub-delims  = "!" / "$" / "&" / "'" / "(" / ")"
              / "*" / "+" / "," / ";" / "="
```

Item name characters, which are not included in the `pchar` group, such as `#` and ` ` (space), must be percent encoded.

### Encoding characters
Microsoft Graph uses standard percent encoding, where URL-invalid characters are encoded with a % and then the UTF-8 character code for the character.
For example:

* `" "` -> `%20`
* `"#"` -> `%23`

### Common URL encoding mistakes
You can't encode an entire URL in one call, because the encoding rules for each segment of a URL are different.
Without proper encoding, the unencoded URL will be ambiguous for which segments contain which content.
As such, you need to encode the URL path when building your URL string.

For example, instead of writing this:

```
string url = url_encode("https://graph.microsoft.com/v1.0/me/drive/root:/" + path + ":/children")
```

Write this:

```
string url = "https://graph.microsoft.com/v1.0/me/drive/root:/" + url_path_encode(path) + ":/children")
```

However, not all URL encoding libraries respect all the requirements of standard URL path encoding.

### .NET / C-Sharp / Visual Basic

The .NET classes for `HttpUtility` and `Uri` include various methods for
URL encoding. However, none of those methods properly encode all reserved
characters for the path component of the URL (including `HttpUtility.UrlPathEncode`).

Instead of using those methods, you should use `UriBuilder` to construct a
properly escaped URL.

```csharp
UriBuilder builder = new UriBuilder("https://graph.microsoft.com");
builder.Path = "/v1.0/me/drive/root:/Documents/My Files/#nine.docx";
Uri url = builder.Uri;
```

### Objective-C / iOS

For Objective-C, iOS and Mac OS X development, use the `stringByAddingPercentEncodingWithAllowedCharacters` method and
`[NSCharacterSet URLPathAllowedCharacterSet]` to properly encode the path
component of the URL.

```objc
NSString *root = @"https://graph.microsoft.com/v1.0/me/drive/root:/";
NSString *path = @"Documents/My Files/#nine.docx";
NSString *encPath = [path stringByAddingPercentEncodingWithAllowedCharacters:[NSCharacterSet URLPathAllowedCharacterSet]];
NSURL *url = [[NSURL alloc] initWithString:[root stringByAppendingString:encPath]];
```


### Android

Use the `Uri.Builder` class to construct a properly encoded URL.

```java
Uri.Builder builder = new Uri.Builder();
builder.
  scheme("https").
  authority("graph.microsoft.com").
  appendPath("v1.0").
  appendPath("me").
  appendPath("drive").
  appendPath("root:").
  appendPath("Documents").
  appendPath("My Files").
  appendPath("#nine.docx");
String url = builder.build().toString();
```

### JavaScript

Use `escape()` in JavaScript to properly encode a path component.

```javascript
var root = "https://graph.microsoft.com/v1.0/me/drive/root:";
var path = "/Documents/My Files/#nine.docx";
var url = root + escape(path);
```

### Examples

Here is an example of a OneDrive user (Adele) with the following folder hierarchy:
```
OneDrive
	\Adele's Files
		\doc (1).docx
    \estimate%s.docx
	\Break#Out
		\saved_game[1].bin
```

To address each of Adele's files, you use percent encoding, as follows:

| Path                     | Encoded URL for path                      |
|:-------------------------|:------------------------------------------|
| `\Adele's Files`          | `/root:/Adele's%20Files`                   |
| `\...\doc (1).docx`      | `/root:/Adele's%20Files/doc%20(1).docx`    |
| `\...\estimate%.docx`    | `/root:/Adele's%20Files/estimate%25s.docx` |
| `\Break#Out`             | `/root:/Break%23Out`                      |
| `\...\saved_game[1].bin` | `/root:/Break%23Out/saved_game[1].bin`    |

## Related content

- [OneDrive file storage API overview](onedrive-concept-overview.md)