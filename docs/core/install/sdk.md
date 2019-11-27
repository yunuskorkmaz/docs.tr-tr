---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core SDK yüklemesi
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamaları geliştirmek için gereken bağımlılıkları bulun.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2f65e9dc39a4cd1076af1a70dfedfa671f20b42d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450879"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="cdc94-104">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="cdc94-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="cdc94-105">Bu makalede, .NET Core SDK nasıl yükleneceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc94-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="cdc94-106">.NET Core SDK .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdc94-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="cdc94-107">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-107">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="cdc94-108">.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cdc94-108">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="cdc94-109">.NET Core 3,1 Preview 3 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cdc94-109">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="cdc94-110">.NET Core 3,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cdc94-110">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="cdc94-111">.NET Core 2,2 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cdc94-111">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="cdc94-112">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cdc94-112">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

<span data-ttu-id="cdc94-113">.NET Core 'u Ayrıca, tümleşik bir geliştirme ortamının (IDE) bir parçası olarak, aşağıdaki bölümlerde ayrıntılı olarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc94-113">You can also install .NET Core as part of an integrated development environment (IDE), detailed in the sections below.</span></span>

## <a name="install-with-an-installer"></a><span data-ttu-id="cdc94-114">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="cdc94-114">Install with an installer</span></span>

<span data-ttu-id="cdc94-115">Hem Windows hem de macOS .NET Core 3,0 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyiciler vardır.</span><span class="sxs-lookup"><span data-stu-id="cdc94-115">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="cdc94-116">Windows [x64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPU](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="cdc94-116">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span></span>
- <span data-ttu-id="cdc94-117">macOS [x64 CPU 'ları](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="cdc94-117">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span></span>

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="cdc94-118">Paket Yöneticisi ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="cdc94-118">Install with a package manager</span></span>

<span data-ttu-id="cdc94-119">.NET Core SDK birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc94-119">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="cdc94-120">Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="cdc94-120">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="cdc94-121">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="cdc94-121">Install with Visual Studio</span></span>

<span data-ttu-id="cdc94-122">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cdc94-122">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="cdc94-123">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="cdc94-123">.NET Core SDK version</span></span> | <span data-ttu-id="cdc94-124">Visual Studio sürümü</span><span class="sxs-lookup"><span data-stu-id="cdc94-124">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="cdc94-125">3,0</span><span class="sxs-lookup"><span data-stu-id="cdc94-125">3.0</span></span>                   | <span data-ttu-id="cdc94-126">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cdc94-126">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="cdc94-127">2.2</span><span class="sxs-lookup"><span data-stu-id="cdc94-127">2.2</span></span>                   | <span data-ttu-id="cdc94-128">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cdc94-128">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="cdc94-129">2.1</span><span class="sxs-lookup"><span data-stu-id="cdc94-129">2.1</span></span>                   | <span data-ttu-id="cdc94-130">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cdc94-130">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="cdc94-131">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc94-131">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="cdc94-132">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="cdc94-132">Open Visual Studio.</span></span>
01. <span data-ttu-id="cdc94-133">**Microsoft Visual Studio hakkında** **Yardım** > seçin.</span><span class="sxs-lookup"><span data-stu-id="cdc94-133">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="cdc94-134">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="cdc94-134">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="cdc94-135">Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-135">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="cdc94-136">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="cdc94-136">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="cdc94-137">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="cdc94-137">Select a workload</span></span>

<span data-ttu-id="cdc94-138">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="cdc94-138">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="cdc94-139">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cdc94-139">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="cdc94-140">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cdc94-140">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="cdc94-141">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cdc94-141">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="cdc94-142">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="cdc94-142">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="cdc94-143">[.NET Core iş yüküne sahip Windows Visual Studio 2019 ![](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cdc94-143">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="cdc94-144">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="cdc94-144">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="cdc94-145">**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-145">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="cdc94-146">MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="cdc94-146">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="cdc94-147">[.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019 ![](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cdc94-147">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-from-visual-studio-code"></a><span data-ttu-id="cdc94-148">Visual Studio Code şuradan yüklensin</span><span class="sxs-lookup"><span data-stu-id="cdc94-148">Install from Visual Studio Code</span></span>

<span data-ttu-id="cdc94-149">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-149">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="cdc94-150">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-150">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="cdc94-151">Visual Studio Code .NET Core desteği ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-151">While Visual Studio Code doesn't come with .NET Core support, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="cdc94-152">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="cdc94-152">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="cdc94-153">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="cdc94-153">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>
01. <span data-ttu-id="cdc94-154">[Uzantıyı Visual Studio Code marketi 'Nden yüklersiniz. C# ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)</span><span class="sxs-lookup"><span data-stu-id="cdc94-154">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="cdc94-155">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="cdc94-155">Install with PowerShell automation</span></span>

<span data-ttu-id="cdc94-156">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdc94-156">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="cdc94-157">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc94-157">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cdc94-158">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-158">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="cdc94-159">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cdc94-159">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="cdc94-160">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="cdc94-160">Install with bash automation</span></span>

<span data-ttu-id="cdc94-161">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdc94-161">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="cdc94-162">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc94-162">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cdc94-163">Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-163">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="cdc94-164">Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cdc94-164">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="cdc94-165">Docker</span><span class="sxs-lookup"><span data-stu-id="cdc94-165">Docker</span></span>

<span data-ttu-id="cdc94-166">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc94-166">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="cdc94-167">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="cdc94-167">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="cdc94-168">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-168">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="cdc94-169">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-169">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="cdc94-170">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cdc94-170">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="cdc94-171">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc94-171">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="cdc94-172">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc94-172">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="cdc94-173">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="cdc94-173">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cdc94-174">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cdc94-174">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="cdc94-175">[Öğretici: C# Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cdc94-175">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="cdc94-176">[Öğretici: Visual Basic Merhaba Dünya öğreticisi](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cdc94-176">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="cdc94-177">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="cdc94-177">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="cdc94-178">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="cdc94-178">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="cdc94-179">[Öğretici: macOS 'u kullanmaya](../tutorials/using-on-mac-vs.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="cdc94-179">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="cdc94-180">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="cdc94-180">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="cdc94-181">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="cdc94-181">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
