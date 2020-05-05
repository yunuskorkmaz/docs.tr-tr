---
title: .NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu
description: .NET Core 'da çalışma zamanı tanımlayıcısı (RID) ve RID 'Lerin nasıl kullanıldığı hakkında bilgi edinin.
ms.date: 02/22/2019
ms.openlocfilehash: b581f46becc6808ca957ac66c0c22e5e5f973bd1
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795566"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="693a1-103">.NET Core RID kataloğu</span><span class="sxs-lookup"><span data-stu-id="693a1-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="693a1-104">*Çalışma zamanı tanımlayıcısı*için RID kısadır.</span><span class="sxs-lookup"><span data-stu-id="693a1-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="693a1-105">RID değerleri, uygulamanın çalıştığı hedef platformları belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="693a1-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="693a1-106">.NET paketleri tarafından, NuGet paketlerindeki platforma özgü varlıkları göstermek için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="693a1-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="693a1-107">Aşağıdaki değerler, rids örnekleri `linux-x64`:, `ubuntu.14.04-x64`, `win7-x64`veya. `osx.10.12-x64`</span><span class="sxs-lookup"><span data-stu-id="693a1-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="693a1-108">Yerel bağımlılıklara sahip paketler için RID, paketin geri yüklenebileceği platformları belirler.</span><span class="sxs-lookup"><span data-stu-id="693a1-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="693a1-109">Tek bir RID, `<RuntimeIdentifier>` proje dosyanızın öğesinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="693a1-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="693a1-110">Çoklu RID 'Ler, proje dosyasının `<RuntimeIdentifiers>` öğesinde noktalı virgülle ayrılmış bir liste olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="693a1-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="693a1-111">Bunlar ayrıca, `--runtime` aşağıdaki [.NET Core CLI komutlarla](./tools/index.md)seçeneği aracılığıyla da kullanılır:</span><span class="sxs-lookup"><span data-stu-id="693a1-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="693a1-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="693a1-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="693a1-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="693a1-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="693a1-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="693a1-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="693a1-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="693a1-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="693a1-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="693a1-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="693a1-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="693a1-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="693a1-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="693a1-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="693a1-119">Somut işletim sistemlerini temsil eden RID 'Ler genellikle şu düzene uyar: `[os].[version]-[architecture]-[additional qualifiers]` burada:</span><span class="sxs-lookup"><span data-stu-id="693a1-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="693a1-120">`[os]`işletim/platform sistem adıdır.</span><span class="sxs-lookup"><span data-stu-id="693a1-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="693a1-121">Örneğin, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="693a1-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="693a1-122">`[version]`, bir noktayla ayrılmış (`.`) sürüm numarası biçimindeki işletim sistemi sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="693a1-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="693a1-123">Örneğin, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="693a1-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="693a1-124">Sürüm, genellikle farklı platform API yüzey alanı ile birlikte işletim sisteminin birden fazla ayrı sürümünü temsil ettiğinden, **Pazarlama sürümü olmamalıdır** .</span><span class="sxs-lookup"><span data-stu-id="693a1-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="693a1-125">`[architecture]`işlemci mimarisidir.</span><span class="sxs-lookup"><span data-stu-id="693a1-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="693a1-126">Örneğin: `x86`, `x64` `arm`, veya. `arm64`</span><span class="sxs-lookup"><span data-stu-id="693a1-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="693a1-127">`[additional qualifiers]`farklı platformları daha da birbirinden ayırt edin.</span><span class="sxs-lookup"><span data-stu-id="693a1-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="693a1-128">Örneğin: `aot`.</span><span class="sxs-lookup"><span data-stu-id="693a1-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="693a1-129">RID grafiği</span><span class="sxs-lookup"><span data-stu-id="693a1-129">RID graph</span></span>

<span data-ttu-id="693a1-130">RID Graf veya çalışma zamanı geri dönüş grafiği, birbirleriyle uyumlu RID 'lerin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="693a1-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="693a1-131">RID 'Ler, [Microsoft. NETCore. Platform](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paketinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="693a1-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="693a1-132">Desteklenen RID 'lerin ve RID grafiğinin listesini `dotnet/runtime` depoda bulunan [*Runtime. JSON*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasında görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="693a1-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the `dotnet/runtime` repository.</span></span> <span data-ttu-id="693a1-133">Bu dosyada, temel öğe hariç tüm RID 'lerin bir `"#import"` ekstre içerdiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="693a1-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="693a1-134">Bu deyimler, uyumlu RID 'Ler gösterir.</span><span class="sxs-lookup"><span data-stu-id="693a1-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="693a1-135">NuGet paketleri geri yüklediğinde, belirtilen çalışma zamanı için tam bir eşleşme bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="693a1-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="693a1-136">Tam eşleşme bulunamazsa NuGet, RID grafiğine göre en yakın uyumlu sistemi bulana kadar grafiği geri yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="693a1-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="693a1-137">Aşağıdaki örnek, `osx.10.12-x64` RID için gerçek giriştir:</span><span class="sxs-lookup"><span data-stu-id="693a1-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="693a1-138">Yukarıdaki RID, `osx.10.12-x64` içeri aktarmaların `osx.10.11-x64`belirtir.</span><span class="sxs-lookup"><span data-stu-id="693a1-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="693a1-139">Bu nedenle, NuGet paketleri geri yüklediğinde, pakette tam eşleşmeyi `osx.10.12-x64` bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="693a1-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="693a1-140">NuGet belirli çalışma zamanını bulamazsa, örneğin çalışma zamanlarını belirten `osx.10.11-x64` paketleri geri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="693a1-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="693a1-141">Aşağıdaki örnek, *çalışma zamanı. JSON* dosyasında de tanımlanan biraz daha büyük bir RID grafiği göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="693a1-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="693a1-142">Tüm RID 'Ler sonunda kök `any` RID 'e geri eşlenir.</span><span class="sxs-lookup"><span data-stu-id="693a1-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="693a1-143">RID 'Ler hakkında, bunlarla çalışırken göz önünde bulundurmanız gereken bazı noktalar vardır:</span><span class="sxs-lookup"><span data-stu-id="693a1-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="693a1-144">RID 'ler **donuk dizelerdir** ve siyah kutular olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="693a1-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="693a1-145">Program aracılığıyla RID oluşturma.</span><span class="sxs-lookup"><span data-stu-id="693a1-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="693a1-146">Platform için önceden tanımlanmış olan RID 'leri kullanın.</span><span class="sxs-lookup"><span data-stu-id="693a1-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="693a1-147">RID 'Lerin özel olması gerekir, bu nedenle gerçek RID değerinden herhangi bir şeyi varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="693a1-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="693a1-148">RID 'leri kullanma</span><span class="sxs-lookup"><span data-stu-id="693a1-148">Using RIDs</span></span>

<span data-ttu-id="693a1-149">RID 'leri kullanabilmeniz için hangi RID 'Lerin mevcut olduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="693a1-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="693a1-150">Yeni değerler platforma düzenli olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="693a1-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="693a1-151">En son ve tüm sürüm için `dotnet/runtime` depodaki [Runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="693a1-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="693a1-152">.NET Core 2,0 SDK, taşınabilir RID kavramını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="693a1-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="693a1-153">Bunlar, belirli bir sürüme veya işletim sistemi dağıtımına bağlı olmayan RID grafiğine eklenen yeni değerlerdir ve .NET Core 2,0 ve üzeri kullanılırken tercih edilen seçenektir.</span><span class="sxs-lookup"><span data-stu-id="693a1-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="693a1-154">Çoğu dağıtım merkezi taşınabilir RID 'lerle eşlendiğinden, bunlar özellikle birden çok Linux ile ilgilenirken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="693a1-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="693a1-155">Aşağıdaki liste, her bir işletim sistemi için kullanılan en yaygın RID 'lerin küçük bir alt kümesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="693a1-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="693a1-156">Windows RID 'leri</span><span class="sxs-lookup"><span data-stu-id="693a1-156">Windows RIDs</span></span>

<span data-ttu-id="693a1-157">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="693a1-157">Only common values are listed.</span></span> <span data-ttu-id="693a1-158">En son ve tüm sürüm için `dotnet/runtime` depodaki [Runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="693a1-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="693a1-159">Taşınabilir (.NET Core 2,0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="693a1-160">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="693a1-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="693a1-161">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="693a1-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="693a1-162">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="693a1-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="693a1-163">Daha fazla bilgi için bkz. [.NET Core Dependencies ve gereksinimleri](install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="693a1-163">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="693a1-164">Linux RID 'leri</span><span class="sxs-lookup"><span data-stu-id="693a1-164">Linux RIDs</span></span>

<span data-ttu-id="693a1-165">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="693a1-165">Only common values are listed.</span></span> <span data-ttu-id="693a1-166">En son ve tüm sürüm için `dotnet/runtime` depodaki [Runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="693a1-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span> <span data-ttu-id="693a1-167">Aşağıda listelenmeyen bir dağıtımı çalıştıran cihazlar taşınabilir RID 'Ler ile çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="693a1-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="693a1-168">Örneğin, listelenmemiş bir Linux dağıtımını çalıştıran Raspberry PI cihazları ile `linux-arm`hedeflenebilir.</span><span class="sxs-lookup"><span data-stu-id="693a1-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="693a1-169">Taşınabilir (.NET Core 2,0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="693a1-170">`linux-x64`(CentOS, deler, Fedora, Ubuntu ve türetmeler gibi masaüstü dağıtımlarını en iyi şekilde)</span><span class="sxs-lookup"><span data-stu-id="693a1-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="693a1-171">`linux-musl-x64`(Alp Linux gibi [MUSL](https://wiki.musl-libc.org/projects-using-musl.html) kullanan hafif dağıtımlar)</span><span class="sxs-lookup"><span data-stu-id="693a1-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="693a1-172">`linux-arm`(Raspbian gibi ARM üzerinde çalışan Linux dağıtımları Raspberry PI model 2 +)</span><span class="sxs-lookup"><span data-stu-id="693a1-172">`linux-arm` (Linux distributions running on ARM like Raspbian on Raspberry Pi Model 2+)</span></span>
  - <span data-ttu-id="693a1-173">`linux-arm64`(Raspberry PI model 3 + üzerinde Ubuntu Server 64-bit gibi 64 bit ARM üzerinde çalışan Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="693a1-173">`linux-arm64` (Linux distributions running on 64-bit ARM like Ubuntu Server 64-bit on Raspberry Pi Model 3+)</span></span>
- <span data-ttu-id="693a1-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="693a1-174">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="693a1-175">`rhel-x64`(X `linux-x64` sürüm 6 ' dan önce RHEL için yerine geçti)</span><span class="sxs-lookup"><span data-stu-id="693a1-175">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="693a1-176">`rhel.6-x64`(.NET Core 2,0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-176">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="693a1-177">Tizen (.NET Core 2,0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="693a1-178">Daha fazla bilgi için bkz. [.NET Core Dependencies ve gereksinimleri](install/dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="693a1-178">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="693a1-179">macOS RIDs</span><span class="sxs-lookup"><span data-stu-id="693a1-179">macOS RIDs</span></span>

<span data-ttu-id="693a1-180">macOS 'Ler eski "OSX" markasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="693a1-180">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="693a1-181">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="693a1-181">Only common values are listed.</span></span> <span data-ttu-id="693a1-182">En son ve tüm sürüm için `dotnet/runtime` depodaki [Runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="693a1-182">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="693a1-183">Taşınabilir (.NET Core 2,0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-183">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="693a1-184">`osx-x64`(En düşük işletim sistemi sürümü macOS 10,12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="693a1-184">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="693a1-185">macOS 10,10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="693a1-185">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="693a1-186">macOS 10,11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="693a1-186">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="693a1-187">macOS 10,12 Sierra (.NET Core 1,1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-187">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="693a1-188">macOS 10,13 High Sierra (.NET Core 1,1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-188">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="693a1-189">macOS 10,14 Mojave (.NET Core 1,1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="693a1-189">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="693a1-190">Daha fazla bilgi için bkz. [.NET Core Dependencies ve gereksinimleri](install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="693a1-190">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos).</span></span>

## <a name="see-also"></a><span data-ttu-id="693a1-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="693a1-191">See also</span></span>

- [<span data-ttu-id="693a1-192">Çalışma zamanı kimlikleri</span><span class="sxs-lookup"><span data-stu-id="693a1-192">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
