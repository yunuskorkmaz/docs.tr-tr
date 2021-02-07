---
description: 'Daha fazla bilgi edinin: ıcorprofilerınfo6:: Enumngenmodulemethodsınliningthismethod yöntemi'
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: bd43dcecabe9a75f7ce3a94996727b192574e321
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737174"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="67ea9-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67ea9-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="67ea9-104">Belirli bir NGen modülünde tanımlanan tüm yöntemlere bir Numaralandırıcı ve satır içi verilen bir yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="67ea9-104">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="67ea9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67ea9-105">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="67ea9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67ea9-106">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="67ea9-107">'ndaki NGen modülünün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="67ea9-107">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="67ea9-108">'ndaki Tanımlayan bir modülün tanımlayıcısı `inlineeMethodId` .</span><span class="sxs-lookup"><span data-stu-id="67ea9-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="67ea9-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="67ea9-109">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="67ea9-110">'ndaki Satır içine alınan metodun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="67ea9-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="67ea9-111">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="67ea9-111">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="67ea9-112">dışı `ppEnum` Tüm yöntemlerin belirli bir yöntemi içerip içermediğini gösteren bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="67ea9-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="67ea9-113">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="67ea9-113">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="67ea9-114">dışı Numaralandırıcı adresine yönelik bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="67ea9-114">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="67ea9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67ea9-115">Remarks</span></span>

<span data-ttu-id="67ea9-116">`inlineeModuleId` ve `inlineeMethodId` birlikte, satır içine alınmış olabilecek yöntemin tam tanımlayıcısını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67ea9-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="67ea9-117">Örneğin, modülün `A` bir yöntemi tanımladığını varsayın `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="67ea9-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="67ea9-118">ve B modülü `Fancy.AddTwice` şunları tanımlar:</span><span class="sxs-lookup"><span data-stu-id="67ea9-118">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="67ea9-119">Ayrıca `Fancy.AddTwice` , çağrının Inlines olduğunu varsaymaktadır `SimpleAdd` .</span><span class="sxs-lookup"><span data-stu-id="67ea9-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="67ea9-120">Profil Oluşturucu, satır içi olarak B modülünde tanımlanan tüm yöntemleri bulmak için bu numaralandırıcısı kullanabilir `Simple.Add` ve sonuç numaralandırılırdı `AddTwice` .</span><span class="sxs-lookup"><span data-stu-id="67ea9-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="67ea9-121">`inlineeModuleId` , modülünün tanımlayıcısıdır `A` ve `inlineeMethodId` tanıtıcıdır `Simple.Add(int a, int b)` .</span><span class="sxs-lookup"><span data-stu-id="67ea9-121">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="67ea9-122">`incompleteData`İşlev çağrıldıktan sonra true ise, Numaralandırıcı belirli bir yöntemi geçersiz kılma tüm yöntemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="67ea9-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="67ea9-123">Bu durum, bir veya daha fazla ınliners modülünün doğrudan veya dolaylı bağımlılıkları henüz yüklenmediği zaman gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="67ea9-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="67ea9-124">Bir profil oluşturucunun doğru verilere ihtiyacı varsa daha sonra, tercihen her modül yükünde daha fazla modül yüklendiğinde yeniden denenmelidir.</span><span class="sxs-lookup"><span data-stu-id="67ea9-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="67ea9-125">`EnumNgenModuleMethodsInliningThisMethod`Yöntemi, ReJIT için satır içi sınırlamalar konusunda geçici çözüm bulmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67ea9-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="67ea9-126">ReJIT, bir profil oluşturucunun bir yöntemin uygulamasını değiştirmesini ve ardından anında yeni kod oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="67ea9-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="67ea9-127">Örneğin, aşağıdaki gibi değiştirebiliriz `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="67ea9-127">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="67ea9-128">Ancak `Fancy.AddTwice` , zaten satır içine alınmış olduğundan `Simple.Add` , önceki ile aynı davranışa sahip olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="67ea9-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="67ea9-129">Bu sınırlamaya geçici bir çözüm bulmak için çağıranın, `Simple.Add` `ICorProfilerInfo5::RequestRejit` Bu yöntemlerin her birinde satır içi ve kullanılan tüm modüllerdeki tüm yöntemleri araması gerekir.</span><span class="sxs-lookup"><span data-stu-id="67ea9-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="67ea9-130">Yöntemler yeniden derlendiğinde, `Simple.Add` eski davranış yerine yeni davranışı olur.</span><span class="sxs-lookup"><span data-stu-id="67ea9-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="67ea9-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67ea9-131">Requirements</span></span>

<span data-ttu-id="67ea9-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ea9-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="67ea9-133">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="67ea9-133">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="67ea9-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="67ea9-134">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="67ea9-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67ea9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="67ea9-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67ea9-136">See also</span></span>

- [<span data-ttu-id="67ea9-137">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67ea9-137">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
