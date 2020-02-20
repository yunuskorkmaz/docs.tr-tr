---
title: .NET Core çalışma zamanını ve SDK 'sını kaldırma
description: Bu makalede, .NET Core çalışma zamanı ve SDK 'sının hangi sürümlerinin yüklü olduğunu ve sonra Windows, Mac ve Linux 'ta nasıl kaldırılacağını belirleme açıklanmaktadır.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503468"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="0ccee-103">.NET Core çalışma zamanı ve SDK 'sını kaldırma</span><span class="sxs-lookup"><span data-stu-id="0ccee-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="0ccee-104">Zaman içinde, .NET Core çalışma zamanının ve SDK 'sının güncelleştirilmiş sürümlerini yüklerken, eski .NET Core sürümlerini makinenizden kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ccee-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="0ccee-105">Çalışma zamanının eski sürümlerini kaldırmak, [.NET Core sürümü seçiminde](selection.md)makalesinde açıklandığı gibi, paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma zamanını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="0ccee-106">Bir sürümü kaldırmalıyım mıyım?</span><span class="sxs-lookup"><span data-stu-id="0ccee-106">Should I remove a version?</span></span>

<span data-ttu-id="0ccee-107">.NET Core [Sürüm seçimi](selection.md) davranışları ve .NET Core çalışma zamanı uyumluluğu, önceki sürümlerin güvenli şekilde kaldırılmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="0ccee-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="0ccee-108">.NET Core çalışma zamanı güncelleştirmeleri, 1. x ve 2. x gibi ana sürüm ' bantlı ' içinde uyumludur.</span><span class="sxs-lookup"><span data-stu-id="0ccee-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="0ccee-109">Ayrıca, .NET Core SDK daha yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="0ccee-110">Genel olarak, uygulamanız için gereken çalışma zamanlarının yalnızca en son SDK ve en son düzeltme eki sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="0ccee-111">Eski SDK veya çalışma zamanı sürümlerinin tutulması, **Project. JSON**tabanlı uygulamaların tutulmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="0ccee-112">Uygulamanızın önceki SDK 'lar veya çalışma zamanları için belirli nedenleri yoksa, eski sürümleri güvenle kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ccee-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="0ccee-113">Nelerin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="0ccee-113">Determine what is installed</span></span>

<span data-ttu-id="0ccee-114">.NET Core 2,1 ile başlayarak, .NET CLı, makinenizde yüklü olan SDK ve çalışma zamanının sürümlerini listelemek için kullanabileceğiniz seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="0ccee-115">Makinenizde yüklü SDK 'ların listesini görmek için [`dotnet --list-sdks`](../tools/dotnet.md#options) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ccee-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="0ccee-116">Makinenizde yüklü olan çalışma zamanlarının listesini görmek için [`dotnet --list-runtimes`](../tools/dotnet.md#options) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ccee-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="0ccee-117">Aşağıdaki metin Windows, macOS veya Linux için tipik çıktıyı gösterir:</span><span class="sxs-lookup"><span data-stu-id="0ccee-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="0ccee-118">Windows</span><span class="sxs-lookup"><span data-stu-id="0ccee-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="0ccee-119">Aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="0ccee-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="0ccee-120">Aşağıdakine benzer bir çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0ccee-120">You get output similar to the following:</span></span>

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

<span data-ttu-id="0ccee-121">Ve aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="0ccee-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="0ccee-122">Aşağıdakine benzer bir çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0ccee-122">You get output similar to the following:</span></span>

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

# <a name="linux"></a>[<span data-ttu-id="0ccee-123">Linux</span><span class="sxs-lookup"><span data-stu-id="0ccee-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="0ccee-124">Aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="0ccee-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="0ccee-125">Aşağıdakine benzer bir çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0ccee-125">You get output similar to the following:</span></span>

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

<span data-ttu-id="0ccee-126">Ve aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="0ccee-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="0ccee-127">Aşağıdakine benzer bir çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0ccee-127">You get output similar to the following:</span></span>

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

# <a name="macos"></a>[<span data-ttu-id="0ccee-128">macOS</span><span class="sxs-lookup"><span data-stu-id="0ccee-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="0ccee-129">Aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="0ccee-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="0ccee-130">Aşağıdakine benzer bir çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0ccee-130">You get output similar to the following:</span></span>

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

<span data-ttu-id="0ccee-131">Ve aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="0ccee-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="0ccee-132">Aşağıdakine benzer bir çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0ccee-132">You get output similar to the following:</span></span>

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

## <a name="uninstall-net-core"></a><span data-ttu-id="0ccee-133">.NET Core kaldır</span><span class="sxs-lookup"><span data-stu-id="0ccee-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="0ccee-134">Windows</span><span class="sxs-lookup"><span data-stu-id="0ccee-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="0ccee-135">.NET Core, .NET Core çalışma zamanının ve SDK 'nın sürümlerini kaldırmak için Windows **Program Ekle/Kaldır** iletişim kutusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="0ccee-136">Aşağıdaki şekilde, .NET çalışma zamanının ve SDK 'nın birkaç sürümü yüklü olan **Program Ekle/Kaldır** iletişim kutusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![.NET Core kaldırmak için Program Ekle/Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="0ccee-138">Makinenizden kaldırmak istediğiniz herhangi bir sürümü seçip **Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0ccee-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="0ccee-139">Linux</span><span class="sxs-lookup"><span data-stu-id="0ccee-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="0ccee-140">Linux 'ta .NET Core (SDK veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="0ccee-141">.NET Core ' u kaldırmanın en iyi yolu, .NET Core yüklemek için kullandığınız eylemi yansıtmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="0ccee-142">Ayrıntılar, seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ccee-143">Red Hat yüklemeleri için, .NET Core 'u yükleme ve kaldırma hakkında bilgi için, [Red Hat kullanmaya başlama kılavuzuna](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) bakın.</span><span class="sxs-lookup"><span data-stu-id="0ccee-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="0ccee-144">.NET Core 2,1 ' den itibaren, bir paket Yöneticisi kullanılarak yükseltilirken .NET Core SDK kaldırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0ccee-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="0ccee-145">Paket Yöneticisi `update` veya `refresh` komutları, daha yeni bir sürümün başarıyla yüklenmesinden sonra eski sürümü otomatik olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="0ccee-146">.NET Core 'u bir paket Yöneticisi kullanarak yüklediyseniz, .NET SDK veya çalışma zamanı 'nı kaldırmak için aynı paket yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ccee-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="0ccee-147">.NET Core yüklemeleri en popüler paket yöneticilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="0ccee-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="0ccee-148">Ortamınızdaki kesin bir sözdizimi için dağıtımın Paket Yöneticisi belgelerine başvurun:</span><span class="sxs-lookup"><span data-stu-id="0ccee-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="0ccee-149">[apt-get (8)](https://linux.die.net/man/8/apt-get) , Ubuntu dahil olmak üzere, dekim tabanlı sistemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="0ccee-150">Fedora, CentOS ve Oracle Linux için [yılum (8)](https://linux.die.net/man/8/yum) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="0ccee-151">[zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) , openSUSE ve SUSE Linux Enterprise System (SLES) ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="0ccee-152">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) , Fedora 'da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="0ccee-153">Neredeyse tüm durumlarda, bir paketi kaldırma komutu `remove`.</span><span class="sxs-lookup"><span data-stu-id="0ccee-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="0ccee-154">Çoğu paket yöneticisi için .NET Core SDK yüklemesinin paket adı `dotnet-sdk`ve ardından sürüm numarası gelir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="0ccee-155">Çalışma zamanının .NET Core SDK ve sürümü `2.1` sürümü ile başlayarak, yalnızca büyük ve küçük sürüm numaraları gereklidir: Örneğin, .NET Core SDK sürümü 2.1.300 paket `dotnet-sdk-2.1`olarak başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="0ccee-156">Önceki sürümler tüm sürüm dizesini gerektirir: Örneğin, .NET Core SDK sürüm 2.1.200 için `dotnet-sdk-2.1.200` gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="0ccee-157">SDK değil yalnızca çalışma zamanını yükleyen makineler için, paket adı .NET Core çalışma zamanı için `dotnet-runtime-<version>` ve tüm çalışma zamanı yığını için `aspnetcore-runtime-<version>`.</span><span class="sxs-lookup"><span data-stu-id="0ccee-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="0ccee-158">2,0 ' den önceki .NET Core yüklemeleri, SDK Paket Yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı.</span><span class="sxs-lookup"><span data-stu-id="0ccee-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="0ccee-159">`apt-get`kullanarak komut şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="0ccee-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="0ccee-160">`dotnet-host`bağlı bir sürüm olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0ccee-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="0ccee-161">Bir tarbol kullanarak yüklediyseniz, el ile yöntemini kullanarak .NET Core 'u kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="0ccee-162">SDK 'Ları ve çalışma zamanlarını, bu sürümü içeren dizini kaldırarak ayrı olarak kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="0ccee-162">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="0ccee-163">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ccee-163">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="0ccee-164">SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-164">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="0ccee-165">macOS</span><span class="sxs-lookup"><span data-stu-id="0ccee-165">macOS</span></span>](#tab/macos)

<span data-ttu-id="0ccee-166">Mac üzerinde, bu sürümü içeren dizini kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-166">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="0ccee-167">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ccee-167">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="0ccee-168">SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-168">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="0ccee-169">.NET Core Kaldırma Aracı</span><span class="sxs-lookup"><span data-stu-id="0ccee-169">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="0ccee-170">[.NET Core kaldırma aracı](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`), bir sistemden .NET Core SDK 'larını ve çalışma zamanlarını kaldırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ccee-170">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="0ccee-171">Hangi sürümlerin kaldırılacağını belirlemek için bir seçenek koleksiyonu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-171">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="0ccee-172">.NET Core SDK sürümlerindeki Visual Studio bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="0ccee-172">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="0ccee-173">Visual Studio 2019 sürüm 16,3 ' den önce, Visual Studio yükleyicileri tek başına .NET Core SDK yükleyicisini çağırdı.</span><span class="sxs-lookup"><span data-stu-id="0ccee-173">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="0ccee-174">Sonuç olarak, SDK sürümleri Windows **Ekle/Kaldır** iletişim kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="0ccee-174">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="0ccee-175">Visual Studio tarafından tek başına yükleyici kullanılarak yüklenen .NET Core SDK 'larını kaldırmak, Visual Studio 'Yu bozabilir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-175">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="0ccee-176">SDK 'Ları kaldırdıktan sonra Visual Studio sorunları varsa, Visual Studio 'nun söz konusu sürümünde Onar ' ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0ccee-176">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="0ccee-177">Aşağıdaki tabloda .NET Core SDK sürümlerindeki bazı Visual Studio bağımlılıkları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0ccee-177">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="0ccee-178">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="0ccee-178">Visual Studio version</span></span> | <span data-ttu-id="0ccee-179">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="0ccee-179">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="0ccee-180">Visual Studio 2019 sürüm 16,2</span><span class="sxs-lookup"><span data-stu-id="0ccee-180">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="0ccee-181">.NET Core SDK 2.2.4 xx, 2.1.8 xx</span><span class="sxs-lookup"><span data-stu-id="0ccee-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="0ccee-182">Visual Studio 2019 sürüm 16,1</span><span class="sxs-lookup"><span data-stu-id="0ccee-182">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="0ccee-183">.NET Core SDK 2.2.3 xx, 2.1.7 xx</span><span class="sxs-lookup"><span data-stu-id="0ccee-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="0ccee-184">Visual Studio 2019 sürüm 16,0</span><span class="sxs-lookup"><span data-stu-id="0ccee-184">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="0ccee-185">.NET Core SDK 2.2.2 xx, 2.1.6 xx</span><span class="sxs-lookup"><span data-stu-id="0ccee-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="0ccee-186">Visual Studio 2017 sürüm 15,9</span><span class="sxs-lookup"><span data-stu-id="0ccee-186">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="0ccee-187">.NET Core SDK 2.2.1 xx, 2.1.5 xx</span><span class="sxs-lookup"><span data-stu-id="0ccee-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="0ccee-188">Visual Studio 2017 sürüm 15,8</span><span class="sxs-lookup"><span data-stu-id="0ccee-188">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="0ccee-189">.NET Core SDK 2.1.4 xx</span><span class="sxs-lookup"><span data-stu-id="0ccee-189">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="0ccee-190">Visual Studio 2019 sürüm 16,3 ' den itibaren, Visual Studio .NET Core SDK kendi kopyasına göre ücretlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-190">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="0ccee-191">Bu nedenle, bu SDK sürümlerini **Program Ekle/Kaldır** iletişim kutusunda artık göremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ccee-191">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="0ccee-192">NuGet geri dönüş klasörünü kaldır</span><span class="sxs-lookup"><span data-stu-id="0ccee-192">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="0ccee-193">.NET Core SDK yükleyicileri, .NET Core 3,0 SDK 'dan önce bir NuGet paketleri önbelleğini depolamak için *Nugetfallbackfolder* kullandı.</span><span class="sxs-lookup"><span data-stu-id="0ccee-193">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="0ccee-194">Bu önbellek, `dotnet restore` veya `dotnet build /t:Restore`gibi işlemler sırasında kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-194">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="0ccee-195">`NuGetFallbackFolder`, Windows üzerinde *C:\Program Files\dotnet\sdk* konumunda ve MacOS 'ta */usr/local/share/DotNet/SDK* konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="0ccee-195">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="0ccee-196">Şu durumlarda bu klasörü kaldırmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ccee-196">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="0ccee-197">Yalnızca .NET Core 3,0 SDK veya sonraki sürümlerini kullanarak geliştiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="0ccee-197">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="0ccee-198">3,0 'den önceki .NET Core SDK sürümlerini kullanarak geliştiriyoruz, ancak çevrimiçi çalışabilirsiniz ve bir kez daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-198">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="0ccee-199">NuGet geri dönüş klasörünü kaldırmak istiyorsanız, onu silebilirsiniz, ancak bunu yapmak için yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ccee-199">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="0ccee-200">*DotNet* klasörünün silinmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="0ccee-200">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="0ccee-201">Bunu yapmak, daha önce yüklediğiniz tüm küresel araçları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-201">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="0ccee-202">Ayrıca, Windows üzerinde:</span><span class="sxs-lookup"><span data-stu-id="0ccee-202">Also, on Windows:</span></span>

- <span data-ttu-id="0ccee-203">Visual Studio 2019 sürüm 16,3 ve sonraki sürümlerini bozacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0ccee-203">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="0ccee-204">Kurtarmak için **onarmayı** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ccee-204">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="0ccee-205">**Program Ekle/Kaldır** iletişim kutusunda .NET Core SDK girdileri varsa, bunlar yalnız bırakılmış olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0ccee-205">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
