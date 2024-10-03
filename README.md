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
├── config.yaml      # Configuration file
└── logtag/           # Folder containing tag files
    ├── 01-general.yaml  # (Example) Tag file for category: general
    ├── 02-errors.yaml   # (Example) Tag file for category: errors
    └── 03-warnings.yaml # (Example) Tag file for category: warnings
```

- `config.yaml`: This file manages the display and filter settings for tags.
- `logtag/`: A folder containing the tag files, divided by category.
  - `01-general.yaml`: (Example) Tag file for general log messages. Category: "general".
  - `02-errors.yaml`: (Example) Tag file for error messages. Category: "errors".
  - `03-warnings.yaml`: (Example) Tag file for warning messages. Category: "warnings".

## `config.yaml` Explanation

`config.yaml` defines the format of log messages output by LogTag, the columns displayed, and category filters. Here is an example of `config.yaml`:

```yaml
column:
  - name: TAG
    display: TAG
    enable: true
  - name: CATEGORY
    display: CATEGORY
    enable: true
  - name: FILE
    display: LOG-FILE
    enable: true
  - name: LOG
    display: LOG
    enable: true

category:
  - errors
```

### Configuration Items:

- **`column`**: Defines the columns to be shown in the log output, including whether they are enabled and the display name for each column.
  - `name`: The internal name of the column.
  - `display`: The display name that will be shown in the log output.
  - `enable`: Whether the column should be shown (`true` to show, `false` to hide).
- **`category`**: Defines log tag categories for filtering purposes. You can add or remove categories depending on your needs. If all categories are valid, leave this section empty.

## Tag File Naming and Explanation

### Naming Convention

Tag files follow this naming format:

```
[number]-[category].yaml
```

Example:

- `01-general.yaml`: (Example) Tags for general log messages.
- `02-errors.yaml`: (Example) Tags for error messages.
- `03-warnings.yaml`: (Example) Tags for warning messages.

The number represents the priority of the category, with lower numbers having higher priority.

### Tag File Content

Tag files define keywords to be detected in log messages and their corresponding tag messages. Regular expressions are supported.

```yaml
- keyword: "ERROR"
  message: "An error has occurred"
- keyword: "INFO"
  message: "Information"
- keyword: "^WARN.*"
  message: "Warning"
  regex: true
```

- **`<category>`**: The file name corresponds to the category name, and each file can define multiple keywords for that specific category.
- **`keyword`**: The specific log keyword to be matched.
- **`message`**: A description or explanation for the keyword.
- **`regex`**: Specifies if the keyword should be interpreted as a regular expression (`true`). If omitted, the keyword will be treated as a literal string.

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
