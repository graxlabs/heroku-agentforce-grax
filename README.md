# GRAX Agentforce Action

A Flask API service that enables natural language querying of Salesforce data in the GRAX data lake. The service uses LangChain and GPT-4 to translate natural language questions into SQL queries and return formatted results.

## Setup

### Environment Variables

Required environment variables can be set in your environment or in a `.env` file:

```bash
# AWS Athena Connection
AWS_ACCESS_KEY_ID=        # AWS access key with Athena permissions
AWS_SECRET_ACCESS_KEY=    # AWS secret key
ATHENA_DATABASE=          # Athena database/schema name
AWS_REGION=              # AWS region (e.g. us-east-1)
S3_STAGING_DIR=          # S3 location for query results
AWS_WORKGROUP=primary    # Athena workgroup (default: primary)

# OpenAI API
OPENAI_API_KEY=          # Your OpenAI API key for GPT-4 access

# Optional
PORT=5001                # Server port (default: 5001)

# Google OAuth
GOOGLE_CLIENT_ID=        # Google OAuth client ID
GOOGLE_CLIENT_SECRET=    # Google OAuth client secret
SECRET_KEY=             # Flask secret key for sessions

# Database
DATABASE_URL=           # Database URL (default: sqlite:///app.db)
```

### Installation

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Start the server:

```bash
python app.py
```

### Usage Example

You can query the API using curl:

```bash
curl -X POST http://localhost:5001/query \
  -H "Content-Type: application/json" \
  -u heroku:agent \
  -d '{"query": "Show me the top 5 accounts by revenue"}'
```

The API will return a JSON response containing the query results and any relevant explanations.