# Windows VPS: How Much RAM You Actually Need, What the Licence Costs After Day 180, and Where a Cheap Plan Turns Expensive (Rainyun Prices Compared)

Rainyun's cheapest KVM cloud server is ¥20 a month (roughly $2.80) for 1 vCPU, 1 GB of RAM and 30 GB of SSD, and a Windows Server image is one of the options at checkout. That machine is enough for one person on Remote Desktop running one application. Add a second or third user, or put SQL Server Express next to IIS, and the ¥39 plan with 2 vCPU and 4 GB is the one that keeps working past the first week.

Below you'll find every plan on Rainyun's KVM line with the monthly price, the licensing rules that decide whether a $4 Windows VPS really costs $4, how to size a server by workload instead of by price tag, and the details that turn a cheap Windows plan into an expensive one after month two.

> **Quick pick:** the 2 vCPU / 4 GB plan at ¥39/month covers a small team's remote desktop, a .NET site with a light database, or a bot that has to stay online around the clock. If you need one login and one app, the ¥20 entry plan is enough. 👉 [Check Rainyun's current Windows VPS plans and prices](https://bit.ly/RaiNyun)

## Rainyun's Windows VPS plans at a glance

All six plans below are KVM virtual machines with full administrator access over RDP. You choose the operating system at order time, and Windows Server is on the list alongside the usual Linux distributions.

| Plan | vCPU / RAM | Storage | Price (CNY/month) | Order |
| --- | --- | --- | --- | --- |
| KVM Entry | 1 core / 1 GB | 30 GB SSD | ¥20 | [Order](https://bit.ly/RaiNyun) |
| KVM Standard | 2 cores / 2 GB | 30 GB SSD | ¥29 | [Order](https://bit.ly/RaiNyun) |
| KVM Mid | 2 cores / 4 GB | 30 GB SSD | ¥39 | [Order](https://bit.ly/RaiNyun) |
| KVM Advanced | 4 cores / 4 GB | 30 GB SSD | ¥55 | [Order](https://bit.ly/RaiNyun) |
| KVM High-End | 4 cores / 8 GB | 30 GB SSD | ¥108 | [Order](https://bit.ly/RaiNyun) |
| KVM Flagship | 8 cores / 16 GB | 30 GB SSD | ¥192 | [Order](https://bit.ly/RaiNyun) |

Prices are monthly and in Chinese yuan, before any term discount. Rainyun prices the same plan name differently depending on which node you pick and whether you choose a metered or unmetered traffic model, so treat the figures above as the standard monthly rate and the order page as the number you'll actually pay.

Storage is expandable well beyond the 30 GB baseline, which matters on Windows: a Server install plus updates eats 15 to 20 GB before you add a single application. Plan on at least 40 GB if you're installing SQL Server or keeping Windows Update history around.

Term commitments carry a real discount: quarterly billing takes 10% off, semi-annual 20%, annual 30%. On the ¥39 plan that puts the effective monthly cost at about ¥27.30 if you pay for a year up front.

## The licence is the whole reason Windows costs more than Linux

On every host that publishes a Linux and a Windows price for identical hardware, Windows is the expensive one. Atlantic.Net's Windows VPS starts at about $15 a month while its Linux VPS starts at $4, and the gap is Microsoft licensing, which is baked into the Windows price rather than billed separately. Linux has no licence fee at all.

There's a legal boundary you should know about, because it explains a lot of confusing product pages. A hosting provider can rent you a **Windows Server** licence. It cannot rent you desktop Windows. When you see a Windows 11 Pro template on a VPS provider, that template installs unactivated and you supply your own product key, because Microsoft doesn't allow providers to resell desktop licences. Windows 11 Pro also needs at least 2 GB of RAM, so the smallest desktop configuration on a typical host costs more than the smallest Server one.

Then there's the evaluation image, the single most expensive detail to overlook. Many low-cost Windows hosts install Windows Server as a Microsoft evaluation build, which costs the provider nothing. The clock starts when you activate online, which has to happen within the first 10 days. You get 180 days of full function with the remaining days shown on the desktop. After day 180 the machine still holds your files and installed software, but it shuts itself down every hour and only accepts security updates. Converting to a licensed install is done in place, without a reinstall.

So the question to ask before paying is short: **does this Windows image carry a licence, or is it an evaluation build, and what happens on day 181?** Rainyun's order flow lets you choose a Windows Server image; confirm which of those two you're getting while you're still on the configuration screen, because the answer is the difference between a ¥39 server and a ¥39 server plus a licence.

One date to keep in mind for any new Windows deployment: Microsoft ended support for Windows 10 on 14 October 2025. It no longer receives security updates, so new machines should run Windows 11 Pro or Windows Server, not Windows 10.

## How much server does your workload actually need?

Match the plan to what's running on it, not to how much you'd like to spend.

**One person, one Windows application.** Accounting software, a trading terminal, an ERP client, a single line-of-business app. The ¥20 entry plan with 1 GB works, and 2 GB gives you room to keep a browser open next to the app. This is the most common Windows VPS purchase and the most commonly oversold.

**Two to three concurrent Remote Desktop users.** Windows Server allows two administrative RDP sessions out of the box. A third user needs RDS user licences, and those are billed per user per month on top of the server. One host quotes $8.90 per extra user per month, which on a three-person team adds more to the bill than the server itself. Do that arithmetic before you upgrade the CPU.

**SQL Server, or IIS under constant load.** Shared vCPU plans are fine for bursty work and bad for sustained load, because you're sharing physical cores with other tenants. A database that runs queries all day, or a site with steady traffic, belongs on reserved cores. MassiveGRID draws that line explicitly: its shared Windows VPS starts at $3.99, and its dedicated-core Windows VPS starts at $18.84 for exactly these workloads.

**Bots, trading terminals, scheduled jobs.** The requirement here isn't CPU, it's session persistence. Closing the RDP window disconnects you; it doesn't log you out, so the session and everything running in it keeps going. A KVM console in the control panel matters just as much, because a firewall rule or a bad RDP setting can lock you out of your own machine, and console access is how you get back in.

## What Rainyun is good at, and where it doesn't fit

Rainyun runs nodes in Los Angeles and in several Chinese locations, including a Wenzhou high-protection node that ships with 100 Gbps DDoS filtering. Measured latency is the reason to care about location: roughly 10 to 50 ms from major Chinese cities to domestic nodes, 30 to 80 ms from mainland China to Hong Kong, and 150 to 250 ms from mainland China to Los Angeles. From Japan, the LA nodes sit around 100 to 150 ms.

Two practical points if you're outside China. Payment runs through Alipay and WeChat Pay, so check that you can complete a payment before you build a plan around this provider. Documentation and the user forum are mostly in Chinese, which translation tools handle well enough for setup guides but adds friction to troubleshooting. If your users and your traffic are in Europe or North America, a provider with a datacentre in that region will beat these latency numbers.

What you get for the price is genuine: 100 Gbps DDoS filtering on the protected node at no extra charge, unmetered traffic options, one-click application templates, and an entry price around $2.80 a month that most Western hosts can't approach for a Windows machine.

👉 [Compare the plan specs and pick a node on Rainyun's order page](https://bit.ly/RaiNyun)

## Five details that make a cheap Windows VPS expensive

1. **Evaluation expiry.** Covered above, and it's the big one. Day 181 means an hourly shutdown until you license the machine.
2. **You may not be able to change the operating system.** IONOS states outright that a Windows VPS can't be switched to Linux after ordering, and that a new order is required. Windows plans are commonly locked this way because the licence is attached at provisioning. Ask before you buy if there's any chance you'll want Linux later.
3. **"Unlimited traffic" often has geography attached.** OVHcloud's VPS plans include unlimited traffic except in its Asia-Pacific datacentres, and its Local Zones don't support Windows at all. Read the asterisk.
4. **A low headline price may be a two-year price.** Contabo lists its cheapest Windows VPS rate as valid for the first 24 months, which tells you plainly that month 25 costs more. Budget for the renewal number, not the signup number.
5. **Add-ons move the monthly total.** Atlantic.Net charges $3.65 a month for an extra IPv4 address and prices daily backup at 20% of the server price with a $1 minimum, bills $0.02 per GB for outbound traffic beyond the free allowance.

## How the entry prices compare

| Provider | Windows entry price | Licence handling | Notes |
| --- | --- | --- | --- |
| Rainyun | ¥20/month (~$2.80), 1 core / 1 GB / 30 GB SSD | Windows Server image selectable at order; confirm bundled vs evaluation | CN nodes plus Los Angeles; Alipay and WeChat Pay |
| MassiveGRID | $3.99/month, 1 vCPU / 1 GB / 32 GB, shared cores | 180-day evaluation, or $6.31 per vCPU | Extra RDP user $8.90/month; dedicated-core Windows VPS from $18.84 |
| Atlantic.Net | About $15/month | Licence included in the price | Linux VPS from $4; 8 datacentre regions |
| OVHcloud | VPS-2 from US$8.50/month ex GST, 4 vCore / 8 GB / 75 GB NVMe | Windows Server pre-installed | 99.9% SLA; unlimited traffic excludes APAC datacentres |
| Contabo | Lowest Windows rate marked as valid for the first 24 months | Windows Server 2016 to 2025 images | Unmanaged; 9 regions |

These aren't a price ranking. A shared-core evaluation install, a licensed dedicated-core machine and a two-year introductory rate are three different products, and lining them up by the first number on the page hides that.

## Which plan to order

One user on one Windows application: the ¥20 entry plan, and don't let anyone talk you into more. Two or three people sharing a desktop, or a .NET site with a small database: the ¥39 mid plan with 4 GB is the comfortable floor. SQL Server with real query load, IIS with steady traffic, or more than three RDP users: price the RDS licences first, then look at the ¥55 and ¥108 plans, keeping in mind that shared cores have a ceiling under sustained load.

Before you pay, confirm two things on the order screen: whether the Windows Server image includes a licence or is an evaluation build, and whether you can reinstall with a different operating system later. Both answers change what the server costs you over a year far more than the difference between ¥20 and ¥39.

👉 [Start with Rainyun's Windows VPS plans and choose the configuration that fits](https://bit.ly/RaiNyun)
