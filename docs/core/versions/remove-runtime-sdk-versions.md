---
title: .NET Core çalışma süresini ve SDK'yı kaldırın
description: Bu makalede, .NET Core Runtime ve SDK'nın şu anda hangi sürümlerinin yüklendiği ve windows, mac ve Linux'ta bunların nasıl kaldırılılabildiğini nasıl belirleyeceğiz açıklanmaktadır.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398841"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="47881-103">.NET Çekirdek Çalışma Süresi ve SDK nasıl kaldırılır?</span><span class="sxs-lookup"><span data-stu-id="47881-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="47881-104">Zaman içinde ,.NET Core çalışma zamanı ve SDK'nın güncelleştirilmiş sürümlerini yüklerken, .NET Core'un eski sürümlerini makinenizden kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47881-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="47881-105">Çalışma zamanının eski sürümlerini kaldırmak, [.NET Core sürüm seçimiyle](selection.md)ilgili makalede ayrıntılı olarak açıklandığı gibi paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma süresini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="47881-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="47881-106">Bir sürümü kaldırmalı mıyım?</span><span class="sxs-lookup"><span data-stu-id="47881-106">Should I remove a version?</span></span>

<span data-ttu-id="47881-107">[.NET Core sürüm seçim](selection.md) davranışları ve .NET Core'un güncelleştirmeler arasında çalışma zamanı uyumluluğu, önceki sürümlerin güvenli bir şekilde kaldırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="47881-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="47881-108">.NET Core çalışma zamanı güncelleştirmeleri, 1.x ve 2.x gibi ana sürüm 'bandı' içinde uyumludur.</span><span class="sxs-lookup"><span data-stu-id="47881-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="47881-109">Ayrıca, .NET Core SDK'nın yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturma yeteneğini korur.</span><span class="sxs-lookup"><span data-stu-id="47881-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="47881-110">Genel olarak, yalnızca uygulamanız için gereken çalışma sürelerinin en son SDK ve en son yama sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="47881-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="47881-111">Eski SDK veya Runtime sürümlerini tutmanın **project.json**tabanlı uygulamaları korumayı içerdiği durumlar.</span><span class="sxs-lookup"><span data-stu-id="47881-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="47881-112">Uygulamanızın önceki SDK'lar veya çalışma süreleri için belirli nedenleri olmadığı sürece, eski sürümleri güvenle kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47881-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="47881-113">Nenin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="47881-113">Determine what is installed</span></span>

<span data-ttu-id="47881-114">.NET Core 2.1 ile başlayarak ,.NET CLI,.makinenize yüklenen SDK ve çalışma süresini listelemek için kullanabileceğiniz seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="47881-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="47881-115">Makinenize yüklenen SDK'ların listesini görmek için kullanın. [`dotnet --list-sdks`](../tools/dotnet.md#options)</span><span class="sxs-lookup"><span data-stu-id="47881-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="47881-116">Makinenizde yüklü çalışma sürelerinin listesini görmek için kullanın. [`dotnet --list-runtimes`](../tools/dotnet.md#options)</span><span class="sxs-lookup"><span data-stu-id="47881-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="47881-117">Aşağıdaki metin, Windows, macOS veya Linux için tipik çıktıyı gösterir:</span><span class="sxs-lookup"><span data-stu-id="47881-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="47881-118">Windows</span><span class="sxs-lookup"><span data-stu-id="47881-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="47881-119">Aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="47881-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="47881-120">Aşağıdakilere benzer çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-120">You get output similar to the following:</span></span>

```console
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]
```

<span data-ttu-id="47881-121">Ve aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="47881-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="47881-122">Aşağıdakilere benzer çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-122">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linux"></a>[<span data-ttu-id="47881-123">Linux</span><span class="sxs-lookup"><span data-stu-id="47881-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="47881-124">Aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="47881-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="47881-125">Aşağıdakilere benzer çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-125">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

<span data-ttu-id="47881-126">Ve aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="47881-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="47881-127">Aşağıdakilere benzer çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-127">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macos"></a>[<span data-ttu-id="47881-128">Macos</span><span class="sxs-lookup"><span data-stu-id="47881-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="47881-129">Aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="47881-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="47881-130">Aşağıdakilere benzer çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-130">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

<span data-ttu-id="47881-131">Ve aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="47881-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="47881-132">Aşağıdakilere benzer çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-132">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstall-net-core"></a><span data-ttu-id="47881-133">.NET Core'u kaldır</span><span class="sxs-lookup"><span data-stu-id="47881-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="47881-134">Windows</span><span class="sxs-lookup"><span data-stu-id="47881-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="47881-135">.NET Core, .NET Core çalışma zamanı ve SDK sürümlerini kaldırmak için Windows **Ekle/Kaldır** iletişim kutusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="47881-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="47881-136">Aşağıdaki şekilde .NET çalışma zamanı ve SDK yüklü çeşitli sürümleri ile **Programlar Ekle/ Kaldır** iletişim kutusunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="47881-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![.NET Core'u kaldırmak için program ekleme / kaldırma](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="47881-138">Makinenizden kaldırmak istediğiniz sürümleri seçin ve **Kaldır'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47881-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="47881-139">Linux</span><span class="sxs-lookup"><span data-stu-id="47881-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="47881-140">Linux'ta .NET Core'u (SDK veya çalışma süresi) kaldırmak için daha fazla seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="47881-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="47881-141">.NET Core'u kaldırmanın en iyi yolu ,.NET Core'u yüklemek için kullandığınız eylemi yansıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="47881-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="47881-142">Ayrıntılar seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="47881-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47881-143">Red Hat kurulumları için ,NET Core'un yüklenmesi ve yüklenmesi hakkında bilgi almak için [Red Hat Getting Started Guide'a](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) başvurun.</span><span class="sxs-lookup"><span data-stu-id="47881-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="47881-144">.NET Core 2.1 ile başlayarak, bir paket yöneticisi kullanarak yükseltirken .NET Core SDK'yı kaldırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="47881-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="47881-145">Paket yöneticisi `update` `refresh` veya komutları, daha yeni bir sürümün başarılı bir şekilde yüklenmesi yle eski sürümü otomatik olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="47881-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="47881-146">Bir paket yöneticisi kullanarak .NET Core'u yüklediyseniz, .NET SDK'yı veya çalışma süresini kaldırmak için aynı paket yöneticisini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="47881-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="47881-147">.NET Core kurulumları en popüler paket yöneticilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="47881-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="47881-148">Ortamınızdaki kesin sözdizimi için dağıtımınızın paket yöneticisine ilişkin belgelere başvurun:</span><span class="sxs-lookup"><span data-stu-id="47881-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="47881-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) Ubuntu dahil olmak üzere Debian tabanlı sistemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47881-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="47881-150">[yum(8)](https://linux.die.net/man/8/yum) Fedora, CentOS ve Oracle Linux'ta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47881-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="47881-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) openSUSE ve SUSE Linux Enterprise System (SLES) üzerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47881-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="47881-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) Fedora'da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47881-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="47881-153">Hemen hemen her durumda, bir paketi `remove`kaldırmak için komutu .</span><span class="sxs-lookup"><span data-stu-id="47881-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="47881-154">Çoğu paket yöneticisi için .NET Core SDK `dotnet-sdk`kurulumuiçin paket adı, sürüm numarası takip eder.</span><span class="sxs-lookup"><span data-stu-id="47881-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="47881-155">.NET Core SDK'nın 2.1.300 sürümü `2.1` nden başlayarak ve çalışma zamanının sürümünden başlayarak, yalnızca büyük ve küçük sürüm numaraları gereklidir: örneğin, .NET `dotnet-sdk-2.1`Core SDK sürüm 2.1.300 paket olarak başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="47881-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="47881-156">Önceki sürümler tüm sürüm dizesini gerektirir: örneğin, `dotnet-sdk-2.1.200` .NET Core SDK'nın 2.1.200 sürümü için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="47881-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="47881-157">SDK değil, yalnızca çalışma süresini yüklemiş makineler için paket adı `dotnet-runtime-<version>` .NET Core çalışma zamanı `aspnetcore-runtime-<version>` ve tüm çalışma zamanı yığını içindir.</span><span class="sxs-lookup"><span data-stu-id="47881-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="47881-158">.NET Core yüklemeleri 2.0'dan önce, SDK paket yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı.</span><span class="sxs-lookup"><span data-stu-id="47881-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="47881-159">Kullanarak, `apt-get`komutu:</span><span class="sxs-lookup"><span data-stu-id="47881-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="47881-160">'ye bağlı bir sürüm olmadığını `dotnet-host`unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47881-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="47881-161">Bir tarball kullanarak yüklediyseniz, el ile yöntemi kullanarak .NET Core'u kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47881-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="47881-162">SDK'ları ve çalışma sürelerini, bu sürümü içeren dizini kaldırarak ayrı ayrı kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="47881-162">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="47881-163">Örneğin, 1.0.1 SDK ve çalışma süresini kaldırmak için aşağıdaki bash komutlarını kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-163">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="47881-164">SDK ve çalışma zamanı nın üst dizinleri, `dotnet --list-sdks` önceki `dotnet --list-runtimes` tabloda gösterildiği gibi, ve komuttan çıktıda listelenir.</span><span class="sxs-lookup"><span data-stu-id="47881-164">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="47881-165">Macos</span><span class="sxs-lookup"><span data-stu-id="47881-165">macOS</span></span>](#tab/macos)

<span data-ttu-id="47881-166">Mac'te, bu sürümü içeren dizini kaldırarak SDK'ları ve çalışma sürelerini ayrı ayrı kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47881-166">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="47881-167">Örneğin, 1.0.1 SDK ve çalışma süresini kaldırmak için aşağıdaki bash komutlarını kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="47881-167">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="47881-168">SDK ve çalışma zamanı nın üst dizinleri, `dotnet --list-sdks` önceki `dotnet --list-runtimes` tabloda gösterildiği gibi, ve komuttan çıktıda listelenir.</span><span class="sxs-lookup"><span data-stu-id="47881-168">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="47881-169">.NET Core Kaldırma Aracı</span><span class="sxs-lookup"><span data-stu-id="47881-169">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="47881-170">[.NET Çekirdek Kaldırma](../additional-tools/uninstall-tool.md) Aracı`dotnet-core-uninstall`( ) bir sistemden .NET Core SDK'ları ve çalışma sürelerini kaldırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="47881-170">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="47881-171">Hangi sürümlerin kaldırılması gerektiğini belirtmek için seçenekler topluluğu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47881-171">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="47881-172">.NET Core SDK sürümlerinde Visual Studio bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="47881-172">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="47881-173">Visual Studio 2019 sürüm 16.3'ten önce Visual Studio yükleyiciler bağımsız .NET Core SDK yükleyicisini aradılar.</span><span class="sxs-lookup"><span data-stu-id="47881-173">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="47881-174">Sonuç olarak, Windows **Programları Ekle/Kaldır** iletişim kutusunda SDK sürümleri görünür.</span><span class="sxs-lookup"><span data-stu-id="47881-174">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="47881-175">Visual Studio tarafından tek başına yükleyici kullanılarak yüklenen .NET Core SDK'ların kaldırılması Visual Studio'yu bozabilir.</span><span class="sxs-lookup"><span data-stu-id="47881-175">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="47881-176">SDK'ları kaldırdıktan sonra Visual Studio'da sorun yaşıyorsanız, Visual Studio'nun belirli sürümünde Onarım'ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="47881-176">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="47881-177">Aşağıdaki tabloda .NET Core SDK sürümlerindeki Visual Studio bağımlılıklarından bazıları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="47881-177">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="47881-178">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="47881-178">Visual Studio version</span></span> | <span data-ttu-id="47881-179">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="47881-179">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="47881-180"> Visual Studio 2019 sürüm 16.2 </span><span class="sxs-lookup"><span data-stu-id="47881-180">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="47881-181">.NET Çekirdek SDK 2.2.4xx, 2.1.8xx</span><span class="sxs-lookup"><span data-stu-id="47881-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="47881-182"> Visual Studio 2019 sürüm 16.1</span><span class="sxs-lookup"><span data-stu-id="47881-182">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="47881-183">.NET Çekirdek SDK 2.2.3xx, 2.1.7xx</span><span class="sxs-lookup"><span data-stu-id="47881-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="47881-184">Visual Studio 2019 sürüm 16.0</span><span class="sxs-lookup"><span data-stu-id="47881-184">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="47881-185">.NET Çekirdek SDK 2.2.2xx, 2.1.6xx</span><span class="sxs-lookup"><span data-stu-id="47881-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="47881-186">Visual Studio 2017 sürümü 15.9</span><span class="sxs-lookup"><span data-stu-id="47881-186">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="47881-187">.NET Çekirdek SDK 2.2.1xx, 2.1.5xx</span><span class="sxs-lookup"><span data-stu-id="47881-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="47881-188">Visual Studio 2017 sürümü 15.8</span><span class="sxs-lookup"><span data-stu-id="47881-188">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="47881-189">.NET Çekirdek SDK 2.1.4xx</span><span class="sxs-lookup"><span data-stu-id="47881-189">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="47881-190">Visual Studio 2019 sürüm 16.3 ile başlayan Visual Studio, .NET Core SDK'nın kendi kopyasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="47881-190">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="47881-191">Bu nedenle, Artık Bu SDK sürümlerini **Programlar Ekle/Kaldır** iletişim kutusunda görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="47881-191">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="47881-192">NuGet geri dönüş klasörünü kaldırma</span><span class="sxs-lookup"><span data-stu-id="47881-192">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="47881-193">.NET Core 3.0 SDK'dan önce,.NET Core SDK yükleyiciler NuGet paketlerini saklamak için *NuGetFallbackFolder'ı* kullanmıştı.</span><span class="sxs-lookup"><span data-stu-id="47881-193">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="47881-194">Bu önbellek `dotnet restore` gibi işlemler sırasında `dotnet build /t:Restore`kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="47881-194">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="47881-195">`NuGetFallbackFolder` *C:\Program Files\dotnet\sdk* adresinde Windows'da ve */usr/local/share/dotnet/sdk* adresinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="47881-195">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="47881-196">Bu klasörü kaldırmak isteyebilirsiniz, eğer:</span><span class="sxs-lookup"><span data-stu-id="47881-196">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="47881-197">Yalnızca .NET Core 3.0 SDK veya sonraki sürümleri kullanarak geliştiriyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="47881-197">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="47881-198">.NET Core SDK sürümlerini 3.0'dan önce kullanıyorsunuz, ancak çevrimiçi olarak çalışabilirsiniz ve işler bir kez daha yavaş olabilir.</span><span class="sxs-lookup"><span data-stu-id="47881-198">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="47881-199">NuGet geri dönüş klasörünü kaldırmak istiyorsanız, silebilirsiniz, ancak bunu yapmak için yönetici ayrıcalıklarına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="47881-199">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="47881-200">*Dotnet* klasörünü silmek önerilmez.</span><span class="sxs-lookup"><span data-stu-id="47881-200">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="47881-201">Bunu yapmak, daha önce yüklediğiniz tüm genel araçları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="47881-201">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="47881-202">Ayrıca, Windows'da:</span><span class="sxs-lookup"><span data-stu-id="47881-202">Also, on Windows:</span></span>

- <span data-ttu-id="47881-203">Visual Studio 2019 sürüm 16.3 ve sonraki sürümlerini kıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="47881-203">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="47881-204">Kurtarmak için **Onarım'ı** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47881-204">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="47881-205">**Programları Ekle/Kaldır** iletişim kutusunda .NET Core SDK girişleri varsa, bunlar yetim kalır.</span><span class="sxs-lookup"><span data-stu-id="47881-205">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
