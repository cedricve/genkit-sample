# Genkit for Go

## Open the devcontainer

1. Install Docker and the VS Code **Dev Containers** extension.
2. Open this repository in VS Code and run **Dev Containers: Reopen in Container**.
3. Wait for setup to finish. The container includes Go 1.26, Go editor tools,
   Node.js 24, the Genkit CLI, and Claude Code.

Verify the tools in the container terminal:

```sh
go version
node --version
genkit --version
claude --version
```

## Claude Code

After changing the devcontainer configuration, run **Dev Containers: Rebuild
Container** to install the updated tools.

Run `claude` in the container terminal and follow the sign-in prompts.
Authenticate inside the container; host credentials are not mounted or copied.

## Create and run a Genkit app

This repository provides the development environment, not an application yet.
Initialize the Go module inside the container:

```sh
go mod init github.com/cedricve/genkit-sample
go get github.com/firebase/genkit/go
```

Follow the [Genkit Go quickstart](https://genkit.dev/docs/go/get-started/) to
create `main.go`. If using Gemini, set your key in the container terminal:

```sh
export GEMINI_API_KEY='your-api-key'
go mod tidy
genkit start -- go run .
```

Open <http://localhost:4000> for the Genkit Developer UI. VS Code forwards this
port from the container. Keep the application running while using the UI.

Do not commit API keys. Local `.env` files and Genkit runtime data are ignored.
Environment files are not automatically loaded; export credentials in the
terminal before starting the application.
