---
title: Kırpma seçenekleri
description: Kendi içindeki uygulamaların kırpılacağını nasıl denetleyeceğinizi öğrenin.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: d6081a24cc18e424b55d40e152f519c680f11aa0
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271886"
---
# <a name="trimming-options"></a><span data-ttu-id="3bb4f-103">Kırpma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="3bb4f-103">Trimming options</span></span>

<span data-ttu-id="3bb4f-104">Aşağıdaki MSBuild özellikleri ve öğeleri, [kırpılan kendi içindeki dağıtımların](trim-self-contained.md)davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="3bb4f-105">Bir kısmı `ILLink` , kırpmayı uygulayan temel aracın adı olan bahsetme seçenekleridir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="3bb4f-106">Komut satırı aracı hakkında daha fazla bilgi için `ILLink` [ıllink seçenekleri](https://github.com/mono/linker/blob/master/docs/illink-options.md)adresinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-106">More information about the `ILLink` command-line tool can be found at [illink options](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="3bb4f-107">Kırpmayı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="3bb4f-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="3bb4f-108">SDK tarafından tanımlanan varsayılan ayarlarla yayınlama sırasında kırpmayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="3bb4f-109">Kullanırken `Microsoft.NET.Sdk` , bu, netcoreapp çalışma zamanı paketinden çerçeve derlemelerinin derleme düzeyinde kırpmasını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="3bb4f-110">Uygulama kodu ve Framework olmayan kitaplıklar kırpılmamış.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="3bb4f-111">Diğer SDK 'lar farklı varsayılanlar tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="3bb4f-112">Parçalı yapısı kırpma</span><span class="sxs-lookup"><span data-stu-id="3bb4f-112">Trimming granularity</span></span>

<span data-ttu-id="3bb4f-113">Aşağıdaki ayrıntı düzeyi ayarları, kullanılmamış olmayan Il 'nin nasıl atılma olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="3bb4f-114">Bu, bir özellik olarak veya [tek bir derlemede](#trimmed-assemblies)meta veriler olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-114">This can be set as a property, or as metadata on an [individual assembly](#trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="3bb4f-115">Derleme düzeyinde kırpmasını etkinleştirin ve bu, herhangi bir bölümü (statik olarak anlaşılmış bir şekilde) kullanılırsa tüm bütünleştirilmiş kodu saklar.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically-understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="3bb4f-116">Kullanılmayan üyeleri türlerden kaldıran üye düzeyinde kırpmayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="3bb4f-117">`<IsTrimmable>true</IsTrimmable>`Meta veri içeren derlemeler, ancak açık olmaz `TrimMode` Global kullanır `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="3bb4f-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="3bb4f-118">İçin varsayılandır `TrimMode` `Microsoft.NET.Sdk` `copyused` .</span><span class="sxs-lookup"><span data-stu-id="3bb4f-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="3bb4f-119">Kırpılan derlemeler</span><span class="sxs-lookup"><span data-stu-id="3bb4f-119">Trimmed assemblies</span></span>

<span data-ttu-id="3bb4f-120">Kırpılan bir uygulamayı yayımlarken, SDK, `ItemGroup` `ManagedAssemblyToLink` kırpma için işlenecek dosya kümesini temsil eden bir çağrılan öğesini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="3bb4f-121">`ManagedAssemblyToLink` derleme başına kırpma davranışını denetleyen meta verilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="3bb4f-122">Bu meta verileri ayarlamak için, yerleşik hedeften önce çalışan bir hedef oluşturun `PrepareForILLink` .</span><span class="sxs-lookup"><span data-stu-id="3bb4f-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="3bb4f-123">Bu örnek, kırpılacağını nasıl etkinleştireceğinizi göstermektedir `MyAssembly` :</span><span class="sxs-lookup"><span data-stu-id="3bb4f-123">This example shows how to enable trimming of `MyAssembly`:</span></span>

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

<span data-ttu-id="3bb4f-124">`ManagedAssemblyToLink`SDK bu kümeyi yayımlama sırasında hesapladığı ve değişmemelidir beklediği için öğe ekleme veya kaldırma.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="3bb4f-125">Desteklenen meta veriler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3bb4f-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="3bb4f-126">Verilen derlemenin kırpılmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="3bb4f-127">`<TrimMode>copyused</TrimMode>` veya `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="3bb4f-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="3bb4f-128">Bu derlemenin [kırpma parçalı yapısını](#trimming-granularity) denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-128">Control the [trimming granularity](#trimming-granularity) of this assembly.</span></span> <span data-ttu-id="3bb4f-129">Bu genel olarak önceliklidir `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="3bb4f-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="3bb4f-130">`TrimMode`Bir derlemenin ayarlanması, ' i belirtir `<IsTrimmable>true</IsTrimmable>` .</span><span class="sxs-lookup"><span data-stu-id="3bb4f-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="3bb4f-131">Kök derlemeler</span><span class="sxs-lookup"><span data-stu-id="3bb4f-131">Root assemblies</span></span>

<span data-ttu-id="3bb4f-132">Olmayan tüm derlemeler `<IsTrimmable>true</IsTrimmable>` analize yönelik kökleri olarak kabul edilir, bu da bunların ve statik olarak anladıkları bağımlılıkların tutulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-132">All assemblies which do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="3bb4f-133">Ek derlemeler ada göre "kökü belirtilmiş" olabilir (uzantı olmadan `.dll` ):</span><span class="sxs-lookup"><span data-stu-id="3bb4f-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="3bb4f-134">Kök tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="3bb4f-134">Root descriptors</span></span>

<span data-ttu-id="3bb4f-135">Analize yönelik kökleri belirtmenin başka bir yolu, bağlayıcı [tanımlayıcı biçimini](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)kullanan bir XML dosyası kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="3bb4f-136">Bu, tüm derleme yerine belirli üyeleri köklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="3bb4f-137">Örneğin, `MyRoots.xml` uygulama tarafından dinamik olarak erişilen belirli bir yöntemi kökleyebilir:</span><span class="sxs-lookup"><span data-stu-id="3bb4f-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="3bb4f-138">Analiz uyarıları</span><span class="sxs-lookup"><span data-stu-id="3bb4f-138">Analysis warnings</span></span>

<span data-ttu-id="3bb4f-139">Kırpma statik olarak erişilebilen Il 'yi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="3bb4f-140">Yansıma veya dinamik bağımlılıklar oluşturan diğer desenleri kullanan uygulamalar, kırparak kırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="3bb4f-141">Bu tür desenler hakkında uyarı almak için:</span><span class="sxs-lookup"><span data-stu-id="3bb4f-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="3bb4f-142">Kırpma Analizi uyarılarını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="3bb4f-143">Bu, kendi kodunuz, kitaplık kodu ve çerçeve kodunuz da dahil olmak üzere tüm uygulama hakkındaki uyarıları içerir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="3bb4f-144">Uyarı sürümleri</span><span class="sxs-lookup"><span data-stu-id="3bb4f-144">Warning versions</span></span>

<span data-ttu-id="3bb4f-145">Kırpma analizi, [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) SDK genelinde analiz uyarıları sürümünü denetleyen özelliği uyar.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="3bb4f-146">Kırpma Analizi uyarılarının sürümünü bağımsız olarak denetleyen başka bir özellik vardır (derleyiciye benzer şekilde `WarningLevel` ):</span><span class="sxs-lookup"><span data-stu-id="3bb4f-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="3bb4f-147">Yalnızca verilen düzeyin veya daha düşük olan uyarıları yay.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="3bb4f-148">Bu, `9999` tüm uyarı sürümlerinin dahil olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="3bb4f-149">Gizleme uyarıları</span><span class="sxs-lookup"><span data-stu-id="3bb4f-149">Suppressing warnings</span></span>

<span data-ttu-id="3bb4f-150">Tek [uyarı kodları](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) ,,, ve dahil olmak üzere araç zinciri tarafından kullanılan olağan MSBuild özellikleri kullanılarak `NoWarn` gizlenebilir `WarningsAsErrors` `WarningsNotAsErrors` `TreatWarningsAsErrors` .</span><span class="sxs-lookup"><span data-stu-id="3bb4f-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="3bb4f-151">Illınk hata durumu davranışını bağımsız olarak denetleyen ek bir seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="3bb4f-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="3bb4f-152">Illınk uyarılarını hata olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="3bb4f-153">Bu durum, derleyici uyarılarını hata olarak bir genel olarak düşünerek uyarı çözümleme uyarılarını hatalara karşı açıp çözmemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="3bb4f-154">Sembolleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="3bb4f-154">Removing symbols</span></span>

<span data-ttu-id="3bb4f-155">Simgeler normalde kırpılan Derlemelerle eşleşecek şekilde kırpılacak.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="3bb4f-156">Tüm sembolleri de kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3bb4f-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="3bb4f-157">Katıştırılmış pdb 'leri ve ayrı PDB dosyaları dahil olmak üzere kırpılan uygulamadan sembolleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="3bb4f-158">Bu hem uygulama kodu hem de simgelerle gelen bağımlılıklar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3bb4f-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="3bb4f-159">SDK, özelliği kullanarak hata ayıklayıcı desteğini devre dışı bırakmayı da mümkün kılar `DebuggerSupport` .</span><span class="sxs-lookup"><span data-stu-id="3bb4f-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="3bb4f-160">Hata ayıklayıcı desteği devre dışı bırakıldığında, kırpma sembolleri otomatik olarak kaldırır ( `TrimmerRemoveSymbols` Varsayılan olarak true olur).</span><span class="sxs-lookup"><span data-stu-id="3bb4f-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>
