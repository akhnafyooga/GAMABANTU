# GAMABANTU

**Help around campus, paid safely.**

GAMABANTU is a fixed-price marketplace for everyday tasks around Universitas Gadjah Mada. Requesters can post jobs such as cleaning a kos room or picking up laundry. Taskers can browse nearby jobs, claim one, and track their work and earnings.

[Desktop prototype](https://www.figma.com/proto/KPJRbVHRgXNFJPGUcVcywO/Mokap--Copy-?page-id=4001%3A2279&node-id=4003-1140&starting-point-node-id=4003%3A1140) · [Mobile prototype](https://www.figma.com/proto/KPJRbVHRgXNFJPGUcVcywO/Mokap--Copy-?page-id=4001%3A2279&node-id=4003-1531&starting-point-node-id=4003%3A1531)

## Explore the prototype

Both flows start on the **New Design** landing page. Desktop uses dropdown navigation. Mobile groups role actions in a compact menu and uses a separate category picker.

| Journey | What to explore |
| --- | --- |
| Public and onboarding | Explore the landing page and walkthrough, open **Panduan** for payment and help, then follow **Masuk** through login, signup, and onboarding. |
| Minta bantuan · Requester | Browse categories, create a fixed-price task, track it in **Permintaanku**, and follow the payment and completion screens. |
| Bantu orang · Tasker | Search for jobs, filter by category or price, open a listing, and explore claiming, active jobs, photo proof, and **Penghasilan**. |
| Shared navigation | Review the role menus, **Kabar** notifications, profile and settings, and help. |

Search for laundry, filter to cleaning, or try the Rp 50.000 price cap to see how the designs handle filtered and empty results. Listings cover cleaning, pet care, delivery, tutoring, and other services.

### Planned task lifecycle

1. **Open** — The requester posts a task with a fixed IDR price. The first successful claim reserves it for one tasker.
2. **Awaiting payment** — The requester starts checkout in the Midtrans sandbox. The payment flow shows pending and verified states.
3. **In progress** — Verified payment unlocks the WhatsApp handoff. The tasker can submit completion proof.
4. **Completed** — The requester confirms the work, and the tasker can track earnings and payout status.

The repository currently contains the application starter and the API health endpoint. The prototype covers the planned experience. Sign-in, marketplace data, task claiming, payments, and payouts are future implementation work.

## Build and run

Install the [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) and use a browser with WebAssembly support. The first restore needs access to NuGet.org. The starter runs without a database or external credentials.

From the repository root:

```sh
dotnet restore GAMABANTU.slnx
dotnet build GAMABANTU.slnx --no-restore
```

Run the projects in separate terminals:

| Project | Command | Local URL |
| --- | --- | --- |
| [Blazor WebAssembly client](src/GAMABANTU.Client) | `dotnet run --project src/GAMABANTU.Client --launch-profile http` | [localhost:5062](http://localhost:5062/) |
| [ASP.NET Core API](src/GAMABANTU.Api) | `dotnet run --project src/GAMABANTU.Api --launch-profile http` | [localhost:5038/health](http://localhost:5038/health) |

The [build workflow](.github/workflows/build.yml) restores, builds in Release mode, and publishes both projects on pull requests and pushes to `main`.

## Implementation order

1. Establish the public layout and responsive navigation, then wire up UGM sign-in, role onboarding, and WhatsApp number capture.
2. Build task posting, search, category and price filters, listing details, and atomic claiming.
3. Connect sandbox checkout and verified payment events, then add the WhatsApp handoff, completion confirmation, and earnings views.
