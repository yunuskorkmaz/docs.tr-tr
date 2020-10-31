---
ms.openlocfilehash: 36f1ee26def82d426b6637ae96f382fc89791a2f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135940"
---

### <a name="install-the-sdk"></a><span data-ttu-id="e9b8d-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="e9b8d-101">Install the SDK</span></span>

<span data-ttu-id="e9b8d-102">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9b8d-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="e9b8d-103">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9b8d-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="e9b8d-104">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="e9b8d-104">Install the runtime</span></span>

<span data-ttu-id="e9b8d-105">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e9b8d-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="e9b8d-106">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="e9b8d-106">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="e9b8d-107">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9b8d-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="e9b8d-108">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanını yükleyebilirsiniz: `aspnetcore-runtime-2.1` ile önceki komutta değiştirin `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="e9b8d-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
