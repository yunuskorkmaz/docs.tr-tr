---
title: Windows, Linux ve macOS'a .NET Core SDK'yı yükleyin - .NET Core
description: .NET Core'u Windows, Linux ve macOS'a nasıl yükleyin öğrenin. .NET Core uygulamalarını geliştirmek için gereken bağımlılıkları keşfedin.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399009"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="9476a-104">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="9476a-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="9476a-105">Bu makalede, .NET Core SDK'yı nasıl yükleyeceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="9476a-106">.NET Core SDK ,NET Core uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9476a-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="9476a-107">.NET Core çalışma süresi her zaman SDK ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9476a-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="9476a-108">Yükleyiciyle yükleme</span><span class="sxs-lookup"><span data-stu-id="9476a-108">Install with an installer</span></span>

<span data-ttu-id="9476a-109">Windows'da .NET Core 3.1 SDK'yı yüklemek için kullanılabilecek bağımsız yükleyiciler vardır:</span><span class="sxs-lookup"><span data-stu-id="9476a-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9476a-110">x64 (64-bit) CPU'lar</span><span class="sxs-lookup"><span data-stu-id="9476a-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9476a-111">x86 (32-bit) CPU'lar</span><span class="sxs-lookup"><span data-stu-id="9476a-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="9476a-112">Yükleyiciyle yükleme</span><span class="sxs-lookup"><span data-stu-id="9476a-112">Install with an installer</span></span>

<span data-ttu-id="9476a-113">macOS,.NET Core 3.1 SDK'yı yüklemek için kullanılabilecek bağımsız yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9476a-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9476a-114">x64 (64-bit) CPU'lar</span><span class="sxs-lookup"><span data-stu-id="9476a-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="9476a-115">İndirin ve el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="9476a-115">Download and manually install</span></span>

<span data-ttu-id="9476a-116">.NET Core için macOS yükleyicilere alternatif olarak SDK'yı indirebilir ve el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="9476a-117">SDK'yı ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads)</span><span class="sxs-lookup"><span data-stu-id="9476a-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9476a-118">Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9476a-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="9476a-119">Çalışma zamanının `~/Downloads/dotnet-sdk.pkg` dosyaya indirilmiş olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9476a-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="9476a-120">Paket yöneticisiyle yükleme</span><span class="sxs-lookup"><span data-stu-id="9476a-120">Install with a package manager</span></span>

<span data-ttu-id="9476a-121">.NET Core SDK'yı birçok ortak Linux paket yöneticisiyle birlikte yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="9476a-122">Daha fazla bilgi için [Linux Package Manager - Install .NET Core](linux-package-managers.md)'a bakın.</span><span class="sxs-lookup"><span data-stu-id="9476a-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="9476a-123">Paket yöneticisiyle yükleme yalnızca x64 mimarisinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9476a-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="9476a-124">.NET Core SDK'yı ARM gibi farklı bir mimariyle yüklüyorsanız, [İndirme'yi](#download-and-manually-install) izleyin ve aşağıdaki talimatları el ile yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9476a-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="9476a-125">Hangi mimarilerin desteklendirilip desteklendirildigini daha fazla bilgi için [.NET Core bağımlılıkları ve gereksinimleri](dependencies.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9476a-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9476a-126">İndirin ve el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="9476a-126">Download and manually install</span></span>

<span data-ttu-id="9476a-127">SDK'yı ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads)</span><span class="sxs-lookup"><span data-stu-id="9476a-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9476a-128">Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9476a-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="9476a-129">Önceki `export` komutlar yalnızca çalıştırıldığı terminal oturumu için .NET Core CLI komutlarını kullanılabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="9476a-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="9476a-130">Komutları kalıcı olarak eklemek için kabuk profilinizi edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="9476a-131">Linux için farklı kabukları bir dizi vardır ve her biri farklı bir profile sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9476a-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="9476a-132">Örnek:</span><span class="sxs-lookup"><span data-stu-id="9476a-132">For example:</span></span>
>
> - <span data-ttu-id="9476a-133">**Bash Kabuk**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="9476a-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="9476a-134">**Korn Kabuk**: *~/.kshrc* veya *.profile*</span><span class="sxs-lookup"><span data-stu-id="9476a-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="9476a-135">**Z Kabuk**: *~/.zshrc* veya *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="9476a-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="9476a-136">Kabuğunuz için uygun kaynak dosyayı `:$HOME/dotnet` edin ve `PATH` varolan ifadenin sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9476a-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="9476a-137">Hiçbir `PATH` deyim dahil değilse, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9476a-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="9476a-138">Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9476a-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="9476a-139">Visual Studio ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="9476a-139">Install with Visual Studio</span></span>

<span data-ttu-id="9476a-140">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda Visual Studio'nun hedef .NET Core SDK sürümüne göre en az gerekli sürümünü açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9476a-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="9476a-141">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="9476a-141">.NET Core SDK version</span></span> | <span data-ttu-id="9476a-142">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="9476a-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="9476a-143">3.1</span><span class="sxs-lookup"><span data-stu-id="9476a-143">3.1</span></span>                   | <span data-ttu-id="9476a-144">Visual Studio 2019 sürüm 16.4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9476a-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="9476a-145">3,0</span><span class="sxs-lookup"><span data-stu-id="9476a-145">3.0</span></span>                   | <span data-ttu-id="9476a-146">Visual Studio 2019 sürüm 16.3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9476a-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="9476a-147">2,2</span><span class="sxs-lookup"><span data-stu-id="9476a-147">2.2</span></span>                   | <span data-ttu-id="9476a-148">Visual Studio 2017 sürümü 15.9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9476a-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="9476a-149">2.1</span><span class="sxs-lookup"><span data-stu-id="9476a-149">2.1</span></span>                   | <span data-ttu-id="9476a-150">Visual Studio 2017 sürüm 15.7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9476a-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="9476a-151">Visual Studio zaten yüklüyse, sürümünüzü aşağıdaki adımlarla kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="9476a-152">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="9476a-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="9476a-153">**Microsoft Visual Studio Hakkında** **Yardım'ı** > seçin.</span><span class="sxs-lookup"><span data-stu-id="9476a-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="9476a-154">**Hakkında** iletişim kutusundan sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="9476a-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="9476a-155">Visual Studio en son .NET Core SDK'yı ve çalışma süresini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9476a-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="9476a-156">[Karşıdan yükleme Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="9476a-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="9476a-157">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="9476a-157">Select a workload</span></span>

<span data-ttu-id="9476a-158">Visual Studio'yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulama türüne bağlı olarak aşağıdaki iş yüklerinden birini veya birkaçını seçin:</span><span class="sxs-lookup"><span data-stu-id="9476a-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="9476a-159">**Diğer Araç Kümeleri** **bölümündeki .NET Core çapraz platform geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9476a-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="9476a-160">**Web & Bulut** bölümündeki ASP.NET ve web **geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9476a-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9476a-161">**Web & Bulut** **bölümündeki Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9476a-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9476a-162">**Masaüstü & Mobil** bölümündeki **.NET masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9476a-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="9476a-163">[![.NET Core iş yükü ile Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9476a-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9476a-164">İndirin ve el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="9476a-164">Download and manually install</span></span>

<span data-ttu-id="9476a-165">Çalışma süresini ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads)</span><span class="sxs-lookup"><span data-stu-id="9476a-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9476a-166">Ardından, yüklemek için bir dizin `%USERPROFILE%\dotnet`oluşturun, örneğin.</span><span class="sxs-lookup"><span data-stu-id="9476a-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="9476a-167">Son olarak, indirilen zip dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="9476a-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="9476a-168">Varsayılan olarak, .NET Core CLI komutları ve uygulamaları bu şekilde yüklenen .NET Core'u kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="9476a-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="9476a-169">Açıkça kullanmayı seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="9476a-170">Bunu yapmak için, bir uygulamanın başlatıldıği ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9476a-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="9476a-171">Bu yaklaşım, birden çok sürümü ayrı konumlara yüklemenize olanak tanır, ardından uygulamayı o konumu işaret eden ortam değişkenleri ile çalıştırarak uygulamanın hangi yükleme konumunu kullanması gerektiğini açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="9476a-172">Bu ortam değişkenleri ayarlandığında bile,.NET Core, uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yükleme konumunu dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="9476a-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="9476a-173">Varsayılan genellikle `C:\Program Files\dotnet`, yükleyiciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="9476a-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="9476a-174">Çalışma zamanını yalnızca bu ortam değişkenini ayarlayarak özel yükleme konumunu kullanması için talimat verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9476a-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="9476a-175">Mac için Visual Studio ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="9476a-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="9476a-176">Mac için Visual **Studio,.NET Core** iş yükü seçildiğinde .NET Core SDK'yı yükler.</span><span class="sxs-lookup"><span data-stu-id="9476a-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="9476a-177">macOS'ta .NET Core geliştirmeye başlamak [için Mac için Visual Studio 2019'u yükle'ye](/visualstudio/mac/installation)bakın.</span><span class="sxs-lookup"><span data-stu-id="9476a-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="9476a-178">Son sürüm olan .NET Core 3.1 için Mac 8.4 Önizleme için Visual Studio'yu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9476a-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="9476a-179">[![macOS Visual Studio 2019 mac için .NET Core iş yükü özelliği ile Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9476a-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="9476a-180">Visual Studio Code'un yanına yükleyin</span><span class="sxs-lookup"><span data-stu-id="9476a-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="9476a-181">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="9476a-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="9476a-182">Visual Studio Code, Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9476a-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9476a-183">Visual Studio Code Visual Studio gibi otomatik bir .NET Core yükleyici ile gelmiyor olsa da, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="9476a-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="9476a-184">[Visual Studio Code'u indirin ve kurun.](https://code.visualstudio.com/Download)</span><span class="sxs-lookup"><span data-stu-id="9476a-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="9476a-185">[.NET Core SDK'yı indirin ve kurun.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="9476a-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="9476a-186">[Visual Studio Code pazar yerinden C# uzantısını yükleyin.](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)</span><span class="sxs-lookup"><span data-stu-id="9476a-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="9476a-187">PowerShell otomasyonu ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9476a-187">Install with PowerShell automation</span></span>

<span data-ttu-id="9476a-188">[Dotnet yükleme komut dosyaları](../tools/dotnet-install-script.md) Otomasyon ve SDK'nın yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9476a-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9476a-189">Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9476a-190">Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9476a-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9476a-191">.NET Core'un geçerli sürümüne yüklemek için komut dosyasını aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9476a-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="9476a-192">Bash otomasyonu ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="9476a-192">Install with bash automation</span></span>

<span data-ttu-id="9476a-193">[Dotnet yükleme komut dosyaları](../tools/dotnet-install-script.md) Otomasyon ve SDK'nın yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9476a-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9476a-194">Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9476a-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9476a-195">Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9476a-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9476a-196">.NET Core'un geçerli sürümüne yüklemek için komut dosyasını aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9476a-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="9476a-197">Tüm .NET Core indirmeleri</span><span class="sxs-lookup"><span data-stu-id="9476a-197">All .NET Core downloads</span></span>

<span data-ttu-id="9476a-198">.NET Core'u aşağıdaki bağlantılardan biriyle doğrudan indirip yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9476a-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="9476a-199">.NET Core 3.1 indirme</span><span class="sxs-lookup"><span data-stu-id="9476a-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9476a-200">.NET Core 3.0 indirme</span><span class="sxs-lookup"><span data-stu-id="9476a-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="9476a-201">.NET Core 2.2 indirme</span><span class="sxs-lookup"><span data-stu-id="9476a-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="9476a-202">.NET Core 2.1 indirme</span><span class="sxs-lookup"><span data-stu-id="9476a-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="9476a-203">Docker</span><span class="sxs-lookup"><span data-stu-id="9476a-203">Docker</span></span>

<span data-ttu-id="9476a-204">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için hafif bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9476a-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="9476a-205">Aynı makinedeki kaplar sadece çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9476a-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="9476a-206">.NET Core bir Docker konteynerinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9476a-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="9476a-207">Resmi .NET Core Docker görüntüleri Microsoft Konteyner Kayıt Defteri'nde (MCR) yayınlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)keşfedilebilir.</span><span class="sxs-lookup"><span data-stu-id="9476a-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="9476a-208">Her depo, kullanabilirsiniz .NET (SDK veya Runtime) ve işletim sistemi farklı kombinasyonları için görüntüler içerir.</span><span class="sxs-lookup"><span data-stu-id="9476a-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="9476a-209">Microsoft, belirli senaryolar için özel leştirilmiş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9476a-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="9476a-210">Örneğin, [ASP.NET Core deposu,](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde Core uygulamaları ASP.NET çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9476a-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="9476a-211">Docker konteynerinde .NET Core kullanma hakkında daha fazla bilgi için [.NET ve Docker ve Örneklere Giriş'e](../docker/introduction.md) bakın. [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)</span><span class="sxs-lookup"><span data-stu-id="9476a-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9476a-212">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9476a-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="9476a-213">[Öğretici: Merhaba Dünya öğretici](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9476a-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="9476a-214">[Öğretici: Visual Studio Code ile yeni bir uygulama oluşturun.](../tutorials/with-visual-studio-code.md)</span><span class="sxs-lookup"><span data-stu-id="9476a-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9476a-215">[Öğretici: Containerize bir .NET Core uygulaması](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9476a-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="9476a-216">[macOS Catalina noterizasyonu ile çalışma.](macos-notarization-issues.md)</span><span class="sxs-lookup"><span data-stu-id="9476a-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="9476a-217">[Öğretici: macOS'a başlayın.](../tutorials/using-on-mac-vs.md)</span><span class="sxs-lookup"><span data-stu-id="9476a-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="9476a-218">[Öğretici: Visual Studio Code ile yeni bir uygulama oluşturun.](../tutorials/with-visual-studio-code.md)</span><span class="sxs-lookup"><span data-stu-id="9476a-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9476a-219">[Öğretici: Containerize bir .NET Core uygulaması](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9476a-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="9476a-220">[Öğretici: Visual Studio Code ile yeni bir uygulama oluşturun.](../tutorials/with-visual-studio-code.md)</span><span class="sxs-lookup"><span data-stu-id="9476a-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9476a-221">[Öğretici: Containerize bir .NET Core uygulaması](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9476a-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
