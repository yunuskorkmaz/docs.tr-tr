---
title: .NET Core Runtime Tanımlayıcı (RID) kataloğu
description: Runtime Tanımlayıcı (RID) ve RID'lerin .NET Core'da nasıl kullanıldığı hakkında bilgi edinin.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451739"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="fb75c-103">.NET Core RID Kataloğu</span><span class="sxs-lookup"><span data-stu-id="fb75c-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="fb75c-104">RID, *Runtime Tanımlayıcı'nın kısaltmasıdır.*</span><span class="sxs-lookup"><span data-stu-id="fb75c-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="fb75c-105">RID değerleri, uygulamanın çalıştığı hedef platformları tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb75c-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="fb75c-106">.NET paketleri tarafından NuGet paketlerinde platforma özgü varlıkları temsil etmek için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="fb75c-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="fb75c-107">Aşağıdaki değerler, RID'lere `linux-x64`örnektir: `win7-x64`, `osx.10.12-x64`, `ubuntu.14.04-x64`veya .</span><span class="sxs-lookup"><span data-stu-id="fb75c-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="fb75c-108">Yerel bağımlılıkları olan paketler için RID, paketin hangi platformlarda geri yüklenebileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="fb75c-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="fb75c-109">Proje dosyanızın `<RuntimeIdentifier>` öğesinde tek bir RID ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="fb75c-110">Birden çok RID, proje dosyasının `<RuntimeIdentifiers>` öğesinde yarı sütunlu sınırlı bir liste olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="fb75c-111">Ayrıca aşağıdaki `--runtime` [.NET Core CLI komutları](./tools/index.md)ile seçenek üzerinden kullanılır:</span><span class="sxs-lookup"><span data-stu-id="fb75c-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="fb75c-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="fb75c-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="fb75c-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="fb75c-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="fb75c-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="fb75c-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="fb75c-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="fb75c-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="fb75c-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="fb75c-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="fb75c-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="fb75c-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="fb75c-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="fb75c-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="fb75c-119">Beton işletim sistemlerini temsil eden RID'ler genellikle şu deseni izler: `[os].[version]-[architecture]-[additional qualifiers]` aşağıdakiler:</span><span class="sxs-lookup"><span data-stu-id="fb75c-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="fb75c-120">`[os]`işletim/platform sistem takma adıdır.</span><span class="sxs-lookup"><span data-stu-id="fb75c-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="fb75c-121">Örneğin, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="fb75c-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="fb75c-122">`[version]`nokta ayrılmış (`.`) sürüm numarası şeklinde işletim sistemi sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="fb75c-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="fb75c-123">Örneğin, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="fb75c-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="fb75c-124">Sürüm pazarlama sürümleri **olmamalıdır,** çünkü bunlar genellikle farklı platform API yüzey alanına sahip işletim sisteminin birden fazla ayrı sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb75c-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="fb75c-125">`[architecture]`işlemci mimarisidir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="fb75c-126">Örneğin: `x86`, `x64` `arm`, `arm64`, veya .</span><span class="sxs-lookup"><span data-stu-id="fb75c-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="fb75c-127">`[additional qualifiers]`farklı platformları daha da farklılaştırmak.</span><span class="sxs-lookup"><span data-stu-id="fb75c-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="fb75c-128">Örneğin: `aot`.</span><span class="sxs-lookup"><span data-stu-id="fb75c-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="fb75c-129">RID grafiği</span><span class="sxs-lookup"><span data-stu-id="fb75c-129">RID graph</span></span>

<span data-ttu-id="fb75c-130">RID grafiği veya çalışma zamanı geri dönüş grafiği, birbiriyle uyumlu OLAN RID'lerin listesidir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="fb75c-131">RID'ler [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paketinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fb75c-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="fb75c-132">Desteklenen RID'lerin listesini ve depoda bulunan [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasında RID grafiğini `dotnet/runtime` görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb75c-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the `dotnet/runtime` repository.</span></span> <span data-ttu-id="fb75c-133">Bu dosyada, temel bir hariç tüm RID'lerin bir `"#import"` deyim içerdiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb75c-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="fb75c-134">Bu ifadeler uyumlu RID'leri gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="fb75c-135">NuGet paketleri geri yüklediğinde, belirtilen çalışma süresi için tam bir eşleşme bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="fb75c-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="fb75c-136">Tam bir eşleşme bulunamazsa, NuGet RID grafiğine göre en yakın uyumlu sistemi bulana kadar grafiği geri alır.</span><span class="sxs-lookup"><span data-stu-id="fb75c-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="fb75c-137">Aşağıdaki örnek `osx.10.12-x64` RID için gerçek giriştir:</span><span class="sxs-lookup"><span data-stu-id="fb75c-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="fb75c-138">Yukarıdaki RID bu `osx.10.12-x64` ithalat `osx.10.11-x64`belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="fb75c-139">Bu nedenle, NuGet paketleri geri yüklediğinde, pakettekilerle `osx.10.12-x64` tam olarak eşleşmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="fb75c-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="fb75c-140">NuGet belirli çalışma zamanını bulamıyorsa, örneğin `osx.10.11-x64` çalışma sürelerini belirten paketleri geri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="fb75c-141">Aşağıdaki örnek, *runtime.json* dosyasında da tanımlanan biraz daha büyük bir RID grafiği ni gösterir:</span><span class="sxs-lookup"><span data-stu-id="fb75c-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="fb75c-142">Tüm RID'ler sonunda kök `any` RID geri eşler.</span><span class="sxs-lookup"><span data-stu-id="fb75c-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="fb75c-143">RID'ler hakkında onlarla çalışırken göz önünde bulundurmanız gereken bazı hususlar vardır:</span><span class="sxs-lookup"><span data-stu-id="fb75c-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="fb75c-144">RID'ler **opak dizeleri** ve kara kutular olarak kabul edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="fb75c-145">PROGRAMLI RİD'ler oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="fb75c-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="fb75c-146">Platform için zaten tanımlanmış OLAN RID'leri kullanın.</span><span class="sxs-lookup"><span data-stu-id="fb75c-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="fb75c-147">RID'lerin belirli olması gerekir, bu nedenle gerçek RID değerinden hiçbir şey varsayma.</span><span class="sxs-lookup"><span data-stu-id="fb75c-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="fb75c-148">RID'leri kullanma</span><span class="sxs-lookup"><span data-stu-id="fb75c-148">Using RIDs</span></span>

<span data-ttu-id="fb75c-149">RID'leri kullanabilmek için, hangi RID'lerin var olduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="fb75c-150">Platforma düzenli olarak yeni değerler eklenir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="fb75c-151">En son ve tam sürüm için depodaki [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına `dotnet/runtime` bakın.</span><span class="sxs-lookup"><span data-stu-id="fb75c-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="fb75c-152">.NET Core 2.0 SDK taşınabilir RED kavramını tanıttı.</span><span class="sxs-lookup"><span data-stu-id="fb75c-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="fb75c-153">Rid grafiğine belirli bir sürüme veya işletim sistemi dağıtımına bağlı olmayan yeni değerlerdir ve .NET Core 2.0 ve üzeri ni kullanırken tercih edilen değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="fb75c-154">Çoğu dağıtım RID'si taşınabilir RID'lere eşlendiğinden, birden fazla Linux dağıtımıyla uğraşırken özellikle yararlıdırlar.</span><span class="sxs-lookup"><span data-stu-id="fb75c-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="fb75c-155">Aşağıdaki liste, her işletim sistemi için kullanılan en yaygın RID'lerin küçük bir alt kümesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="fb75c-156">Windows RID'leri</span><span class="sxs-lookup"><span data-stu-id="fb75c-156">Windows RIDs</span></span>

<span data-ttu-id="fb75c-157">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-157">Only common values are listed.</span></span> <span data-ttu-id="fb75c-158">En son ve tam sürüm için, depodaki `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="fb75c-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="fb75c-159">Taşınabilir (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="fb75c-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="fb75c-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fb75c-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="fb75c-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fb75c-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="fb75c-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fb75c-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="fb75c-163">Daha fazla bilgi için [bkz.](install/dependencies.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="fb75c-163">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="fb75c-164">Linux RID'leri</span><span class="sxs-lookup"><span data-stu-id="fb75c-164">Linux RIDs</span></span>

<span data-ttu-id="fb75c-165">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-165">Only common values are listed.</span></span> <span data-ttu-id="fb75c-166">En son ve tam sürüm için depodaki [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına `dotnet/runtime` bakın.</span><span class="sxs-lookup"><span data-stu-id="fb75c-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span> <span data-ttu-id="fb75c-167">Aşağıda listelenmemiş bir dağıtım çalıştıran aygıtlar Taşınabilir KOPYALARDAN biriyle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="fb75c-168">Örneğin, listelenmemiş bir Linux dağıtımı çalıştıran Raspberry `linux-arm`Pi cihazları .</span><span class="sxs-lookup"><span data-stu-id="fb75c-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="fb75c-169">Taşınabilir (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="fb75c-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="fb75c-170">`linux-x64`(CentOS, Debian, Fedora, Ubuntu ve türevleri gibi çoğu masaüstü dağıtımı)</span><span class="sxs-lookup"><span data-stu-id="fb75c-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="fb75c-171">`linux-musl-x64`(Alpine Linux gibi [musl](https://wiki.musl-libc.org/projects-using-musl.html) kullanarak hafif dağıtımlar)</span><span class="sxs-lookup"><span data-stu-id="fb75c-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="fb75c-172">`linux-arm`(Linux dağıtımları Raspberry Pi gibi ARM çalışan)</span><span class="sxs-lookup"><span data-stu-id="fb75c-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="fb75c-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fb75c-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="fb75c-174">`rhel-x64`(Sürüm 6 yukarıdaki `linux-x64` RHEL için superseded)</span><span class="sxs-lookup"><span data-stu-id="fb75c-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="fb75c-175">`rhel.6-x64`(.NET Core 2.0 veya sonraki sürümleri)</span><span class="sxs-lookup"><span data-stu-id="fb75c-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="fb75c-176">Tizen (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="fb75c-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="fb75c-177">Daha fazla bilgi için [bkz.](install/dependencies.md?pivots=os-linux)</span><span class="sxs-lookup"><span data-stu-id="fb75c-177">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="fb75c-178">macOS IDA'ları</span><span class="sxs-lookup"><span data-stu-id="fb75c-178">macOS RIDs</span></span>

<span data-ttu-id="fb75c-179">macOS ID'leri eski "OSX" markasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb75c-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="fb75c-180">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="fb75c-180">Only common values are listed.</span></span> <span data-ttu-id="fb75c-181">En son ve tam sürüm için depodaki [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına `dotnet/runtime` bakın.</span><span class="sxs-lookup"><span data-stu-id="fb75c-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="fb75c-182">Taşınabilir (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="fb75c-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="fb75c-183">`osx-x64`(Minimum işletim sistemi sürümü macOS 10.12 Sierra' dır)</span><span class="sxs-lookup"><span data-stu-id="fb75c-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="fb75c-184">macOS 10.10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="fb75c-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="fb75c-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="fb75c-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="fb75c-186">macOS 10.12 Sierra (.NET Core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="fb75c-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="fb75c-187">macOS 10.13 High Sierra (.NET Core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="fb75c-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="fb75c-188">macOS 10.14 Mojave (.NET Core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="fb75c-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="fb75c-189">Daha fazla bilgi için [bkz.](install/dependencies.md?pivots=os-macos)</span><span class="sxs-lookup"><span data-stu-id="fb75c-189">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb75c-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb75c-190">See also</span></span>

- [<span data-ttu-id="fb75c-191">Çalışma Zamanı T'leri</span><span class="sxs-lookup"><span data-stu-id="fb75c-191">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
