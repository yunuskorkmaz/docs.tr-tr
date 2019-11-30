---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core SDK yüklemesi
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamaları geliştirmek için gereken bağımlılıkları bulun.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 54819b409422e8bda9efe25478aa3424683a380b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567467"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="573f4-104">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="573f4-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="573f4-105">Bu makalede, .NET Core SDK nasıl yükleneceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="573f4-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="573f4-106">.NET Core SDK .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="573f4-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="573f4-107">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="573f4-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="573f4-108">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="573f4-108">Install with an installer</span></span>

<span data-ttu-id="573f4-109">Hem Windows hem de macOS .NET Core 3,0 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyiciler vardır.</span><span class="sxs-lookup"><span data-stu-id="573f4-109">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="573f4-110">Windows [x64 (64-bit) cpu](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32 bit) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.0) 'lar</span><span class="sxs-lookup"><span data-stu-id="573f4-110">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="573f4-111">macOS [x64 (64-bit) CPU 'ları](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="573f4-111">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="573f4-112">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="573f4-112">Install with a package manager</span></span>

<span data-ttu-id="573f4-113">.NET Core SDK birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="573f4-113">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="573f4-114">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="573f4-114">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="573f4-115">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="573f4-115">Download and manually install</span></span>

<span data-ttu-id="573f4-116">SDK 'Yı ayıklamak ve komutları terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) .</span><span class="sxs-lookup"><span data-stu-id="573f4-116">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="573f4-117">Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="573f4-117">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.0.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="573f4-118">Yukarıdaki komutlar yalnızca .NET SDK komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="573f4-118">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="573f4-119">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="573f4-119">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="573f4-120">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="573f4-120">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="573f4-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="573f4-121">For example:</span></span>
>
> - <span data-ttu-id="573f4-122">**Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="573f4-122">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="573f4-123">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="573f4-123">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="573f4-124">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="573f4-124">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="573f4-125">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="573f4-125">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="573f4-126">`PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="573f4-126">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="573f4-127">Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="573f4-127">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="573f4-128">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="573f4-128">Install with Visual Studio</span></span>

<span data-ttu-id="573f4-129">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="573f4-129">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="573f4-130">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="573f4-130">.NET Core SDK version</span></span> | <span data-ttu-id="573f4-131">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="573f4-131">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="573f4-132">3,1 Önizleme</span><span class="sxs-lookup"><span data-stu-id="573f4-132">3.1 Preview</span></span>           | <span data-ttu-id="573f4-133">Visual Studio 2019 sürüm 16,4 Önizleme veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="573f4-133">Visual Studio 2019 version 16.4 preview or higher.</span></span> |
| <span data-ttu-id="573f4-134">3.0</span><span class="sxs-lookup"><span data-stu-id="573f4-134">3.0</span></span>                   | <span data-ttu-id="573f4-135">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="573f4-135">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="573f4-136">2,2</span><span class="sxs-lookup"><span data-stu-id="573f4-136">2.2</span></span>                   | <span data-ttu-id="573f4-137">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="573f4-137">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="573f4-138">2,1</span><span class="sxs-lookup"><span data-stu-id="573f4-138">2.1</span></span>                   | <span data-ttu-id="573f4-139">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="573f4-139">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="573f4-140">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="573f4-140">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="573f4-141">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="573f4-141">Open Visual Studio.</span></span>
01. <span data-ttu-id="573f4-142">**Microsoft Visual Studio hakkında** **Yardım** > seçin.</span><span class="sxs-lookup"><span data-stu-id="573f4-142">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="573f4-143">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="573f4-143">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="573f4-144">Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="573f4-144">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="573f4-145">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="573f4-145">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="573f4-146">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="573f4-146">Select a workload</span></span>

<span data-ttu-id="573f4-147">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="573f4-147">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="573f4-148">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="573f4-148">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="573f4-149">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="573f4-149">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="573f4-150">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="573f4-150">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="573f4-151">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="573f4-151">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="573f4-152">[.NET Core iş yüküne sahip Windows Visual Studio 2019 ![](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="573f4-152">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="573f4-153">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="573f4-153">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="573f4-154">**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir.</span><span class="sxs-lookup"><span data-stu-id="573f4-154">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="573f4-155">MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="573f4-155">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="573f4-156">[.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019 ![](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="573f4-156">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="573f4-157">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="573f4-157">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="573f4-158">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="573f4-158">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="573f4-159">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="573f4-159">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="573f4-160">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="573f4-160">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="573f4-161">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="573f4-161">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="573f4-162">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="573f4-162">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="573f4-163">[Uzantıyı Visual Studio Code marketi 'Nden yüklersiniz. C# ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)</span><span class="sxs-lookup"><span data-stu-id="573f4-163">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="573f4-164">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="573f4-164">Install with PowerShell automation</span></span>

<span data-ttu-id="573f4-165">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="573f4-165">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="573f4-166">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="573f4-166">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="573f4-167">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="573f4-167">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="573f4-168">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="573f4-168">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="573f4-169">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="573f4-169">Install with bash automation</span></span>

<span data-ttu-id="573f4-170">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="573f4-170">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="573f4-171">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="573f4-171">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="573f4-172">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="573f4-172">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="573f4-173">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="573f4-173">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="573f4-174">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="573f4-174">All .NET Core downloads</span></span>

<span data-ttu-id="573f4-175">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="573f4-175">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="573f4-176">.NET Core 3,1 Preview İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="573f4-176">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="573f4-177">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="573f4-177">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="573f4-178">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="573f4-178">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="573f4-179">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="573f4-179">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="573f4-180">Docker</span><span class="sxs-lookup"><span data-stu-id="573f4-180">Docker</span></span>

<span data-ttu-id="573f4-181">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="573f4-181">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="573f4-182">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="573f4-182">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="573f4-183">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="573f4-183">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="573f4-184">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="573f4-184">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="573f4-185">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="573f4-185">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="573f4-186">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="573f4-186">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="573f4-187">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="573f4-187">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="573f4-188">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="573f4-188">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="573f4-189">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="573f4-189">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="573f4-190">[Öğretici: C# Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="573f4-190">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="573f4-191">[Öğretici: Visual Basic Merhaba Dünya öğreticisi](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="573f4-191">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="573f4-192">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="573f4-192">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="573f4-193">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="573f4-193">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="573f4-194">[Öğretici: macOS 'u kullanmaya](../tutorials/using-on-mac-vs.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="573f4-194">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="573f4-195">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="573f4-195">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="573f4-196">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="573f4-196">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
