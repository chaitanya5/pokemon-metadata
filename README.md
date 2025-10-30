# Pokemon NFT Metadata Generation Pipeline 🎴

A comprehensive pipeline for generating, processing, and uploading Pokemon NFT metadata and images. This tool provides a step-by-step process to convert Pokemon data into NFT-compatible metadata format and manage associated images.

## 🚀 Features

- Interactive CLI interface with progress tracking
- Modular pipeline architecture
- Support for CSV to JSON conversion
- Metadata generation and sanitization
- Automatic image downloading
- S3 bucket integration for images and metadata
- Status tracking and detailed reporting
- Prerequisites validation
- Step-by-step execution monitoring

## 📋 Pipeline Steps

1. **CSV to JSON Conversion** 📊
   - Converts Pokemon CSV data to JSON format
   - Input: `data/pokemon.csv`
   - Output: `data/pokemon.json`

2. **Generate Metadata** 🏗️
   - Creates NFT metadata from Pokemon data
   - Input: `data/pokemon.json`, `data/all_pokemon_data.json`
   - Output: `data/metadata.json`

3. **Sanitize Metadata** 🧹
   - Cleans and validates generated metadata
   - Input: `data/metadata.json`
   - Output: `data/sanitized-metadata.json`

4. **Download Images** ⬇️
   - Downloads Pokemon front and back images
   - Input: `data/sanitized-metadata.json`
   - Output: `data/metadata_with_local_paths.json`

5. **Upload Images to S3** ☁️
   - Uploads Pokemon images to S3 bucket
   - Input: `data/metadata_with_local_paths.json`
   - Output: `data/metadata_with_S3.json`

6. **Split Metadata** ✂️
   - Splits metadata into individual files
   - Input: `data/metadata_with_S3.json`
   - Output: Individual files in `metadata` directory

7. **Upload Metadata to S3** ☁️
   - Uploads individual metadata files to S3
   - Input: `metadata` directory
   - Output: `data/metadata_with_S3_and_metadata_urls.json`

## 🛠️ Setup and Configuration

1. Ensure Node.js is installed on your system
2. Clone this repository
3. Install dependencies:
   ```bash
   npm install
   ```
4. Configure your S3 bucket settings in `config.json`
5. Prepare your input data files in the `data` directory

## 📦 Project Structure

```
pokemon-metadata/
├── config.json        # Pipeline configuration
├── data/             # Data directory for input/output files
├── images/           # Downloaded Pokemon images
├── metadata/         # Individual metadata files
└── scripts/          # Pipeline step scripts
```

## 🚀 Usage

Run the pipeline interface:

```bash
node start.js
```

The interactive CLI provides the following options:
1. Run Step - Execute individual pipeline steps
2. View Pipeline Status - Check overall progress
3. View Step Details - See detailed step information
4. Check Prerequisites - Validate required files
5. View Step Status History - Track execution history

## ⚙️ Configuration

The pipeline can be configured through `config.json`:

- **Paths**: Configure directory locations
- **Pipeline Steps**: Modify step configurations
- **Settings**:
  - `parallel_execution`: Enable/disable parallel processing
  - `continue_on_error`: Continue pipeline despite errors
  - `backup_outputs`: Enable output backups
  - `log_level`: Set logging verbosity

## 📝 Status Tracking

The pipeline maintains a status file (`data/status.json`) tracking:
- Step completion status
- Execution timestamps
- Error messages
- Step-specific details

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

## 📄 License

## ✨ Acknowledgments

- Pokemon data sources
- Contributors and maintainers
