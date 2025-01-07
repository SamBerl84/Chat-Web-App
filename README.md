**Chat Web Application**
This frontend application allows users to upload documents and chat with Open AI model to ask questions related to the information in the document. Built with React.js and TypeScript, front-end. 
It uploads the document to SFTP and calls Mule application in the backend to trigger the flow to integrate document contect into vector database. 
Then it takes a question from user and sends to AI agent to answer questions with respect to the knowledge (Uploaded document) provided.

**Prerequisites**
Before starting, ensure you have the following:

React.js 
npm 
SFTP credentials from [SFTP Cloud](https://sftpcloud.io/tools/free-sftp-server)
Visual Studio Code and/or Preferred IDE
Notepad to keep credentials
Obtaining SFTP Credentials
Browse to [SFTP Cloud](https://sftpcloud.io/tools/free-sftp-server)
Click "Create test SFTP server"
Note the populated SFTP details for the project.
Free test SFTP access is valid for 60 mins.
**Setup**
Supabase Setup
Creating a Supabase Account
Visit Supabase
Click "Start your project" or "Sign up"
Sign up using your email or GitHub account
If using email, confirm your email address after registration
**Creating a New Project**
Log in to your Supabase account
Click "New Project"
**Fill in the project details:**
Project Name: Choose a name for your project
Database Password: Set a strong password
Region: Select the closest region for better performance
Click "Create new project"
**Enabling pgvector**
Navigate to the "Database" section in the left sidebar
In database settings, find the extensions list
Search for vector and enable it
**Retrieving Connection Settings**
Once your Supabase Database is spun up, at the very top of the Navigation Menu, click the button labeled 'Connect'.

In the Connection String tab, select Type = JDBC

Copy the connection string for 'Transaction Pooler'

example: jdbc:postgresql://aws-0-us-east-1.pooler.supabase.com:6543/postgres?user=postgres.kbffoiphnqxaghmnmbcw&password=[YOUR-PASSWORD]
Extract the following connection properties:

host = aws-0-us-east-1.pooler.supabase.com:6543
port = 6543
user = postgres.kbffoiphnqxaghmnmbc
password = your-password-you-created
database = postgres
Setting	Value
POSTGRES_HOST	REPLACEME
POSTGRES_PORT	REPLACEME
POSTGRES_DATABASE	REPLACEME
POSTGRES_USER	REPLACEME
POSTGRES_PASSWORD	REPLACEME
Copy the provided connection properties for easy reference

**Project Setup**
Open up Terminal

Clone the repository

git clone https://github.com/samberl84/Chat-Web-App.git
cd Chat-Web-App

**Install dependencies**

npm install
Set up environment variables

cp .env.example .env.local
Edit .env.local and add your SFTP credentials:

SFTP_HOST=your_sftp_host
SFTP_PORT=your_sftp_port
SFTP_USERNAME=your_sftp_username
SFTP_PASSWORD=your_sftp_password
Update other variables as needed.

**Run the project locally**

npm run dev
The application should now be running on http://localhost:3000 (or another port if specified).

**MuleSoft Application Setup**
Creating an OpenAI API Key
Visit OpenAI
Log in or sign up for an account
Navigate to the API Keys section in your dashboard
Click "Create new secret key"
Copy and securely store your API key
Importing the MuleSoft Project
Download the "mulesoft-ai-chain-demo.jar" file (located in the root of this repo)
Open Anypoint Studio
Go to File > Import... > Mule > Packaged mule application (.jar)
Select the downloaded JAR file and click "Finish"
Configuring the MuleSoft Application
In Anypoint Studio, locate src/main/resources/envVars.json

Replace placeholder values with your actual connection settings (These are the values you got from the Supabase setup):

{
  "OPENAI": {
    "OPENAI_API_KEY": "YOUR_OPENAI_API_KEY"
  },
  "PGVECTOR": {
    "POSTGRES_HOST": "REPLACEME",
    "POSTGRES_PORT": "REPLACEME",
    "POSTGRES_DATABASE": "REPLACEME",
    "POSTGRES_USER": "REPLACEME",
    "POSTGRES_PASSWORD": "REPLACEME"
  }
}
Open the Global Elements, select SFTP Config and edit the SFTP Connection Properties with your credentials from SE Platform

In the sftpNewFile flow, update the localPath variable with your desired local folder path

Running the MuleSoft Application
Right-click on your project in Anypoint Studio
Select Run As > Mule Application
**
A Snapshot of how the Frontend Application Looks!**
![image](https://github.com/user-attachments/assets/b0286d75-fc8d-409f-9220-60010dee148c)
