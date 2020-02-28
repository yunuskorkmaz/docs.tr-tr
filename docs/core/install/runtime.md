---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a41bbdf5419585f06773583dbe82ab0d84ebaa4c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157642"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="aa9eb-104">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="aa9eb-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="aa9eb-105">Bu makalede, .NET Core çalışma zamanının nasıl indirileceği ve kurulacağı hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="aa9eb-106">.NET Core çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="aa9eb-107">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="aa9eb-107">Install with an installer</span></span>

<span data-ttu-id="aa9eb-108">Windows, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aa9eb-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="aa9eb-109">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="aa9eb-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="aa9eb-110">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="aa9eb-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="aa9eb-111">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="aa9eb-111">Install with an installer</span></span>

<span data-ttu-id="aa9eb-112">macOS, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aa9eb-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="aa9eb-113">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="aa9eb-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="aa9eb-114">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="aa9eb-114">Download and manually install</span></span>

<span data-ttu-id="aa9eb-115">.NET Core için macOS yükleyicilerine alternatif olarak, çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="aa9eb-116">Çalışma zamanını yüklemek ve terminalde bulunan .NET Core CLI komutlarını etkinleştirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="aa9eb-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="aa9eb-117">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="aa9eb-118">Çalışma zamanının `~/Downloads/dotnet-runtime.pkg` dosyasına indirildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="aa9eb-119">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="aa9eb-119">Install with a package manager</span></span>

<span data-ttu-id="aa9eb-120">.NET Core çalışma zamanını birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="aa9eb-121">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="aa9eb-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="aa9eb-122">Paketi bir paket yöneticisi ile yüklemek yalnızca x64 mimarisinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="aa9eb-123">.NET Core çalışma zamanını ARM gibi farklı bir mimariye yüklüyorsanız, [indir ve el ile yükle](#download-and-manually-install) bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="aa9eb-124">Desteklenen mimariler hakkında daha fazla bilgi için bkz. [.NET Core Dependencies ve Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="aa9eb-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="aa9eb-125">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="aa9eb-125">Download and manually install</span></span>

<span data-ttu-id="aa9eb-126">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="aa9eb-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="aa9eb-127">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="aa9eb-128">Yukarıdaki `export` komutları yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="aa9eb-129">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="aa9eb-130">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="aa9eb-131">Örnek:</span><span class="sxs-lookup"><span data-stu-id="aa9eb-131">For example:</span></span>
>
> - <span data-ttu-id="aa9eb-132">**Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="aa9eb-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="aa9eb-133">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="aa9eb-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="aa9eb-134">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="aa9eb-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="aa9eb-135">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="aa9eb-136">`PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="aa9eb-137">Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="aa9eb-138">Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="aa9eb-139">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="aa9eb-139">Install with PowerShell automation</span></span>

<span data-ttu-id="aa9eb-140">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="aa9eb-141">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="aa9eb-142">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="aa9eb-143">`Channel` anahtarını belirterek belirli bir yayını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="aa9eb-144">Çalışma zamanı yüklemek için `Runtime` anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="aa9eb-145">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="aa9eb-146">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="aa9eb-147">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="aa9eb-148">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="aa9eb-148">Download and manually install</span></span>

<span data-ttu-id="aa9eb-149">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="aa9eb-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="aa9eb-150">Ardından, yüklemek için bir dizin oluşturun, örneğin `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="aa9eb-151">Son olarak, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="aa9eb-152">Varsayılan olarak, .NET Core CLI komutları ve uygulamalar .NET Core 'u bu şekilde kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="aa9eb-153">Açıkça kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="aa9eb-154">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="aa9eb-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="aa9eb-155">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="aa9eb-156">Bu ortam değişkenleri ayarlansa bile, .NET Core uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yüklemesi konumunu yine de dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="aa9eb-157">Varsayılan değer genellikle yükleyicilerin kullanacağı `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="aa9eb-158">Çalışma zamanına yalnızca bu ortam değişkenini de ayarlayarak özel bir yüklemede kullanmak üzere talimat verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aa9eb-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="aa9eb-159">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="aa9eb-159">Install with bash automation</span></span>

<span data-ttu-id="aa9eb-160">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="aa9eb-161">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="aa9eb-162">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="aa9eb-163">`current` anahtarını belirterek belirli bir yayını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="aa9eb-164">Çalışma zamanı yüklemek için `runtime` anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="aa9eb-165">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="aa9eb-166">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="aa9eb-167">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="aa9eb-168">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="aa9eb-168">All .NET Core downloads</span></span>

<span data-ttu-id="aa9eb-169">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aa9eb-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="aa9eb-170">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="aa9eb-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="aa9eb-171">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="aa9eb-171">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="aa9eb-172">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="aa9eb-172">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="aa9eb-173">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="aa9eb-173">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="aa9eb-174">Docker</span><span class="sxs-lookup"><span data-stu-id="aa9eb-174">Docker</span></span>

<span data-ttu-id="aa9eb-175">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-175">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="aa9eb-176">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-176">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="aa9eb-177">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-177">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="aa9eb-178">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-178">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="aa9eb-179">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-179">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="aa9eb-180">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-180">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="aa9eb-181">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-181">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="aa9eb-182">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="aa9eb-182">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="aa9eb-183">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="aa9eb-183">Next steps</span></span>

- <span data-ttu-id="aa9eb-184">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="aa9eb-184">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
