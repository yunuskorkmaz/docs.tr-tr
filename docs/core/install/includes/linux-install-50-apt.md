---
ms.openlocfilehash: 87c7abf6a20dd8e9769f3b3b3cbe271d32fd62c3
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507006"
---

### <a name="install-the-sdk"></a><span data-ttu-id="6bcfa-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="6bcfa-101">Install the SDK</span></span>

<span data-ttu-id="6bcfa-102">.NET SDK, .NET ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="6bcfa-103">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="6bcfa-104">.NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6bcfa-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="6bcfa-105">**DotNet-SDK-5,0** ' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-5.0** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="6bcfa-106">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="6bcfa-106">Install the runtime</span></span>

<span data-ttu-id="6bcfa-107">ASP.NET Core çalışma zamanı, .NET ile yapılan ve çalışma zamanı sağlamayan uygulamaları çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-107">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="6bcfa-108">Aşağıdaki komutlar, .NET için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="6bcfa-109">Terminalinizde aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6bcfa-109">In your terminal, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="6bcfa-110">Bir hata iletisi alırsanız, **aspnetcore-Runtime-5,0 paketini bulamazsanız** , bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-5.0** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="6bcfa-111">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: `aspnetcore-runtime-5.0` önceki komutta ile değiştirin `dotnet-runtime-5.0` :</span><span class="sxs-lookup"><span data-stu-id="6bcfa-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo apt-get install -y dotnet-runtime-5.0
```
