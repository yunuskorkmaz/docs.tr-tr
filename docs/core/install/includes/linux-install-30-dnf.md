---
ms.openlocfilehash: f9ea0ee6402187365cec5cdced1617ee2ae66bed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603071"
---

### <a name="install-the-sdk"></a><span data-ttu-id="6514a-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="6514a-101">Install the SDK</span></span>

<span data-ttu-id="6514a-102">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6514a-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="6514a-103">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6514a-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="6514a-104">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6514a-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-3.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="6514a-105">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="6514a-105">Install the runtime</span></span>

<span data-ttu-id="6514a-106">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6514a-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="6514a-107">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="6514a-107">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="6514a-108">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6514a-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.0
```

<span data-ttu-id="6514a-109">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: `aspnetcore-runtime-3.0` Yukarıdaki komutu ile değiştirin `dotnet-runtime-3.0` .</span><span class="sxs-lookup"><span data-stu-id="6514a-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.0` in the command above with `dotnet-runtime-3.0`.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
```
