---
title: .NET Core dağıtımı paketleme
description: Dağıtım için .NET Core 'u paketleme, adlandırma ve sürüm hakkında bilgi edinin.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394155"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="1ea5b-103">.NET Core dağıtımı paketleme</span><span class="sxs-lookup"><span data-stu-id="1ea5b-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="1ea5b-104">.NET Core daha fazla ve daha fazla platformda kullanıma sunulduğunda, bu uygulamayı paketleme, adlandırma ve sürüm hakkında bilgi edinmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="1ea5b-105">Bu şekilde, paket bakım yapanlar, kullanıcıların .NET çalıştırmayı tercih etmeksizin tutarlı bir deneyim sağlanmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="1ea5b-106">Bu makale, şu kullanıcılar için yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="1ea5b-107">Kaynaktan .NET Core oluşturmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="1ea5b-108">.NET Core CLI, oluşturulan yerleşimi veya paketleri etkileyebilecek değişiklikler yapmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="1ea5b-109">Disk düzeni</span><span class="sxs-lookup"><span data-stu-id="1ea5b-109">Disk layout</span></span>

<span data-ttu-id="1ea5b-110">Yüklendiğinde, .NET Core dosya sisteminde aşağıdaki gibi çeşitli bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="1ea5b-111">(1) **DotNet** ana bilgisayar ("muxer" olarak da bilinir) iki ayrı role sahiptir: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirin ve BIR SDK 'yı ona komut göndermek için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="1ea5b-112">Ana bilgisayar yerel bir yürütülebilir dosyadır (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="1ea5b-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="1ea5b-113">Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu sürümlü dizinlerde (2, 3, 5, 6) bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="1ea5b-114">Bu, tarafında yan yana yüklendiklerinden bu yana birden çok sürümün mevcut olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="1ea5b-115">(2) **Host/FXR/\<FXR sürümü >** ana bilgisayar tarafından kullanılan çerçeve çözümleme mantığını içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="1ea5b-116">Ana bilgisayar, yüklü en son hostfxr 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="1ea5b-117">Hostfxr, .NET Core uygulaması yürütürken uygun çalışma zamanının seçilmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="1ea5b-118">Örneğin, .NET Core 2.0.0 için oluşturulmuş bir uygulama, varsa 2.0.5 çalışma zamanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="1ea5b-119">Benzer şekilde, hostfxr geliştirme sırasında uygun SDK 'Yı seçer.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="1ea5b-120">(3) SDK **/\<SDK sürümü >** SDK ("araç oluşturma" olarak da bilinir), .NET Core kitaplıklarını ve uygulamalarını yazmak ve derlemek için kullanılan bir yönetilen araçlar kümesidir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="1ea5b-121">SDK, .NET Core komut satırı arabirimi (CLı), yönetilen diller derleyicileri, MSBuild ve ilişkili derleme görevleri ile hedefleri, NuGet, yeni proje şablonları vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="1ea5b-122">(4) **SDK/nugetfallbackfolder** , veya `dotnet restore` `dotnet build /t:Restore`çalıştırılırken olduğu gibi, geri yükleme işlemi sırasında bir SDK tarafından kullanılan NuGet paketlerinin bir önbelleğini içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="1ea5b-123">Bu klasör yalnızca .NET Core 3,0 ' den önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="1ea5b-124">' Den `nuget.org`önceden oluşturulmuş ikili varlıklar içerdiğinden kaynaktan derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="1ea5b-125">**Paylaşılan** klasör çerçeveler içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="1ea5b-126">Paylaşılan bir çerçeve, farklı uygulamalar tarafından kullanılabilmesi için merkezi bir konumda bir kitaplık kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="1ea5b-127">(5) **paylaşılan/Microsoft. netcore. app/\<Runtime sürümü >** bu çerçeve .NET Core çalışma zamanı ve yönetilen kitaplıkları destekler.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="1ea5b-128">(6) **paylaşılan/Microsoft. AspNetCore. { App, All}/\<aspnetcore sürüm >** ASP.NET Core kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="1ea5b-129">Altındaki `Microsoft.AspNetCore.App` kitaplıklar, .NET Core projesinin bir parçası olarak geliştirilir ve desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="1ea5b-130">Altındaki `Microsoft.AspNetCore.All` kitaplıklar, üçüncü taraf kitaplıklarını da içeren bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="1ea5b-131">(7) **paylaşılan/Microsoft. Desktop. app/\<Desktop uygulama sürümü >** Windows Masaüstü kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="1ea5b-132">Bu, Windows dışı platformlarda bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="1ea5b-133">(8) **LICENSE. txt, üçüncü taraf bildirimleri. txt** , .NET Core 'un sırasıyla kullanıldığı üçüncü taraf kitaplıkların .NET Core lisansı ve lisanslarıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="1ea5b-134">(9, 10) **DotNet. 1. gz, DotNet** `dotnet.1.gz` , DotNet el ile yapılan bir sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="1ea5b-135">`dotnet`, DotNet konağının (1) bir symbağlantıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="1ea5b-136">Bu dosyalar, sistem tümleştirmesi için iyi bilinen konumlara yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-136">These files are installed at well known locations for system integration.</span></span>

- <span data-ttu-id="1ea5b-137">(11, 12) **Microsoft. netcore. app. ref, Microsoft. aspnetcore. app. ref** bir `x.y` .NET Core sürümü ve sırasıyla ASP.NET Core API 'sini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="1ea5b-138">Bu paketler, bu hedef sürümler için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="1ea5b-139">(13) **Microsoft. NETCore. app. Host.\< RID >** , Platform `rid`için yerel bir ikili içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="1ea5b-140">Bu ikili, bir .NET Core uygulamasını bu platform için yerel ikilide derlerken kullanılan bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="1ea5b-141">(14) **Microsoft. windowsdesktop. app. ref** , Windows masaüstü uygulamalarının `x.y` sürümünün API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="1ea5b-142">Bu dosyalar, bu hedef için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="1ea5b-143">Bu, Windows dışı platformlarda sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="1ea5b-144">(15) **netstandart. Library. ref** netstandart `x.y` API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="1ea5b-145">Bu dosyalar, bu hedef için derlenirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="1ea5b-146">(16) **/etc/DotNet/ınstall_location** , `dotnet` ana bilgisayar ikilisini içeren klasörün tam yolunu içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-146">(16) **/etc/dotnet/install_location** is a file that contains the full path to the folder that contains the `dotnet` host binary.</span></span> <span data-ttu-id="1ea5b-147">Yol, bir yeni satır ile sonlandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-147">The path may be terminated with a newline.</span></span> <span data-ttu-id="1ea5b-148">Kök olduğunda bu dosyanın eklenmesi gerekli değildir `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="1ea5b-149">(17) **şablonları** , SDK tarafından kullanılan şablonları içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="1ea5b-150">Örneğin, `dotnet new` burada proje şablonlarını bulur.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-150">For example, `dotnet new` finds project templates here.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="1ea5b-151">Önerilen paketler</span><span class="sxs-lookup"><span data-stu-id="1ea5b-151">Recommended packages</span></span>

<span data-ttu-id="1ea5b-152">.NET Core sürümü oluşturma çalışma zamanı bileşen `[major].[minor]` sürüm numaralarına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-152">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="1ea5b-153">SDK sürümü aynı `[major].[minor]` kullanır ve SDK için özellik ve düzeltme `[patch]` eki semantiğini birleştiren bir bağımsız içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-153">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="1ea5b-154">Örneğin: SDK sürümü 2.2.302, SDK 'nın 2,2 çalışma zamanını destekleyen üçüncü Özellik sürümünün ikinci düzeltme eki sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-154">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="1ea5b-155">Sürüm oluşturma 'nın nasıl çalıştığı hakkında daha fazla bilgi için bkz. [.NET Core sürümü genel bakış](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ea5b-155">For more information about how versioning works, see [.NET Core versioning overview](../versions/index.md).</span></span>

<span data-ttu-id="1ea5b-156">Bazı paketler, kendi adında sürüm numarasının bir parçasını içerir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-156">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="1ea5b-157">Bu, belirli bir sürümü yüklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-157">This allows you to install a specific version.</span></span>
<span data-ttu-id="1ea5b-158">Sürümün geri kalanı sürüm adına dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-158">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="1ea5b-159">Bu, işletim sistemi paket yöneticisinin paketleri güncelleştirmesine izin verir (örneğin, otomatik olarak güvenlik düzeltmelerini yükleme).</span><span class="sxs-lookup"><span data-stu-id="1ea5b-159">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="1ea5b-160">Desteklenen paket yöneticileri Linux 'a özgüdür.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-160">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="1ea5b-161">Önerilen paketleri aşağıda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-161">The following lists the recommended packages:</span></span>

- <span data-ttu-id="1ea5b-162">`dotnet-sdk-[major].[minor]`-Belirli çalışma zamanı için en son SDK 'yı yükleme</span><span class="sxs-lookup"><span data-stu-id="1ea5b-162">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="1ea5b-163">**Sürüm:** \<çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-163">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="1ea5b-164">**Örnek:** DotNet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="1ea5b-164">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="1ea5b-165">**Vardır** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-165">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="1ea5b-166">**Bağımlılıklar:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="1ea5b-166">**Dependencies:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="1ea5b-167">`aspnetcore-runtime-[major].[minor]`-Belirli bir ASP.NET Core çalışma zamanı yükleme</span><span class="sxs-lookup"><span data-stu-id="1ea5b-167">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="1ea5b-168">**Sürüm:** \<aspnetcore çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-168">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="1ea5b-169">**Örnek:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="1ea5b-169">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="1ea5b-170">**Vardır** (6)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-170">**Contains:** (6)</span></span>
  - <span data-ttu-id="1ea5b-171">**Bağımlılıklar:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="1ea5b-171">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="1ea5b-172">`dotnet-runtime-deps-[major].[minor]` _(Isteğe bağlı)_ -kendi içindeki uygulamaları çalıştırmaya yönelik bağımlılıkları yükleme</span><span class="sxs-lookup"><span data-stu-id="1ea5b-172">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="1ea5b-173">**Sürüm:** \<çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-173">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="1ea5b-174">**Örnek:** DotNet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="1ea5b-174">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="1ea5b-175">**Bağımlılıklar:** _özel olmayan bağımlılıklar_</span><span class="sxs-lookup"><span data-stu-id="1ea5b-175">**Dependencies:** _distro specific dependencies_</span></span>

- <span data-ttu-id="1ea5b-176">`dotnet-runtime-[major].[minor]`-Belirli bir çalışma zamanını yükleme</span><span class="sxs-lookup"><span data-stu-id="1ea5b-176">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="1ea5b-177">**Sürüm:** \<çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="1ea5b-178">**Örnek:** DotNet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="1ea5b-178">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="1ea5b-179">**Vardır** (5)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-179">**Contains:** (5)</span></span>
  - <span data-ttu-id="1ea5b-180">**Bağımlılıklar:** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="1ea5b-180">**Dependencies:** `dotnet-hostfxr:<runtime version>+`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="1ea5b-181">`dotnet-hostfxr`-Dependency</span><span class="sxs-lookup"><span data-stu-id="1ea5b-181">`dotnet-hostfxr` - dependency</span></span>
  - <span data-ttu-id="1ea5b-182">**Sürüm:** \<çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-182">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="1ea5b-183">**Örnek:** DotNet-hostfxr</span><span class="sxs-lookup"><span data-stu-id="1ea5b-183">**Example:** dotnet-hostfxr</span></span>
  - <span data-ttu-id="1ea5b-184">**Vardır** (2)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-184">**Contains:** (2)</span></span>
  - <span data-ttu-id="1ea5b-185">**Bağımlılıklar:** `host:<runtime version>+`</span><span class="sxs-lookup"><span data-stu-id="1ea5b-185">**Dependencies:** `host:<runtime version>+`</span></span>

- <span data-ttu-id="1ea5b-186">`dotnet-host`-Dependency</span><span class="sxs-lookup"><span data-stu-id="1ea5b-186">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="1ea5b-187">**Sürüm:** \<çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-187">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="1ea5b-188">**Örnek:** DotNet-konak</span><span class="sxs-lookup"><span data-stu-id="1ea5b-188">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="1ea5b-189">**Vardır** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-189">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="1ea5b-190">`dotnet-apphost-pack-[major].[minor]`-Dependency</span><span class="sxs-lookup"><span data-stu-id="1ea5b-190">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="1ea5b-191">**Sürüm:** \<çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="1ea5b-192">**Vardır** hatası</span><span class="sxs-lookup"><span data-stu-id="1ea5b-192">**Contains:** (13)</span></span>

- <span data-ttu-id="1ea5b-193">`dotnet-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="1ea5b-193">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="1ea5b-194">**Sürüm:** \<çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="1ea5b-195">**Vardır** +</span><span class="sxs-lookup"><span data-stu-id="1ea5b-195">**Contains:** (12)</span></span>

- <span data-ttu-id="1ea5b-196">`aspnetcore-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="1ea5b-196">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="1ea5b-197">**Sürüm:** \<aspnetcore çalışma zamanı sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-197">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="1ea5b-198">**Vardır** üst</span><span class="sxs-lookup"><span data-stu-id="1ea5b-198">**Contains:** (11)</span></span>

- <span data-ttu-id="1ea5b-199">`netstandard-targeting-pack-[major].[minor]`-Netstandard sürümünün hedeflenmesini sağlar</span><span class="sxs-lookup"><span data-stu-id="1ea5b-199">`netstandard-targeting-pack-[major].[minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="1ea5b-200">**Sürüm:** \<SDK sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-200">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="1ea5b-201">**Vardır** aşamaz</span><span class="sxs-lookup"><span data-stu-id="1ea5b-201">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="1ea5b-202">**Sürüm:** \<SDK sürüm ></span><span class="sxs-lookup"><span data-stu-id="1ea5b-202">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="1ea5b-203">**Vardır** aşamaz</span><span class="sxs-lookup"><span data-stu-id="1ea5b-203">**Contains:** (15)</span></span>

<span data-ttu-id="1ea5b-204">, `dotnet-runtime-deps-[major].[minor]` _Özel olmayan bağımlılıkların_anlaşılmasına gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-204">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro specific dependencies_.</span></span> <span data-ttu-id="1ea5b-205">Diski derleme sistemi bunu otomatik olarak türetebildiğinden, paket isteğe bağlıdır; bu durumda bu bağımlılıklar `dotnet-runtime-[major].[minor]` pakete doğrudan eklenir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-205">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="1ea5b-206">Paket içeriği sürümlü bir klasör altında olduğunda, paket adı `[major].[minor]` sürümlü klasör adıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-206">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="1ea5b-207">Dışındaki `netstandard-targeting-pack-[major].[minor]`tüm paketler için, bu, .NET Core sürümü ile de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-207">For all packages, except the `netstandard-targeting-pack-[major].[minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="1ea5b-208">Paketler arasındaki bağımlılıklar, sürüm gereksinimini _eşit veya daha büyük_ kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-208">Dependencies between packages should use a _equal or greater than_ version requirement.</span></span> <span data-ttu-id="1ea5b-209">Örneğin, `dotnet-sdk-2.2:2.2.401` gerektirir `aspnetcore-runtime-2.2 >= 2.2.6`.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-209">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="1ea5b-210">Bu, kullanıcının yüklemelerini bir kök paket (ör. `dnf update dotnet-sdk-2.2`) aracılığıyla yükseltmesini mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-210">This makes it possible for the user to upgrade their installation via a root package (e.g. `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="1ea5b-211">Çoğu dağıtım, kaynaktan oluşturulacak tüm yapıtları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-211">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="1ea5b-212">Bu, paketlere bazı etkileri vardır:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-212">This has some impact on the packages:</span></span>

- <span data-ttu-id="1ea5b-213">Altındaki `shared/Microsoft.AspNetCore.All` üçüncü taraf kitaplıkları kaynaktan kolayca derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-213">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="1ea5b-214">Bu nedenle, bu klasör `aspnetcore-runtime` paketten çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-214">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="1ea5b-215">, `NuGetFallbackFolder` Öğesinden`nuget.org`ikili yapıtlar kullanılarak doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-215">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="1ea5b-216">Boş kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-216">It should remain empty.</span></span>

<span data-ttu-id="1ea5b-217">Birden `dotnet-sdk` çok paket `NuGetFallbackFolder`için aynı dosyaları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-217">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="1ea5b-218">Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyaların aynı olması gerekir (sağlama toplamı, değiştirme tarihi vb.).</span><span class="sxs-lookup"><span data-stu-id="1ea5b-218">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="1ea5b-219">Paket oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ea5b-219">Building packages</span></span>

<span data-ttu-id="1ea5b-220">[DotNet/Source-Build](https://github.com/dotnet/source-build) deposu .NET Core SDK kaynak tarbol 'in ve tüm bileşenlerinin nasıl oluşturulacağı hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-220">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="1ea5b-221">Kaynak-derleme deposunun çıktısı, bu makalenin ilk bölümünde açıklanan düzen ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-221">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
