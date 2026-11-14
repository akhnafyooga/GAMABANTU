# GAMABANTU

GAMABANTU is a campus marketplace for requesting and providing everyday services around Universitas Gadjah Mada.

## Prerequisites

- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0)
- A browser with WebAssembly support

## Build

```sh
dotnet restore GAMABANTU.slnx
dotnet build GAMABANTU.slnx --no-restore
```

## Run locally

Start each project in a separate terminal from the repository root.

```sh
dotnet run --project src/GAMABANTU.Api --launch-profile http
dotnet run --project src/GAMABANTU.Client --launch-profile http
```

Open the Blazor WebAssembly client at <http://localhost:5062>. Check the ASP.NET Core API at <http://localhost:5038/health>.

The starter runs without external accounts or secrets. Google sign-in, the Midtrans sandbox, and the task workflow are planned application features.
