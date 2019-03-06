---
title: Icorprofilerınfo6::enumngenmodulemethodsınliningthismethod yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ae413ae8944757fc90bcde752b9a5fe53cc68f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365327"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="5f181-102">Icorprofilerınfo6::enumngenmodulemethodsınliningthismethod yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f181-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="5f181-103">Verilen NGen modül ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f181-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f181-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f181-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="5f181-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f181-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="5f181-106">[in] NGen modülü tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5f181-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="5f181-107">[in] Tanımlayan bir modül tanıtıcısı `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="5f181-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="5f181-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5f181-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="5f181-109">[in] Satır içine alınmış bir yöntem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5f181-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="5f181-110">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5f181-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="5f181-111">[out] Gösteren bir bayrak olmadığını `ppEnum` belirli bir yöntemin tüm yöntemleri inlining'i içerir.</span><span class="sxs-lookup"><span data-stu-id="5f181-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="5f181-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5f181-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="5f181-113">[out] Bir numaralandırıcı adresini bir işaretçiye</span><span class="sxs-lookup"><span data-stu-id="5f181-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="5f181-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f181-114">Remarks</span></span>

<span data-ttu-id="5f181-115">`inlineeModuleId` ve `inlineeMethodId` birlikte satır içine alınmış olabilecek yöntemi için tam tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f181-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="5f181-116">Örneğin, modülü varsayın `A` bir yöntem tanımlar `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="5f181-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="5f181-117">Modül B tanımlar `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="5f181-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="5f181-118">Ayrıca varsayımında sağlar `Fancy.AddTwice` satır içleri çağrı için `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="5f181-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="5f181-119">Bir profil oluşturucu, bu Numaralandırıcının tüm yöntemler, hangi satır içi B modülde tanımlanan bulmak için kullanabilir `Simple.Add`, ve sonucu listeleme `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="5f181-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="5f181-120">`inlineeModuleId` Modülün tanımlayıcı `A`, ve `inlineeMethodId` tanımlayıcısıdır `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="5f181-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="5f181-121">Varsa `incompleteData` işlevinden sonra doğrudur döndürür, numaralandırıcı belirli bir yöntemin tüm yöntemleri inlining'i içermiyor.</span><span class="sxs-lookup"><span data-stu-id="5f181-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="5f181-122">Bu durum bir veya daha doğrudan veya dolaylı bağımlılıkları inliners modülü henüz yüklenen henüz.</span><span class="sxs-lookup"><span data-stu-id="5f181-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="5f181-123">Bir profil oluşturucu doğru veri alması gerekiyorsa daha fazla modüller, tercihen her modülü yükü yüklendiğinde, daha sonra yeniden denemelidir.</span><span class="sxs-lookup"><span data-stu-id="5f181-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="5f181-124">`EnumNgenModuleMethodsInliningThisMethod` Yöntemi sınırlamaların üzerinde çalışmak için kullanılabilir ReJIT için satır içi kullanım.</span><span class="sxs-lookup"><span data-stu-id="5f181-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="5f181-125">ReJIT bir profil oluşturucu bir yöntemin uygulanmasını değiştirin ve ardından yeni kod için oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5f181-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="5f181-126">Örneğin, biz değiştirme imkanınız `Simple.Add` gibi:</span><span class="sxs-lookup"><span data-stu-id="5f181-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="5f181-127">Ancak çünkü `Fancy.AddTwice` sahip zaten satır içine alınmış `Simple.Add`, önceden olduğu gibi aynı davranışa sahip devam eder.</span><span class="sxs-lookup"><span data-stu-id="5f181-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="5f181-128">Bu sınırlamaya geçici bir çözüm için tüm yöntemleri için bu işlemi satır içinde tüm modüllerde aramak çağıranın sahip `Simple.Add` ve `ICorProfilerInfo5::RequestRejit` bu yöntemlerin her biri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5f181-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="5f181-129">Yöntemleri yeniden derlenen sonra yeni davranış olacaktır `Simple.Add` eski davranışı yerine.</span><span class="sxs-lookup"><span data-stu-id="5f181-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f181-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f181-130">Requirements</span></span>

<span data-ttu-id="5f181-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f181-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5f181-132">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f181-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5f181-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f181-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5f181-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f181-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5f181-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f181-135">See also</span></span>

- [<span data-ttu-id="5f181-136">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f181-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)