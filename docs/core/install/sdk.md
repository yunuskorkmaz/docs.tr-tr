---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core SDK yüklemesi
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamaları geliştirmek için gereken bağımlılıkları bulun.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 4a6c8b27812e9f60e52132169dda0464c24abcc2
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740573"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="1f4e6-104">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="1f4e6-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="1f4e6-105">Bu makalede, .NET Core SDK nasıl yükleneceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="1f4e6-106">.NET Core SDK .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="1f4e6-107">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="1f4e6-108">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="1f4e6-108">Install with an installer</span></span>

<span data-ttu-id="1f4e6-109">Windows, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1f4e6-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="1f4e6-110">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="1f4e6-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="1f4e6-111">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="1f4e6-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="1f4e6-112">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="1f4e6-112">Install with an installer</span></span>

<span data-ttu-id="1f4e6-113">macOS, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1f4e6-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="1f4e6-114">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="1f4e6-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="1f4e6-115">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1f4e6-115">Install with a package manager</span></span>

<span data-ttu-id="1f4e6-116">.NET Core SDK birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="1f4e6-117">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="1f4e6-118">Paket Yöneticisi ile yükleme yalnızca x64 mimarisinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-118">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="1f4e6-119">ARM gibi farklı bir mimariye sahip .NET Core SDK yüklüyorsanız, aşağıdaki [indirme ve el ile yükleme](#download-and-manually-install) yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-119">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="1f4e6-120">Desteklenen mimariler hakkında daha fazla bilgi için bkz. [.NET Core Dependencies ve Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-120">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="1f4e6-121">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="1f4e6-121">Download and manually install</span></span>

<span data-ttu-id="1f4e6-122">SDK 'Yı ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="1f4e6-122">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="1f4e6-123">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-123">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="1f4e6-124">Yukarıdaki `export` komutları yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-124">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="1f4e6-125">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-125">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="1f4e6-126">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-126">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="1f4e6-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1f4e6-127">For example:</span></span>
>
> - <span data-ttu-id="1f4e6-128">**Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="1f4e6-128">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="1f4e6-129">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="1f4e6-129">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="1f4e6-130">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="1f4e6-130">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="1f4e6-131">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-131">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="1f4e6-132">`PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-132">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="1f4e6-133">Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-133">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="1f4e6-134">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="1f4e6-134">Install with Visual Studio</span></span>

<span data-ttu-id="1f4e6-135">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-135">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="1f4e6-136">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="1f4e6-136">.NET Core SDK version</span></span> | <span data-ttu-id="1f4e6-137">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="1f4e6-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="1f4e6-138">3.1</span><span class="sxs-lookup"><span data-stu-id="1f4e6-138">3.1</span></span>                   | <span data-ttu-id="1f4e6-139">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-139">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="1f4e6-140">3.0</span><span class="sxs-lookup"><span data-stu-id="1f4e6-140">3.0</span></span>                   | <span data-ttu-id="1f4e6-141">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-141">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="1f4e6-142">2.2</span><span class="sxs-lookup"><span data-stu-id="1f4e6-142">2.2</span></span>                   | <span data-ttu-id="1f4e6-143">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-143">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="1f4e6-144">2.1</span><span class="sxs-lookup"><span data-stu-id="1f4e6-144">2.1</span></span>                   | <span data-ttu-id="1f4e6-145">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-145">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="1f4e6-146">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-146">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="1f4e6-147">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-147">Open Visual Studio.</span></span>
01. <span data-ttu-id="1f4e6-148">**Microsoft Visual Studio hakkında** **Yardım** > seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-148">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="1f4e6-149">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-149">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="1f4e6-150">Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-150">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="1f4e6-151">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-151">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="1f4e6-152">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="1f4e6-152">Select a workload</span></span>

<span data-ttu-id="1f4e6-153">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="1f4e6-153">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="1f4e6-154">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-154">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="1f4e6-155">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-155">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="1f4e6-156">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-156">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="1f4e6-157">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-157">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="1f4e6-158">[.NET Core iş yüküne sahip Windows Visual Studio 2019 ![](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="1f4e6-158">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="1f4e6-159">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="1f4e6-159">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="1f4e6-160">**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-160">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="1f4e6-161">MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-161">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="1f4e6-162">En son sürüm olan .NET Core 3,1 için Mac için Visual Studio 8,4 Preview ' i kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-162">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="1f4e6-163">[.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019 ![](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="1f4e6-163">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="1f4e6-164">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="1f4e6-164">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="1f4e6-165">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-165">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="1f4e6-166">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-166">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="1f4e6-167">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-167">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="1f4e6-168">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-168">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="1f4e6-169">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-169">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="1f4e6-170">[Uzantıyı Visual Studio Code marketi 'Nden yüklersiniz. C# ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)</span><span class="sxs-lookup"><span data-stu-id="1f4e6-170">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="1f4e6-171">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="1f4e6-171">Install with PowerShell automation</span></span>

<span data-ttu-id="1f4e6-172">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-172">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="1f4e6-173">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-173">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="1f4e6-174">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-174">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="1f4e6-175">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-175">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="1f4e6-176">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="1f4e6-176">Install with bash automation</span></span>

<span data-ttu-id="1f4e6-177">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-177">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="1f4e6-178">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-178">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="1f4e6-179">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-179">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="1f4e6-180">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-180">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="1f4e6-181">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="1f4e6-181">All .NET Core downloads</span></span>

<span data-ttu-id="1f4e6-182">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1f4e6-182">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="1f4e6-183">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="1f4e6-183">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="1f4e6-184">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="1f4e6-184">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="1f4e6-185">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="1f4e6-185">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="1f4e6-186">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="1f4e6-186">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="1f4e6-187">Docker</span><span class="sxs-lookup"><span data-stu-id="1f4e6-187">Docker</span></span>

<span data-ttu-id="1f4e6-188">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-188">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="1f4e6-189">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-189">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="1f4e6-190">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-190">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="1f4e6-191">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-191">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="1f4e6-192">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-192">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="1f4e6-193">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-193">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="1f4e6-194">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-194">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="1f4e6-195">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-195">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f4e6-196">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1f4e6-196">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="1f4e6-197">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-197">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="1f4e6-198">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-198">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="1f4e6-199">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-199">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="1f4e6-200">[Öğretici: macOS 'u kullanmaya](../tutorials/using-on-mac-vs.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="1f4e6-201">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="1f4e6-202">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="1f4e6-203">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e6-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="1f4e6-204">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="1f4e6-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
