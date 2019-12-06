---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 8f4a895ad66dea3063a32f785e4c521196266978
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835730"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="58feb-104">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="58feb-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="58feb-105">Bu makalede, .NET Core çalışma zamanının nasıl indirileceği ve kurulacağı hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="58feb-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="58feb-106">.NET Core çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58feb-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="58feb-107">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="58feb-107">Install with an installer</span></span>

<span data-ttu-id="58feb-108">Windows, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="58feb-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="58feb-109">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="58feb-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="58feb-110">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="58feb-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="58feb-111">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="58feb-111">Install with an installer</span></span>

<span data-ttu-id="58feb-112">macOS, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="58feb-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="58feb-113">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="58feb-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="58feb-114">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="58feb-114">Install with a package manager</span></span>

<span data-ttu-id="58feb-115">.NET Core çalışma zamanını birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58feb-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="58feb-116">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="58feb-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="58feb-117">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="58feb-117">Install with PowerShell automation</span></span>

<span data-ttu-id="58feb-118">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58feb-118">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="58feb-119">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58feb-119">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="58feb-120">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="58feb-120">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="58feb-121">`Channel` anahtarını belirterek belirli bir yayını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58feb-121">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="58feb-122">Çalışma zamanı yüklemek için `Runtime` anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58feb-122">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="58feb-123">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="58feb-123">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="58feb-124">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="58feb-124">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="58feb-125">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="58feb-125">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="58feb-126">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="58feb-126">Install with bash automation</span></span>

<span data-ttu-id="58feb-127">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58feb-127">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="58feb-128">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58feb-128">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="58feb-129">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="58feb-129">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="58feb-130">`current` anahtarını belirterek belirli bir yayını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58feb-130">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="58feb-131">Çalışma zamanı yüklemek için `runtime` anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58feb-131">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="58feb-132">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="58feb-132">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="58feb-133">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="58feb-133">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="58feb-134">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="58feb-134">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="58feb-135">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="58feb-135">All .NET Core downloads</span></span>

<span data-ttu-id="58feb-136">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58feb-136">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="58feb-137">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="58feb-137">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="58feb-138">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="58feb-138">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="58feb-139">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="58feb-139">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="58feb-140">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="58feb-140">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="58feb-141">Docker</span><span class="sxs-lookup"><span data-stu-id="58feb-141">Docker</span></span>

<span data-ttu-id="58feb-142">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="58feb-142">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="58feb-143">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="58feb-143">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="58feb-144">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="58feb-144">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="58feb-145">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="58feb-145">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="58feb-146">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="58feb-146">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="58feb-147">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="58feb-147">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="58feb-148">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="58feb-148">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="58feb-149">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="58feb-149">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="58feb-150">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="58feb-150">Next steps</span></span>

- <span data-ttu-id="58feb-151">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="58feb-151">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
