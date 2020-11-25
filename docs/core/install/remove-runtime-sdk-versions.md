---
title: .NET çalışma zamanını ve SDK 'Yı kaldırma
description: Bu makalede, .NET çalışma zamanının ve SDK 'sının hangi sürümlerinin yüklü olduğunu ve sonra Windows, Mac ve Linux 'ta nasıl kaldırılacağını belirleme açıklanmaktadır.
author: adegeo
ms.author: adegeo
ms.date: 11/20/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f07a9acdc5be310d38da18602dde2ebf678e9a1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031728"
---
# <a name="how-to-remove-the-net-runtime-and-sdk"></a><span data-ttu-id="ef165-103">.NET çalışma zamanını ve SDK 'sını kaldırma</span><span class="sxs-lookup"><span data-stu-id="ef165-103">How to remove the .NET Runtime and SDK</span></span>

<span data-ttu-id="ef165-104">Zaman içinde, .NET çalışma zamanının ve SDK 'sının güncelleştirilmiş sürümlerini yüklerken, eski .NET sürümlerini makinenizden kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef165-104">Over time, as you install updated versions of the .NET runtime and SDK, you may want to remove outdated versions of .NET from your machine.</span></span> <span data-ttu-id="ef165-105">Çalışma zamanının eski sürümlerini kaldırmak, [.NET sürümü seçiminde](../versions/selection.md)makalesinde açıklandığı gibi, paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma zamanını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ef165-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET version selection](../versions/selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="ef165-106">Bir sürümü kaldırmalıyım mıyım?</span><span class="sxs-lookup"><span data-stu-id="ef165-106">Should I remove a version?</span></span>

<span data-ttu-id="ef165-107">.Net [Sürüm seçimi](../versions/selection.md) davranışları ve .NET çalışma zamanı uyumluluğu, önceki sürümlerin güvenli şekilde kaldırılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ef165-107">The [.NET version selection](../versions/selection.md) behaviors and the runtime compatibility of .NET across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="ef165-108">.NET çalışma zamanı güncelleştirmeleri, 1. x ve 2. x gibi bir ana sürüm **bandı** içinde uyumludur.</span><span class="sxs-lookup"><span data-stu-id="ef165-108">.NET runtime updates are compatible within a major version **band** such as 1.x and 2.x.</span></span> <span data-ttu-id="ef165-109">Ayrıca, .NET SDK 'sının daha yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturma özelliğini korur.</span><span class="sxs-lookup"><span data-stu-id="ef165-109">Additionally, newer releases of the .NET SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="ef165-110">Genel olarak, uygulamanız için gereken çalışma zamanlarının yalnızca en son SDK ve en son düzeltme eki sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ef165-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="ef165-111">Daha eski SDK veya çalışma zamanı sürümlerini tutmak isteyebileceğiniz örnekler, *project.js* tabanlı uygulamalar için koruma içerir.</span><span class="sxs-lookup"><span data-stu-id="ef165-111">Instances where you might want to keep older SDK or runtime versions include maintaining *project.json*-based applications.</span></span> <span data-ttu-id="ef165-112">Uygulamanızın önceki SDK 'lar veya çalışma zamanları için belirli nedenleri yoksa, eski sürümleri güvenle kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef165-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="ef165-113">Nelerin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="ef165-113">Determine what is installed</span></span>

<span data-ttu-id="ef165-114">.NET CLı, makinenizde yüklü olan SDK ve çalışma zamanının sürümlerini listelemek için kullanabileceğiniz seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ef165-114">The .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="ef165-115">[`dotnet --list-sdks`](../tools/dotnet.md#options)Makinenizde yüklü SDK 'ların listesini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef165-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="ef165-116">[`dotnet --list-runtimes`](../tools/dotnet.md#options)Makinenizde yüklü olan çalışma zamanlarının listesini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef165-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="ef165-117">Daha fazla bilgi için bkz. [.net 'in zaten yüklü olduğunu denetleme](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ef165-117">For more information, see [How to check that .NET is already installed](how-to-detect-installed-versions.md).</span></span>

## <a name="uninstall-net"></a><span data-ttu-id="ef165-118">.NET 'i kaldır</span><span class="sxs-lookup"><span data-stu-id="ef165-118">Uninstall .NET</span></span>

::: zone pivot="os-windows"

<span data-ttu-id="ef165-119">.NET, .NET çalışma zamanının ve SDK 'nın sürümlerini kaldırmak için Windows **uygulamaları & özellikleri** iletişim kutusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef165-119">.NET uses the Windows **Apps & features** dialog to remove versions of the .NET runtime and SDK.</span></span> <span data-ttu-id="ef165-120">Aşağıdaki şekilde, **uygulamalar & özellikleri** iletişim kutusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef165-120">The following figure shows the **Apps & features** dialog.</span></span> <span data-ttu-id="ef165-121">.NET ' in yüklü sürümlerini filtrelemek ve göstermek için **Core SDK** veya **.NET SDK** araması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef165-121">You can search for **core sdk** or **.net sdk** to filter and show installed versions of .NET.</span></span>

![.NET kaldırmak için Program Ekle/Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="ef165-123">Makinenizden kaldırmak istediğiniz herhangi bir sürümü seçip **Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ef165-123">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

::: zone-end

::: zone pivot="os-linux"

<span data-ttu-id="ef165-124">Linux 'ta .NET (SDK veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="ef165-124">There are more options to uninstall .NET (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="ef165-125">.NET ' i kaldırmanın en iyi yolu, .NET yüklemek için kullandığınız eylemi yansıtmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef165-125">The best way for you to uninstall .NET is to mirror the action you used to install .NET.</span></span> <span data-ttu-id="ef165-126">Ayrıntılar, seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ef165-126">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef165-127">Red Hat yüklemeleri için, [.net Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/en-us/net/5.0/)başvurun.</span><span class="sxs-lookup"><span data-stu-id="ef165-127">For Red Hat installations, consult the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/en-us/net/5.0/).</span></span>

<span data-ttu-id="ef165-128">Bir önizleme sürümünden yükseltmediğiniz takdirde, bir paket Yöneticisi kullanılarak yükseltilirken .NET SDK 'Yı kaldırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ef165-128">There's no need to uninstall the .NET SDK when upgrading it using a package manager, unless you're upgrading from a preview version.</span></span> <span data-ttu-id="ef165-129">Paket Yöneticisi `update` veya `refresh` komutları, daha yeni bir sürümü başarıyla yüklendikten sonra eski sürümü otomatik olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ef165-129">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span> <span data-ttu-id="ef165-130">Yüklü bir önizleme sürümü varsa, bu sürümü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ef165-130">If you have a preview version installed, uninstall it.</span></span>

<span data-ttu-id="ef165-131">Bir paket Yöneticisi kullanarak .NET yüklediyseniz, .NET SDK veya çalışma zamanı 'nı kaldırmak için aynı paket yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef165-131">If you installed .NET using a package manager, use that same package manager to uninstall the .NET SDK or runtime.</span></span> <span data-ttu-id="ef165-132">.NET yüklemeleri en popüler paket yöneticilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ef165-132">.NET installations support most popular package managers.</span></span> <span data-ttu-id="ef165-133">Ortamınızdaki kesin bir sözdizimi için dağıtımın Paket Yöneticisi belgelerine başvurun:</span><span class="sxs-lookup"><span data-stu-id="ef165-133">Consult the documentation for your distribution's package manager for the precise syntax in your environment:</span></span>

- <span data-ttu-id="ef165-134">[apt-get (8)](https://linux.die.net/man/8/apt-get) , Ubuntu dahil olmak üzere, dekim tabanlı sistemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef165-134">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="ef165-135">Fedora, CentOS ve Oracle Linux için [yılum (8)](https://linux.die.net/man/8/yum) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef165-135">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="ef165-136">[zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) , openSUSE ve SUSE Linux Enterprise System (SLES) ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef165-136">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="ef165-137">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) , Fedora 'da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef165-137">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="ef165-138">Neredeyse tüm durumlarda, bir paketi kaldırma komutu olur `remove` .</span><span class="sxs-lookup"><span data-stu-id="ef165-138">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="ef165-139">Çoğu paket yöneticisi için .NET SDK yüklemesinin paket adı ve `dotnet-sdk` ardından sürüm numarası gelir.</span><span class="sxs-lookup"><span data-stu-id="ef165-139">The package name for the .NET SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="ef165-140">.NET SDK 'nın sürümü 2.1.300 ve çalışma zamanının sürümü ile başlayarak `2.1` , yalnızca büyük ve küçük sürüm numaraları gereklidir: Örneğin, .NET SDK sürümü 2.1.300, paket olarak başvurulabilirler `dotnet-sdk-2.1` .</span><span class="sxs-lookup"><span data-stu-id="ef165-140">Starting with the version 2.1.300 of the .NET SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="ef165-141">Önceki sürümler sürüm dizesinin tamamını gerektirir: Örneğin, `dotnet-sdk-2.1.200` .NET SDK 'nın sürümü 2.1.200 için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ef165-141">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET SDK.</span></span>

<span data-ttu-id="ef165-142">SDK değil yalnızca çalışma zamanını yükleyen makineler için, paket adı `dotnet-runtime-<version>` .NET çalışma zamanına ve `aspnetcore-runtime-<version>` tüm çalışma zamanı yığınına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ef165-142">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

> [!TIP]
> <span data-ttu-id="ef165-143">2,0 ' den önceki .NET Core yüklemeleri, SDK Paket Yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı.</span><span class="sxs-lookup"><span data-stu-id="ef165-143">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="ef165-144">Kullanarak `apt-get` , komut şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="ef165-144">Using `apt-get`, the command is:</span></span>
>
> ```bash
> apt-get remove dotnet-host
> ```
>
> <span data-ttu-id="ef165-145">Uygulamasına iliştirilmiş bir sürüm yok `dotnet-host` .</span><span class="sxs-lookup"><span data-stu-id="ef165-145">There's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="ef165-146">Bir tarbol kullanarak yüklediyseniz, el ile yöntemini kullanarak .NET 'i kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef165-146">If you installed using a tarball, you must remove .NET using the manual method.</span></span>

<span data-ttu-id="ef165-147">Linux 'ta, sürümlü dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef165-147">On Linux, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="ef165-148">Bunları kaldırmak, SDK ve çalışma zamanını diskten siler.</span><span class="sxs-lookup"><span data-stu-id="ef165-148">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="ef165-149">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ef165-149">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="ef165-150">SDK ve çalışma zamanının üst dizinleri, `dotnet --list-sdks` `dotnet --list-runtimes` önceki tabloda gösterildiği gibi, ve komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="ef165-150">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="ef165-151">Mac üzerinde, sürümlenmiş dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef165-151">On Mac, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="ef165-152">Bunları kaldırmak, SDK ve çalışma zamanını diskten siler.</span><span class="sxs-lookup"><span data-stu-id="ef165-152">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="ef165-153">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ef165-153">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="ef165-154">SDK ve çalışma zamanının üst dizinleri, `dotnet --list-sdks` `dotnet --list-runtimes` önceki tabloda gösterildiği gibi, ve komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="ef165-154">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

## <a name="net-uninstall-tool"></a><span data-ttu-id="ef165-155">.NET kaldırma aracı</span><span class="sxs-lookup"><span data-stu-id="ef165-155">.NET Uninstall Tool</span></span>

<span data-ttu-id="ef165-156">[.Net kaldırma aracı](../additional-tools/uninstall-tool.md) ( `dotnet-core-uninstall` ), bir sistemden .NET SDK 'ları ve çalışma zamanlarını kaldırmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef165-156">The [.NET Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET SDKs and runtimes from a system.</span></span> <span data-ttu-id="ef165-157">Hangi sürümlerin kaldırılacağını belirlemek için bir seçenek koleksiyonu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef165-157">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="ef165-158">.NET Core SDK sürümlerindeki Visual Studio bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="ef165-158">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="ef165-159">Visual Studio 2019 sürüm 16,3 ' den önce, Visual Studio yükleyicileri tek başına .NET Core SDK yükleyicisini çağırdı.</span><span class="sxs-lookup"><span data-stu-id="ef165-159">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="ef165-160">Sonuç olarak, SDK sürümleri Windows **uygulamaları & özellikleri** iletişim kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="ef165-160">As a result, the SDK versions appear in the Windows **Apps & features** dialog.</span></span> <span data-ttu-id="ef165-161">Visual Studio tarafından tek başına yükleyici kullanılarak yüklenen .NET Core SDK 'larını kaldırmak, Visual Studio 'Yu bozabilir.</span><span class="sxs-lookup"><span data-stu-id="ef165-161">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="ef165-162">SDK 'Ları kaldırdıktan sonra Visual Studio sorunları varsa, Visual Studio 'nun söz konusu sürümünde Onar ' ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ef165-162">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="ef165-163">Aşağıdaki tabloda .NET Core SDK sürümlerindeki bazı Visual Studio bağımlılıkları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ef165-163">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="ef165-164">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="ef165-164">Visual Studio version</span></span>           | <span data-ttu-id="ef165-165">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="ef165-165">.NET Core SDK version</span></span>          |
|---------------------------------|--------------------------------|
| <span data-ttu-id="ef165-166"> Visual Studio 2019 sürüm 16.2 </span><span class="sxs-lookup"><span data-stu-id="ef165-166">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="ef165-167">.NET Core SDK 2.2.4 xx, 2.1.8 xx</span><span class="sxs-lookup"><span data-stu-id="ef165-167">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="ef165-168"> Visual Studio 2019 sürüm 16.1</span><span class="sxs-lookup"><span data-stu-id="ef165-168">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="ef165-169">.NET Core SDK 2.2.3 xx, 2.1.7 xx</span><span class="sxs-lookup"><span data-stu-id="ef165-169">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="ef165-170">Visual Studio 2019 sürüm 16,0</span><span class="sxs-lookup"><span data-stu-id="ef165-170">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="ef165-171">.NET Core SDK 2.2.2 xx, 2.1.6 xx</span><span class="sxs-lookup"><span data-stu-id="ef165-171">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="ef165-172">Visual Studio 2017 sürüm 15,9</span><span class="sxs-lookup"><span data-stu-id="ef165-172">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="ef165-173">.NET Core SDK 2.2.1 xx, 2.1.5 xx</span><span class="sxs-lookup"><span data-stu-id="ef165-173">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="ef165-174">Visual Studio 2017 sürüm 15,8</span><span class="sxs-lookup"><span data-stu-id="ef165-174">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="ef165-175">.NET Core SDK 2.1.4 xx</span><span class="sxs-lookup"><span data-stu-id="ef165-175">.NET Core SDK 2.1.4xx</span></span>          |

<span data-ttu-id="ef165-176">Visual Studio 2019 sürüm 16,3 ' den itibaren, Visual Studio .NET SDK 'sının kendi kopyasına göre ücretlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ef165-176">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET SDK.</span></span> <span data-ttu-id="ef165-177">Bu nedenle, artık bu SDK sürümlerini **uygulamalar & Özellikler** iletişim kutusunda görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef165-177">For that reason, you no longer see those SDK versions in the **Apps & features** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="ef165-178">NuGet geri dönüş klasörünü kaldır</span><span class="sxs-lookup"><span data-stu-id="ef165-178">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="ef165-179">.NET Core SDK yükleyicileri, .NET Core 3,0 SDK 'dan önce bir NuGet paketleri önbelleğini depolamak için *Nugetfallbackfolder* adlı bir klasör kullandı.</span><span class="sxs-lookup"><span data-stu-id="ef165-179">Before .NET Core 3.0 SDK, the .NET Core SDK installers used a folder named *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="ef165-180">Bu önbellek, veya gibi işlemler sırasında kullanılır `dotnet restore` `dotnet build /t:Restore` .</span><span class="sxs-lookup"><span data-stu-id="ef165-180">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="ef165-181">*Nugetfallbackfolder* , Windows üzerinde *C:\Program Files\dotnet\sdk* konumunda ve MacOS 'ta */usr/local/share/DotNet/SDK* konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ef165-181">The *NuGetFallbackFolder* is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="ef165-182">Şu durumlarda bu klasörü kaldırmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef165-182">You may want to remove this folder, if:</span></span>

- <span data-ttu-id="ef165-183">Yalnızca .NET Core 3,0 SDK veya .NET 5,0 ya da sonraki sürümlerini kullanarak geliştiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="ef165-183">You're only developing using .NET Core 3.0 SDK or .NET 5.0 or later versions.</span></span>
- <span data-ttu-id="ef165-184">3,0 'den önceki .NET Core SDK sürümlerini kullanarak geliştiriyoruz, ancak çevrimiçi çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef165-184">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online.</span></span>

<span data-ttu-id="ef165-185">NuGet geri dönüş klasörünü kaldırmak istiyorsanız, onu silebilirsiniz, ancak bunu yapmak için yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef165-185">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="ef165-186">*DotNet* klasörünün silinmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ef165-186">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="ef165-187">Bunu yapmak, daha önce yüklediğiniz tüm küresel araçları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ef165-187">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="ef165-188">Ayrıca, Windows üzerinde:</span><span class="sxs-lookup"><span data-stu-id="ef165-188">Also, on Windows:</span></span>

- <span data-ttu-id="ef165-189">Visual Studio 2019 sürüm 16,3 ve sonraki sürümlerini bozacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ef165-189">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="ef165-190">Kurtarmak için **onarmayı** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef165-190">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="ef165-191">**Uygulamalar & Özellikler** iletişim kutusunda .NET Core SDK girdileri varsa, bunlar yalnız bırakılmış olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ef165-191">If there are .NET Core SDK entries in the **Apps & features** dialog, they'll be orphaned.</span></span>
