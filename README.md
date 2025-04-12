# MCP CSV Analysis with Gemini AI

A powerful Model Context Protocol (MCP) server that provides advanced CSV analysis and thinking generation capabilities using Google's Gemini AI. This tool integrates seamlessly with Claude Desktop and offers sophisticated data analysis, visualization, and natural language processing features.

## 🌟 Features

### 1. CSV Analysis Tool (`analyze-csv`)
- **Comprehensive Data Analysis**: Performs detailed Exploratory Data Analysis (EDA) on CSV files
- **Two Analysis Modes**:
  - `basic`: Quick overview and essential statistics
  - `detailed`: In-depth analysis with advanced insights
- **Analysis Components**:
  - Statistical analysis of all columns
  - Data quality assessment
  - Pattern recognition
  - Correlation analysis
  - Feature importance evaluation
  - Preprocessing recommendations
  - Business insights
  - Visualization suggestions

### 2. Data Visualization Tool (`visualize-data`)
- **Interactive Visualizations**: Creates beautiful and informative charts using Plotly
- **Visualization Types**:
  - `basic`: Automatic visualization selection based on data types
  - `advanced`: Complex multi-variable visualizations
  - `custom`: User-defined chart configurations
- **Chart Types**:
  - Histograms for distribution analysis
  - Correlation heatmaps
  - Scatter plots
  - Line charts
  - Bar charts
  - Box plots
- **Features**:
  - Automatic data type detection
  - Smart chart selection
  - Interactive plots
  - High-resolution exports
  - Customizable layouts

### 3. Thinking Generation Tool (`generate-thinking`)
- Generates detailed thinking process text using Gemini's experimental model
- Supports complex reasoning and analysis
- Saves responses with timestamps
- Customizable output directory

## 🚀 Quick Start

### Prerequisites
- Node.js (v16 or higher)
- TypeScript
- Claude Desktop
- Google Gemini API Key
- Plotly Account (for visualizations)

### Installation

1. Clone and setup:
```bash
git clone [your-repo-url]
cd mcp-csv-analysis-gemini
npm install
```

2. Create `.env` file:
```env
GEMINI_API_KEY=your_api_key_here
PLOTLY_USERNAME=your_plotly_username
PLOTLY_API_KEY=your_plotly_api_key
```

3. Build the project:
```bash
npm run build
```

### Claude Desktop Configuration

1. Create/Edit `%AppData%/Claude/claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "CSV Analysis": {
      "command": "node",
      "args": ["path/to/mcp-csv-analysis-gemini/dist/index.js"],
      "cwd": "path/to/mcp-csv-analysis-gemini",
      "env": {
        "GEMINI_API_KEY": "your_api_key_here",
        "PLOTLY_USERNAME": "your_plotly_username",
        "PLOTLY_API_KEY": "your_plotly_api_key"
      }
    }
  }
}
```

2. Restart Claude Desktop

## 📊 Using the Tools

### CSV Analysis
```json
{
  "name": "analyze-csv",
  "arguments": {
    "csvPath": "./data/your_file.csv",
    "analysisType": "detailed",
    "outputDir": "./custom_output"
  }
}
```

### Data Visualization
```json
{
  "name": "visualize-data",
  "arguments": {
    "csvPath": "./data/your_file.csv",
    "visualizationType": "basic",
    "columns": ["column1", "column2"],
    "chartTypes": ["histogram", "scatter"],
    "outputDir": "./custom_output"
  }
}
```

### Thinking Generation
```json
{
  "name": "generate-thinking",
  "arguments": {
    "prompt": "Your complex analysis prompt here",
    "outputDir": "./custom_output"
  }
}
```

## 📁 Output Structure
```
output/
├── analysis/
│   ├── csv_analysis_[timestamp]_part1.txt
│   ├── csv_analysis_[timestamp]_part2.txt
│   └── csv_analysis_[timestamp]_summary.txt
├── visualizations/
│   ├── histogram_[column]_[timestamp].png
│   ├── scatter_[columns]_[timestamp].png
│   └── correlation_heatmap_[timestamp].png
└── thinking/
    └── gemini_thinking_[timestamp].txt
```

## 📊 Visualization Types

### Basic Visualizations
- Automatically generated based on data types
- Includes:
  - Histograms for numeric columns
  - Correlation heatmaps
  - Basic scatter plots

### Advanced Visualizations
- More sophisticated charts
- Multiple variables
- Enhanced layouts
- Custom color schemes

### Custom Visualizations
- User-defined chart types
- Configurable parameters
- Custom styling options
- Advanced plot layouts

## 🛠️ Development

### Available Scripts
- `npm run build`: Compile TypeScript to JavaScript
- `npm run start`: Start the MCP server
- `npm run dev`: Run in development mode with ts-node

### Environment Variables
- `GEMINI_API_KEY`: Your Google Gemini API key
- `PLOTLY_USERNAME`: Your Plotly username
- `PLOTLY_API_KEY`: Your Plotly API key

## 📝 Analysis Details

### Basic Analysis Includes
1. Basic statistical summary for each column
2. Data quality assessment
3. Key insights and patterns
4. Potential correlations
5. Recommendations for further analysis

### Detailed Analysis Includes
1. Comprehensive statistical analysis
   - Distribution analysis
   - Central tendency measures
   - Dispersion measures
   - Outlier detection
2. Advanced data quality assessment
3. Pattern recognition
4. Correlation analysis
5. Feature importance analysis
6. Preprocessing recommendations
7. Visualization suggestions
8. Business insights

## ⚠️ Limitations

- Maximum file size: Dependent on system memory
- Rate limits: Based on Gemini API and Plotly quotas
- Output token limit: 65,536 tokens per response
- CSV format: Standard CSV files only
- Analysis time: Varies with data size and complexity
- Visualization limits: Based on Plotly free tier restrictions

## 🔒 Security Notes

- Store your API keys securely
- Don't share your `.env` file
- Review CSV data for sensitive information
- Use custom output directories for sensitive analyses
- Secure your Plotly credentials

## 🐛 Troubleshooting

### Common Issues
1. **API Key Error**
   - Verify `.env` file exists
   - Check API key validity
   - Ensure proper environment loading

2. **CSV Parsing Error**
   - Verify CSV file format
   - Check file permissions
   - Ensure file is not empty

3. **Claude Desktop Connection**
   - Verify config.json syntax
   - Check file paths in config
   - Restart Claude Desktop

### Debug Mode
Add `DEBUG=true` to your `.env` file for verbose logging:
```env
GEMINI_API_KEY=your_key_here
DEBUG=true
```

## 📚 API Reference

### CSV Analysis Tool
```typescript
interface AnalyzeCSVParams {
  csvPath: string;          // Path to CSV file
  outputDir?: string;       // Optional output directory
  analysisType?: 'basic' | 'detailed';  // Analysis type
}
```

### Data Visualization Tool
```typescript
interface VisualizeDataParams {
  csvPath: string;          // Path to CSV file
  outputDir?: string;       // Optional output directory
  visualizationType?: 'basic' | 'advanced' | 'custom';  // Visualization type
  columns?: string[];       // Columns to visualize
  chartTypes?: ('scatter' | 'line' | 'bar' | 'histogram' | 'box' | 'heatmap')[];  // Chart types
  customConfig?: Record<string, any>;  // Custom configuration
}
```

### Thinking Generation Tool
```typescript
interface GenerateThinkingParams {
  prompt: string;           // Analysis prompt
  outputDir?: string;       // Optional output directory
}
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

MIT License - See LICENSE file for details