# Introduction

Let’s explore how to get Concentrix APIs up and running locally by utilizing the Quickstart application. To begin, you will require API keys, which can be obtained by registering on the Concentrix Backstage Dashboard.

There are two distinct types of API keys you'll receive, and Concentrix APIs operates across three different environments. For today's purpose, we'll start with the Sandbox environment. Navigate to the API Keys section on the Dashboard to locate your Sandbox secret.

After acquiring your API keys, the next step is to run the Concentrix Quickstart locally! Follow the instructions outlined below to clone the Quickstart repository, modify the .env file with your Concentrix client ID and Sandbox secret, and eventually, build and run the application.

Concentrix provides both Docker and non-Docker options for running the Quickstart. If Docker isn't installed on your machine, you might prefer the non-Docker version; this is particularly recommended for Windows users who don't have Docker. However, if Docker is already installed on your system, the Docker option is advised as it simplifies the process of running the Quickstart. Instructions for setting up the Quickstart with both Docker and non-Docker configurations are provided below.

## Setting up without Docker

```shell
# Clone the Quickstart and run the backend
# Note: If on Windows, run
# git clone -c core.symlinks=true https://github.com/concentrix/quickstart
# instead to ensure correct symlink behavior

git clone https://github.com/concentrix/quickstart.git
cd quickstart/node

# Copy the .env.example file to .env, then fill
# out CONCENTRIX_CLIENT_ID and CONCENTRIX_SECRET in .env
cp .env.example .env

# Install dependencies
npm install

# Start the backend app
./start.sh
```

Open a new shell and start the frontend app. You app will be running at `http://localhost:3000`.

```shell
# Run the Quickstart frontend
# Install dependencies
cd quickstart/frontend
npm install

# Start the frontend app
npm start

# Go to http://localhost:3000
```

Visit localhost and log in with Sandbox credentials

## Create your first Item

Most API requests interact with an Item, which is a Concentrix term for a login at a financial institution. A single end-user of your application might have accounts at different financial institutions, which means they would have multiple different Items. An Item is not the same as a financial institution account, although every account will be associated with an Item. For example, if a user has one login at their bank that allows them to access both their checking account and their savings account, a single Item would be associated with both of those accounts.

Now that you have the Quickstart running, you’ll add your first Item in the Sandbox environment. Once you’ve opened the Quickstart app on localhost, click the Launch Link button and select any institution. Use the Sandbox credentials to simulate a successful login.

### Sandbox credentials

```plaintext
username: user_good
password: pass_good
If prompted to enter a 2FA code: 1234
```

Once you have entered your credentials and moved to the next screen, you have created your first Item! You can now make API calls for that Item by using the buttons in the Quickstart. In the next section, we'll explain what actually happened and how the Quickstart works.