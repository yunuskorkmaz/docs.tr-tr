---
title: ".NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu"
description: "Çalışma zamanı tanımlayıcı (RID) ve RID .NET Core nasıl kullanıldığı hakkında bilgi edinin."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 067f9cfc283a14b7ea59a7454b7f593ce6eb5806
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="f5b5f-103">.NET core RID Kataloğu</span><span class="sxs-lookup"><span data-stu-id="f5b5f-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="f5b5f-104">RID kısaltması *çalışma zamanı tanımlayıcı*.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="f5b5f-105">RID değerler, uygulamanın çalıştığı Hedef platformlar tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="f5b5f-106">.NET paketleri tarafından bunlar NuGet paketlerini platforma özgü varlıkları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="f5b5f-107">Aşağıdaki değerleri RID örnekleri şunlardır: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, veya `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="f5b5f-108">Yerel bağımlılıkları olan paketleri için hangi platformlarda paketi geri yüklemesi RID belirler.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="f5b5f-109">RID ayarlanabilir `<RuntimeIdentifier>` proje dosyanızı öğesidir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-109">RIDs can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="f5b5f-110">Ayrıca aracılığıyla kullanıldıklarından `--runtime` aşağıdaki seçeneğiyle [.NET Core CLI komutları](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="f5b5f-110">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="f5b5f-111">DotNet derleme</span><span class="sxs-lookup"><span data-stu-id="f5b5f-111">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="f5b5f-112">DotNet Temizle</span><span class="sxs-lookup"><span data-stu-id="f5b5f-112">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="f5b5f-113">DotNet paketi</span><span class="sxs-lookup"><span data-stu-id="f5b5f-113">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="f5b5f-114">DotNet yayımlama</span><span class="sxs-lookup"><span data-stu-id="f5b5f-114">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="f5b5f-115">DotNet geri yükleme</span><span class="sxs-lookup"><span data-stu-id="f5b5f-115">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="f5b5f-116">dotnet çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f5b5f-116">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="f5b5f-117">DotNet deposu</span><span class="sxs-lookup"><span data-stu-id="f5b5f-117">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="f5b5f-118">Temsil somut işletim sistemleri genellikle bu deseni izlemenizi kurtarmaları: `[os].[version]-[architecture]-[additional qualifiers]` burada:</span><span class="sxs-lookup"><span data-stu-id="f5b5f-118">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="f5b5f-119">`[os]`platform/işletim sistemi addır.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-119">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="f5b5f-120">Örneğin, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-120">For example, `ubuntu`.</span></span>

- <span data-ttu-id="f5b5f-121">`[version]`işletim sistemi sürümü biçiminde noktalı virgülle ayrılmış (`.`) sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-121">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="f5b5f-122">Örneğin, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-122">For example, `15.10`.</span></span>

  - <span data-ttu-id="f5b5f-123">Sürüm **döndürmemelidir** pazarlama sürümleri, bunlar genellikle birden fazla ayrı platform API yüzey alanını değişen ile işletim sistemi sürümünü temsil.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-123">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="f5b5f-124">`[architecture]`İşlemci mimarisi ' dir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-124">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="f5b5f-125">Örneğin: `x86`, `x64`, `arm`, veya `arm64`.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-125">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="f5b5f-126">`[additional qualifiers]`Daha fazla farklı platformlarda ayırt.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-126">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="f5b5f-127">Örneğin: `aot` veya `corert`.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-127">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="f5b5f-128">RID grafiği</span><span class="sxs-lookup"><span data-stu-id="f5b5f-128">RID graph</span></span>

<span data-ttu-id="f5b5f-129">RID grafik veya çalışma zamanı geri dönüş grafik birbiriyle uyumlu RID listesidir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-129">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="f5b5f-130">RID tanımlanan [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paket.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-130">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="f5b5f-131">Desteklenen RID'ler ve RID grafikte listesini görebilir [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) CoreFX depodaki bulunduğu dosya.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-131">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="f5b5f-132">Bu dosyada, tüm RID olduğunu, temel biri için içeren dışında görebilirsiniz bir `"#import"` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-132">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="f5b5f-133">Bu deyimler uyumlu RID gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-133">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="f5b5f-134">NuGet paketleri geri yüklerken belirtilen çalışma zamanı için tam bir eşleşme bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-134">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="f5b5f-135">Tam bir eşleşme bulunmazsa RID grafik göre en yakın uyumlu sistem bulana kadar NuGet geri grafiği anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-135">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="f5b5f-136">Aşağıdaki örnek için gerçek giriştir `osx.10.12-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="f5b5f-136">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="f5b5f-137">Yukarıdaki RID belirleyen `osx.10.12-x64` alır `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-137">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="f5b5f-138">NuGet paketleri geri yüklerse, bu nedenle, onu için tam bir eşleşme bulmaya çalışır `osx.10.12-x64` paketinde.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-138">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="f5b5f-139">NuGet belirli çalışma zamanı bulamazsanız, belirttiğiniz paketler geri yükleyebilirsiniz `osx.10.11-x64` örneğin çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-139">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="f5b5f-140">Aşağıdaki örnek, ayrıca tanımlanan biraz daha büyük bir RID grafik gösterir *runtime.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="f5b5f-140">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="f5b5f-141">Tüm RID sonunda kök geri eşlemek `any` RID.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-141">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="f5b5f-142">Bunları ile çalışırken göz önünde bulundurmanız gereken RID hakkında bazı noktalar vardır:</span><span class="sxs-lookup"><span data-stu-id="f5b5f-142">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="f5b5f-143">RID olan **donuk dizeleri** ve siyah kutular değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-143">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="f5b5f-144">RID program aracılığıyla yapı yok.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-144">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="f5b5f-145">Önceden tanımlanmış RID platformu için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-145">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="f5b5f-146">RID herhangi bir şeyin gerçek RID değer varsaymayın şekilde belirli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-146">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="f5b5f-147">RID kullanma</span><span class="sxs-lookup"><span data-stu-id="f5b5f-147">Using RIDs</span></span>

<span data-ttu-id="f5b5f-148">RID kullanmak, RID mevcut bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-148">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="f5b5f-149">Yeni değerler düzenli aralıklarla platforma eklenir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-149">New values are added regularly to the platform.</span></span>
<span data-ttu-id="f5b5f-150">En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) CoreFX depodaki dosyada.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-150">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="f5b5f-151">.NET core 2.0 SDK taşınabilir RID kavramını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-151">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="f5b5f-152">Belirli bir sürüm ya da işletim sistemi dağıtım bağlı olmayan RID grafiğe eklenen yeni değerleri oldukları.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-152">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="f5b5f-153">Bunlar, birden çok Linux distro'lar ile ilgilenirken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-153">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="f5b5f-154">Aşağıdaki liste, her işletim sistemi için kullanılan en yaygın RID gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-154">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="f5b5f-155">Bu kapsamıyordur `arm` veya `corert` değerleri.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-155">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="f5b5f-156">Windows RID</span><span class="sxs-lookup"><span data-stu-id="f5b5f-156">Windows RIDs</span></span>

- <span data-ttu-id="f5b5f-157">Taşınabilir</span><span class="sxs-lookup"><span data-stu-id="f5b5f-157">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="f5b5f-158">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="f5b5f-158">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="f5b5f-159">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f5b5f-159">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="f5b5f-160">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f5b5f-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="f5b5f-161">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="f5b5f-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="f5b5f-162">Bkz: [.NET Core Windows önkoşulları](windows-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-162">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="f5b5f-163">Linux RID</span><span class="sxs-lookup"><span data-stu-id="f5b5f-163">Linux RIDs</span></span>

- <span data-ttu-id="f5b5f-164">Taşınabilir</span><span class="sxs-lookup"><span data-stu-id="f5b5f-164">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="f5b5f-165">CentOS</span><span class="sxs-lookup"><span data-stu-id="f5b5f-165">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="f5b5f-166">Debian</span><span class="sxs-lookup"><span data-stu-id="f5b5f-166">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="f5b5f-167">Fedora</span><span class="sxs-lookup"><span data-stu-id="f5b5f-167">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="f5b5f-168">`fedora.25-x64`(.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-168">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="f5b5f-169">`fedora.26-x64`(.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-169">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="f5b5f-170">Gentoo (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-170">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="f5b5f-171">openSUSE</span><span class="sxs-lookup"><span data-stu-id="f5b5f-171">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="f5b5f-172">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="f5b5f-172">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="f5b5f-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="f5b5f-173">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="f5b5f-174">`rhel.6-x64`(.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-174">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="f5b5f-175">`rhel.7.3-x64`(.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-175">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="f5b5f-176">`rhel.7.4-x64`(.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-176">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="f5b5f-177">Tizen (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="f5b5f-178">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f5b5f-178">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="f5b5f-179">Ubuntu türevleri</span><span class="sxs-lookup"><span data-stu-id="f5b5f-179">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="f5b5f-180">`linuxmint.18.1-x64`(.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-180">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="f5b5f-181">Bkz: [.NET Core Linux önkoşulları](linux-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-181">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="f5b5f-182">macOS RID</span><span class="sxs-lookup"><span data-stu-id="f5b5f-182">macOS RIDs</span></span>

<span data-ttu-id="f5b5f-183">macOS RID eski markalama "OSX" kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-183">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="f5b5f-184">`osx-x64`(.NET core 2.0 veya sonraki sürümler, en düşük sürüm olan `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-184">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="f5b5f-185">`osx.10.12-x64`(.NET core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-185">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="f5b5f-186">Bkz: [.NET Core üzerinde macOS önkoşulları](macos-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-186">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="f5b5f-187">Android RID (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="f5b5f-187">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="f5b5f-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5b5f-188">See also</span></span>

[<span data-ttu-id="f5b5f-189">Çalışma zamanı kimlikleri</span><span class="sxs-lookup"><span data-stu-id="f5b5f-189">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
