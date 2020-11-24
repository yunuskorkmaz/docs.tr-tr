---
title: ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 56795c6879d95253383c26c92e060f252a018914
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690219"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="50c38-102">ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50c38-102">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>

<span data-ttu-id="50c38-103">Sanal modül bölmeyi etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="50c38-103">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c38-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="50c38-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50c38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50c38-105">Parameters</span></span>  

 `enableSplitting`  
 <span data-ttu-id="50c38-106">`true` sanal modül bölmeyi etkinleştirmek için; `false` devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="50c38-106">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50c38-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50c38-107">Remarks</span></span>  

 <span data-ttu-id="50c38-108">Sanal modül bölünmesi, [ICorDebug](icordebug-interface.md) 'ın derleme işlemi sırasında birlikte birleştirilmiş modülleri tanımasını ve bunları tek bir büyük modül yerine ayrı modüller grubu olarak sunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c38-108">Virtual module splitting causes [ICorDebug](icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="50c38-109">Bunun yapılması, aşağıda açıklanan çeşitli [ICorDebug](icordebug-interface.md) yöntemlerinin davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="50c38-109">Doing this changes the behavior of various [ICorDebug](icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50c38-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-110">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="50c38-111">Bu yöntem çağrılabilir ve değeri `enableSplitting` herhangi bir zamanda değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-111">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="50c38-112">Bir [ICorDebug](icordebug-interface.md) nesnesinde durum bilgisi olan herhangi bir işlev değişikliğine neden olmaz, bu, [sanal modül bölme ve yönetilmeyen hata ayıklama API 'leri](#APIs) bölümünde listelenen yöntemlerin davranışını değiştirdikleri sırada değiştirmemiştir.</span><span class="sxs-lookup"><span data-stu-id="50c38-112">It does not cause any stateful functional changes in an [ICorDebug](icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="50c38-113">Sanal modüllerin kullanılması, bu yöntemler çağrılırken bir performans cezası uygular.</span><span class="sxs-lookup"><span data-stu-id="50c38-113">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="50c38-114">Ayrıca, [IMetaDataImport](../metadata/imetadataimport-interface.md) API 'lerinin doğru bir şekilde uygulanması için sanallaştırılan önemli bellek içi önbelleğe alma gerekebilir ve sanal modül bölünmesi devre dışı bırakılsa bile bu önbellekler korunabilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-114">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="50c38-115">Terminoloji</span><span class="sxs-lookup"><span data-stu-id="50c38-115">Terminology</span></span>  

 <span data-ttu-id="50c38-116">Sanal modül bölünmesi açıklanırken aşağıdaki terimler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="50c38-116">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="50c38-117">kapsayıcı modülleri veya kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="50c38-117">container modules, or containers</span></span>  
 <span data-ttu-id="50c38-118">Toplama modülleri.</span><span class="sxs-lookup"><span data-stu-id="50c38-118">The aggregate modules.</span></span>  
  
 <span data-ttu-id="50c38-119">alt modüller veya sanal modüller</span><span class="sxs-lookup"><span data-stu-id="50c38-119">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="50c38-120">Kapsayıcıda bulunan modüller.</span><span class="sxs-lookup"><span data-stu-id="50c38-120">The modules found in a container.</span></span>  
  
 <span data-ttu-id="50c38-121">normal modüller</span><span class="sxs-lookup"><span data-stu-id="50c38-121">regular modules</span></span>  
 <span data-ttu-id="50c38-122">Derleme zamanında birleştirilmeyen modüller.</span><span class="sxs-lookup"><span data-stu-id="50c38-122">Modules that were not merged at build time.</span></span> <span data-ttu-id="50c38-123">Bunlar kapsayıcı modülleri veya alt modüller değildir.</span><span class="sxs-lookup"><span data-stu-id="50c38-123">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="50c38-124">Hem kapsayıcı modülleri hem de alt modüller ICorDebugModule arabirim nesneleriyle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-124">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="50c38-125">Ancak, bölümünde açıklandığı gibi, arabirimin davranışı her durumda biraz farklıdır \<x-ref to section> .</span><span class="sxs-lookup"><span data-stu-id="50c38-125">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="50c38-126">Modüller ve derlemeler</span><span class="sxs-lookup"><span data-stu-id="50c38-126">Modules and assemblies</span></span>  

 <span data-ttu-id="50c38-127">Birden çok modüllü derlemeler derleme birleştirme senaryolarında desteklenmez, bu nedenle bir modül ve derleme arasında bire bir ilişki vardır.</span><span class="sxs-lookup"><span data-stu-id="50c38-127">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="50c38-128">Her ICorDebugModule nesnesi, bir kapsayıcı modülünü mi yoksa bir alt modülün mi temsil ettiğini bağımsız olarak karşılık gelen bir ICorDebugAssembly nesnesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="50c38-128">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="50c38-129">[ICorDebugModule:: GetAssembly](icordebugmodule-getassembly-method.md) yöntemi modülünden derlemeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-129">The [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="50c38-130">Diğer yönde eşlemek için [ICorDebugAssembly:: EnumerateModules](icordebugassembly-enumeratemodules-method.md) yöntemi yalnızca 1 modül numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="50c38-130">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="50c38-131">Derleme ve modül bu durumda sıkı bir şekilde bağlanmış bir çift biçimli olduğundan, hüküm derlemesi ve modülü büyük ölçüde değiştirilebilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="50c38-131">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="50c38-132">Davranış farkları</span><span class="sxs-lookup"><span data-stu-id="50c38-132">Behavioral differences</span></span>  

 <span data-ttu-id="50c38-133">Kapsayıcı modülleri aşağıdaki davranış ve özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="50c38-133">Container modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="50c38-134">Tüm bileşen alt modüllerinin meta verileri birlikte birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-134">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
- <span data-ttu-id="50c38-135">Tür adları karışmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-135">Their type names may be mangled.</span></span>  
  
- <span data-ttu-id="50c38-136">[ICorDebugModule:: GetName](icordebugmodule-getname-method.md) yöntemi, disk üzerindeki bir modülün yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-136">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
- <span data-ttu-id="50c38-137">[ICorDebugModule:: GetSize](icordebugmodule-getsize-method.md) yöntemi bu görüntünün boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-137">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
- <span data-ttu-id="50c38-138">ICorDebugAssembly3. EnumerateContainedAssemblies yöntemi alt modülleri listeler.</span><span class="sxs-lookup"><span data-stu-id="50c38-138">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
- <span data-ttu-id="50c38-139">ICorDebugAssembly3. GetContainerAssembly yöntemi döndürür `S_FALSE` .</span><span class="sxs-lookup"><span data-stu-id="50c38-139">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="50c38-140">Alt modüller aşağıdaki davranış ve özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="50c38-140">Sub-modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="50c38-141">Yalnızca birleştirilen özgün derlemeye karşılık gelen azaltılmış meta veri kümesine sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="50c38-141">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
- <span data-ttu-id="50c38-142">Meta veri adları karışmış değil.</span><span class="sxs-lookup"><span data-stu-id="50c38-142">The metadata names are not mangled.</span></span>  
  
- <span data-ttu-id="50c38-143">Meta veri belirteçleri, derleme sürecinde birleştirilmeden önce özgün derlemedeki belirteçlerle eşleşmek düşüktür.</span><span class="sxs-lookup"><span data-stu-id="50c38-143">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
- <span data-ttu-id="50c38-144">[ICorDebugModule:: GetName](icordebugmodule-getname-method.md) metodu, bir dosya yolu değil, derleme adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-144">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
- <span data-ttu-id="50c38-145">[ICorDebugModule:: GetSize](icordebugmodule-getsize-method.md) yöntemi orijinal birleştirilmemiş görüntünün boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-145">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
- <span data-ttu-id="50c38-146">ICorDebugModule3. EnumerateContainedAssemblies yöntemi döndürür `S_FALSE` .</span><span class="sxs-lookup"><span data-stu-id="50c38-146">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
- <span data-ttu-id="50c38-147">ICorDebugAssembly3. GetContainerAssembly yöntemi kapsayan modülü döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-147">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="50c38-148">Modüllerden alınan arabirimler</span><span class="sxs-lookup"><span data-stu-id="50c38-148">Interfaces retrieved from modules</span></span>  

 <span data-ttu-id="50c38-149">Modüllerden çeşitli arabirimler oluşturulabilir veya alınalınabilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-149">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="50c38-150">Bunlardan bazıları:</span><span class="sxs-lookup"><span data-stu-id="50c38-150">Some of these include:</span></span>  
  
- <span data-ttu-id="50c38-151">[ICorDebugModule:: GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) yöntemi tarafından döndürülen bir ICorDebugClass nesnesi.</span><span class="sxs-lookup"><span data-stu-id="50c38-151">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
- <span data-ttu-id="50c38-152">[ICorDebugModule:: GetAssembly](icordebugmodule-getassembly-method.md) yöntemi tarafından döndürülen bir ICorDebugAssembly nesnesi.</span><span class="sxs-lookup"><span data-stu-id="50c38-152">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="50c38-153">Bu nesneler her zaman [ICorDebug](icordebug-interface.md)tarafından önbelleğe alınır ve kapsayıcı modülünden veya bir alt modülden oluşturulup sorgulanmadığına bakılmaksızın aynı işaretçi kimliğine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="50c38-153">These objects are always cached by [ICorDebug](icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="50c38-154">Alt modül, bu önbelleğe alınmış nesnelerin filtrelenmiş bir görünümünü sağlar, kendi kopyaları olan ayrı bir önbellek değildir.</span><span class="sxs-lookup"><span data-stu-id="50c38-154">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>

## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="50c38-155">Sanal modül bölme ve yönetilmeyen hata ayıklama API 'Leri</span><span class="sxs-lookup"><span data-stu-id="50c38-155">Virtual module splitting and the unmanaged debugging APIs</span></span>  

 <span data-ttu-id="50c38-156">Aşağıdaki tabloda, sanal modül ayırmanın yönetilmeyen hata ayıklama API 'sindeki diğer yöntemlerin davranışını nasıl etkilediği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50c38-156">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="50c38-157">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50c38-157">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="50c38-158">ICorDebugFunction:: GetModule</span><span class="sxs-lookup"><span data-stu-id="50c38-158">ICorDebugFunction::GetModule</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="50c38-159">Bu işlevin ilk olarak tanımlandığı alt modülü döndürür</span><span class="sxs-lookup"><span data-stu-id="50c38-159">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="50c38-160">Bu işlevin birleştirildiği kapsayıcı modülünü döndürür</span><span class="sxs-lookup"><span data-stu-id="50c38-160">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="50c38-161">ICorDebugClass:: GetModule</span><span class="sxs-lookup"><span data-stu-id="50c38-161">ICorDebugClass::GetModule</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="50c38-162">Bu sınıfın başlangıçta tanımlandığı alt modülü döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-162">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="50c38-163">Bu sınıfın birleştirildiği kapsayıcı modülünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-163">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="50c38-164">Icordebugmoduledebugger gevent:: GetModule</span><span class="sxs-lookup"><span data-stu-id="50c38-164">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="50c38-165">Yüklenen kapsayıcı modülünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-165">Returns the container module that was loaded.</span></span> <span data-ttu-id="50c38-166">Bu ayardan bağımsız olarak alt modüllere, yük olayları verilmez.</span><span class="sxs-lookup"><span data-stu-id="50c38-166">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="50c38-167">Yüklenen kapsayıcı modülünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-167">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="50c38-168">ICorDebugAppDomain:: EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="50c38-168">ICorDebugAppDomain::EnumerateAssemblies</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="50c38-169">Alt derlemelerin ve normal derlemelerin bir listesini döndürür; kapsayıcı derlemeleri dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="50c38-169">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="50c38-170">**Note:**  Herhangi bir kapsayıcı derlemesinde sembol yoksa, alt derlemelerin hiçbiri NUMARALANDIRILAMAZ.</span><span class="sxs-lookup"><span data-stu-id="50c38-170">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="50c38-171">Herhangi bir normal derlemede sembol eksikse, bu, numaralandırılabilir veya Numaralandırılmayabilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-171">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="50c38-172">Kapsayıcı derlemelerinin ve normal derlemelerin bir listesini döndürür; hiçbir alt derleme dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="50c38-172">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="50c38-173">**Note:**  Herhangi bir normal derlemede sembol eksikse, bu, numaralandırılabilir veya Numaralandırılmayabilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-173">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="50c38-174">[ICorDebugCode:: GetCode](icordebugcode-getcode-method.md) (yalnızca Il koduna başvuru yaparken)</span><span class="sxs-lookup"><span data-stu-id="50c38-174">[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="50c38-175">Bir birleştirme öncesi derleme görüntüsünde geçerli olacak Il 'yi döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-175">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="50c38-176">Özellikle, başvuruda bulunulan türler Il 'yi içeren sanal modülde tanımlanmadığında, satır içi meta veri belirteçleri doğru şekilde TypeRef veya MemberRef belirteçleri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="50c38-176">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="50c38-177">Bu TypeRef veya MemberRef belirteçleri, karşılık gelen sanal ICorDebugModule nesnesi için [IMetaDataImport](../metadata/imetadataimport-interface.md) nesnesinde aranabilir.</span><span class="sxs-lookup"><span data-stu-id="50c38-177">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="50c38-178">Birleştirme sonrası derleme görüntüsündeki Il 'yi döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c38-178">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50c38-179">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50c38-179">Requirements</span></span>  

 <span data-ttu-id="50c38-180">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50c38-180">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c38-181">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50c38-181">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50c38-182">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50c38-182">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50c38-183">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c38-183">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c38-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50c38-184">See also</span></span>

- [<span data-ttu-id="50c38-185">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50c38-185">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="50c38-186">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50c38-186">Debugging Interfaces</span></span>](debugging-interfaces.md)
