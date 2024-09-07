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
