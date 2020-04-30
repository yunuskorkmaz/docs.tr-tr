---
title: .NET Core çalışma zamanını ve SDK 'sını kaldırma
description: Bu makalede, .NET Core çalışma zamanı ve SDK 'sının hangi sürümlerinin yüklü olduğunu ve sonra Windows, Mac ve Linux 'ta nasıl kaldırılacağını belirleme açıklanmaktadır.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f1482c243ba22fa81c69ede847a0f6b36a9cb83c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595785"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="b7882-103">.NET Core çalışma zamanı ve SDK 'sını kaldırma</span><span class="sxs-lookup"><span data-stu-id="b7882-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="b7882-104">Zaman içinde, .NET Core çalışma zamanının ve SDK 'sının güncelleştirilmiş sürümlerini yüklerken, eski .NET Core sürümlerini makinenizden kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7882-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="b7882-105">Çalışma zamanının eski sürümlerini kaldırmak, [.NET Core sürümü seçiminde](../versions/selection.md)makalesinde açıklandığı gibi, paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma zamanını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b7882-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](../versions/selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="b7882-106">Bir sürümü kaldırmalıyım mıyım?</span><span class="sxs-lookup"><span data-stu-id="b7882-106">Should I remove a version?</span></span>

<span data-ttu-id="b7882-107">.NET Core [Sürüm seçimi](../versions/selection.md) davranışları ve .NET Core çalışma zamanı uyumluluğu, önceki sürümlerin güvenli şekilde kaldırılmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="b7882-107">The [.NET Core version selection](../versions/selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="b7882-108">.NET Core çalışma zamanı güncelleştirmeleri, 1. x ve 2. x gibi ana sürüm ' bantlı ' içinde uyumludur.</span><span class="sxs-lookup"><span data-stu-id="b7882-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="b7882-109">Ayrıca, .NET Core SDK daha yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b7882-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="b7882-110">Genel olarak, uygulamanız için gereken çalışma zamanlarının yalnızca en son SDK ve en son düzeltme eki sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="b7882-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="b7882-111">Eski SDK veya çalışma zamanı sürümlerini tutmak isteyebileceğiniz örnekler, *Project. JSON*tabanlı uygulamaların tutulmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="b7882-111">Instances where you might want to keep older SDK or runtime versions include maintaining *project.json*-based applications.</span></span> <span data-ttu-id="b7882-112">Uygulamanızın önceki SDK 'lar veya çalışma zamanları için belirli nedenleri yoksa, eski sürümleri güvenle kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7882-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="b7882-113">Nelerin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="b7882-113">Determine what is installed</span></span>

<span data-ttu-id="b7882-114">.NET Core 2,1 ile başlayarak, .NET CLı, makinenizde yüklü olan SDK ve çalışma zamanının sürümlerini listelemek için kullanabileceğiniz seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b7882-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="b7882-115">Makinenizde [`dotnet --list-sdks`](../tools/dotnet.md#options) yüklü SDK 'ların listesini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7882-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="b7882-116">Makinenizde [`dotnet --list-runtimes`](../tools/dotnet.md#options) yüklü olan çalışma zamanlarının listesini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7882-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="b7882-117">Daha fazla bilgi için bkz. [.NET Core 'un zaten yüklü olduğunu denetleme](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b7882-117">For more information, see [How to check that .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>

## <a name="uninstall-net-core"></a><span data-ttu-id="b7882-118">.NET Core kaldır</span><span class="sxs-lookup"><span data-stu-id="b7882-118">Uninstall .NET Core</span></span>

::: zone pivot="os-windows"

<span data-ttu-id="b7882-119">.NET Core, .NET Core çalışma zamanının ve SDK 'nın sürümlerini kaldırmak için Windows **uygulamaları & özellikleri** iletişim kutusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7882-119">.NET Core uses the Windows **Apps & features** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="b7882-120">Aşağıdaki şekilde, **uygulamalar & özellikleri** iletişim kutusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7882-120">The following figure shows the **Apps & features** dialog.</span></span> <span data-ttu-id="b7882-121">.NET Core 'un yüklü sürümlerini filtrelemek ve göstermek için **Core SDK** araması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7882-121">You can search for **core sdk** to filter and show installed versions of .NET Core.</span></span>

![.NET Core kaldırmak için Program Ekle/Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="b7882-123">Makinenizden kaldırmak istediğiniz herhangi bir sürümü seçip **Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b7882-123">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

::: zone-end

::: zone pivot="os-linux"

<span data-ttu-id="b7882-124">Linux 'ta .NET Core (SDK veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="b7882-124">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="b7882-125">.NET Core ' u kaldırmanın en iyi yolu, .NET Core yüklemek için kullandığınız eylemi yansıtmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b7882-125">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="b7882-126">Ayrıntılar, seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7882-126">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7882-127">Red Hat yüklemeleri için, .NET Core 'u yükleme ve kaldırma hakkında bilgi için, [Red Hat kullanmaya başlama kılavuzuna](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) bakın.</span><span class="sxs-lookup"><span data-stu-id="b7882-127">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="b7882-128">.NET Core 2,1 ' den itibaren, bir paket Yöneticisi kullanılarak yükseltilirken .NET Core SDK kaldırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b7882-128">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="b7882-129">Paket Yöneticisi `update` veya `refresh` komutları, daha yeni bir sürümü başarıyla yüklendikten sonra eski sürümü otomatik olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b7882-129">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="b7882-130">.NET Core 'u bir paket Yöneticisi kullanarak yüklediyseniz, .NET SDK veya çalışma zamanı 'nı kaldırmak için aynı paket yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7882-130">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="b7882-131">.NET Core yüklemeleri en popüler paket yöneticilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="b7882-131">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="b7882-132">Ortamınızdaki kesin bir sözdizimi için dağıtımın Paket Yöneticisi belgelerine başvurun:</span><span class="sxs-lookup"><span data-stu-id="b7882-132">Consult the documentation for your distribution's package manager for the precise syntax in your environment:</span></span>

- <span data-ttu-id="b7882-133">[apt-get (8)](https://linux.die.net/man/8/apt-get) , Ubuntu dahil olmak üzere, dekim tabanlı sistemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7882-133">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="b7882-134">Fedora, CentOS ve Oracle Linux için [yılum (8)](https://linux.die.net/man/8/yum) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7882-134">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="b7882-135">[zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) , openSUSE ve SUSE Linux Enterprise System (SLES) ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7882-135">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="b7882-136">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) , Fedora 'da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7882-136">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="b7882-137">Neredeyse tüm durumlarda, bir paketi kaldırma komutu olur `remove`.</span><span class="sxs-lookup"><span data-stu-id="b7882-137">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="b7882-138">Çoğu paket yöneticisi için .NET Core SDK yüklemesinin paket adı ve ardından sürüm numarası `dotnet-sdk`gelir.</span><span class="sxs-lookup"><span data-stu-id="b7882-138">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="b7882-139">Çalışma zamanının .NET Core SDK ve sürümünün `2.1` sürümü 2.1.300 başlayarak, yalnızca büyük ve küçük sürüm numaraları gereklidir: örneğin, .NET Core SDK sürüm 2.1.300, paket `dotnet-sdk-2.1`olarak başvurulabilirler.</span><span class="sxs-lookup"><span data-stu-id="b7882-139">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="b7882-140">Önceki sürümler sürüm dizesinin tamamını gerektirir: Örneğin, `dotnet-sdk-2.1.200` .NET Core SDK sürüm 2.1.200 için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7882-140">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="b7882-141">SDK değil yalnızca çalışma zamanını yükleyen makineler için, paket adı `dotnet-runtime-<version>` .NET Core çalışma zamanına ve `aspnetcore-runtime-<version>` tüm çalışma zamanı yığınına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b7882-141">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="b7882-142">2,0 ' den önceki .NET Core yüklemeleri, SDK Paket Yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı.</span><span class="sxs-lookup"><span data-stu-id="b7882-142">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="b7882-143">Kullanarak `apt-get`, komut şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="b7882-143">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="b7882-144">Uygulamasına `dotnet-host`iliştirilmiş bir sürüm olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b7882-144">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="b7882-145">Bir tarbol kullanarak yüklediyseniz, el ile yöntemini kullanarak .NET Core 'u kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7882-145">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="b7882-146">Linux 'ta, sürümlü dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7882-146">On Linux, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="b7882-147">Bunları kaldırmak, SDK ve çalışma zamanını diskten siler.</span><span class="sxs-lookup"><span data-stu-id="b7882-147">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="b7882-148">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="b7882-148">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="b7882-149">SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi, `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="b7882-149">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="b7882-150">Mac üzerinde, sürümlenmiş dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7882-150">On Mac, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="b7882-151">Bunları kaldırmak, SDK ve çalışma zamanını diskten siler.</span><span class="sxs-lookup"><span data-stu-id="b7882-151">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="b7882-152">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="b7882-152">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="b7882-153">SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi, `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="b7882-153">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="b7882-154">.NET Core Kaldırma Aracı</span><span class="sxs-lookup"><span data-stu-id="b7882-154">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="b7882-155">[.NET Core kaldırma aracı](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`), bir sistemden .NET Core SDK 'larını ve çalışma zamanlarını kaldırmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7882-155">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="b7882-156">Hangi sürümlerin kaldırılacağını belirlemek için bir seçenek koleksiyonu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7882-156">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="b7882-157">.NET Core SDK sürümlerindeki Visual Studio bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="b7882-157">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="b7882-158">Visual Studio 2019 sürüm 16,3 ' den önce, Visual Studio yükleyicileri tek başına .NET Core SDK yükleyicisini çağırdı.</span><span class="sxs-lookup"><span data-stu-id="b7882-158">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="b7882-159">Sonuç olarak, SDK sürümleri Windows **uygulamaları & özellikleri** iletişim kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="b7882-159">As a result, the SDK versions appear in the Windows **Apps & features** dialog.</span></span> <span data-ttu-id="b7882-160">Visual Studio tarafından tek başına yükleyici kullanılarak yüklenen .NET Core SDK 'larını kaldırmak, Visual Studio 'Yu bozabilir.</span><span class="sxs-lookup"><span data-stu-id="b7882-160">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="b7882-161">SDK 'Ları kaldırdıktan sonra Visual Studio sorunları varsa, Visual Studio 'nun söz konusu sürümünde Onar ' ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7882-161">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="b7882-162">Aşağıdaki tabloda .NET Core SDK sürümlerindeki bazı Visual Studio bağımlılıkları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b7882-162">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="b7882-163">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="b7882-163">Visual Studio version</span></span>           | <span data-ttu-id="b7882-164">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="b7882-164">.NET Core SDK version</span></span>          |
|---------------------------------|--------------------------------|
| <span data-ttu-id="b7882-165"> Visual Studio 2019 sürüm 16.2 </span><span class="sxs-lookup"><span data-stu-id="b7882-165">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="b7882-166">.NET Core SDK 2.2.4 xx, 2.1.8 xx</span><span class="sxs-lookup"><span data-stu-id="b7882-166">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="b7882-167"> Visual Studio 2019 sürüm 16.1</span><span class="sxs-lookup"><span data-stu-id="b7882-167">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="b7882-168">.NET Core SDK 2.2.3 xx, 2.1.7 xx</span><span class="sxs-lookup"><span data-stu-id="b7882-168">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="b7882-169">Visual Studio 2019 sürüm 16,0</span><span class="sxs-lookup"><span data-stu-id="b7882-169">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="b7882-170">.NET Core SDK 2.2.2 xx, 2.1.6 xx</span><span class="sxs-lookup"><span data-stu-id="b7882-170">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="b7882-171">Visual Studio 2017 sürüm 15,9</span><span class="sxs-lookup"><span data-stu-id="b7882-171">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="b7882-172">.NET Core SDK 2.2.1 xx, 2.1.5 xx</span><span class="sxs-lookup"><span data-stu-id="b7882-172">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="b7882-173">Visual Studio 2017 sürüm 15,8</span><span class="sxs-lookup"><span data-stu-id="b7882-173">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="b7882-174">.NET Core SDK 2.1.4 xx</span><span class="sxs-lookup"><span data-stu-id="b7882-174">.NET Core SDK 2.1.4xx</span></span>          |

<span data-ttu-id="b7882-175">Visual Studio 2019 sürüm 16,3 ' den itibaren, Visual Studio .NET Core SDK kendi kopyasına göre ücretlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b7882-175">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="b7882-176">Bu nedenle, artık bu SDK sürümlerini **uygulamalar & Özellikler** iletişim kutusunda görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7882-176">For that reason, you no longer see those SDK versions in the **Apps & features** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="b7882-177">NuGet geri dönüş klasörünü kaldır</span><span class="sxs-lookup"><span data-stu-id="b7882-177">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="b7882-178">.NET Core SDK yükleyicileri, .NET Core 3,0 SDK 'dan önce bir NuGet paketleri önbelleğini depolamak için *Nugetfallbackfolder* adlı bir klasör kullandı.</span><span class="sxs-lookup"><span data-stu-id="b7882-178">Before .NET Core 3.0 SDK, the .NET Core SDK installers used a folder named *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="b7882-179">Bu önbellek, `dotnet restore` veya `dotnet build /t:Restore`gibi işlemler sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7882-179">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="b7882-180">*Nugetfallbackfolder* , Windows üzerinde *C:\Program Files\dotnet\sdk* konumunda ve MacOS 'ta */usr/local/share/DotNet/SDK* konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b7882-180">The *NuGetFallbackFolder* is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="b7882-181">Şu durumlarda bu klasörü kaldırmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b7882-181">You may want to remove this folder, if:</span></span>

- <span data-ttu-id="b7882-182">Yalnızca .NET Core 3,0 SDK veya sonraki sürümlerini kullanarak geliştiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="b7882-182">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
- <span data-ttu-id="b7882-183">3,0 'den önceki .NET Core SDK sürümlerini kullanarak geliştiriyoruz, ancak çevrimiçi çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7882-183">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online.</span></span>

<span data-ttu-id="b7882-184">NuGet geri dönüş klasörünü kaldırmak istiyorsanız, onu silebilirsiniz, ancak bunu yapmak için yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7882-184">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="b7882-185">*DotNet* klasörünün silinmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b7882-185">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="b7882-186">Bunu yapmak, daha önce yüklediğiniz tüm küresel araçları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b7882-186">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="b7882-187">Ayrıca, Windows üzerinde:</span><span class="sxs-lookup"><span data-stu-id="b7882-187">Also, on Windows:</span></span>

- <span data-ttu-id="b7882-188">Visual Studio 2019 sürüm 16,3 ve sonraki sürümlerini bozacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b7882-188">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="b7882-189">Kurtarmak için **onarmayı** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7882-189">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="b7882-190">**Uygulamalar & Özellikler** iletişim kutusunda .NET Core SDK girdileri varsa, bunlar yalnız bırakılmış olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7882-190">If there are .NET Core SDK entries in the **Apps & features** dialog, they'll be orphaned.</span></span>
