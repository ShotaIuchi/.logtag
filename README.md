# .logtag

This repository manages tags and configurations for the LogTag tool. Different branches are prepared for each language, and each branch contains tag files and configuration files suited for that language.

## LogTag Repository

https://github.com/ShotaIuchi/LogTag.git

## Branch Structure

Each language has its own branch, and the branch contains tag files and configuration files for that language.

- `main`: The default branch with basic settings.
- `en`: English-specific settings and tag files.
- `ja`: Japanese-specific settings and tag files.

Each branch stores the necessary tags and configuration to perform log analysis in the respective language.

## Folder Structure

```
/
├── config.hjson      # Configuration file
└── logtag/           # Folder containing tag files
    ├── 01-general.hjson  # (Example) Tag file for category: general
    ├── 02-errors.hjson   # (Example) Tag file for category: errors
    └── 03-warnings.hjson # (Example) Tag file for category: warnings
```

- `config.hjson`: This file manages the display and filter settings for tags.
- `logtag/`: A folder containing the tag files, divided by category.
  - `01-general.hjson`: (Example) Tag file for general log messages. Category: "general".
  - `02-errors.hjson`: (Example) Tag file for error messages. Category: "errors".
  - `03-warnings.hjson`: (Example) Tag file for warning messages. Category: "warnings".

## `config.hjson` Explanation

`config.hjson` defines the format of log messages output by LogTag, the columns displayed, and category filters. Here is an example of `config.hjson`:

```hjson
{
  "column": [
    {"name": "TAG", "display": "Tag", "enable": true},
    {"name": "CATEGORY", "display": "Category", "enable": true},
    {"name": "FILE", "display": "File", "enable": true},
    {"name": "LOG", "display": "Log Message", "enable": true}
  ],
  "category": ["general", "errors", "warnings"]
}
```

### Configuration Items:

- `column`: Defines the columns to be displayed in the output. For each column, specify the display name (`display`) and whether it is enabled (`enable`).
- `category`: Defines which tag categories are applied. Only the specified categories will be used.

### When `category` is not set

If `category` is not specified in `config.hjson`, all tag categories will be applied. All tag files will be searched, and corresponding tags will be added to the log messages.

## Tag File Naming and Explanation

### Naming Convention

Tag files follow this naming format:

```
[number]-[category].hjson
```

Example:

- `01-general.hjson`: (Example) Tags for general log messages.
- `02-errors.hjson`: (Example) Tags for error messages.
- `03-warnings.hjson`: (Example) Tags for warning messages.

The number represents the priority of the category, with lower numbers having higher priority.

### Tag File Content

Tag files define keywords to be detected in log messages and their corresponding tag messages. Regular expressions are supported.

```hjson
{
  "ERROR": "An error has occurred",
  "INFO": "Information",
  "^WARN.*": "Warning: "
}
```

- `ERROR`: If a log message contains "ERROR", the tag "An error has occurred" will be added.
- `INFO`: If a log message contains "INFO", the tag "Information" will be added.
- `^WARN.*`: Any log message starting with "WARN" will be tagged with "Warning: ".

## Example Usage

To apply the English tags using the `en` branch, follow these steps:

1. Clone the `en` branch of the `.logtag` repository to your home directory:

```sh
git clone -b en https://github.com/ShotaIuchi/.logtag.git ~/.logtag
```

2. Run the LogTag tool:

```sh
logtag *.txt
```

For other languages, use the corresponding branch for that language.
