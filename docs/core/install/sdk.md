---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core SDK yüklemesi
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamaları geliştirmek için gereken bağımlılıkları bulun.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 0aa323533dd9136372c2bbc330c9c3056fdf428c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157577"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="9e636-104">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="9e636-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="9e636-105">Bu makalede, .NET Core SDK nasıl yükleneceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="9e636-106">.NET Core SDK .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e636-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="9e636-107">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9e636-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="9e636-108">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9e636-108">Install with an installer</span></span>

<span data-ttu-id="9e636-109">Windows, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9e636-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9e636-110">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="9e636-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9e636-111">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="9e636-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="9e636-112">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9e636-112">Install with an installer</span></span>

<span data-ttu-id="9e636-113">macOS, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9e636-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9e636-114">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="9e636-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="9e636-115">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9e636-115">Download and manually install</span></span>

<span data-ttu-id="9e636-116">.NET Core için macOS yükleyicilerine alternatif olarak SDK 'yı indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="9e636-117">SDK 'Yı ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="9e636-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9e636-118">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e636-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="9e636-119">Çalışma zamanının `~/Downloads/dotnet-sdk.pkg` dosyasına indirildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9e636-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="9e636-120">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="9e636-120">Install with a package manager</span></span>

<span data-ttu-id="9e636-121">.NET Core SDK birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="9e636-122">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="9e636-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="9e636-123">Paket Yöneticisi ile yükleme yalnızca x64 mimarisinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9e636-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="9e636-124">ARM gibi farklı bir mimariye sahip .NET Core SDK yüklüyorsanız, aşağıdaki [indirme ve el ile yükleme](#download-and-manually-install) yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="9e636-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="9e636-125">Desteklenen mimariler hakkında daha fazla bilgi için bkz. [.NET Core Dependencies ve Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="9e636-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9e636-126">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9e636-126">Download and manually install</span></span>

<span data-ttu-id="9e636-127">SDK 'Yı ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="9e636-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9e636-128">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e636-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="9e636-129">Yukarıdaki `export` komutları yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9e636-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="9e636-130">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="9e636-131">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="9e636-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="9e636-132">Örnek:</span><span class="sxs-lookup"><span data-stu-id="9e636-132">For example:</span></span>
>
> - <span data-ttu-id="9e636-133">**Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="9e636-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="9e636-134">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="9e636-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="9e636-135">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="9e636-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="9e636-136">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e636-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="9e636-137">`PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e636-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="9e636-138">Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e636-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="9e636-139">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="9e636-139">Install with Visual Studio</span></span>

<span data-ttu-id="9e636-140">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e636-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="9e636-141">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="9e636-141">.NET Core SDK version</span></span> | <span data-ttu-id="9e636-142">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="9e636-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="9e636-143">3.1</span><span class="sxs-lookup"><span data-stu-id="9e636-143">3.1</span></span>                   | <span data-ttu-id="9e636-144">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9e636-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="9e636-145">3.0</span><span class="sxs-lookup"><span data-stu-id="9e636-145">3.0</span></span>                   | <span data-ttu-id="9e636-146">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9e636-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="9e636-147">2.2</span><span class="sxs-lookup"><span data-stu-id="9e636-147">2.2</span></span>                   | <span data-ttu-id="9e636-148">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9e636-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="9e636-149">2.1</span><span class="sxs-lookup"><span data-stu-id="9e636-149">2.1</span></span>                   | <span data-ttu-id="9e636-150">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="9e636-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="9e636-151">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="9e636-152">Visual Studio’yu açın.</span><span class="sxs-lookup"><span data-stu-id="9e636-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="9e636-153">**Microsoft Visual Studio hakkında** **Yardım** > seçin.</span><span class="sxs-lookup"><span data-stu-id="9e636-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="9e636-154">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="9e636-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="9e636-155">Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9e636-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="9e636-156">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="9e636-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="9e636-157">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="9e636-157">Select a workload</span></span>

<span data-ttu-id="9e636-158">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="9e636-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="9e636-159">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9e636-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="9e636-160">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9e636-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9e636-161">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9e636-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9e636-162">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="9e636-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="9e636-163">[.NET Core iş yüküne sahip Windows Visual Studio 2019 ![](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9e636-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9e636-164">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9e636-164">Download and manually install</span></span>

<span data-ttu-id="9e636-165">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="9e636-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9e636-166">Ardından, yüklemek için bir dizin oluşturun, örneğin `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="9e636-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="9e636-167">Son olarak, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="9e636-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="9e636-168">Varsayılan olarak, .NET Core CLI komutları ve uygulamalar .NET Core 'u bu şekilde kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="9e636-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="9e636-169">Açıkça kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e636-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="9e636-170">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9e636-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="9e636-171">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="9e636-172">Bu ortam değişkenleri ayarlansa bile, .NET Core uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yüklemesi konumunu yine de dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="9e636-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="9e636-173">Varsayılan değer genellikle yükleyicilerin kullanacağı `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="9e636-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="9e636-174">Çalışma zamanına yalnızca bu ortam değişkenini de ayarlayarak özel bir yüklemede kullanmak üzere talimat verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e636-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="9e636-175">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="9e636-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="9e636-176">**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9e636-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="9e636-177">MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="9e636-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="9e636-178">En son sürüm olan .NET Core 3,1 için Mac için Visual Studio 8,4 Preview ' i kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e636-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="9e636-179">[.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019 ![](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9e636-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="9e636-180">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="9e636-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="9e636-181">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="9e636-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="9e636-182">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e636-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9e636-183">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="9e636-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="9e636-184">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="9e636-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="9e636-185">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="9e636-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="9e636-186">[Uzantıyı Visual Studio Code marketi 'Nden yüklersiniz. C# ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)</span><span class="sxs-lookup"><span data-stu-id="9e636-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="9e636-187">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="9e636-187">Install with PowerShell automation</span></span>

<span data-ttu-id="9e636-188">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e636-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9e636-189">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9e636-190">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e636-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9e636-191">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e636-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="9e636-192">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="9e636-192">Install with bash automation</span></span>

<span data-ttu-id="9e636-193">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e636-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9e636-194">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e636-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9e636-195">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e636-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9e636-196">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e636-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="9e636-197">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="9e636-197">All .NET Core downloads</span></span>

<span data-ttu-id="9e636-198">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e636-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="9e636-199">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="9e636-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9e636-200">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="9e636-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="9e636-201">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="9e636-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="9e636-202">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="9e636-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="9e636-203">Docker</span><span class="sxs-lookup"><span data-stu-id="9e636-203">Docker</span></span>

<span data-ttu-id="9e636-204">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e636-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="9e636-205">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e636-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="9e636-206">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e636-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="9e636-207">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="9e636-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="9e636-208">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9e636-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="9e636-209">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e636-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="9e636-210">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e636-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="9e636-211">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="9e636-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e636-212">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9e636-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="9e636-213">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9e636-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="9e636-214">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9e636-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9e636-215">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="9e636-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="9e636-216">[MacOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="9e636-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="9e636-217">[Öğretici: macOS 'u kullanmaya](../tutorials/using-on-mac-vs.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="9e636-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="9e636-218">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9e636-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9e636-219">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="9e636-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="9e636-220">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9e636-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9e636-221">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="9e636-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
