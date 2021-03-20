---
description: 'Daha fazla bilgi edinin: ıcorprofilerınfo6:: Enumngenmodulemethodsınliningthismethod yöntemi'
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 236aaa820162dcc1d5c6c8ade1e8da78f5f4acb0
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759136"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="83b0c-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83b0c-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="83b0c-104">Belirli bir NGen modülünde tanımlanan tüm yöntemlere bir Numaralandırıcı ve satır içi verilen bir yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="83b0c-104">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="83b0c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83b0c-105">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="83b0c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83b0c-106">Parameters</span></span>

<span data-ttu-id="83b0c-107">`inlinersModuleId` 'ndaki NGen modülünün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="83b0c-107">`inlinersModuleId` [in] The identifier of an NGen module.</span></span>

<span data-ttu-id="83b0c-108">`inlineeModuleId` 'ndaki Tanımlayan bir modülün tanımlayıcısı `inlineeMethodId` .</span><span class="sxs-lookup"><span data-stu-id="83b0c-108">`inlineeModuleId` [in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="83b0c-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="83b0c-109">See the Remarks section for more information.</span></span>

<span data-ttu-id="83b0c-110">`inlineeMethodId` 'ndaki Satır içine alınan metodun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="83b0c-110">`inlineeMethodId` [in] The identifier of an inlined method.</span></span> <span data-ttu-id="83b0c-111">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="83b0c-111">See the Remarks section for more information.</span></span>

<span data-ttu-id="83b0c-112">`incompleteData` dışı `ppEnum` Tüm yöntemlerin belirli bir yöntemi içerip içermediğini gösteren bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="83b0c-112">`incompleteData` [out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="83b0c-113">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="83b0c-113">See the Remarks section for more information.</span></span>

<span data-ttu-id="83b0c-114">`ppEnum` dışı Numaralandırıcı adresine yönelik bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="83b0c-114">`ppEnum` [out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="83b0c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83b0c-115">Remarks</span></span>

<span data-ttu-id="83b0c-116">`inlineeModuleId` ve `inlineeMethodId` birlikte, satır içine alınmış olabilecek yöntemin tam tanımlayıcısını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83b0c-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="83b0c-117">Örneğin, modülün `A` bir yöntemi tanımladığını varsayın `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="83b0c-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="83b0c-118">ve B modülü `Fancy.AddTwice` şunları tanımlar:</span><span class="sxs-lookup"><span data-stu-id="83b0c-118">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="83b0c-119">Ayrıca `Fancy.AddTwice` , çağrının Inlines olduğunu varsaymaktadır `SimpleAdd` .</span><span class="sxs-lookup"><span data-stu-id="83b0c-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="83b0c-120">Profil Oluşturucu, satır içi olarak B modülünde tanımlanan tüm yöntemleri bulmak için bu numaralandırıcısı kullanabilir `Simple.Add` ve sonuç numaralandırılırdı `AddTwice` .</span><span class="sxs-lookup"><span data-stu-id="83b0c-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="83b0c-121">`inlineeModuleId` , modülünün tanımlayıcısıdır `A` ve `inlineeMethodId` tanıtıcıdır `Simple.Add(int a, int b)` .</span><span class="sxs-lookup"><span data-stu-id="83b0c-121">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="83b0c-122">`incompleteData`İşlev çağrıldıktan sonra true ise, Numaralandırıcı belirli bir yöntemi geçersiz kılma tüm yöntemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="83b0c-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="83b0c-123">Bu durum, bir veya daha fazla ınliners modülünün doğrudan veya dolaylı bağımlılıkları henüz yüklenmediği zaman gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="83b0c-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="83b0c-124">Bir profil oluşturucunun doğru verilere ihtiyacı varsa daha sonra, tercihen her modül yükünde daha fazla modül yüklendiğinde yeniden denenmelidir.</span><span class="sxs-lookup"><span data-stu-id="83b0c-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="83b0c-125">`EnumNgenModuleMethodsInliningThisMethod`Yöntemi, ReJIT için satır içi sınırlamalar konusunda geçici çözüm bulmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83b0c-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="83b0c-126">ReJIT, bir profil oluşturucunun bir yöntemin uygulamasını değiştirmesini ve ardından anında yeni kod oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="83b0c-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="83b0c-127">Örneğin, aşağıdaki gibi değiştirebiliriz `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="83b0c-127">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="83b0c-128">Ancak `Fancy.AddTwice` , zaten satır içine alınmış olduğundan `Simple.Add` , önceki ile aynı davranışa sahip olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="83b0c-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="83b0c-129">Bu sınırlamaya geçici bir çözüm bulmak için çağıranın, `Simple.Add` `ICorProfilerInfo5::RequestRejit` Bu yöntemlerin her birinde satır içi ve kullanılan tüm modüllerdeki tüm yöntemleri araması gerekir.</span><span class="sxs-lookup"><span data-stu-id="83b0c-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="83b0c-130">Yöntemler yeniden derlendiğinde, `Simple.Add` eski davranış yerine yeni davranışı olur.</span><span class="sxs-lookup"><span data-stu-id="83b0c-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="83b0c-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83b0c-131">Requirements</span></span>

<span data-ttu-id="83b0c-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83b0c-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="83b0c-133">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="83b0c-133">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="83b0c-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="83b0c-134">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="83b0c-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83b0c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="83b0c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83b0c-136">See also</span></span>

- [<span data-ttu-id="83b0c-137">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83b0c-137">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
