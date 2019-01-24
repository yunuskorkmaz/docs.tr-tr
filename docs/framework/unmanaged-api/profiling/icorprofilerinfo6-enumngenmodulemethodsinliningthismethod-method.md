---
title: Icorprofilerınfo6::enumngenmodulemethodsınliningthismethod yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568159"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="104ca-102">Icorprofilerınfo6::enumngenmodulemethodsınliningthismethod yöntemi</span><span class="sxs-lookup"><span data-stu-id="104ca-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="104ca-103">[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="104ca-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="104ca-104">Verilen NGen modül ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="104ca-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="104ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="104ca-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="104ca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="104ca-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="104ca-107">[in] NGen modülü tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="104ca-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="104ca-108">[in] Tanımlayan bir modül tanıtıcısı `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="104ca-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="104ca-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="104ca-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="104ca-110">[in] Satır içine alınmış bir yöntem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="104ca-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="104ca-111">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="104ca-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="104ca-112">[out] Gösteren bir bayrak olmadığını `ppEnum` belirli bir yöntemin tüm yöntemleri inlining'i içerir.</span><span class="sxs-lookup"><span data-stu-id="104ca-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="104ca-113">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="104ca-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="104ca-114">[out] Bir numaralandırıcı adresini bir işaretçiye</span><span class="sxs-lookup"><span data-stu-id="104ca-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="104ca-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="104ca-115">Remarks</span></span>  
 <span data-ttu-id="104ca-116">`inlineeModuleId` ve `inlineeMethodId` birlikte satır içine alınmış olabilecek yöntemi için tam tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="104ca-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="104ca-117">Örneğin, modülü varsayın `A` bir yöntem tanımlar `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="104ca-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="104ca-118">ve modül Bdefines `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="104ca-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="104ca-119">Ayrıca varsayımında sağlar `Fancy.AddTwice` satır içleri çağrı için `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="104ca-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="104ca-120">Bir profil oluşturucu, bu Numaralandırıcının tüm yöntemler, hangi satır içi B modülde tanımlanan bulmak için kullanabilir `Simple.Add`, ve sonucu listeleme `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="104ca-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="104ca-121">`inlineeModuleId` Modülün tanımlayıcı `A`, ve `inlineeeMethodId` tanımlayıcısıdır `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="104ca-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="104ca-122">Varsa `incompleteData` işlevinden sonra doğrudur döndürür, numaralandırıcı belirli bir yöntemin tüm yöntemleri inlining'i içermiyor.</span><span class="sxs-lookup"><span data-stu-id="104ca-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="104ca-123">Bu durum bir veya daha doğrudan veya dolaylı bağımlılıkları inliners modülü henüz yüklenen henüz.</span><span class="sxs-lookup"><span data-stu-id="104ca-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="104ca-124">Bir profil oluşturucu doğru veri alması gerekiyorsa daha fazla modüller, tercihen her modülü yükü yüklendiğinde, daha sonra yeniden denemelidir.</span><span class="sxs-lookup"><span data-stu-id="104ca-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="104ca-125">`EnumNgenModuleMethodsInliningThisMethod` Yöntemi sınırlamaların üzerinde çalışmak için kullanılabilir ReJIT için satır içi kullanım.</span><span class="sxs-lookup"><span data-stu-id="104ca-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="104ca-126">ReJIT bir profil oluşturucu bir yöntemin uygulanmasını değiştirin ve ardından yeni kod için oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="104ca-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="104ca-127">Örneğin, biz değiştirme imkanınız `Simple.Add` gibi:</span><span class="sxs-lookup"><span data-stu-id="104ca-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="104ca-128">Ancak çünkü `Fancy.AddTwice` sahip zaten satır içine alınmış `Simple.Add`, önceden olduğu gibi aynı davranışa sahip devam eder.</span><span class="sxs-lookup"><span data-stu-id="104ca-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="104ca-129">Bu sınırlamaya geçici bir çözüm için tüm yöntemleri için bu işlemi satır içinde tüm modüllerde aramak çağıranın sahip `Simple.Add` ve `ICorProfilerInfo5::RequestRejit` bu yöntemlerin her biri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="104ca-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="104ca-130">Yöntemleri yeniden derlenen sonra yeni davranış olacaktır `Simple.Add` eski davranışı yerine.</span><span class="sxs-lookup"><span data-stu-id="104ca-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="104ca-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="104ca-131">Requirements</span></span>  
 <span data-ttu-id="104ca-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="104ca-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="104ca-133">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="104ca-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="104ca-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="104ca-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="104ca-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="104ca-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104ca-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="104ca-136">See also</span></span>
- [<span data-ttu-id="104ca-137">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="104ca-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
