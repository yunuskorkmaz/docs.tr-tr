---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d3f7083366e2019d01884b5dff6e60d05ed565dd
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768293"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="0fddf-104">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="0fddf-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="0fddf-105">Bu makalede, .NET Core çalışma zamanının nasıl indirileceği ve kurulacağı hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0fddf-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="0fddf-106">.NET Core çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0fddf-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="0fddf-107">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="0fddf-107">Install with an installer</span></span>

<span data-ttu-id="0fddf-108">Windows, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0fddf-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="0fddf-109">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="0fddf-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="0fddf-110">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="0fddf-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="0fddf-111">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="0fddf-111">Install with an installer</span></span>

<span data-ttu-id="0fddf-112">macOS, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0fddf-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="0fddf-113">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="0fddf-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="0fddf-114">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="0fddf-114">Download and manually install</span></span>

<span data-ttu-id="0fddf-115">.NET Core için macOS yükleyicilerine alternatif olarak, çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fddf-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="0fddf-116">Çalışma zamanını yüklemek ve terminalde bulunan .NET Core CLI komutlarını etkinleştirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="0fddf-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="0fddf-117">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0fddf-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="0fddf-118">Çalışma zamanının dosyaya indirildiği varsayılır `~/Downloads/dotnet-runtime.pkg` .</span><span class="sxs-lookup"><span data-stu-id="0fddf-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="0fddf-119">Linux'ta yükleme</span><span class="sxs-lookup"><span data-stu-id="0fddf-119">Install on Linux</span></span>

<span data-ttu-id="0fddf-120">Bu makale yakında kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="0fddf-120">This article will be removed soon.</span></span> <span data-ttu-id="0fddf-121">Şu anda [Linux üzerinde .NET Core 'u](linux.md)yükleyerek değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-121">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="0fddf-122">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="0fddf-122">Install with PowerShell automation</span></span>

<span data-ttu-id="0fddf-123">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0fddf-123">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="0fddf-124">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fddf-124">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="0fddf-125">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-125">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="0fddf-126">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="0fddf-126">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="0fddf-127">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0fddf-127">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="0fddf-128">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="0fddf-128">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="0fddf-129">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="0fddf-129">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="0fddf-130">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-130">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="0fddf-131">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="0fddf-131">Download and manually install</span></span>

<span data-ttu-id="0fddf-132">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="0fddf-132">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="0fddf-133">Daha sonra, örneğin, yüklemek için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="0fddf-133">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="0fddf-134">Son olarak, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="0fddf-134">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="0fddf-135">Varsayılan olarak, .NET Core CLI komutları ve uygulamalar .NET Core 'u bu şekilde kullanmaz ve açıkça kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-135">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="0fddf-136">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0fddf-136">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="0fddf-137">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fddf-137">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="0fddf-138">Bu ortam değişkenleri ayarlansa bile, .NET Core uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yüklemesi konumunu yine de dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="0fddf-138">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="0fddf-139">Varsayılan `C:\Program Files\dotnet` olarak, yükleyicilerin kullanması genellikle.</span><span class="sxs-lookup"><span data-stu-id="0fddf-139">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="0fddf-140">Çalışma zamanına yalnızca bu ortam değişkenini de ayarlayarak özel bir yüklemede kullanmak üzere talimat verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0fddf-140">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="0fddf-141">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="0fddf-141">Install with bash automation</span></span>

<span data-ttu-id="0fddf-142">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0fddf-142">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="0fddf-143">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fddf-143">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="0fddf-144">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-144">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="0fddf-145">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `current` .</span><span class="sxs-lookup"><span data-stu-id="0fddf-145">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="0fddf-146">`runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0fddf-146">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="0fddf-147">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="0fddf-147">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="0fddf-148">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="0fddf-148">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="0fddf-149">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-149">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="0fddf-150">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="0fddf-150">All .NET Core downloads</span></span>

<span data-ttu-id="0fddf-151">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0fddf-151">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="0fddf-152">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="0fddf-152">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="0fddf-153">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="0fddf-153">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="0fddf-154">Docker</span><span class="sxs-lookup"><span data-stu-id="0fddf-154">Docker</span></span>

<span data-ttu-id="0fddf-155">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fddf-155">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="0fddf-156">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="0fddf-156">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="0fddf-157">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-157">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="0fddf-158">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-158">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="0fddf-159">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0fddf-159">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="0fddf-160">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fddf-160">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="0fddf-161">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fddf-161">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="0fddf-162">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="0fddf-162">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0fddf-163">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0fddf-163">Next steps</span></span>

- <span data-ttu-id="0fddf-164">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="0fddf-164">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
