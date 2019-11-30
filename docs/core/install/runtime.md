---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: fbe9b9e12dc53d9ab6570299e03f2b0a8868fb53
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567267"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="12206-104">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="12206-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="12206-105">Bu makalede, .NET Core çalışma zamanının nasıl indirileceği ve kurulacağı hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="12206-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="12206-106">.NET Core çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12206-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="12206-107">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="12206-107">Install with an installer</span></span>

<span data-ttu-id="12206-108">Hem Windows hem de macOS .NET Core 3,0 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyiciler vardır.</span><span class="sxs-lookup"><span data-stu-id="12206-108">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 runtime.</span></span>

- <span data-ttu-id="12206-109">Windows [x64 (64-bit) cpu](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32 bit) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.0) 'lar</span><span class="sxs-lookup"><span data-stu-id="12206-109">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="12206-110">macOS [x64 (64-bit) CPU 'ları](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="12206-110">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="12206-111">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="12206-111">Install with a package manager</span></span>

<span data-ttu-id="12206-112">.NET Core çalışma zamanını birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12206-112">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="12206-113">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="12206-113">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="12206-114">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="12206-114">Install with PowerShell automation</span></span>

<span data-ttu-id="12206-115">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12206-115">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="12206-116">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12206-116">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="12206-117">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="12206-117">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="12206-118">Geçerli .NET Core sürümünü (3,0) yüklemek için betiği aşağıdaki anahtarla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="12206-118">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="12206-119">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="12206-119">Install with bash automation</span></span>

<span data-ttu-id="12206-120">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12206-120">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="12206-121">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12206-121">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="12206-122">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="12206-122">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="12206-123">Geçerli .NET Core sürümünü (3,0) yüklemek için betiği aşağıdaki anahtarla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="12206-123">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="12206-124">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="12206-124">All .NET Core downloads</span></span>

<span data-ttu-id="12206-125">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="12206-125">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="12206-126">.NET Core 3,1 Preview İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="12206-126">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="12206-127">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="12206-127">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="12206-128">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="12206-128">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="12206-129">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="12206-129">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="12206-130">Docker</span><span class="sxs-lookup"><span data-stu-id="12206-130">Docker</span></span>

<span data-ttu-id="12206-131">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="12206-131">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="12206-132">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="12206-132">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="12206-133">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="12206-133">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="12206-134">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="12206-134">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="12206-135">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="12206-135">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="12206-136">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="12206-136">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="12206-137">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="12206-137">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="12206-138">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="12206-138">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="12206-139">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="12206-139">Next steps</span></span>

- <span data-ttu-id="12206-140">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="12206-140">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
