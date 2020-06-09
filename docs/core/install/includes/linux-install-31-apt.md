---
ms.openlocfilehash: b6f2af7af77398d5e902aae995590b5dde4cf76a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602910"
---

### <a name="install-the-sdk"></a><span data-ttu-id="63bf7-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="63bf7-101">Install the SDK</span></span>

<span data-ttu-id="63bf7-102">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="63bf7-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="63bf7-103">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="63bf7-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="63bf7-104">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="63bf7-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="63bf7-105">**DotNet-SDK-3,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.</span><span class="sxs-lookup"><span data-stu-id="63bf7-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="63bf7-106">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="63bf7-106">Install the runtime</span></span>

<span data-ttu-id="63bf7-107">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="63bf7-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="63bf7-108">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="63bf7-108">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="63bf7-109">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="63bf7-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="63bf7-110">Bir hata iletisi alırsanız, **aspnetcore-Runtime-3,1 paketini bulamazsanız**, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.</span><span class="sxs-lookup"><span data-stu-id="63bf7-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="63bf7-111">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: `aspnetcore-runtime-3.1` Yukarıdaki komutu ile değiştirin `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="63bf7-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
