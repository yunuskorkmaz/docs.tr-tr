---
ms.openlocfilehash: b8a1454dba1651911563557557cfddc38de24375
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135842"
---

### <a name="install-the-sdk"></a><span data-ttu-id="88282-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="88282-101">Install the SDK</span></span>

<span data-ttu-id="88282-102">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="88282-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="88282-103">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="88282-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="88282-104">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="88282-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="88282-105">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="88282-105">Install the runtime</span></span>

<span data-ttu-id="88282-106">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="88282-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="88282-107">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="88282-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="88282-108">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="88282-108">In your terminal, run the following commands.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

<span data-ttu-id="88282-109">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanını yükleyebilirsiniz: `aspnetcore-runtime-2.1` ile önceki komutta değiştirin `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="88282-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```
