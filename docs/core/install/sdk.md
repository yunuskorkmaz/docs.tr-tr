---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core SDK yüklemesi
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamaları geliştirmek için gereken bağımlılıkları bulun.
author: adegeo
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a11d1eb3bae6affaa548407cbd68c166a30e99da
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324660"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="8c63c-104">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="8c63c-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="8c63c-105">Bu makalede, .NET Core SDK nasıl yükleneceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8c63c-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="8c63c-106">.NET Core SDK .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c63c-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="8c63c-107">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="8c63c-108">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="8c63c-108">Install with an installer</span></span>

<span data-ttu-id="8c63c-109">Windows, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8c63c-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="8c63c-110">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="8c63c-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="8c63c-111">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="8c63c-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="8c63c-112">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="8c63c-112">Install with an installer</span></span>

<span data-ttu-id="8c63c-113">macOS, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8c63c-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="8c63c-114">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="8c63c-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="8c63c-115">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="8c63c-115">Download and manually install</span></span>

<span data-ttu-id="8c63c-116">.NET Core için macOS yükleyicilerine alternatif olarak SDK 'yı indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c63c-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="8c63c-117">SDK 'Yı ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="8c63c-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="8c63c-118">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8c63c-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="8c63c-119">Çalışma zamanının dosyaya indirildiği varsayılır `~/Downloads/dotnet-sdk.pkg` .</span><span class="sxs-lookup"><span data-stu-id="8c63c-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="8c63c-120">Linux'ta yükleme</span><span class="sxs-lookup"><span data-stu-id="8c63c-120">Install on Linux</span></span>

<span data-ttu-id="8c63c-121">Bu makale yakında kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="8c63c-121">This article will be removed soon.</span></span> <span data-ttu-id="8c63c-122">Şu anda [Linux üzerinde .NET Core 'u](linux.md)yükleyerek değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-122">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="8c63c-123">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="8c63c-123">Install with Visual Studio</span></span>

<span data-ttu-id="8c63c-124">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c63c-124">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="8c63c-125">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="8c63c-125">.NET Core SDK version</span></span> | <span data-ttu-id="8c63c-126">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="8c63c-126">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="8c63c-127">3,1</span><span class="sxs-lookup"><span data-stu-id="8c63c-127">3.1</span></span>                   | <span data-ttu-id="8c63c-128">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="8c63c-128">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="8c63c-129">3.0</span><span class="sxs-lookup"><span data-stu-id="8c63c-129">3.0</span></span>                   | <span data-ttu-id="8c63c-130">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="8c63c-130">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="8c63c-131">2,2</span><span class="sxs-lookup"><span data-stu-id="8c63c-131">2.2</span></span>                   | <span data-ttu-id="8c63c-132">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="8c63c-132">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="8c63c-133">2.1</span><span class="sxs-lookup"><span data-stu-id="8c63c-133">2.1</span></span>                   | <span data-ttu-id="8c63c-134">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="8c63c-134">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="8c63c-135">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c63c-135">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="8c63c-136">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="8c63c-136">Open Visual Studio.</span></span>
01. <span data-ttu-id="8c63c-137">**Help**  >  **Microsoft Visual Studio hakkında**yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8c63c-137">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="8c63c-138">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="8c63c-138">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="8c63c-139">Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-139">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="8c63c-140">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="8c63c-140">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="8c63c-141">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="8c63c-141">Select a workload</span></span>

<span data-ttu-id="8c63c-142">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="8c63c-142">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="8c63c-143">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="8c63c-143">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="8c63c-144">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="8c63c-144">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="8c63c-145">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="8c63c-145">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="8c63c-146">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="8c63c-146">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="8c63c-147">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="8c63c-147">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="8c63c-148">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="8c63c-148">Download and manually install</span></span>

<span data-ttu-id="8c63c-149">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="8c63c-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="8c63c-150">Daha sonra, örneğin, yüklemek için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="8c63c-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="8c63c-151">Son olarak, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="8c63c-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="8c63c-152">Varsayılan olarak, .NET Core CLI komutları ve uygulamalar .NET Core 'u bu şekilde kullanmaz ve açıkça kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-152">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="8c63c-153">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8c63c-153">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="8c63c-154">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c63c-154">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="8c63c-155">Bu ortam değişkenleri ayarlansa bile, .NET Core uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yüklemesi konumunu yine de dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="8c63c-155">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="8c63c-156">Varsayılan `C:\Program Files\dotnet` olarak, yükleyicilerin kullanması genellikle.</span><span class="sxs-lookup"><span data-stu-id="8c63c-156">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="8c63c-157">Çalışma zamanına yalnızca bu ortam değişkenini de ayarlayarak özel bir yüklemede kullanmak üzere talimat verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c63c-157">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="8c63c-158">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="8c63c-158">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="8c63c-159">**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-159">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="8c63c-160">MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="8c63c-160">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="8c63c-161">En son sürüm olan .NET Core 3,1 için Mac için Visual Studio 8,4 Preview ' i kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-161">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="8c63c-162">[![.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="8c63c-162">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-windows,os-macos"

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="8c63c-163">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="8c63c-163">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="8c63c-164">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-164">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="8c63c-165">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-165">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="8c63c-166">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-166">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="8c63c-167">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="8c63c-167">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="8c63c-168">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8c63c-168">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="8c63c-169">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="8c63c-169">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="8c63c-170">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="8c63c-170">Install with PowerShell automation</span></span>

<span data-ttu-id="8c63c-171">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c63c-171">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="8c63c-172">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c63c-172">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="8c63c-173">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-173">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="8c63c-174">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8c63c-174">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="8c63c-175">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="8c63c-175">Install with bash automation</span></span>

<span data-ttu-id="8c63c-176">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c63c-176">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="8c63c-177">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c63c-177">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="8c63c-178">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-178">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="8c63c-179">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8c63c-179">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="8c63c-180">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="8c63c-180">All .NET Core downloads</span></span>

<span data-ttu-id="8c63c-181">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c63c-181">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="8c63c-182">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="8c63c-182">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="8c63c-183">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="8c63c-183">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="8c63c-184">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="8c63c-184">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="8c63c-185">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="8c63c-185">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="8c63c-186">Docker</span><span class="sxs-lookup"><span data-stu-id="8c63c-186">Docker</span></span>

<span data-ttu-id="8c63c-187">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c63c-187">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="8c63c-188">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c63c-188">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="8c63c-189">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-189">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="8c63c-190">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-190">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="8c63c-191">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8c63c-191">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="8c63c-192">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c63c-192">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="8c63c-193">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c63c-193">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="8c63c-194">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="8c63c-194">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8c63c-195">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8c63c-195">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="8c63c-196">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="8c63c-196">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="8c63c-197">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="8c63c-197">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="8c63c-198">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="8c63c-198">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="8c63c-199">[MacOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="8c63c-199">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="8c63c-200">[Öğretici: macOS 'u kullanmaya](../tutorials/using-on-mac-vs.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="8c63c-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="8c63c-201">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="8c63c-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="8c63c-202">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="8c63c-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="8c63c-203">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="8c63c-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="8c63c-204">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="8c63c-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
