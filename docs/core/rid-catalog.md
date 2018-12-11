---
title: .NET core çalışma zamanı tanımlayıcı (RID) Kataloğu
description: Çalışma zamanı tanımlayıcı (RID) ve RID'de .NET Core nasıl kullanıldığı hakkında bilgi edinin.
ms.date: 07/19/2018
ms.openlocfilehash: b801b7866b563ae06499d8ccd2d07cf5fd52b928
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170216"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="d9926-103">.NET core RID Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d9926-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="d9926-104">RID kısaltması *çalışma zamanı tanımlayıcısı*.</span><span class="sxs-lookup"><span data-stu-id="d9926-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="d9926-105">RID değerler, uygulamanın çalıştığı hedef platformları belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9926-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="d9926-106">.NET paketleri tarafından NuGet paketlerini platforma özgü varlıkları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9926-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="d9926-107">Aşağıdaki değerleri RID'ler örnekleridir: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, veya `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="d9926-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="d9926-108">Yerel bağımlılıkları olan paketleri için hangi platformlarda paket geri yüklenebilir RID belirler.</span><span class="sxs-lookup"><span data-stu-id="d9926-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="d9926-109">Tek bir RID ayarlanabilir `<RuntimeIdentifier>` proje dosyanızın öğesi.</span><span class="sxs-lookup"><span data-stu-id="d9926-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="d9926-110">Proje dosyasının noktalı virgülle ayrılmış bir liste olarak birden fazla RID tanımlanabilir `<RuntimeIdentifiers>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d9926-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="d9926-111">Bunlar ayrıca aracılığıyla kullanılırlar `--runtime` aşağıdaki seçeneğiyle [.NET Core CLI komutları](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="d9926-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="d9926-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d9926-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="d9926-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d9926-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="d9926-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d9926-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="d9926-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d9926-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="d9926-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d9926-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="d9926-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d9926-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="d9926-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d9926-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="d9926-119">Temsil somut işletim sistemleri genellikle bu deseni izlemenizi kurtarmaları: `[os].[version]-[architecture]-[additional qualifiers]` burada:</span><span class="sxs-lookup"><span data-stu-id="d9926-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="d9926-120">`[os]` / platform işletim sistemi addır.</span><span class="sxs-lookup"><span data-stu-id="d9926-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="d9926-121">Örneğin: `ubuntu`</span><span class="sxs-lookup"><span data-stu-id="d9926-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="d9926-122">`[version]` işletim sistemi sürümü biçiminde noktalı virgülle ayrılmış (`.`) sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="d9926-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="d9926-123">Örneğin: `15.10`</span><span class="sxs-lookup"><span data-stu-id="d9926-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="d9926-124">Sürüm **olmamalıdır** pazarlama sürümleri gibi bunlar genellikle ayrı birden çok platformu API yüzey alanı değişen ile işletim sistemi sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9926-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="d9926-125">`[architecture]` İşlemci mimaridir.</span><span class="sxs-lookup"><span data-stu-id="d9926-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="d9926-126">Örneğin: `x86`, `x64`, `arm`, veya `arm64`.</span><span class="sxs-lookup"><span data-stu-id="d9926-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="d9926-127">`[additional qualifiers]` Daha fazla farklı platformları ayırt.</span><span class="sxs-lookup"><span data-stu-id="d9926-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="d9926-128">Örneğin: `aot` veya `corert`.</span><span class="sxs-lookup"><span data-stu-id="d9926-128">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="d9926-129">RID grafiği</span><span class="sxs-lookup"><span data-stu-id="d9926-129">RID graph</span></span>

<span data-ttu-id="d9926-130">RID grafik veya çalışma zamanı geri dönüş graf birbiriyle uyumlu RID'ler bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="d9926-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="d9926-131">RID tanımlanan [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paket.</span><span class="sxs-lookup"><span data-stu-id="d9926-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="d9926-132">Desteklenen RID'ler ve RID grafikte listesini görebilirsiniz [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) adresinde Corefx'te deponun bulunan dosya.</span><span class="sxs-lookup"><span data-stu-id="d9926-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="d9926-133">Bu dosyada, tüm RID olduğunu, temel bir için içermesi dışında görebilirsiniz bir `"#import"` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d9926-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="d9926-134">Bu deyimler uyumlu RID'ler gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9926-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="d9926-135">NuGet paketleri geri yükler, belirtilen çalışma zamanı için tam bir eşleşme bulmayı dener.</span><span class="sxs-lookup"><span data-stu-id="d9926-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="d9926-136">Tam bir eşleşme bulunmazsa, RID grafiğe göre en yakın uyumlu sistemi bulana kadar NuGet geri graf gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9926-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="d9926-137">Aşağıdaki örnek, gerçek girişini `osx.10.12-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="d9926-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="d9926-138">Yukarıdaki RID belirten `osx.10.12-x64` aktarır `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="d9926-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="d9926-139">NuGet paketleri geri yükler, bu nedenle, tam bir eşleşme için bulmayı dener `osx.10.12-x64` paketteki.</span><span class="sxs-lookup"><span data-stu-id="d9926-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="d9926-140">NuGet belirli çalışma zamanı bulamazsanız, belirttiğiniz paketleri geri yükleyebilirsiniz `osx.10.11-x64` örneğin çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="d9926-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="d9926-141">Aşağıdaki örnek, ayrıca tanımlanan biraz daha büyük bir RID grafiği gösterir. *runtime.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="d9926-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="d9926-142">Tüm RID sonunda kök dizinine eşlemek `any` RID.</span><span class="sxs-lookup"><span data-stu-id="d9926-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="d9926-143">Bunları ile çalışırken göz önünde bulundurmanız sahip RID'ler hakkında bazı noktalar vardır:</span><span class="sxs-lookup"><span data-stu-id="d9926-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="d9926-144">RID olan **donuk dizeleri** ve kara kutular değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d9926-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="d9926-145">RID programlı olarak oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="d9926-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="d9926-146">Önceden tanımlanmış RID'ler platformu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9926-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="d9926-147">RID gerçek RID değerinden herhangi bir şey varsaymayın şekilde belirli gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9926-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="d9926-148">RID kullanma</span><span class="sxs-lookup"><span data-stu-id="d9926-148">Using RIDs</span></span>

<span data-ttu-id="d9926-149">RID kullanabilmek için RID mevcut bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9926-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="d9926-150">Yeni değerleri, platform için düzenli olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9926-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="d9926-151">En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.</span><span class="sxs-lookup"><span data-stu-id="d9926-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="d9926-152">.NET core 2.0 SDK'sını taşınabilir RID'ler kavramını sunar.</span><span class="sxs-lookup"><span data-stu-id="d9926-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="d9926-153">Belirli bir sürümü ya da işletim sistemi dağıtım bağlı olmayan RID grafiğe eklenen yeni değerleri oldukları.</span><span class="sxs-lookup"><span data-stu-id="d9926-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="d9926-154">Bunlar, birden çok Linux dağıtımları ile ilgilenirken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d9926-154">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="d9926-155">Aşağıdaki liste, her bir işletim sistemi için kullanılan en yaygın RID'ler gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9926-155">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="d9926-156">Ele alınmamıştır `arm` veya `corert` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d9926-156">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="d9926-157">Windows RID</span><span class="sxs-lookup"><span data-stu-id="d9926-157">Windows RIDs</span></span>

- <span data-ttu-id="d9926-158">Taşınabilir</span><span class="sxs-lookup"><span data-stu-id="d9926-158">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="d9926-159">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d9926-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="d9926-160">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d9926-160">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="d9926-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d9926-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="d9926-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d9926-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="d9926-163">Bkz: [Windows üzerinde .NET Core önkoşulları](windows-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d9926-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="d9926-164">Linux RID</span><span class="sxs-lookup"><span data-stu-id="d9926-164">Linux RIDs</span></span>

- <span data-ttu-id="d9926-165">Taşınabilir</span><span class="sxs-lookup"><span data-stu-id="d9926-165">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="d9926-166">CentOS</span><span class="sxs-lookup"><span data-stu-id="d9926-166">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="d9926-167">Debian</span><span class="sxs-lookup"><span data-stu-id="d9926-167">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
  - <span data-ttu-id="d9926-168">`debian.9-x64` (.NET core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-168">`debian.9-x64` (.NET Core 1.1 or later versions)</span></span>
- <span data-ttu-id="d9926-169">Fedora</span><span class="sxs-lookup"><span data-stu-id="d9926-169">Fedora</span></span>
  - `fedora-x64`
  - `fedora.27-x64`
  - <span data-ttu-id="d9926-170">`fedora.28-x64` (.NET core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-170">`fedora.28-x64` (.NET Core 1.1 or later versions)</span></span>
- <span data-ttu-id="d9926-171">Gentoo (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-171">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="d9926-172">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d9926-172">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.3-x64`
- <span data-ttu-id="d9926-173">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d9926-173">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
  - `ol.7.3-x64`
  - `ol.7.4-x64`
- <span data-ttu-id="d9926-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d9926-174">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="d9926-175">`rhel.6-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="d9926-176">`rhel.7.3-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-176">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="d9926-177">`rhel.7.4-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-177">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="d9926-178">Tizen (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-178">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`
- <span data-ttu-id="d9926-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d9926-179">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.17.10-x64`
  - `ubuntu.18.04-x64`
- <span data-ttu-id="d9926-180">Ubuntu türevleri</span><span class="sxs-lookup"><span data-stu-id="d9926-180">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - <span data-ttu-id="d9926-181">`linuxmint.18-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-181">`linuxmint.18-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="d9926-182">`linuxmint.18.1-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-182">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="d9926-183">`linuxmint.18.2-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-183">`linuxmint.18.2-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="d9926-184">`linuxmint.18.3-x64` (.NET core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-184">`linuxmint.18.3-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="d9926-185">SUSE Enterprise Linux (SLES) (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-185">SUSE Enterprise Linux (SLES) (.NET Core 2.0 or later versions)</span></span>
  - `sles-x64`
  - `sles.12-x64`
  - `sles.12.1-x64`
  - `sles.12.2-x64`
  - `sles.12.3-x64`
- <span data-ttu-id="d9926-186">Alpine Linux'ı (.NET Core 2.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-186">Alpine Linux (.NET Core 2.1 or later versions)</span></span>
  - `alpine-x64`
  - `alpine.3.7-x64`

<span data-ttu-id="d9926-187">Bkz: [Linux üzerinde .NET Core önkoşulları](linux-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d9926-187">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="d9926-188">macOS RID</span><span class="sxs-lookup"><span data-stu-id="d9926-188">macOS RIDs</span></span>

<span data-ttu-id="d9926-189">macOS RID'ler eski markalama "OSX" kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9926-189">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="d9926-190">`osx-x64` (.NET core 2.0 veya sonraki sürümler için en düşük sürüm olan `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="d9926-190">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="d9926-191">`osx.10.12-x64` (.NET core 1.1 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-191">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="d9926-192">Bkz: [macos'ta .NET Core önkoşulları](macos-prerequisites.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d9926-192">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="d9926-193">Android RID'ler (.NET Core 2.0 veya sonraki sürümler)</span><span class="sxs-lookup"><span data-stu-id="d9926-193">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="d9926-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9926-194">See also</span></span>

* [<span data-ttu-id="d9926-195">Çalışma zamanı kimlikleri</span><span class="sxs-lookup"><span data-stu-id="d9926-195">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
