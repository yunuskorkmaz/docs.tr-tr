---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ba50eb222d9eab6bffbb8ebfdf0ecf47951ce719
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543527"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="6d9d6-104">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="6d9d6-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="6d9d6-105">Bu makalede, .NET Core çalışma zamanının nasıl indirileceği ve kurulacağı hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="6d9d6-106">.NET Core çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="6d9d6-107">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="6d9d6-107">Install with an installer</span></span>

<span data-ttu-id="6d9d6-108">Windows, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6d9d6-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="6d9d6-109">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="6d9d6-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="6d9d6-110">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="6d9d6-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="6d9d6-111">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="6d9d6-111">Install with an installer</span></span>

<span data-ttu-id="6d9d6-112">macOS, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6d9d6-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="6d9d6-113">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="6d9d6-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="6d9d6-114">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="6d9d6-114">Install with a package manager</span></span>

<span data-ttu-id="6d9d6-115">.NET Core çalışma zamanını birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="6d9d6-116">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="6d9d6-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="6d9d6-117">Paketi bir paket yöneticisi ile yüklemek yalnızca x64 mimarisinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-117">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="6d9d6-118">.NET Core çalışma zamanını ARM gibi farklı bir mimariye yüklüyorsanız, [indir ve el ile yükle](#download-and-manually-install) bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-118">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="6d9d6-119">Desteklenen mimariler hakkında daha fazla bilgi için bkz. [.NET Core Dependencies ve Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="6d9d6-119">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="6d9d6-120">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="6d9d6-120">Download and manually install</span></span>

<span data-ttu-id="6d9d6-121">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="6d9d6-121">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="6d9d6-122">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-122">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="6d9d6-123">Yukarıdaki `export` komutları yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-123">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="6d9d6-124">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-124">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="6d9d6-125">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-125">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="6d9d6-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6d9d6-126">For example:</span></span>
>
> - <span data-ttu-id="6d9d6-127">**Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="6d9d6-127">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="6d9d6-128">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="6d9d6-128">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="6d9d6-129">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="6d9d6-129">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="6d9d6-130">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-130">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="6d9d6-131">`PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-131">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="6d9d6-132">Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-132">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="6d9d6-133">Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-133">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="6d9d6-134">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="6d9d6-134">Install with PowerShell automation</span></span>

<span data-ttu-id="6d9d6-135">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-135">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="6d9d6-136">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-136">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6d9d6-137">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-137">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="6d9d6-138">`Channel` anahtarını belirterek belirli bir yayını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-138">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="6d9d6-139">Çalışma zamanı yüklemek için `Runtime` anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-139">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="6d9d6-140">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-140">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="6d9d6-141">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-141">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="6d9d6-142">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-142">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="6d9d6-143">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="6d9d6-143">Download and manually install</span></span>

<span data-ttu-id="6d9d6-144">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="6d9d6-144">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="6d9d6-145">Ardından, yüklemek için bir dizin oluşturun, örneğin `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-145">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="6d9d6-146">Son olarak, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-146">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="6d9d6-147">Varsayılan olarak, .NET Core CLI komutları ve uygulamalar .NET Core 'u bu şekilde kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-147">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="6d9d6-148">Açıkça kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-148">You have to explicitly choose to use it.</span></span> <span data-ttu-id="6d9d6-149">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6d9d6-149">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="6d9d6-150">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-150">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="6d9d6-151">Bu ortam değişkenleri ayarlansa bile, .NET Core uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yüklemesi konumunu yine de dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-151">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="6d9d6-152">Varsayılan değer genellikle yükleyicilerin kullanacağı `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-152">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="6d9d6-153">Çalışma zamanına yalnızca bu ortam değişkenini de ayarlayarak özel bir yüklemede kullanmak üzere talimat verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d9d6-153">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="6d9d6-154">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="6d9d6-154">Install with bash automation</span></span>

<span data-ttu-id="6d9d6-155">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="6d9d6-156">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-156">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6d9d6-157">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-157">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="6d9d6-158">`current` anahtarını belirterek belirli bir yayını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-158">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="6d9d6-159">Çalışma zamanı yüklemek için `runtime` anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-159">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="6d9d6-160">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-160">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="6d9d6-161">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-161">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="6d9d6-162">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-162">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="6d9d6-163">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="6d9d6-163">All .NET Core downloads</span></span>

<span data-ttu-id="6d9d6-164">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d9d6-164">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="6d9d6-165">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="6d9d6-165">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="6d9d6-166">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="6d9d6-166">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="6d9d6-167">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="6d9d6-167">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="6d9d6-168">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="6d9d6-168">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="6d9d6-169">Docker</span><span class="sxs-lookup"><span data-stu-id="6d9d6-169">Docker</span></span>

<span data-ttu-id="6d9d6-170">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-170">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="6d9d6-171">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-171">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="6d9d6-172">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-172">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="6d9d6-173">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-173">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="6d9d6-174">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-174">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="6d9d6-175">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-175">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="6d9d6-176">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-176">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="6d9d6-177">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="6d9d6-177">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d9d6-178">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6d9d6-178">Next steps</span></span>

- <span data-ttu-id="6d9d6-179">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="6d9d6-179">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
