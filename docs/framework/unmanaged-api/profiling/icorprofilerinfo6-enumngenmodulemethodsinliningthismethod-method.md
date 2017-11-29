---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6cf0bccebbfe5620ef329cc8c6f72582a7afe85a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="fdfad-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdfad-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="fdfad-103">[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="fdfad-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="fdfad-104">Verilen NGen modülü ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdfad-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdfad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdfad-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fdfad-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdfad-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="fdfad-107">[in] NGen modülü tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="fdfad-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="fdfad-108">[in] Tanımlayan bir modül tanıtıcısı `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="fdfad-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="fdfad-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fdfad-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="fdfad-110">[in] Satır içi bir yöntem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="fdfad-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="fdfad-111">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fdfad-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="fdfad-112">[out] Belirten bir bayrak olup olmadığını `ppEnum` belirli bir yöntemin satır içi kullanım tüm yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="fdfad-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="fdfad-113">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fdfad-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="fdfad-114">[out] Bir numaralandırıcı adresini gösteren bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="fdfad-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdfad-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdfad-115">Remarks</span></span>  
 <span data-ttu-id="fdfad-116">`inlineeModuleId`ve `inlineeMethodId` birlikte içermesinden olabilir yöntemi için tam tanımlayıcı oluştururlar.</span><span class="sxs-lookup"><span data-stu-id="fdfad-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="fdfad-117">Örneğin, modülü varsayın `A` yöntemi tanımlar `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="fdfad-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="fdfad-118">ve modülü Bdefines `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="fdfad-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="fdfad-119">Ayrıca varsayımında sağlar `Fancy.AddTwice` Inlines çağrı için `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="fdfad-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="fdfad-120">Bir profil oluşturucu tüm yöntemleri hangi satır içi B modülde tanımlanan bulmak için bu Numaralandırıcının kullanabilirsiniz `Simple.Add`, ve sonucu numaralandırmak `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="fdfad-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="fdfad-121">`inlineeModuleId`Modül tanıtıcısı `A`, ve `inlineeeMethodId` tanımlayıcısıdır `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="fdfad-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="fdfad-122">Varsa `incompleteData` sonra işlevi doğrudur döndürür, numaralandırıcı belirli bir yöntemin tüm yöntemleri satır içi kullanım içermiyor.</span><span class="sxs-lookup"><span data-stu-id="fdfad-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="fdfad-123">Bu bir ortaya çıkar veya diğer doğrudan veya dolaylı bağımlılıklar inliners modülünün henüz yüklenen henüz.</span><span class="sxs-lookup"><span data-stu-id="fdfad-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="fdfad-124">Bir profil oluşturucu doğru verileri gerekirse, daha fazla modülleri, tercihen her modül yük yüklendiğinde, daha sonra yeniden denemelidir.</span><span class="sxs-lookup"><span data-stu-id="fdfad-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="fdfad-125">`EnumNgenModuleMethodsInliningThisMethod` Yöntemi, üzerinde sınırlamaların çalışmak için kullanılabilir ReJIT için satır içi kullanım.</span><span class="sxs-lookup"><span data-stu-id="fdfad-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="fdfad-126">Bir yöntemin kullanımı değiştirin ve ardından yeni kod için anında oluşturun bir profil oluşturucu ReJIT sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdfad-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="fdfad-127">Örneğin, biz değiştirebilir `Simple.Add` gibi:</span><span class="sxs-lookup"><span data-stu-id="fdfad-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="fdfad-128">Ancak çünkü `Fancy.AddTwice` sahip zaten içermesinden `Simple.Add`, öncekiyle aynı davranışı sağlamak devam eder.</span><span class="sxs-lookup"><span data-stu-id="fdfad-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="fdfad-129">Bu sınırlamaya geçici bir çözüm için bu işlemi satır içinde tüm modüllerdeki tüm yöntemleri için aranacak çağıran sahip `Simple.Add` ve `ICorProfilerInfo5::RequestRejit` bu yöntemlerin her biri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="fdfad-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="fdfad-130">Yöntemleri yeniden derlenmiş olduğunda yeni davranışını olacaktır `Simple.Add` yerine eski davranışı.</span><span class="sxs-lookup"><span data-stu-id="fdfad-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdfad-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdfad-131">Requirements</span></span>  
 <span data-ttu-id="fdfad-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdfad-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdfad-133">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fdfad-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdfad-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdfad-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdfad-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdfad-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdfad-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdfad-136">See Also</span></span>  
 [<span data-ttu-id="fdfad-137">ICorProfilerInfo6 arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdfad-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
