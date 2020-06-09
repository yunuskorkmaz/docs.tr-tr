---
ms.openlocfilehash: 9ba55c45dc8087c2f7766e5cad32dae97784ffd0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603029"
---

### <a name="install-the-sdk"></a><span data-ttu-id="04b00-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="04b00-101">Install the SDK</span></span>

<span data-ttu-id="04b00-102">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="04b00-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="04b00-103">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="04b00-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="04b00-104">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="04b00-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="04b00-105">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="04b00-105">Install the runtime</span></span>

<span data-ttu-id="04b00-106">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="04b00-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="04b00-107">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="04b00-107">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="04b00-108">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="04b00-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

<span data-ttu-id="04b00-109">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: `aspnetcore-runtime-3.1` Yukarıdaki komutu ile değiştirin `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="04b00-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```
