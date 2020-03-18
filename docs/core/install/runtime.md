---
title: Windows, Linux ve macOS'a .NET Core çalışma süresini yükleme - .NET Core
description: .NET Core'u Windows, Linux ve macOS'a nasıl yükleyin öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları keşfedin.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399016"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="02975-104">.NET Çekirdek Çalışma Süresini Yükleyin</span><span class="sxs-lookup"><span data-stu-id="02975-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="02975-105">Bu makalede, .NET Core çalışma saatini nasıl indireceğinizi ve yükleyeceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="02975-106">.NET Core çalışma süresi , .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02975-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="02975-107">Yükleyiciyle yükleme</span><span class="sxs-lookup"><span data-stu-id="02975-107">Install with an installer</span></span>

<span data-ttu-id="02975-108">Windows'da .NET Core 3.1 çalışma süresini yüklemek için kullanılabilecek bağımsız yükleyiciler vardır:</span><span class="sxs-lookup"><span data-stu-id="02975-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="02975-109">x64 (64-bit) CPU'lar</span><span class="sxs-lookup"><span data-stu-id="02975-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="02975-110">x86 (32-bit) CPU'lar</span><span class="sxs-lookup"><span data-stu-id="02975-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="02975-111">Yükleyiciyle yükleme</span><span class="sxs-lookup"><span data-stu-id="02975-111">Install with an installer</span></span>

<span data-ttu-id="02975-112">macOS,.NET Core 3.1 çalışma süresini yüklemek için kullanılabilecek bağımsız yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="02975-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="02975-113">x64 (64-bit) CPU'lar</span><span class="sxs-lookup"><span data-stu-id="02975-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="02975-114">İndirin ve el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="02975-114">Download and manually install</span></span>

<span data-ttu-id="02975-115">.NET Core için macOS yükleyicilere alternatif olarak çalışma süresini indirebilir ve el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="02975-116">Çalışma süresini yüklemek ve terminalde bulunan .NET Core CLI komutlarını etkinleştirmek için önce bir .NET Core ikili sürümü [indirin.](#all-net-core-downloads)</span><span class="sxs-lookup"><span data-stu-id="02975-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="02975-117">Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02975-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="02975-118">Çalışma zamanının `~/Downloads/dotnet-runtime.pkg` dosyaya indirilmiş olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="02975-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="02975-119">Paket yöneticisiyle yükleme</span><span class="sxs-lookup"><span data-stu-id="02975-119">Install with a package manager</span></span>

<span data-ttu-id="02975-120">.NET Core Runtime'ı birçok ortak Linux paket yöneticisiyle birlikte yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="02975-121">Daha fazla bilgi için [Linux Package Manager - Install .NET Core](linux-package-managers.md)'a bakın.</span><span class="sxs-lookup"><span data-stu-id="02975-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="02975-122">Bir paket yöneticisi ile yükleme yalnızca x64 mimarisinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="02975-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="02975-123">.NET Core Runtime'ı ARM gibi farklı bir mimariyle yüklüyorsanız, İndir meyhanedeki yönergeleri izleyin [ve el ile yükleyin.](#download-and-manually-install)</span><span class="sxs-lookup"><span data-stu-id="02975-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="02975-124">Hangi mimarilerin desteklendirilip desteklendirildigini daha fazla bilgi için [.NET Core bağımlılıkları ve gereksinimleri](dependencies.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="02975-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="02975-125">İndirin ve el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="02975-125">Download and manually install</span></span>

<span data-ttu-id="02975-126">Çalışma süresini ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads)</span><span class="sxs-lookup"><span data-stu-id="02975-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="02975-127">Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02975-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="02975-128">Önceki `export` komutlar yalnızca çalıştırıldığı terminal oturumu için .NET Core CLI komutlarını kullanılabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="02975-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="02975-129">Komutları kalıcı olarak eklemek için kabuk profilinizi edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="02975-130">Linux için farklı kabukları bir dizi vardır ve her biri farklı bir profile sahiptir.</span><span class="sxs-lookup"><span data-stu-id="02975-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="02975-131">Örnek:</span><span class="sxs-lookup"><span data-stu-id="02975-131">For example:</span></span>
>
> - <span data-ttu-id="02975-132">**Bash Kabuk**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="02975-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="02975-133">**Korn Kabuk**: *~/.kshrc* veya *.profile*</span><span class="sxs-lookup"><span data-stu-id="02975-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="02975-134">**Z Kabuk**: *~/.zshrc* veya *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="02975-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="02975-135">Kabuğunuz için uygun kaynak dosyayı `:$HOME/dotnet` edin ve `PATH` varolan ifadenin sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02975-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="02975-136">Hiçbir `PATH` deyim dahil değilse, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02975-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="02975-137">Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02975-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="02975-138">Bu yaklaşım, farklı sürümleri ayrı konumlara yüklemenize ve hangi uygulamatarafından kullanılacağını açıkça seçmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="02975-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="02975-139">PowerShell otomasyonu ile yükleme</span><span class="sxs-lookup"><span data-stu-id="02975-139">Install with PowerShell automation</span></span>

<span data-ttu-id="02975-140">[Dotnet yükleme komut dosyaları,](../tools/dotnet-install-script.md) çalışma zamanının otomasyonu ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02975-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="02975-141">Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="02975-142">Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="02975-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="02975-143">`Channel` Anahtarı belirterek belirli bir sürüm seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="02975-144">Çalışma `Runtime` süresini yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02975-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="02975-145">Aksi takdirde, komut dosyası [SDK](sdk.md)yükler.</span><span class="sxs-lookup"><span data-stu-id="02975-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="02975-146">Yukarıdaki komut, maksimum uyumluluk için ASP.NET Core çalışma süresini yükler.</span><span class="sxs-lookup"><span data-stu-id="02975-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="02975-147">core ASP.NET çalışma süresi standart .NET Core çalışma süresini de içerir.</span><span class="sxs-lookup"><span data-stu-id="02975-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="02975-148">İndirin ve el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="02975-148">Download and manually install</span></span>

<span data-ttu-id="02975-149">Çalışma süresini ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads)</span><span class="sxs-lookup"><span data-stu-id="02975-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="02975-150">Ardından, yüklemek için bir dizin `%USERPROFILE%\dotnet`oluşturun, örneğin.</span><span class="sxs-lookup"><span data-stu-id="02975-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="02975-151">Son olarak, indirilen zip dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="02975-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="02975-152">Varsayılan olarak, .NET Core CLI komutları ve uygulamaları bu şekilde yüklenen .NET Core'u kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="02975-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="02975-153">Açıkça kullanmayı seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="02975-154">Bunu yapmak için, bir uygulamanın başlatıldıği ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="02975-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="02975-155">Bu yaklaşım, birden çok sürümü ayrı konumlara yüklemenize olanak tanır, ardından uygulamayı o konumu işaret eden ortam değişkenleri ile çalıştırarak uygulamanın hangi yükleme konumunu kullanması gerektiğini açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="02975-156">Bu ortam değişkenleri ayarlandığında bile,.NET Core, uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yükleme konumunu dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="02975-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="02975-157">Varsayılan genellikle `C:\Program Files\dotnet`, yükleyiciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="02975-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="02975-158">Çalışma zamanını yalnızca bu ortam değişkenini ayarlayarak özel yükleme konumunu kullanması için talimat verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="02975-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="02975-159">Bash otomasyonu ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="02975-159">Install with bash automation</span></span>

<span data-ttu-id="02975-160">[Dotnet yükleme komut dosyaları,](../tools/dotnet-install-script.md) çalışma zamanının otomasyonu ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02975-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="02975-161">Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="02975-162">Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="02975-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="02975-163">`current` Anahtarı belirterek belirli bir sürüm seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02975-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="02975-164">Çalışma `runtime` süresini yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02975-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="02975-165">Aksi takdirde, komut dosyası [SDK](sdk.md)yükler.</span><span class="sxs-lookup"><span data-stu-id="02975-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="02975-166">Yukarıdaki komut, maksimum uyumluluk için ASP.NET Core çalışma süresini yükler.</span><span class="sxs-lookup"><span data-stu-id="02975-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="02975-167">core ASP.NET çalışma süresi standart .NET Core çalışma süresini de içerir.</span><span class="sxs-lookup"><span data-stu-id="02975-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="02975-168">Tüm .NET Core indirmeleri</span><span class="sxs-lookup"><span data-stu-id="02975-168">All .NET Core downloads</span></span>

<span data-ttu-id="02975-169">.NET Core'u aşağıdaki bağlantılardan biriyle doğrudan indirip yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="02975-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="02975-170">.NET Core 3.1 indirme</span><span class="sxs-lookup"><span data-stu-id="02975-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="02975-171">.NET Core 2.1 indirme</span><span class="sxs-lookup"><span data-stu-id="02975-171">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="02975-172">Docker</span><span class="sxs-lookup"><span data-stu-id="02975-172">Docker</span></span>

<span data-ttu-id="02975-173">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için hafif bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="02975-173">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="02975-174">Aynı makinedeki kaplar sadece çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="02975-174">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="02975-175">.NET Core bir Docker konteynerinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="02975-175">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="02975-176">Resmi .NET Core Docker görüntüleri Microsoft Konteyner Kayıt Defteri'nde (MCR) yayınlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)keşfedilebilir.</span><span class="sxs-lookup"><span data-stu-id="02975-176">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="02975-177">Her depo, kullanabilirsiniz .NET (SDK veya Runtime) ve işletim sistemi farklı kombinasyonları için görüntüler içerir.</span><span class="sxs-lookup"><span data-stu-id="02975-177">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="02975-178">Microsoft, belirli senaryolar için özel leştirilmiş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="02975-178">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="02975-179">Örneğin, [ASP.NET Core deposu,](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde Core uygulamaları ASP.NET çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="02975-179">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="02975-180">Docker konteynerinde .NET Core kullanma hakkında daha fazla bilgi için [.NET ve Docker ve Örneklere Giriş'e](../docker/introduction.md) bakın. [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)</span><span class="sxs-lookup"><span data-stu-id="02975-180">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="02975-181">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="02975-181">Next steps</span></span>

- <span data-ttu-id="02975-182">[.NET Core'un zaten yüklü olup olmadığını nasıl kontrol edilir?](how-to-detect-installed-versions.md)</span><span class="sxs-lookup"><span data-stu-id="02975-182">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
