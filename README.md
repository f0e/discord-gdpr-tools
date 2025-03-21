# discord gdpr tools

A CLI tool to work with a Discord GDPR request `messages.csv` (for example, generated by [undiscord-package-util](https://github.com/Dorifor/undiscord-package-util)).

## features

- **Download Attachments**: Downloads attachments from messages that will be deleted
- **Date Cutoff**: Remove messages with timestamps after a specific date

## setup

1. Clone the repository
1. Install dependencies using pip:
   ```sh
   pip install -r requirements.txt
   ```

## usage

The tool offers multiple commands through a CLI interface:

```sh
python -m src.cli [COMMAND] [OPTIONS]
```

### commands

#### download attachments

Downloads attachments from messages in your Discord data export.

```sh
python -m src.cli download-attachments -i <path_to_messages.csv> -e <path_to_discord_export> -o <output_directory>
```

##### arguments:

- `-i, --input` (required): Path to `messages.csv` file containing `CHANNEL_ID,MESSAGE_ID` lines.
- `-e, --export_path` (required): Path to the Discord data export directory.
- `-o, --output` (optional, default=`out`): Path where the output files will be saved.

##### example:

```sh
python -m src.cli download-attachments -i ./data/messages.csv -e ./data/discord_export -o ./output
```

#### date cutoff

Removes messages with timestamps after a specified date from the messages.csv file.

```sh
python -m src.cli date-cutoff -i <path_to_messages.csv> -e <path_to_discord_export> -d <cutoff_date> -o <output_path>
```

##### arguments:

- `-i, --input` (required): Path to `messages.csv` file.
- `-e, --export_path` (required): Path to the Discord data export directory.
- `-d, --date` (required): Cutoff date in YYYY-MM-DD or YYYY-MM-DD HH:MM:SS format.
- `-o, --output` (required): Path to save the filtered messages file.

##### example:

```sh
python -m src.cli date-cutoff -i ./data/messages.csv -e ./data/discord_export -d 2023-01-01 -o ./filtered_messages.csv
```
