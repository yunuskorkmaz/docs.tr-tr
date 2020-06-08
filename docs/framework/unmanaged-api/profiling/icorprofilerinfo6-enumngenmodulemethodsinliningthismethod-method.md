---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495534"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="9624b-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9624b-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="9624b-103">Belirli bir NGen modülünde tanımlanan tüm yöntemlere bir Numaralandırıcı ve satır içi verilen bir yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9624b-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="9624b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9624b-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="9624b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9624b-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="9624b-106">'ndaki NGen modülünün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9624b-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="9624b-107">'ndaki Tanımlayan bir modülün tanımlayıcısı `inlineeMethodId` .</span><span class="sxs-lookup"><span data-stu-id="9624b-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="9624b-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9624b-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="9624b-109">'ndaki Satır içine alınan metodun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9624b-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="9624b-110">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9624b-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="9624b-111">dışı `ppEnum`Tüm yöntemlerin belirli bir yöntemi içerip içermediğini gösteren bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="9624b-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="9624b-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9624b-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="9624b-113">dışı Numaralandırıcı adresine yönelik bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="9624b-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="9624b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9624b-114">Remarks</span></span>

<span data-ttu-id="9624b-115">`inlineeModuleId`ve `inlineeMethodId` birlikte, satır içine alınmış olabilecek yöntemin tam tanımlayıcısını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9624b-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="9624b-116">Örneğin, modülün `A` bir yöntemi tanımladığını varsayın `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="9624b-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="9624b-117">ve B modülü `Fancy.AddTwice` şunları tanımlar:</span><span class="sxs-lookup"><span data-stu-id="9624b-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="9624b-118">Ayrıca `Fancy.AddTwice` , çağrının Inlines olduğunu varsaymaktadır `SimpleAdd` .</span><span class="sxs-lookup"><span data-stu-id="9624b-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="9624b-119">Profil Oluşturucu, satır içi olarak B modülünde tanımlanan tüm yöntemleri bulmak için bu numaralandırıcısı kullanabilir `Simple.Add` ve sonuç numaralandırılırdı `AddTwice` .</span><span class="sxs-lookup"><span data-stu-id="9624b-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="9624b-120">`inlineeModuleId`, modülünün tanımlayıcısıdır `A` ve `inlineeMethodId` tanıtıcıdır `Simple.Add(int a, int b)` .</span><span class="sxs-lookup"><span data-stu-id="9624b-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="9624b-121">`incompleteData`İşlev çağrıldıktan sonra true ise, Numaralandırıcı belirli bir yöntemi geçersiz kılma tüm yöntemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="9624b-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="9624b-122">Bu durum, bir veya daha fazla ınliners modülünün doğrudan veya dolaylı bağımlılıkları henüz yüklenmediği zaman gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="9624b-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="9624b-123">Bir profil oluşturucunun doğru verilere ihtiyacı varsa daha sonra, tercihen her modül yükünde daha fazla modül yüklendiğinde yeniden denenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9624b-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="9624b-124">`EnumNgenModuleMethodsInliningThisMethod`Yöntemi, ReJIT için satır içi sınırlamalar konusunda geçici çözüm bulmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9624b-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="9624b-125">ReJIT, bir profil oluşturucunun bir yöntemin uygulamasını değiştirmesini ve ardından anında yeni kod oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9624b-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="9624b-126">Örneğin, aşağıdaki gibi değiştirebiliriz `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="9624b-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="9624b-127">Ancak `Fancy.AddTwice` , zaten satır içine alınmış olduğundan `Simple.Add` , önceki ile aynı davranışa sahip olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="9624b-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="9624b-128">Bu sınırlamaya geçici bir çözüm bulmak için çağıranın, `Simple.Add` `ICorProfilerInfo5::RequestRejit` Bu yöntemlerin her birinde satır içi ve kullanılan tüm modüllerdeki tüm yöntemleri araması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9624b-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="9624b-129">Yöntemler yeniden derlendiğinde, `Simple.Add` eski davranış yerine yeni davranışı olur.</span><span class="sxs-lookup"><span data-stu-id="9624b-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="9624b-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9624b-130">Requirements</span></span>

<span data-ttu-id="9624b-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9624b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9624b-132">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9624b-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="9624b-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9624b-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9624b-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9624b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9624b-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9624b-135">See also</span></span>

- [<span data-ttu-id="9624b-136">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9624b-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
