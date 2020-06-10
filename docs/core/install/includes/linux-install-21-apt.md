---
ms.openlocfilehash: 164d7a8277cf985735b959c73eb87391944e795b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602903"
---

### <a name="install-the-sdk"></a><span data-ttu-id="3dd49-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="3dd49-101">Install the SDK</span></span>

<span data-ttu-id="3dd49-102">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3dd49-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="3dd49-103">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3dd49-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="3dd49-104">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3dd49-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="3dd49-105">**DotNet-SDK-2,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.</span><span class="sxs-lookup"><span data-stu-id="3dd49-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-2.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="3dd49-106">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="3dd49-106">Install the runtime</span></span>

<span data-ttu-id="3dd49-107">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3dd49-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="3dd49-108">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="3dd49-108">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="3dd49-109">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3dd49-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="3dd49-110">Bir hata iletisi alırsanız, **aspnetcore-Runtime-2,1 paketini bulamazsanız**, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.</span><span class="sxs-lookup"><span data-stu-id="3dd49-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-2.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="3dd49-111">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: `aspnetcore-runtime-2.1` Yukarıdaki komutu ile değiştirin `dotnet-runtime-2.1` .</span><span class="sxs-lookup"><span data-stu-id="3dd49-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the command above with `dotnet-runtime-2.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
