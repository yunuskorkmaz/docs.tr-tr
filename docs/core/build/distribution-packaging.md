---
title: .NET Core dağıtımı paketleme
description: Dağıtım için .NET Core 'u paketleme, adlandırma ve sürüm hakkında bilgi edinin.
author: tmds
ms.date: 10/09/2019
ms.custom: seodec18
ms.openlocfilehash: 715eb944c3e7626696f64e63b874e2f77595cf46
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393590"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="69eb5-103">.NET Core dağıtımı paketleme</span><span class="sxs-lookup"><span data-stu-id="69eb5-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="69eb5-104">.NET Core daha fazla ve daha fazla platformda kullanıma sunulduğunda, bu uygulamayı paketleme, adlandırma ve sürüm hakkında bilgi edinmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="69eb5-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="69eb5-105">Bu şekilde, paket bakım yapanlar, kullanıcıların .NET çalıştırmayı tercih etmeksizin tutarlı bir deneyim sağlanmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="69eb5-106">Bu makale, şu kullanıcılar için yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="69eb5-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="69eb5-107">Kaynaktan .NET Core oluşturmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="69eb5-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="69eb5-108">.NET Core CLI, oluşturulan yerleşimi veya paketleri etkileyebilecek değişiklikler yapmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="69eb5-109">Disk düzeni</span><span class="sxs-lookup"><span data-stu-id="69eb5-109">Disk layout</span></span>

<span data-ttu-id="69eb5-110">Yüklendiğinde, .NET Core dosya sisteminde aşağıdaki gibi çeşitli bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="69eb5-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

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

- <span data-ttu-id="69eb5-111">(1) **DotNet** ana bilgisayar ("muxer" olarak da bilinir) iki ayrı role sahiptir: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirin ve BIR SDK 'yı ona komut göndermek için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="69eb5-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="69eb5-112">Ana bilgisayar yerel bir yürütülebilir dosyadır (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="69eb5-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="69eb5-113">Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu sürümlü dizinlerde (2, 3, 5, 6) bulunur.</span><span class="sxs-lookup"><span data-stu-id="69eb5-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="69eb5-114">Bu, tarafında yan yana yüklendiklerinden bu yana birden çok sürümün mevcut olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="69eb5-115">(2) **Host/FXR/\<FXR sürümü >** ana bilgisayar tarafından kullanılan çerçeve çözümleme mantığını içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="69eb5-116">Ana bilgisayar, yüklü en son hostfxr 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="69eb5-117">Hostfxr, .NET Core uygulaması yürütürken uygun çalışma zamanının seçilmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="69eb5-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="69eb5-118">Örneğin, .NET Core 2.0.0 için oluşturulmuş bir uygulama, varsa 2.0.5 çalışma zamanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="69eb5-119">Benzer şekilde, hostfxr geliştirme sırasında uygun SDK 'Yı seçer.</span><span class="sxs-lookup"><span data-stu-id="69eb5-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="69eb5-120">(3) SDK **/\<SDK sürümü >** SDK ("araç araçları" olarak da bilinir), .NET Core kitaplıklarını ve uygulamalarını yazmak ve derlemek için kullanılan bir yönetilen araçlar kümesidir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="69eb5-121">SDK, .NET Core komut satırı arabirimi (CLı), yönetilen diller derleyicileri, MSBuild ve ilişkili derleme görevleri ile hedefleri, NuGet, yeni proje şablonları vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="69eb5-122">(4) **SDK/NuGetFallbackFolder** , geri yükleme işlemi sırasında, `dotnet restore` veya `dotnet build`çalıştırılırken olduğu gıbı bir SDK tarafından kullanılan NuGet paketlerinin bir önbelleğini içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="69eb5-123">Bu klasör yalnızca .NET Core 3,0 ' den önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="69eb5-124">`nuget.org`'den önceden oluşturulmuş ikili varlıklar içerdiğinden kaynaktan derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="69eb5-125">**Paylaşılan** klasör çerçeveler içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="69eb5-126">Paylaşılan bir çerçeve, farklı uygulamalar tarafından kullanılabilmesi için merkezi bir konumda bir kitaplık kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="69eb5-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="69eb5-127">(5) **paylaşılan/Microsoft. NETCore. app/\<Runtime sürümü >** bu çerçeve .NET Core çalışma zamanı ve yönetilen kitaplıkları destekler.</span><span class="sxs-lookup"><span data-stu-id="69eb5-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="69eb5-128">(6) **paylaşılan/Microsoft. AspNetCore. { Uygulama, All}/\<aspnetcore sürümü >** ASP.NET Core kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="69eb5-129">`Microsoft.AspNetCore.App` altındaki kitaplıklar, .NET Core projesinin bir parçası olarak geliştirilir ve desteklenir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="69eb5-130">`Microsoft.AspNetCore.All` altındaki kitaplıklar, üçüncü taraf kitaplıklarını da içeren bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="69eb5-131">(7) **paylaşılan/Microsoft. Desktop. app/\<masaüstü uygulaması sürümü >** Windows Masaüstü kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="69eb5-132">Bu, Windows dışı platformlarda bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="69eb5-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="69eb5-133">(8) **LICENSE. txt, üçüncü taraf bildirimleri. txt** , .NET Core 'un sırasıyla kullanıldığı üçüncü taraf kitaplıkların .NET Core lisansı ve lisanslarıdır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="69eb5-134">(9, 10) **DotNet. 1. gz, dotnet** `dotnet.1.gz` DotNet el ile yapılan bir sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="69eb5-135">`dotnet`, DotNet konağının (1) bir symbağlantıdır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="69eb5-136">Bu dosyalar, sistem tümleştirmesi için iyi bilinen konumlara yüklenir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-136">These files are installed at well known locations for system integration.</span></span>

- <span data-ttu-id="69eb5-137">(11, 12) **Microsoft. NETCore. app. ref, Microsoft. AspNetCore. app. ref,** .NET Core 'un `x.y` sürümünün API 'sini ve sırasıyla ASP.NET Core tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="69eb5-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="69eb5-138">Bu paketler, bu hedef sürümler için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="69eb5-139">(13) **Microsoft. NETCore. app. Host.\<rid >** , platform `rid`için yerel bir ikili içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="69eb5-140">Bu ikili, bir .NET Core uygulamasını bu platform için yerel ikilide derlerken kullanılan bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="69eb5-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="69eb5-141">(14) **Microsoft. windowsdesktop. app. ref** , Windows masaüstü uygulamalarının `x.y` sürümünün API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="69eb5-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="69eb5-142">Bu dosyalar, bu hedef için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="69eb5-143">Bu, Windows dışı platformlarda sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="69eb5-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="69eb5-144">(15) **netstandart. Library. ref** netstandart `x.y` API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="69eb5-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="69eb5-145">Bu dosyalar, bu hedef için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="69eb5-146">(16) **/etc/DotNet/install_location** , `{dotnet_root}`tam yolunu içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-146">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="69eb5-147">Yol, bir yeni satır ile bitemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-147">The path may end with a newline.</span></span> <span data-ttu-id="69eb5-148">Kök `/usr/share/dotnet`bu dosyayı eklemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="69eb5-149">(17) **şablonları** , SDK tarafından kullanılan şablonları içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="69eb5-150">Örneğin, `dotnet new` proje şablonlarını buradan bulur.</span><span class="sxs-lookup"><span data-stu-id="69eb5-150">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="69eb5-151">`(*)` işaretli klasörler birden çok paket tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-151">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="69eb5-152">Bazı paket biçimleri (örneğin, `rpm`), bu klasörlerin özel işlenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-152">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="69eb5-153">Paket bakımınonu bu şekilde ele almalıdır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-153">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="69eb5-154">Önerilen paketler</span><span class="sxs-lookup"><span data-stu-id="69eb5-154">Recommended packages</span></span>

<span data-ttu-id="69eb5-155">.NET Core sürümü oluşturma, çalışma zamanı bileşeni `[major].[minor]` sürüm numaralarına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-155">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="69eb5-156">SDK sürümü aynı `[major].[minor]` kullanır ve SDK için özellik ve düzeltme eki semantiğini birleştiren bağımsız bir `[patch]` vardır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-156">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="69eb5-157">Örneğin: SDK sürümü 2.2.302, SDK 'nın 2,2 çalışma zamanını destekleyen üçüncü Özellik sürümünün ikinci düzeltme eki sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="69eb5-157">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="69eb5-158">Sürüm oluşturma 'nın nasıl çalıştığı hakkında daha fazla bilgi için bkz. [.NET Core sürümü genel bakış](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="69eb5-158">For more information about how versioning works, see [.NET Core versioning overview](../versions/index.md).</span></span>

<span data-ttu-id="69eb5-159">Bazı paketler, kendi adında sürüm numarasının bir parçasını içerir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-159">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="69eb5-160">Bu, belirli bir sürümü yüklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="69eb5-160">This allows you to install a specific version.</span></span>
<span data-ttu-id="69eb5-161">Sürümün geri kalanı sürüm adına dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-161">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="69eb5-162">Bu, işletim sistemi paket yöneticisinin paketleri güncelleştirmesine izin verir (örneğin, otomatik olarak güvenlik düzeltmelerini yükleme).</span><span class="sxs-lookup"><span data-stu-id="69eb5-162">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="69eb5-163">Desteklenen paket yöneticileri Linux 'a özgüdür.</span><span class="sxs-lookup"><span data-stu-id="69eb5-163">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="69eb5-164">Önerilen paketleri aşağıda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="69eb5-164">The following lists the recommended packages:</span></span>

- <span data-ttu-id="69eb5-165">`dotnet-sdk-[major].[minor]`-belirli çalışma zamanı için en son SDK 'yı yükleme</span><span class="sxs-lookup"><span data-stu-id="69eb5-165">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="69eb5-166">**Sürüm:** \<çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-166">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="69eb5-167">**Örnek:** DotNet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="69eb5-167">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="69eb5-168">**Şunu içerir:** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="69eb5-168">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="69eb5-169">**Bağımlılıklar:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="69eb5-169">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="69eb5-170">`aspnetcore-runtime-[major].[minor]`-belirli bir ASP.NET Core çalışma zamanını yükleme</span><span class="sxs-lookup"><span data-stu-id="69eb5-170">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="69eb5-171">**Sürüm:** \<aspnetcore çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-171">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="69eb5-172">**Örnek:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="69eb5-172">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="69eb5-173">**Şunu içerir:** (6)</span><span class="sxs-lookup"><span data-stu-id="69eb5-173">**Contains:** (6)</span></span>
  - <span data-ttu-id="69eb5-174">**Bağımlılıklar:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="69eb5-174">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="69eb5-175">`dotnet-runtime-deps-[major].[minor]` _(Isteğe bağlı)_ -kendi içindeki uygulamaları çalıştırmaya yönelik bağımlılıkları yükleme</span><span class="sxs-lookup"><span data-stu-id="69eb5-175">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="69eb5-176">**Sürüm:** \<çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-176">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="69eb5-177">**Örnek:** DotNet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="69eb5-177">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="69eb5-178">**Bağımlılıklar:** _geçmiş özel bağımlılıklar_</span><span class="sxs-lookup"><span data-stu-id="69eb5-178">**Dependencies:** _distro specific dependencies_</span></span>

- <span data-ttu-id="69eb5-179">`dotnet-runtime-[major].[minor]`-belirli bir çalışma zamanını yükleme</span><span class="sxs-lookup"><span data-stu-id="69eb5-179">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="69eb5-180">**Sürüm:** \<çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-180">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="69eb5-181">**Örnek:** DotNet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="69eb5-181">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="69eb5-182">**Şunu içerir:** (5)</span><span class="sxs-lookup"><span data-stu-id="69eb5-182">**Contains:** (5)</span></span>
  - <span data-ttu-id="69eb5-183">**Bağımlılıklar:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="69eb5-183">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="69eb5-184">`dotnet-hostfxr-[major].[minor]` bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="69eb5-184">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="69eb5-185">**Sürüm:** \<çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-185">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="69eb5-186">**Örnek:** DotNet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="69eb5-186">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="69eb5-187">**Şunu içerir:** (2)</span><span class="sxs-lookup"><span data-stu-id="69eb5-187">**Contains:** (2)</span></span>
  - <span data-ttu-id="69eb5-188">**Bağımlılıklar:** `dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="69eb5-188">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="69eb5-189">`dotnet-host` bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="69eb5-189">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="69eb5-190">**Sürüm:** \<çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-190">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="69eb5-191">**Örnek:** DotNet-konak</span><span class="sxs-lookup"><span data-stu-id="69eb5-191">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="69eb5-192">**İçerir:** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="69eb5-192">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="69eb5-193">`dotnet-apphost-pack-[major].[minor]` bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="69eb5-193">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="69eb5-194">**Sürüm:** \<çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="69eb5-195">**Şunu içerir:** (13)</span><span class="sxs-lookup"><span data-stu-id="69eb5-195">**Contains:** (13)</span></span>

- <span data-ttu-id="69eb5-196">`dotnet-targeting-pack-[major].[minor]`-son olmayan çalışma zamanının hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="69eb5-196">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="69eb5-197">**Sürüm:** \<çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-197">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="69eb5-198">**Şunu içerir:** (12)</span><span class="sxs-lookup"><span data-stu-id="69eb5-198">**Contains:** (12)</span></span>

- <span data-ttu-id="69eb5-199">`aspnetcore-targeting-pack-[major].[minor]`-son olmayan çalışma zamanının hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="69eb5-199">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="69eb5-200">**Sürüm:** \<aspnetcore çalışma zamanı sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-200">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="69eb5-201">**Şunu içerir:** (11)</span><span class="sxs-lookup"><span data-stu-id="69eb5-201">**Contains:** (11)</span></span>

- <span data-ttu-id="69eb5-202">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`-Netstandard sürümünün hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="69eb5-202">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="69eb5-203">**Sürüm:** \<sdk sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-203">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="69eb5-204">**Şunu içerir:** (15)</span><span class="sxs-lookup"><span data-stu-id="69eb5-204">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="69eb5-205">**Sürüm:** \<sdk sürümü ></span><span class="sxs-lookup"><span data-stu-id="69eb5-205">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="69eb5-206">**Şunu içerir:** (15)</span><span class="sxs-lookup"><span data-stu-id="69eb5-206">**Contains:** (15)</span></span>

<span data-ttu-id="69eb5-207">`dotnet-runtime-deps-[major].[minor]`, _düzensiz bağımlılıkları_anlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-207">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="69eb5-208">Diski derleme sistemi bunu otomatik olarak türetebildiğinden, paket isteğe bağlıdır; bu durumda bu bağımlılıklar doğrudan `dotnet-runtime-[major].[minor]` paketine eklenir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-208">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="69eb5-209">Paket içeriği sürümlü bir klasör altında olduğunda, paket adı `[major].[minor]` sürümlü klasör adıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-209">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="69eb5-210">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`dışındaki tüm paketler için bu, .NET Core sürümü ile de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-210">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="69eb5-211">Paketler arasındaki bağımlılıklar, sürüm gereksinimini _eşit veya daha büyük_ kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-211">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="69eb5-212">Örneğin, `dotnet-sdk-2.2:2.2.401` `aspnetcore-runtime-2.2 >= 2.2.6`gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-212">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="69eb5-213">Bu, kullanıcının yüklemelerini bir kök paket aracılığıyla yükseltmesini (örneğin, `dnf update dotnet-sdk-2.2`) mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-213">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="69eb5-214">Çoğu dağıtım, kaynaktan oluşturulacak tüm yapıtları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-214">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="69eb5-215">Bu, paketlere bazı etkileri vardır:</span><span class="sxs-lookup"><span data-stu-id="69eb5-215">This has some impact on the packages:</span></span>

- <span data-ttu-id="69eb5-216">`shared/Microsoft.AspNetCore.All` altındaki üçüncü taraf kitaplıkları kaynaktan kolayca oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-216">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="69eb5-217">Bu nedenle, bu klasör `aspnetcore-runtime` paketinden atlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-217">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="69eb5-218">`NuGetFallbackFolder`, `nuget.org`ikili yapıtlar kullanılarak doldurulur.</span><span class="sxs-lookup"><span data-stu-id="69eb5-218">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="69eb5-219">Boş kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69eb5-219">It should remain empty.</span></span>

<span data-ttu-id="69eb5-220">Birden çok `dotnet-sdk` paket `NuGetFallbackFolder`için aynı dosyaları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-220">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="69eb5-221">Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyaların aynı olması gerekir (sağlama toplamı, değiştirme tarihi vb.).</span><span class="sxs-lookup"><span data-stu-id="69eb5-221">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="69eb5-222">Paket oluşturma</span><span class="sxs-lookup"><span data-stu-id="69eb5-222">Building packages</span></span>

<span data-ttu-id="69eb5-223">[DotNet/Source-Build](https://github.com/dotnet/source-build) deposu .NET Core SDK kaynak tarbol 'in ve tüm bileşenlerinin nasıl oluşturulacağı hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="69eb5-223">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="69eb5-224">Kaynak-derleme deposunun çıktısı, bu makalenin ilk bölümünde açıklanan düzen ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="69eb5-224">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
