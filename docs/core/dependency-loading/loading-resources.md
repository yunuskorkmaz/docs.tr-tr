---
title: Uydu montaj yükleme algoritması - .NET Core
description: .NET Core'da Uydu montaj yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70105314"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="95a02-103">Uydu montaj yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="95a02-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="95a02-104">Uydu derlemeleri, dil ve kültür için özelleştirilmiş yerelleştirilmiş kaynakları depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95a02-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="95a02-105">Uydu derlemeleri genel yönetilen derlemelerden farklı bir yükleme algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="95a02-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="95a02-106">Uydu meclisleri ne zaman yüklenir?</span><span class="sxs-lookup"><span data-stu-id="95a02-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="95a02-107">Yerelleştirilmiş bir kaynak yüklenirken uydu derlemeleri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="95a02-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="95a02-108">Yerelleştirilmiş kaynakları yüklemek için temel <xref:System.Resources.ResourceManager?displayProperty=fullName> API sınıftır.</span><span class="sxs-lookup"><span data-stu-id="95a02-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="95a02-109">Sonuçta <xref:System.Resources.ResourceManager> sınıf her <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>biri için yöntem çağırır.</span><span class="sxs-lookup"><span data-stu-id="95a02-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="95a02-110">Üst düzey API'ler alt düzey API'yi özetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="95a02-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="95a02-111">Algoritma</span><span class="sxs-lookup"><span data-stu-id="95a02-111">Algorithm</span></span>

<span data-ttu-id="95a02-112">.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="95a02-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="95a02-113">Örneği `active` <xref:System.Runtime.Loader.AssemblyLoadContext> belirleyin.</span><span class="sxs-lookup"><span data-stu-id="95a02-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="95a02-114">Her durumda, `active` örneğin yürütme derlemesi. <xref:System.Runtime.Loader.AssemblyLoadContext></span><span class="sxs-lookup"><span data-stu-id="95a02-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="95a02-115">Örnek, `active` istenen kültür için bir uydu tertibatını öncelik sırasına göre yüklemeye çalışır:</span><span class="sxs-lookup"><span data-stu-id="95a02-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="95a02-116">Önbelleğini kontrol ediyorum.</span><span class="sxs-lookup"><span data-stu-id="95a02-116">Checking its cache.</span></span>
    - <span data-ttu-id="95a02-117">İstenilenle <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> eşleşen bir alt dizini (örneğin) `es-MX`için şu anda çalıştırılan derlemenin dizinini denetleme.</span><span class="sxs-lookup"><span data-stu-id="95a02-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="95a02-118">Bu özellik 3.0'dan önce .NET Core'da uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="95a02-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="95a02-119">Linux ve macOS'ta, alt dizini büyük/küçük harf duyarlıdır ve aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="95a02-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="95a02-120">Kesinlikle uygun durumda.</span><span class="sxs-lookup"><span data-stu-id="95a02-120">Exactly match case.</span></span>
        > - <span data-ttu-id="95a02-121">Küçük harfli ol.</span><span class="sxs-lookup"><span data-stu-id="95a02-121">Be in lower case.</span></span>

    - <span data-ttu-id="95a02-122">Örnek ise, [varsayılan uydu (kaynak) derleme sondalama](default-probing.md#satellite-resource-assembly-probing) mantığı çalıştırarak. `active` <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="95a02-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="95a02-123"><xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> İşlevi çağırıyor.</span><span class="sxs-lookup"><span data-stu-id="95a02-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="95a02-124">Olayı <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> yükseltiyor.</span><span class="sxs-lookup"><span data-stu-id="95a02-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="95a02-125">Olayı <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> yükseltiyor.</span><span class="sxs-lookup"><span data-stu-id="95a02-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="95a02-126">Uydu montajı yüklenirse:</span><span class="sxs-lookup"><span data-stu-id="95a02-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="95a02-127">Olay <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="95a02-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="95a02-128">Derleme istenen kaynak için aranır.</span><span class="sxs-lookup"><span data-stu-id="95a02-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="95a02-129">Çalışma zamanı, derlemedeki kaynağı bulursa, onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="95a02-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="95a02-130">Kaynağı bulamazsa, aramaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="95a02-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="95a02-131">Uydu derlemesi içinde bir kaynak bulmak <xref:System.Resources.ResourceManager> için, çalışma zamanı geçerli <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>için istenen kaynak dosyası için arar.</span><span class="sxs-lookup"><span data-stu-id="95a02-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95a02-132">Kaynak dosyası içinde, istenen kaynak adını arar.</span><span class="sxs-lookup"><span data-stu-id="95a02-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="95a02-133">Ya bulunamazsa, kaynak bulunamadı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="95a02-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="95a02-134">Çalışma zamanı sonraki birçok potansiyel düzeyleri üzerinden ana kültür derlemeleri arar, her zaman adımları 2 & 3 yinelenen.</span><span class="sxs-lookup"><span data-stu-id="95a02-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="95a02-135">Her kültürün <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> yalnızca bir üst öğesi vardır ve bu özellik tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="95a02-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="95a02-136">Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> özelliği <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>olduğunda ana kültürleri arama durur.</span><span class="sxs-lookup"><span data-stu-id="95a02-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="95a02-137"><xref:System.Globalization.CultureInfo.InvariantCulture>Için, biz adım 2 & 3 dönmek değil, daha ziyade adım 5 ile devam edin.</span><span class="sxs-lookup"><span data-stu-id="95a02-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="95a02-138">Kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürü için kaynak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95a02-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="95a02-139">Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesi dahildir.</span><span class="sxs-lookup"><span data-stu-id="95a02-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="95a02-140">Ancak, <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> özellik <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> için belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95a02-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="95a02-141">Bu değer, kaynaklar için nihai geri dönüş konumunun ana derleme yerine uydu derlemesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="95a02-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="95a02-142">Varsayılan kültür nihai geri dönüş.</span><span class="sxs-lookup"><span data-stu-id="95a02-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="95a02-143">Bu nedenle, varsayılan kaynak dosyasına her zaman kapsamlı bir kaynak kümesi eklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="95a02-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="95a02-144">Bu, özel durumların atılmasını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="95a02-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="95a02-145">Ayrıntılı bir kümeye sahip olarak, tüm kaynaklar için bir geri dönüş sağlar ve kültürel olarak özel olmasa bile, kullanıcı için her zaman en az bir kaynağın bulunduğundan emin olursunuz.</span><span class="sxs-lookup"><span data-stu-id="95a02-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="95a02-146">Sonunda</span><span class="sxs-lookup"><span data-stu-id="95a02-146">Finally,</span></span>
   - <span data-ttu-id="95a02-147">Çalışma süresi varsayılan (geri dönüş) kültürü için bir kaynak dosyası <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> bulamazsa, bir veya özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="95a02-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="95a02-148">Kaynak dosyası bulunurancak istenen kaynak yoksa, istek döndürür. `null`</span><span class="sxs-lookup"><span data-stu-id="95a02-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
