---
title: .NET core çalışma zamanı tanımlayıcı (RID) Kataloğu
description: Çalışma zamanı tanımlayıcı (RID) ve RID'de .NET Core nasıl kullanıldığı hakkında bilgi edinin.
ms.date: 02/22/2019
ms.openlocfilehash: 0d03e39c755b43e145edf5efe48422cbae7abcab
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745748"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="c47fd-103">.NET core RID Kataloğu</span><span class="sxs-lookup"><span data-stu-id="c47fd-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="c47fd-104">RID kısaltması *çalışma zamanı tanımlayıcısı*.</span><span class="sxs-lookup"><span data-stu-id="c47fd-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="c47fd-105">RID değerler, uygulamanın çalıştığı hedef platformları belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c47fd-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="c47fd-106">.NET paketleri tarafından NuGet paketlerini platforma özgü varlıkları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c47fd-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="c47fd-107">Aşağıdaki değerleri RID'ler örnekleridir: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, veya `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="c47fd-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="c47fd-108">Yerel bağımlılıkları olan paketleri için hangi platformlarda paket geri yüklenebilir RID belirler.</span><span class="sxs-lookup"><span data-stu-id="c47fd-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="c47fd-109">Tek bir RID ayarlanabilir `<RuntimeIdentifier>` proje dosyanızın öğesi.</span><span class="sxs-lookup"><span data-stu-id="c47fd-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="c47fd-110">Proje dosyasının noktalı virgülle ayrılmış bir liste olarak birden fazla RID tanımlanabilir `<RuntimeIdentifiers>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c47fd-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="c47fd-111">Bunlar ayrıca aracılığıyla kullanılırlar `--runtime` aşağıdaki seçeneğiyle [.NET Core CLI komutları](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="c47fd-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="c47fd-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c47fd-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="c47fd-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="c47fd-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="c47fd-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="c47fd-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="c47fd-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="c47fd-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="c47fd-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="c47fd-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="c47fd-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="c47fd-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="c47fd-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="c47fd-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="c47fd-119">Temsil somut işletim sistemleri genellikle bu deseni izlemenizi kurtarmaları: `[os].[version]-[architecture]-[additional qualifiers]` burada:</span><span class="sxs-lookup"><span data-stu-id="c47fd-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="c47fd-120">`[os]` / platform işletim sistemi addır.</span><span class="sxs-lookup"><span data-stu-id="c47fd-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="c47fd-121">Örneğin: `ubuntu`</span><span class="sxs-lookup"><span data-stu-id="c47fd-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="c47fd-122">`[version]` işletim sistemi sürümü biçiminde noktalı virgülle ayrılmış (`.`) sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="c47fd-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="c47fd-123">Örneğin: `15.10`</span><span class="sxs-lookup"><span data-stu-id="c47fd-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="c47fd-124">Sürüm **olmamalıdır** pazarlama sürümleri gibi bunlar genellikle ayrı birden çok platformu API yüzey alanı değişen ile işletim sistemi sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c47fd-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="c47fd-125">`[architecture]` İşlemci mimaridir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="c47fd-126">Örneğin: `x86`, `x64`, `arm`, veya `arm64`.</span><span class="sxs-lookup"><span data-stu-id="c47fd-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="c47fd-127">`[additional qualifiers]` Daha fazla farklı platformları ayırt.</span><span class="sxs-lookup"><span data-stu-id="c47fd-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="c47fd-128">Örneğin: `aot`</span><span class="sxs-lookup"><span data-stu-id="c47fd-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="c47fd-129">RID grafiği</span><span class="sxs-lookup"><span data-stu-id="c47fd-129">RID graph</span></span>

<span data-ttu-id="c47fd-130">RID grafik veya çalışma zamanı geri dönüş graf birbiriyle uyumlu RID'ler bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="c47fd-131">RID tanımlanan [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paket.</span><span class="sxs-lookup"><span data-stu-id="c47fd-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="c47fd-132">Desteklenen RID'ler ve RID grafikte listesini görebilirsiniz [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) adresinde Corefx'te deponun bulunan dosya.</span><span class="sxs-lookup"><span data-stu-id="c47fd-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="c47fd-133">Bu dosyada, tüm RID olduğunu, temel bir için içermesi dışında görebilirsiniz bir `"#import"` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c47fd-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="c47fd-134">Bu deyimler uyumlu RID'ler gösterir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="c47fd-135">NuGet paketleri geri yükler, belirtilen çalışma zamanı için tam bir eşleşme bulmayı dener.</span><span class="sxs-lookup"><span data-stu-id="c47fd-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="c47fd-136">Tam bir eşleşme bulunmazsa, RID grafiğe göre en yakın uyumlu sistemi bulana kadar NuGet geri graf gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="c47fd-137">Aşağıdaki örnek, gerçek girişini `osx.10.12-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="c47fd-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="c47fd-138">Yukarıdaki RID belirten `osx.10.12-x64` aktarır `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="c47fd-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="c47fd-139">NuGet paketleri geri yükler, bu nedenle, tam bir eşleşme için bulmayı dener `osx.10.12-x64` paketteki.</span><span class="sxs-lookup"><span data-stu-id="c47fd-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="c47fd-140">NuGet belirli çalışma zamanı bulamazsanız, belirttiğiniz paketleri geri yükleyebilirsiniz `osx.10.11-x64` örneğin çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="c47fd-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="c47fd-141">Aşağıdaki örnek, ayrıca tanımlanan biraz daha büyük bir RID grafiği gösterir. *runtime.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c47fd-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="c47fd-142">Tüm RID sonunda kök dizinine eşlemek `any` RID.</span><span class="sxs-lookup"><span data-stu-id="c47fd-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="c47fd-143">Bunları ile çalışırken göz önünde bulundurmanız sahip RID'ler hakkında bazı noktalar vardır:</span><span class="sxs-lookup"><span data-stu-id="c47fd-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="c47fd-144">RID olan **donuk dizeleri** ve kara kutular değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="c47fd-145">RID programlı olarak oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="c47fd-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="c47fd-146">Önceden tanımlanmış RID'ler platformu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c47fd-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="c47fd-147">RID gerçek RID değerinden herhangi bir şey varsaymayın şekilde belirli gerekir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="c47fd-148">RID kullanma</span><span class="sxs-lookup"><span data-stu-id="c47fd-148">Using RIDs</span></span>

<span data-ttu-id="c47fd-149">RID kullanabilmek için RID mevcut bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="c47fd-150">Yeni değerleri, platform için düzenli olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="c47fd-151">En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.</span><span class="sxs-lookup"><span data-stu-id="c47fd-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="c47fd-152">.NET core 2.0 SDK'sını taşınabilir RID'ler kavramını sunar.</span><span class="sxs-lookup"><span data-stu-id="c47fd-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="c47fd-153">Bunlar, belirli bir sürümü ya da işletim sistemi dağıtım bağlı değil ve .NET Core 2.0 ve üzeri kullanıyorsanız tercih RID grafiğe eklenen yeni değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="c47fd-154">Birden çok Linux dağıtım paketlerini dağıtım RID'ler çoğu bu yana uğraşmanızı eşlendi olduğunda taşınabilir RID'ler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c47fd-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="c47fd-155">Aşağıdaki liste, her bir işletim sistemi için kullanılan en yaygın RID'ler küçük bir kısmı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="c47fd-156">Windows RID</span><span class="sxs-lookup"><span data-stu-id="c47fd-156">Windows RIDs</span></span>

<span data-ttu-id="c47fd-157">Yalnızca ortak değerleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-157">Only common values are listed.</span></span> <span data-ttu-id="c47fd-158">En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.</span><span class="sxs-lookup"><span data-stu-id="c47fd-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="c47fd-159">Taşınabilir (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="c47fd-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c47fd-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="c47fd-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c47fd-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="c47fd-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c47fd-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="c47fd-163">Bkz: [Windows üzerinde .NET Core önkoşulları](windows-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c47fd-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="c47fd-164">Linux RID</span><span class="sxs-lookup"><span data-stu-id="c47fd-164">Linux RIDs</span></span>

<span data-ttu-id="c47fd-165">Yalnızca ortak değerleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-165">Only common values are listed.</span></span> <span data-ttu-id="c47fd-166">En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.</span><span class="sxs-lookup"><span data-stu-id="c47fd-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span> <span data-ttu-id="c47fd-167">Aşağıdaki listede bulunmayan bir dağıtım çalıştıran cihazlar, taşınabilir RID'ler biri ile çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="c47fd-168">Örneğin, listede olmayan bir Linux dağıtımı çalıştıran Raspberry Pi cihazlar ile hedeflenebilir `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="c47fd-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="c47fd-169">Taşınabilir (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="c47fd-170">`linux-x64` (CentOS, Debian, Fedora, Ubuntu ve türevleri çoğu masaüstü dağıtımları ister)</span><span class="sxs-lookup"><span data-stu-id="c47fd-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu and derivatives)</span></span>
  - <span data-ttu-id="c47fd-171">`linux-musl-x64` (Kullanan basit dağıtımlar [musl](https://wiki.musl-libc.org/projects-using-musl.html) ister Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="c47fd-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="c47fd-172">`linux-arm` (ARM üzerinde çalışan Linux dağıtımları, Raspberry Pi gibi)</span><span class="sxs-lookup"><span data-stu-id="c47fd-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="c47fd-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="c47fd-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="c47fd-174">`rhel-x64` (Yerini `linux-x64` RHEL sürümünden sonraki bir sürümü 6'için)</span><span class="sxs-lookup"><span data-stu-id="c47fd-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="c47fd-175">`rhel.6-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="c47fd-176">Tizen (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="c47fd-177">Bkz: [Linux üzerinde .NET Core önkoşulları](linux-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c47fd-177">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="c47fd-178">macOS RID</span><span class="sxs-lookup"><span data-stu-id="c47fd-178">macOS RIDs</span></span>

<span data-ttu-id="c47fd-179">macOS RID'ler eski markalama "OSX" kullanın.</span><span class="sxs-lookup"><span data-stu-id="c47fd-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="c47fd-180">Yalnızca ortak değerleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c47fd-180">Only common values are listed.</span></span> <span data-ttu-id="c47fd-181">En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.</span><span class="sxs-lookup"><span data-stu-id="c47fd-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="c47fd-182">Taşınabilir (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="c47fd-183">`osx-x64` (En düşük işletim sistemi sürümü olan macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="c47fd-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="c47fd-184">macOS 10.10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="c47fd-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="c47fd-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="c47fd-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="c47fd-186">macOS 10.12 Sierra (.NET Core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="c47fd-187">macOS 10.13 High Sierra (.NET Core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="c47fd-188">macOS 10.14 Mojave (.NET Core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="c47fd-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="c47fd-189">Bkz: [macos'ta .NET Core önkoşulları](macos-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c47fd-189">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="c47fd-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c47fd-190">See also</span></span>

- [<span data-ttu-id="c47fd-191">Çalışma zamanı kimlikleri</span><span class="sxs-lookup"><span data-stu-id="c47fd-191">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
