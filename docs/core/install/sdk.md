---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core SDK yüklemesi
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamaları geliştirmek için gereken bağımlılıkları bulun.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 5ac2d7897ee4c6707669e4f9104317aeb2e1f473
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835684"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="cad8e-104">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="cad8e-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="cad8e-105">Bu makalede, .NET Core SDK nasıl yükleneceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cad8e-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="cad8e-106">.NET Core SDK .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cad8e-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="cad8e-107">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="cad8e-108">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="cad8e-108">Install with an installer</span></span>

<span data-ttu-id="cad8e-109">Windows, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cad8e-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="cad8e-110">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="cad8e-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="cad8e-111">x86 (32 bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="cad8e-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="cad8e-112">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="cad8e-112">Install with an installer</span></span>

<span data-ttu-id="cad8e-113">macOS, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cad8e-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="cad8e-114">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="cad8e-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="cad8e-115">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="cad8e-115">Install with a package manager</span></span>

<span data-ttu-id="cad8e-116">.NET Core SDK birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cad8e-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="cad8e-117">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="cad8e-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="cad8e-118">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="cad8e-118">Download and manually install</span></span>

<span data-ttu-id="cad8e-119">SDK 'Yı ayıklamak ve komutları terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="cad8e-119">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="cad8e-120">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cad8e-120">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="cad8e-121">Yukarıdaki komutlar yalnızca .NET SDK komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-121">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="cad8e-122">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cad8e-122">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="cad8e-123">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="cad8e-123">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="cad8e-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cad8e-124">For example:</span></span>
>
> - <span data-ttu-id="cad8e-125">**Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="cad8e-125">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="cad8e-126">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="cad8e-126">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="cad8e-127">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="cad8e-127">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="cad8e-128">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cad8e-128">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="cad8e-129">`PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cad8e-129">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="cad8e-130">Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cad8e-130">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="cad8e-131">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="cad8e-131">Install with Visual Studio</span></span>

<span data-ttu-id="cad8e-132">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cad8e-132">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="cad8e-133">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="cad8e-133">.NET Core SDK version</span></span> | <span data-ttu-id="cad8e-134">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="cad8e-134">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="cad8e-135">3.1</span><span class="sxs-lookup"><span data-stu-id="cad8e-135">3.1</span></span>                   | <span data-ttu-id="cad8e-136">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cad8e-136">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="cad8e-137">3.0</span><span class="sxs-lookup"><span data-stu-id="cad8e-137">3.0</span></span>                   | <span data-ttu-id="cad8e-138">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cad8e-138">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="cad8e-139">2.2</span><span class="sxs-lookup"><span data-stu-id="cad8e-139">2.2</span></span>                   | <span data-ttu-id="cad8e-140">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cad8e-140">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="cad8e-141">2.1</span><span class="sxs-lookup"><span data-stu-id="cad8e-141">2.1</span></span>                   | <span data-ttu-id="cad8e-142">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cad8e-142">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="cad8e-143">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cad8e-143">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="cad8e-144">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="cad8e-144">Open Visual Studio.</span></span>
01. <span data-ttu-id="cad8e-145">**Microsoft Visual Studio hakkında** **Yardım** > seçin.</span><span class="sxs-lookup"><span data-stu-id="cad8e-145">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="cad8e-146">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="cad8e-146">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="cad8e-147">Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-147">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="cad8e-148">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="cad8e-148">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="cad8e-149">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="cad8e-149">Select a workload</span></span>

<span data-ttu-id="cad8e-150">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="cad8e-150">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="cad8e-151">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cad8e-151">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="cad8e-152">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cad8e-152">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="cad8e-153">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cad8e-153">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="cad8e-154">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cad8e-154">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="cad8e-155">[.NET Core iş yüküne sahip Windows Visual Studio 2019 ![](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cad8e-155">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="cad8e-156">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="cad8e-156">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="cad8e-157">**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-157">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="cad8e-158">MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="cad8e-158">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="cad8e-159">En son sürüm olan .NET Core 3,1 için Mac için Visual Studio 8,4 Preview ' i kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-159">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="cad8e-160">[.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019 ![](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cad8e-160">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="cad8e-161">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="cad8e-161">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="cad8e-162">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-162">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="cad8e-163">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-163">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="cad8e-164">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-164">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="cad8e-165">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="cad8e-165">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="cad8e-166">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="cad8e-166">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="cad8e-167">[Uzantıyı Visual Studio Code marketi 'Nden yüklersiniz. C# ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)</span><span class="sxs-lookup"><span data-stu-id="cad8e-167">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="cad8e-168">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="cad8e-168">Install with PowerShell automation</span></span>

<span data-ttu-id="cad8e-169">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cad8e-169">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="cad8e-170">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cad8e-170">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cad8e-171">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-171">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="cad8e-172">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cad8e-172">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="cad8e-173">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="cad8e-173">Install with bash automation</span></span>

<span data-ttu-id="cad8e-174">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cad8e-174">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="cad8e-175">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cad8e-175">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cad8e-176">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-176">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="cad8e-177">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cad8e-177">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="cad8e-178">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cad8e-178">All .NET Core downloads</span></span>

<span data-ttu-id="cad8e-179">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cad8e-179">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="cad8e-180">.NET Core 3,1 Preview İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cad8e-180">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="cad8e-181">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cad8e-181">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="cad8e-182">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cad8e-182">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="cad8e-183">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cad8e-183">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="cad8e-184">Docker</span><span class="sxs-lookup"><span data-stu-id="cad8e-184">Docker</span></span>

<span data-ttu-id="cad8e-185">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cad8e-185">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="cad8e-186">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="cad8e-186">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="cad8e-187">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-187">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="cad8e-188">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-188">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="cad8e-189">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cad8e-189">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="cad8e-190">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cad8e-190">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="cad8e-191">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cad8e-191">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="cad8e-192">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="cad8e-192">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cad8e-193">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cad8e-193">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="cad8e-194">[Öğretici: C# Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cad8e-194">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="cad8e-195">[Öğretici: Visual Basic Merhaba Dünya öğreticisi](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cad8e-195">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="cad8e-196">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="cad8e-196">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="cad8e-197">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="cad8e-197">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="cad8e-198">[Öğretici: macOS 'u kullanmaya](../tutorials/using-on-mac-vs.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="cad8e-198">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="cad8e-199">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="cad8e-199">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="cad8e-200">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="cad8e-200">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="cad8e-201">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="cad8e-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="cad8e-202">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="cad8e-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
