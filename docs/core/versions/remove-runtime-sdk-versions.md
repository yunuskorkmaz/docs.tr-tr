---
title: .NET Core çalışma zamanını ve SDK 'sını kaldırma
description: Bu makalede, .NET Core çalışma zamanı ve SDK 'sının hangi sürümlerinin yüklü olduğunu ve sonra Windows, Mac ve Linux 'ta nasıl kaldırılacağını belirleme açıklanmaktadır.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6d1012b8ddc5fd4a5ee8227902886727dbb10739
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970303"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="5cdef-103">.NET Core çalışma zamanı ve SDK 'sını kaldırma</span><span class="sxs-lookup"><span data-stu-id="5cdef-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="5cdef-104">Zaman içinde, .NET Core çalışma zamanının ve SDK 'sının güncelleştirilmiş sürümlerini yüklerken, eski .NET Core sürümlerini makinenizden kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cdef-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="5cdef-105">Çalışma zamanının eski sürümlerini kaldırmak, [.NET Core sürümü seçiminde](selection.md)makalesinde açıklandığı gibi, paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma zamanını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="5cdef-106">Bir sürümü kaldırmalıyım mıyım?</span><span class="sxs-lookup"><span data-stu-id="5cdef-106">Should I remove a version?</span></span>

<span data-ttu-id="5cdef-107">.NET Core [Sürüm seçimi](selection.md) davranışları ve .NET Core çalışma zamanı uyumluluğu, önceki sürümlerin güvenli şekilde kaldırılmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="5cdef-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="5cdef-108">.NET Core çalışma zamanı güncelleştirmeleri, 1. x ve 2. x gibi ana sürüm ' bantlı ' içinde uyumludur.</span><span class="sxs-lookup"><span data-stu-id="5cdef-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="5cdef-109">Ayrıca, .NET Core SDK daha yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="5cdef-110">Genel olarak, uygulamanız için gereken çalışma zamanlarının yalnızca en son SDK ve en son düzeltme eki sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="5cdef-111">Eski SDK veya çalışma zamanı sürümlerinin korunmasında, **Project. JSON**tabanlı uygulamaların sürdürülmesi dahildir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-111">Instances where retaining older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="5cdef-112">Uygulamanızın önceki SDK 'lar veya çalışma zamanları için belirli nedenleri yoksa, eski sürümleri güvenle kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cdef-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="5cdef-113">Nelerin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="5cdef-113">Determine what is installed</span></span>

<span data-ttu-id="5cdef-114">.NET Core 2,1 ile başlayarak, .NET CLı, makinenizde yüklü olan SDK ve çalışma zamanının sürümlerini listelemek için kullanabileceğiniz seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="5cdef-115">Makinenizde [`dotnet --list-sdks`](../tools/dotnet.md#options) yüklü SDK 'ların listesini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cdef-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="5cdef-116">Makinenizde [`dotnet --list-runtimes`](../tools/dotnet.md#options) yüklü olan çalışma zamanlarının listesini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cdef-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="5cdef-117">Aşağıdaki metin Windows, macOS veya Linux için tipik çıktıyı gösterir:</span><span class="sxs-lookup"><span data-stu-id="5cdef-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="5cdef-118">Windows</span><span class="sxs-lookup"><span data-stu-id="5cdef-118">Windows</span></span>](#tab/windows)

```console
C:\> dotnet --list-sdks
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

C:\> dotnet --list-runtimes
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

# <a name="linuxtablinux"></a>[<span data-ttu-id="5cdef-119">Linux</span><span class="sxs-lookup"><span data-stu-id="5cdef-119">Linux</span></span>](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
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

# <a name="macostabmacos"></a>[<span data-ttu-id="5cdef-120">macOS</span><span class="sxs-lookup"><span data-stu-id="5cdef-120">macOS</span></span>](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
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

## <a name="uninstalling-net-core"></a><span data-ttu-id="5cdef-121">.NET Core kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="5cdef-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="5cdef-122">Windows</span><span class="sxs-lookup"><span data-stu-id="5cdef-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="5cdef-123">.NET Core, .NET Core çalışma zamanının ve SDK 'nın sürümlerini kaldırmak için Windows **Program Ekle/Kaldır** iletişim kutusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="5cdef-124">Aşağıdaki şekilde, .NET çalışma zamanının ve SDK 'nın birkaç sürümü yüklü olan **Program Ekle/Kaldır** iletişim kutusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![.NET Core kaldırmak için Program Ekle/Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="5cdef-126">Makinenizden kaldırmak istediğiniz herhangi bir sürümü seçip **Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5cdef-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="5cdef-127">Linux</span><span class="sxs-lookup"><span data-stu-id="5cdef-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="5cdef-128">Linux 'ta .NET Core (SDK veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="5cdef-129">.NET Core ' u kaldırmanın en iyi yolu, .NET Core yüklemek için kullandığınız eylemi yansıtmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="5cdef-130">Ayrıntılar, seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cdef-131">Red Hat yüklemeleri için, .NET Core 'u yükleme ve kaldırma hakkında bilgi için, [Red Hat kullanmaya başlama kılavuzuna](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) bakın.</span><span class="sxs-lookup"><span data-stu-id="5cdef-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="5cdef-132">.NET Core 2,1 ile başlayarak, bir paket Yöneticisi kullanılarak yükseltilirken .NET Core SDK kaldırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5cdef-132">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="5cdef-133">Paket Yöneticisi `update` veya `refresh` komutları, daha yeni bir sürümü başarıyla yüklendikten sonra eski sürümü otomatik olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="5cdef-134">.NET Core 'u bir paket Yöneticisi kullanarak yüklediyseniz, .NET SDK veya çalışma zamanı 'nı kaldırmak için aynı paket yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cdef-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="5cdef-135">.NET Core yüklemeleri en popüler paket yöneticilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="5cdef-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="5cdef-136">Ortamınızdaki kesin bir sözdizimi için dağıtımın Paket Yöneticisi belgelerine başvurun:</span><span class="sxs-lookup"><span data-stu-id="5cdef-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="5cdef-137">[apt-get (8)](https://linux.die.net/man/8/apt-get) , Ubuntu dahil olmak üzere, dekim tabanlı sistemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="5cdef-138">Fedora, CentOS ve Oracle Linux için [yılum (8)](https://linux.die.net/man/8/yum) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="5cdef-139">[zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) , openSUSE ve SUSE Linux Enterprise System (SLES) ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="5cdef-140">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) , Fedora 'da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="5cdef-141">Neredeyse tüm durumlarda, bir paketi kaldırma komutu olur `remove`.</span><span class="sxs-lookup"><span data-stu-id="5cdef-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="5cdef-142">Çoğu paket yöneticisi için .NET Core SDK yüklemesinin paket adı ve ardından sürüm numarası `dotnet-sdk`gelir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="5cdef-143">Çalışma zamanının .NET Core SDK ve sürümünün `2.1` sürümü 2.1.300 başlayarak, yalnızca büyük ve küçük sürüm numaraları gereklidir: Örneğin, .NET Core SDK sürüm 2.1.300, paket `dotnet-sdk-2.1`olarak başvurulabilirler.</span><span class="sxs-lookup"><span data-stu-id="5cdef-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="5cdef-144">Önceki sürümler sürüm dizesinin tamamını gerektirir: Örneğin, `dotnet-sdk-2.1.200` .NET Core SDK sürüm 2.1.200 için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5cdef-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="5cdef-145">SDK değil yalnızca çalışma zamanını yükleyen makineler için, paket adı `dotnet-runtime-<version>` .NET Core çalışma zamanına ve `aspnetcore-runtime-<version>` tüm çalışma zamanı yığınına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="5cdef-146">2,0 ' dan önceki .NET Core yüklemeleri, SDK Paket Yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı.</span><span class="sxs-lookup"><span data-stu-id="5cdef-146">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="5cdef-147">Kullanarak `apt-get`, komut şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="5cdef-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="5cdef-148">Uygulamasına `dotnet-host`iliştirilmiş bir sürüm olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5cdef-148">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="5cdef-149">Bir tarbol kullanarak yüklediyseniz, el ile yöntemini kullanarak .NET Core 'u kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="5cdef-150">SDK 'Ları ve çalışma zamanlarını, bu sürümü içeren dizini kaldırarak ayrı olarak kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="5cdef-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="5cdef-151">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="5cdef-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="5cdef-152">SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi, `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="5cdef-153">macOS</span><span class="sxs-lookup"><span data-stu-id="5cdef-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="5cdef-154">Mac üzerinde, bu sürümü içeren dizini kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="5cdef-155">Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="5cdef-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="5cdef-156">SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi, `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.</span><span class="sxs-lookup"><span data-stu-id="5cdef-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---
