---
title: .NET çalışma zamanını ve SDK'sı kaldırma
description: Yönergeler için Windows, Mac ve Linux üzerinde .NET Core çalışma zamanı ve SDK bileşenleri kaldırılıyor
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.openlocfilehash: 1806d1af3b10e44ccc2eff788d8958ca976fe85b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787187"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="3fbaf-103">SDK ve .NET Core çalışma zamanı'nı kaldırma</span><span class="sxs-lookup"><span data-stu-id="3fbaf-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="3fbaf-104">Zamanla, SDK ve .NET Core çalışma zamanı güncelleştirilmiş sürümlerini yüklemek gibi .NET Core eski sürümlerini makinenizden kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="3fbaf-105">Çalışma zamanının daha eski sürümleri kaldırılıyor makalesinde ayrıntılı olarak paylaşılan framework uygulamaları çalıştırmak için seçilen çalışma zamanı değişebilir [.NET Core sürüm seçimi](selection.md).</span><span class="sxs-lookup"><span data-stu-id="3fbaf-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

<span data-ttu-id="3fbaf-106">.NET Core 2.1 ile başlayarak, .NET CLI SDK sürümleri listelemek için kullanabileceğiniz seçenekleri ve makinenizde yüklü olan çalışma zamanı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-106">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="3fbaf-107">Kullanım [ `dotnet --list-sdks` ](../tools/dotnet.md#options) makinenizde yüklü bir SDK'ları listesini görmek için.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-107">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="3fbaf-108">Kullanım [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) makinenizde yüklü çalışma zamanları listesini görmek için.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-108">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="3fbaf-109">Aşağıdaki metni, Windows, macOS veya Linux için normal çıktı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3fbaf-109">The following text shows typical output for Windows, macOS, or Linux:</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="3fbaf-110">Windows</span><span class="sxs-lookup"><span data-stu-id="3fbaf-110">Windows</span></span>](#tab/Windows)

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

# <a name="linuxtablinux"></a>[<span data-ttu-id="3fbaf-111">Linux</span><span class="sxs-lookup"><span data-stu-id="3fbaf-111">Linux</span></span>](#tab/Linux)

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

# <a name="macostabmacos"></a>[<span data-ttu-id="3fbaf-112">macOS</span><span class="sxs-lookup"><span data-stu-id="3fbaf-112">macOS</span></span>](#tab/macOS)

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

***

## <a name="uninstalling-net-core"></a><span data-ttu-id="3fbaf-113">.NET Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="3fbaf-113">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="3fbaf-114">Windows</span><span class="sxs-lookup"><span data-stu-id="3fbaf-114">Windows</span></span>](#tab/Windows)

<span data-ttu-id="3fbaf-115">.NET core kullanan Windows **Program Ekle/Kaldır** SDK ve .NET Core çalışma zamanı sürümleri kaldırılmaya iletişim.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-115">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="3fbaf-116">Aşağıdaki şekil gösterir **Program Ekle/Kaldır** çeşitli sürümleri yüklü SDK ve .NET çalışma zamanı ile iletişim.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-116">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![.NET Core kaldırmak için Program Ekle / Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="3fbaf-118">İstediğiniz makinenizden kaldırmak ve tüm sürümlerini seçin **kaldırma**.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-118">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="3fbaf-119">Linux</span><span class="sxs-lookup"><span data-stu-id="3fbaf-119">Linux</span></span>](#tab/Linux)

<span data-ttu-id="3fbaf-120">Linux üzerinde .NET Core (SDK'sı veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-120">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="3fbaf-121">En iyi yolu, .NET Core kaldırmak, .NET Core yüklemek için kullanılan eylem yansıtma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-121">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="3fbaf-122">Özellikleri, seçtiğiniz dağıtım ve yükleme yöntemi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-122">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fbaf-123">Red Hat yüklemelerinde başvurun [Red Hat Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) yükleme ve .NET Core kaldırma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-123">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="3fbaf-124">.NET Core 2.1 ile başlayarak, bir paket Yöneticisi'ni kullanarak yükseltme sırasında .NET Core SDK'yı kaldırmak için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-124">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="3fbaf-125">Paket Yöneticisi `update` veya `refresh` komutları otomatik olarak yeni bir sürüme başarılı yüklenmesinden sonra eski sürümü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-125">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="3fbaf-126">Bir paket Yöneticisi'ni kullanarak .NET Core yüklü değilse, .NET SDK'sı veya çalışma zamanı'nı kaldırmak için aynı paket yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-126">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="3fbaf-127">.NET core yüklemeleri, en popüler paket yöneticileri destekler.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-127">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="3fbaf-128">Ortamınızda kesin sözdizimi için dağıtımınıza ait Paket Yöneticisi için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="3fbaf-128">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="3fbaf-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) Ubuntu dahil olmak üzere Debian tabanlı sistemlerden tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="3fbaf-130">[yum(8)](https://linux.die.net/man/8/yum) Fedora, CentOS ve Oracle Linux kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-130">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="3fbaf-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) openSUSE ve SUSE Linux Enterprise sistem (SLES) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="3fbaf-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) Fedora üzerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="3fbaf-133">Hemen hemen tüm durumlarda, bir paket kaldırmak için komutu olan `remove`.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-133">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="3fbaf-134">Paket adı çoğu paket yöneticileri için .NET Core SDK'sı yüklemesi `dotnet-sdk`takip eden sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-134">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="3fbaf-135">2.1.300 sürümü ve .NET Core SDK sürümüyle başlayarak `2.1` çalışma zamanını, yalnızca birincil ve ikincil sürüm numaraları gereklidir: Örneğin, .NET Core SDK'sı sürüm 2.1.300 paketi olarak başvurulabilir `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-135">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="3fbaf-136">Önceki sürümler gerektiren tüm sürüm dizesini: Örneğin, `dotnet-sdk-2.1.200` .NET Core SDK'sını 2.1.200 sürümü için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-136">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="3fbaf-137">Paket adı yalnızca çalışma zamanını ve SDK yüklü olduğu makineler için olduğundan `dotnet-runtime-<version>` .NET Core çalışma zamanı ve `aspnetcore-runtime-<version>` tüm çalışma zamanı yığını için.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-137">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="3fbaf-138">.NET core yüklemeleri 2.0 önce konak uygulama kaldırmamanız, SDK'sı Paket Yöneticisi'ni kullanarak kaldırdığınızda.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-138">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="3fbaf-139">Kullanarak `apt-get`, komut:</span><span class="sxs-lookup"><span data-stu-id="3fbaf-139">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="3fbaf-140">Hiçbir sürüm unutmayın iliştirilmiş `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-140">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="3fbaf-141">Bir tarball kullanarak yüklediyseniz, .NET Core el ile gerçekleştirilen yöntemi kullanarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-141">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="3fbaf-142">Çalışma zamanları ve SDK'ları ayrı olarak, bu sürümü içeren dizine kaldırarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-142">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="3fbaf-143">Örneğin, 1.0.1 kaldırmak için SDK ve çalışma zamanı, kullandığınız şu bash komutlarını:</span><span class="sxs-lookup"><span data-stu-id="3fbaf-143">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="3fbaf-144">SDK ve çalışma zamanı için üst dizinlerin çıktıda listelenen `dotnet --list-sdks` ve `dotnet --list-runtimes` önceki tabloda gösterildiği gibi komutu.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-144">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="3fbaf-145">macOS</span><span class="sxs-lookup"><span data-stu-id="3fbaf-145">macOS</span></span>](#tab/macOS)

<span data-ttu-id="3fbaf-146">Mac bilgisayarlarda, SDK ve çalışma zamanları ayrı olarak, bu sürümü içeren dizine kaldırarak kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-146">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="3fbaf-147">Örneğin, 1.0.1 kaldırmak için SDK ve çalışma zamanı, kullandığınız şu bash komutlarını:</span><span class="sxs-lookup"><span data-stu-id="3fbaf-147">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="3fbaf-148">SDK ve çalışma zamanı için üst dizinlerin çıktıda listelenen `dotnet --list-sdks` ve `dotnet --list-runtimes` önceki tabloda gösterildiği gibi komutu.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-148">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

<span data-ttu-id="3fbaf-149">.NET Core 2.1 ile başlayarak, bir paket Yöneticisi'ni kullanarak yükseltme sırasında .NET Core SDK'yı kaldırmak için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-149">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="3fbaf-150">Paket Yöneticisi `update` veya `refresh` komutları otomatik olarak yeni bir sürüme başarılı yüklenmesinden sonra eski sürümü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3fbaf-150">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

---
