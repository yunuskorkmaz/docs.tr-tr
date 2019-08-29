---
title: Uydu derleme yükleme algoritması-.NET Core
description: .NET Core 'da uydu derleme yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105314"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="ee112-103">Uydu derleme yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="ee112-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="ee112-104">Uydu derlemeleri, dil ve kültür için özelleştirilmiş yerelleştirilmiş kaynakları depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee112-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="ee112-105">Uydu derlemeleri genel yönetilen derlemelerden farklı bir yükleme algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee112-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="ee112-106">Uydu derlemeleri ne zaman yüklenir?</span><span class="sxs-lookup"><span data-stu-id="ee112-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="ee112-107">Bir yerelleştirilmiş kaynak yüklenirken uydu derlemeleri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ee112-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="ee112-108">Yerelleştirilmiş kaynakları yüklemek için temel API, <xref:System.Resources.ResourceManager?displayProperty=fullName> sınıfındır.</span><span class="sxs-lookup"><span data-stu-id="ee112-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="ee112-109">Sonuç olarak <xref:System.Resources.ResourceManager> , sınıf her biri <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="ee112-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ee112-110">Üst düzey API 'Ler alt düzey API 'YI soyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee112-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="ee112-111">Algoritmalar</span><span class="sxs-lookup"><span data-stu-id="ee112-111">Algorithm</span></span>

<span data-ttu-id="ee112-112">.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="ee112-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="ee112-113">`active` Örneği belirleme<xref:System.Runtime.Loader.AssemblyLoadContext> .</span><span class="sxs-lookup"><span data-stu-id="ee112-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="ee112-114">Her durumda, `active` örnek yürüten <xref:System.Runtime.Loader.AssemblyLoadContext>derleme ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee112-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="ee112-115">Örnek `active` , istenen kültür için şu kadar bir uydu derlemesini yüklemeye çalışır:</span><span class="sxs-lookup"><span data-stu-id="ee112-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="ee112-116">Önbelleği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="ee112-116">Checking its cache.</span></span>
    - <span data-ttu-id="ee112-117">İstenen <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (örneğin `es-MX`) bir alt dizin için şu anda yürütülmekte olan derlemenin dizini denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="ee112-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="ee112-118">Bu özellik 3,0 öncesi .NET Core 'da uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ee112-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="ee112-119">Linux ve macOS 'ta alt dizin büyük/küçük harfe duyarlıdır ve şunlardan biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="ee112-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="ee112-120">Büyük/küçük harf eşleştir.</span><span class="sxs-lookup"><span data-stu-id="ee112-120">Exactly match case.</span></span>
        > - <span data-ttu-id="ee112-121">Küçük bir durumda olun.</span><span class="sxs-lookup"><span data-stu-id="ee112-121">Be in lower case.</span></span>

    - <span data-ttu-id="ee112-122">Örnek ise, [varsayılan uydu (kaynak) derleme yoklama](default-probing.md#satellite-resource-assembly-probing) mantığını çalıştırarak. `active` <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ee112-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="ee112-123"><xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> İşlevi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="ee112-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="ee112-124"><xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> Olayı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ee112-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="ee112-125"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> Olayı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ee112-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="ee112-126">Bir uydu derlemesi yüklüyse:</span><span class="sxs-lookup"><span data-stu-id="ee112-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="ee112-127"><xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="ee112-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="ee112-128">Derleme, istenen kaynak için arandı.</span><span class="sxs-lookup"><span data-stu-id="ee112-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="ee112-129">Çalışma zamanı derlemede kaynağı bulursa, onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee112-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="ee112-130">Kaynak bulamazsa, aramaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="ee112-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ee112-131">Uydu derlemesi içindeki bir kaynağı bulmak için, çalışma zamanı, <xref:System.Resources.ResourceManager> <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>için tarafından istenen kaynak dosyasını arar.</span><span class="sxs-lookup"><span data-stu-id="ee112-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ee112-132">Kaynak dosyasında, istenen kaynak adını arar.</span><span class="sxs-lookup"><span data-stu-id="ee112-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="ee112-133">Herhangi biri bulunmazsa, kaynak bulunamadı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ee112-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="ee112-134">Daha sonra çalışma zamanı, ana kültür derlemelerini birçok olası düzey aracılığıyla arar, her zaman 2 & 3. adımları tekrarlayarak.</span><span class="sxs-lookup"><span data-stu-id="ee112-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="ee112-135">Her kültürün, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan yalnızca bir üst öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="ee112-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="ee112-136">Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> özelliği olduğunda üst kültürleri için arama işlemi <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>duraklar.</span><span class="sxs-lookup"><span data-stu-id="ee112-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="ee112-137"><xref:System.Globalization.CultureInfo.InvariantCulture>İçin adım 2 & 3 ' e dönmedik, ancak 5. adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="ee112-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="ee112-138">Kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürün kaynağı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee112-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="ee112-139">Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesine dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee112-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="ee112-140">Ancak, <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> özelliği için belirtebilirsiniz <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ee112-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ee112-141">Bu değer, kaynaklar için en son geri dönüş konumunun ana derleme yerine bir uydu derlemesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee112-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ee112-142">Varsayılan kültür en son geri dönüş olur.</span><span class="sxs-lookup"><span data-stu-id="ee112-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="ee112-143">Bu nedenle, varsayılan kaynak dosyasına her zaman kapsamlı bir kaynak kümesini dahil etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="ee112-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="ee112-144">Bu, özel durumların oluşmasını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ee112-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="ee112-145">Geniş kapsamlı bir küme sunarak, tüm kaynaklar için bir geri dönüş sağlarsınız ve Kullanıcı için en az bir kaynağın, önemli ölçüde spesifik olmasa bile her zaman mevcut olduğundan emin olursunuz.</span><span class="sxs-lookup"><span data-stu-id="ee112-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="ee112-146">Son olarak</span><span class="sxs-lookup"><span data-stu-id="ee112-146">Finally,</span></span>
   - <span data-ttu-id="ee112-147">Çalışma zamanı varsayılan (geri dönüş) kültürü için bir kaynak dosyası bulamazsa, <xref:System.Resources.MissingManifestResourceException> veya <xref:System.Resources.MissingSatelliteAssemblyException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ee112-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="ee112-148">Kaynak dosyası bulunursa ancak istenen kaynak yoksa istek geri döner `null`.</span><span class="sxs-lookup"><span data-stu-id="ee112-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
