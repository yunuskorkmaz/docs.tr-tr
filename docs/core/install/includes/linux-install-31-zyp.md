---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603015"
---

### <a name="install-the-sdk"></a><span data-ttu-id="1db6e-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="1db6e-101">Install the SDK</span></span>

<span data-ttu-id="1db6e-102">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1db6e-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="1db6e-103">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1db6e-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="1db6e-104">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="1db6e-104">Install the runtime</span></span>

<span data-ttu-id="1db6e-105">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1db6e-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="1db6e-106">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="1db6e-106">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="1db6e-107">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1db6e-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="1db6e-108">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: `aspnetcore-runtime-2.1` Yukarıdaki komutu ile değiştirin `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="1db6e-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
