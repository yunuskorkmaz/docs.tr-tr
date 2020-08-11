---
title: .NET Core dağıtımı paketleme
description: Dağıtım için .NET Core 'u paketleme, adlandırma ve sürüm hakkında bilgi edinin.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 3324a6a151fc6dc46a8f13ea17c89da99d108d82
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062892"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="2b395-103">.NET Core dağıtımı paketleme</span><span class="sxs-lookup"><span data-stu-id="2b395-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="2b395-104">.NET Core daha fazla ve daha fazla platformda kullanıma sunulduğunda, bu uygulamayı paketleme, adlandırma ve sürüm hakkında bilgi edinmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="2b395-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="2b395-105">Bu şekilde, paket bakım yapanlar, kullanıcıların .NET çalıştırmayı tercih etmeksizin tutarlı bir deneyim sağlanmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b395-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="2b395-106">Bu makale, şu kullanıcılar için yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="2b395-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="2b395-107">Kaynaktan .NET Core oluşturmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="2b395-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="2b395-108">.NET Core CLI, oluşturulan yerleşimi veya paketleri etkileyebilecek değişiklikler yapmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="2b395-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="2b395-109">Disk düzeni</span><span class="sxs-lookup"><span data-stu-id="2b395-109">Disk layout</span></span>

<span data-ttu-id="2b395-110">Yüklendiğinde, .NET Core dosya sisteminde aşağıdaki gibi çeşitli bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="2b395-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="2b395-111">(1) **DotNet** ana bilgisayar ("muxer" olarak da bilinir) iki ayrı role sahiptir: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirin ve BIR SDK 'yı ona komut göndermek için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="2b395-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="2b395-112">Ana bilgisayar yerel bir yürütülebilir dosyadır ( `dotnet.exe` ).</span><span class="sxs-lookup"><span data-stu-id="2b395-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="2b395-113">Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu sürümlü dizinlerde (2, 3, 5, 6) bulunur.</span><span class="sxs-lookup"><span data-stu-id="2b395-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="2b395-114">Bu, tarafında yan yana yüklendiklerinden bu yana birden çok sürümün mevcut olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b395-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="2b395-115">(2) \*\*Host/FXR/ \<fxr version> \*\* ana bilgisayar tarafından kullanılan çerçeve çözümleme mantığını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="2b395-116">Ana bilgisayar, yüklü en son hostfxr 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b395-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="2b395-117">Hostfxr, .NET Core uygulaması yürütürken uygun çalışma zamanının seçilmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="2b395-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="2b395-118">Örneğin, .NET Core 2.0.0 için oluşturulmuş bir uygulama, varsa 2.0.5 çalışma zamanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b395-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="2b395-119">Benzer şekilde, hostfxr geliştirme sırasında uygun SDK 'Yı seçer.</span><span class="sxs-lookup"><span data-stu-id="2b395-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="2b395-120">(3) \*\*SDK/ \<sdk version> \*\* SDK ("alet oluşturma" olarak da bilinir), .NET Core kitaplıklarını ve uygulamalarını yazmak ve derlemek için kullanılan bir yönetilen araçlar kümesidir.</span><span class="sxs-lookup"><span data-stu-id="2b395-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="2b395-121">SDK .NET Core CLI, yönetilen diller derleyicileri, MSBuild ve ilişkili derleme görevlerini ve hedeflerini, NuGet, yeni proje şablonlarını vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-121">The SDK includes the .NET Core CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="2b395-122">(4) **SDK/NuGetFallbackFolder** , veya çalıştırılırken olduğu gibi, geri yükleme işlemi SıRASıNDA bir SDK tarafından kullanılan NuGet paketlerinin bir önbelleğini içerir `dotnet restore` `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="2b395-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="2b395-123">Bu klasör yalnızca .NET Core 3,0 ' den önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b395-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="2b395-124">' Den önceden oluşturulmuş ikili varlıklar içerdiğinden kaynaktan derlenebilir `nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="2b395-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="2b395-125">**Paylaşılan** klasör çerçeveler içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="2b395-126">Paylaşılan bir çerçeve, farklı uygulamalar tarafından kullanılabilmesi için merkezi bir konumda bir kitaplık kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b395-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="2b395-127">(5) \*\*paylaşılan/Microsoft. NETCore. app/ \<runtime version> \*\* Bu çerçeve .NET Core çalışma zamanı içerir ve yönetilen kitaplıkları destekler.</span><span class="sxs-lookup"><span data-stu-id="2b395-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="2b395-128">(6) \*\*paylaşılan/Microsoft. AspNetCore. { Uygulama, tümü}/ \<aspnetcore version> \*\* ASP.NET Core kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="2b395-129">Altındaki kitaplıklar, `Microsoft.AspNetCore.App` .NET Core projesinin bir parçası olarak geliştirilir ve desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2b395-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="2b395-130">Altındaki kitaplıklar, `Microsoft.AspNetCore.All` üçüncü taraf kitaplıklarını da içeren bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="2b395-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="2b395-131">(7) \*\*paylaşılan/Microsoft. Desktop. app/ \<desktop app version> \*\* Windows Masaüstü kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="2b395-132">Bu, Windows dışı platformlarda bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="2b395-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="2b395-133">(8) **LICENSE.txt, ThirdPartyNotices.txt** .NET Core 'ta kullanılan üçüncü taraf kitaplıklarının, sırasıyla .NET Core lisanslarıdır.</span><span class="sxs-lookup"><span data-stu-id="2b395-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="2b395-134">(9, 10) **DotNet. 1. gz, DotNet** , `dotnet.1.gz` DotNet el ile yapılan bir sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="2b395-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="2b395-135">`dotnet`, DotNet konağının (1) bir symbağlantıdır.</span><span class="sxs-lookup"><span data-stu-id="2b395-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="2b395-136">Bu dosyalar, sistem tümleştirmesi için iyi bilinen konumlara yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2b395-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="2b395-137">(11, 12) **Microsoft. NETCore. app. ref, Microsoft. AspNetCore. app. ref** bir `x.y` .NET Core sürümü ve sırasıyla ASP.NET Core API 'sini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b395-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="2b395-138">Bu paketler, bu hedef sürümler için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b395-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="2b395-139">(13) \*\*Microsoft. NETCore. app. Host. \<rid> \*\*</span><span class="sxs-lookup"><span data-stu-id="2b395-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="2b395-140">platform için yerel bir ikili içerir `rid` .</span><span class="sxs-lookup"><span data-stu-id="2b395-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="2b395-141">Bu ikili, bir .NET Core uygulamasını bu platform için yerel ikilide derlerken kullanılan bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="2b395-141">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="2b395-142">(14) **Microsoft. windowsdesktop. app. ref** , `x.y` Windows masaüstü uygulamalarının sürümünün API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b395-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="2b395-143">Bu dosyalar, bu hedef için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b395-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="2b395-144">Bu, Windows dışı platformlarda sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="2b395-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="2b395-145">(15) **netstandart. Library. ref** netstandart API 'sini açıklar `x.y` .</span><span class="sxs-lookup"><span data-stu-id="2b395-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="2b395-146">Bu dosyalar, bu hedef için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b395-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="2b395-147">(16) **/etc/DotNet/install_location** , için tam yolu içeren bir dosyadır `{dotnet_root}` .</span><span class="sxs-lookup"><span data-stu-id="2b395-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="2b395-148">Yol, bir yeni satır ile bitemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="2b395-148">The path may end with a newline.</span></span> <span data-ttu-id="2b395-149">Kök olduğunda bu dosyanın eklenmesi gerekli değildir `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="2b395-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="2b395-150">(17) **şablonları** , SDK tarafından kullanılan şablonları içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="2b395-151">Örneğin, `dotnet new` burada proje şablonlarını bulur.</span><span class="sxs-lookup"><span data-stu-id="2b395-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="2b395-152">İle işaretlenen klasörler `(*)` birden çok paket tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b395-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="2b395-153">Bazı paket biçimleri (örneğin, `rpm` ) bu tür klasörlerin özel işlenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b395-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="2b395-154">Paket bakımınonu bu şekilde ele almalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b395-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="2b395-155">Önerilen paketler</span><span class="sxs-lookup"><span data-stu-id="2b395-155">Recommended packages</span></span>

<span data-ttu-id="2b395-156">.NET Core sürümü oluşturma çalışma zamanı bileşen `[major].[minor]` sürüm numaralarına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b395-156">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="2b395-157">SDK sürümü aynı kullanır `[major].[minor]` ve `[patch]` SDK için özellik ve düzeltme eki semantiğini birleştiren bir bağımsız içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="2b395-158">Örneğin: SDK sürümü 2.2.302, SDK 'nın 2,2 çalışma zamanını destekleyen üçüncü Özellik sürümünün ikinci düzeltme eki sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="2b395-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="2b395-159">Sürüm oluşturma 'nın nasıl çalıştığı hakkında daha fazla bilgi için bkz. [.NET Core sürümü genel bakış](./versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b395-159">For more information about how versioning works, see [.NET Core versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="2b395-160">Bazı paketler, kendi adında sürüm numarasının bir parçasını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b395-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="2b395-161">Bu, belirli bir sürümü yüklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b395-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="2b395-162">Sürümün geri kalanı sürüm adına dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="2b395-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="2b395-163">Bu, işletim sistemi paket yöneticisinin paketleri güncelleştirmesine izin verir (örneğin, otomatik olarak güvenlik düzeltmelerini yükleme).</span><span class="sxs-lookup"><span data-stu-id="2b395-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="2b395-164">Desteklenen paket yöneticileri Linux 'a özgüdür.</span><span class="sxs-lookup"><span data-stu-id="2b395-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="2b395-165">Önerilen paketleri aşağıda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="2b395-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="2b395-166">`dotnet-sdk-[major].[minor]`-Belirli çalışma zamanı için en son SDK 'yı yükleme</span><span class="sxs-lookup"><span data-stu-id="2b395-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="2b395-167">**Sürüm:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="2b395-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2b395-168">**Örnek:** DotNet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="2b395-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="2b395-169">**Şunu içerir:** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="2b395-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="2b395-170">**Bağımlılıklar:** `dotnet-runtime-[major].[minor]` , `aspnetcore-runtime-[major].[minor]` , `dotnet-targeting-pack-[major].[minor]` , `aspnetcore-targeting-pack-[major].[minor]` , `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` , `dotnet-apphost-pack-[major].[minor]` ,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2b395-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="2b395-171">`aspnetcore-runtime-[major].[minor]`-Belirli bir ASP.NET Core çalışma zamanı yükleme</span><span class="sxs-lookup"><span data-stu-id="2b395-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="2b395-172">**Sürüm:**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="2b395-173">**Örnek:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="2b395-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="2b395-174">**Şunu içerir:** (6)</span><span class="sxs-lookup"><span data-stu-id="2b395-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="2b395-175">**Bağımlılıklar:**`dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2b395-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="2b395-176">`dotnet-runtime-deps-[major].[minor]`_(Isteğe bağlı)_ -kendi içindeki uygulamaları çalıştırmaya yönelik bağımlılıkları yükleme</span><span class="sxs-lookup"><span data-stu-id="2b395-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="2b395-177">**Sürüm:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2b395-178">**Örnek:** DotNet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="2b395-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="2b395-179">**Bağımlılıklar:** _dağıtıma özgü bağımlılıklar_</span><span class="sxs-lookup"><span data-stu-id="2b395-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="2b395-180">`dotnet-runtime-[major].[minor]`-Belirli bir çalışma zamanını yükleme</span><span class="sxs-lookup"><span data-stu-id="2b395-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="2b395-181">**Sürüm:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2b395-182">**Örnek:** DotNet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="2b395-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="2b395-183">**Şunu içerir:** (5)</span><span class="sxs-lookup"><span data-stu-id="2b395-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="2b395-184">**Bağımlılıklar:** `dotnet-hostfxr-[major].[minor]` ,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2b395-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="2b395-185">`dotnet-hostfxr-[major].[minor]`-Dependency</span><span class="sxs-lookup"><span data-stu-id="2b395-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="2b395-186">**Sürüm:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2b395-187">**Örnek:** DotNet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="2b395-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="2b395-188">**Şunu içerir:** (2)</span><span class="sxs-lookup"><span data-stu-id="2b395-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="2b395-189">**Bağımlılıklar:**`dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="2b395-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="2b395-190">`dotnet-host`-Dependency</span><span class="sxs-lookup"><span data-stu-id="2b395-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="2b395-191">**Sürüm:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2b395-192">**Örnek:** DotNet-konak</span><span class="sxs-lookup"><span data-stu-id="2b395-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="2b395-193">**İçerir:** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="2b395-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="2b395-194">`dotnet-apphost-pack-[major].[minor]`-Dependency</span><span class="sxs-lookup"><span data-stu-id="2b395-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="2b395-195">**Sürüm:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2b395-196">**Şunu içerir:** (13)</span><span class="sxs-lookup"><span data-stu-id="2b395-196">**Contains:** (13)</span></span>

- <span data-ttu-id="2b395-197">`dotnet-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="2b395-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="2b395-198">**Sürüm:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2b395-199">**Şunu içerir:** (12)</span><span class="sxs-lookup"><span data-stu-id="2b395-199">**Contains:** (12)</span></span>

- <span data-ttu-id="2b395-200">`aspnetcore-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="2b395-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="2b395-201">**Sürüm:**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="2b395-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="2b395-202">**Şunu içerir:** (11)</span><span class="sxs-lookup"><span data-stu-id="2b395-202">**Contains:** (11)</span></span>

- <span data-ttu-id="2b395-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`-Netstandard sürümünün hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="2b395-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="2b395-204">**Sürüm:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="2b395-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2b395-205">**Şunu içerir:** (15)</span><span class="sxs-lookup"><span data-stu-id="2b395-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="2b395-206">**Sürüm:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="2b395-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2b395-207">**Şunu içerir:** (15)</span><span class="sxs-lookup"><span data-stu-id="2b395-207">**Contains:** (15)</span></span>

<span data-ttu-id="2b395-208">, `dotnet-runtime-deps-[major].[minor]` _Özel olmayan bağımlılıkları_kavramak istiyor.</span><span class="sxs-lookup"><span data-stu-id="2b395-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="2b395-209">Diski derleme sistemi bunu otomatik olarak türetebildiğinden, paket isteğe bağlıdır; bu durumda bu bağımlılıklar pakete doğrudan eklenir `dotnet-runtime-[major].[minor]` .</span><span class="sxs-lookup"><span data-stu-id="2b395-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="2b395-210">Paket içeriği sürümlü bir klasör altında olduğunda, paket adı `[major].[minor]` sürümlü klasör adıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="2b395-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="2b395-211">Dışındaki tüm paketler için, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` Bu, .NET Core sürümü ile de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="2b395-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="2b395-212">Paketler arasındaki bağımlılıklar, sürüm gereksinimini _eşit veya daha büyük_ kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b395-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="2b395-213">Örneğin, `dotnet-sdk-2.2:2.2.401` gerektirir `aspnetcore-runtime-2.2 >= 2.2.6` .</span><span class="sxs-lookup"><span data-stu-id="2b395-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="2b395-214">Bu, kullanıcının yüklemelerini bir kök paket aracılığıyla yükseltmesini (örneğin,) mümkün hale getirir `dnf update dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="2b395-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="2b395-215">Çoğu dağıtım, kaynaktan oluşturulacak tüm yapıtları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b395-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="2b395-216">Bu, paketlere bazı etkileri vardır:</span><span class="sxs-lookup"><span data-stu-id="2b395-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="2b395-217">Altındaki üçüncü taraf kitaplıkları `shared/Microsoft.AspNetCore.All` kaynaktan kolayca derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="2b395-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="2b395-218">Bu nedenle, bu klasör paketten çıkarılır `aspnetcore-runtime` .</span><span class="sxs-lookup"><span data-stu-id="2b395-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="2b395-219">, `NuGetFallbackFolder` Öğesinden ikili yapıtlar kullanılarak doldurulur `nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="2b395-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="2b395-220">Boş kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b395-220">It should remain empty.</span></span>

<span data-ttu-id="2b395-221">Birden çok `dotnet-sdk` paket için aynı dosyaları sağlayabilir `NuGetFallbackFolder` .</span><span class="sxs-lookup"><span data-stu-id="2b395-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="2b395-222">Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyaların aynı olması gerekir (sağlama toplamı, değiştirme tarihi vb.).</span><span class="sxs-lookup"><span data-stu-id="2b395-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="2b395-223">Paket oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b395-223">Building packages</span></span>

<span data-ttu-id="2b395-224">[DotNet/Source-Build](https://github.com/dotnet/source-build) deposu .NET Core SDK kaynak tarbol 'in ve tüm bileşenlerinin nasıl oluşturulacağı hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b395-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="2b395-225">Kaynak-derleme deposunun çıktısı, bu makalenin ilk bölümünde açıklanan düzen ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="2b395-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
