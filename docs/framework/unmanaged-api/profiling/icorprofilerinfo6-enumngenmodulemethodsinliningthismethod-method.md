---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130378"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="13a04-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13a04-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="13a04-103">Belirli bir NGen modülünde tanımlanan tüm yöntemlere bir Numaralandırıcı ve satır içi verilen bir yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="13a04-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="13a04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13a04-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="13a04-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13a04-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="13a04-106">'ndaki NGen modülünün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="13a04-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="13a04-107">'ndaki `inlineeMethodId`tanımlayan bir modülün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="13a04-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="13a04-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="13a04-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="13a04-109">'ndaki Satır içine alınan metodun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="13a04-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="13a04-110">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="13a04-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="13a04-111">dışı `ppEnum`, belirli bir yöntemi gösteren tüm yöntemleri içerip içermediğini belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="13a04-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="13a04-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="13a04-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="13a04-113">dışı Numaralandırıcı adresine yönelik bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="13a04-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="13a04-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13a04-114">Remarks</span></span>

<span data-ttu-id="13a04-115">`inlineeModuleId` ve `inlineeMethodId` birlikte satır içine alınmış olabilecek yöntemin tam tanımlayıcısını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13a04-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="13a04-116">Örneğin, modülün `A` bir yöntemi `Simple.Add`tanımlıyor olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="13a04-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="13a04-117">ve Modül B `Fancy.AddTwice`tanımlar:</span><span class="sxs-lookup"><span data-stu-id="13a04-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="13a04-118">Ayrıca, `Fancy.AddTwice` `SimpleAdd`çağrının satır içinde olduğunu varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="13a04-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="13a04-119">Profil Oluşturucu, satır içi `Simple.Add`Modül B 'de tanımlanan tüm yöntemleri bulmak için bu numaralandırıcısı kullanabilir ve sonuç `AddTwice`numaralandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="13a04-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="13a04-120">`inlineeModuleId`, modül `A`tanımlayıcısıdır ve `inlineeMethodId` `Simple.Add(int a, int b)`tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="13a04-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="13a04-121">İşlev çağrıldıktan sonra `incompleteData` true ise, Numaralandırıcı belirli bir yöntemi geçersiz kılma tüm yöntemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="13a04-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="13a04-122">Bu durum, bir veya daha fazla ınliners modülünün doğrudan veya dolaylı bağımlılıkları henüz yüklenmediği zaman gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="13a04-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="13a04-123">Bir profil oluşturucunun doğru verilere ihtiyacı varsa daha sonra, tercihen her modül yükünde daha fazla modül yüklendiğinde yeniden denenmelidir.</span><span class="sxs-lookup"><span data-stu-id="13a04-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="13a04-124">`EnumNgenModuleMethodsInliningThisMethod` yöntemi, ReJIT için satır içi sınırlamalar konusunda geçici çözüm sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13a04-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="13a04-125">ReJIT, bir profil oluşturucunun bir yöntemin uygulamasını değiştirmesini ve ardından anında yeni kod oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="13a04-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="13a04-126">Örneğin, `Simple.Add` aşağıdaki gibi değiştirebiliriz:</span><span class="sxs-lookup"><span data-stu-id="13a04-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="13a04-127">Ancak `Fancy.AddTwice` zaten `Simple.Add`satır içine alınmış olduğundan, önceki ile aynı davranışa sahip olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="13a04-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="13a04-128">Bu sınırlamaya geçici bir çözüm bulmak için çağıranın satır içi `Simple.Add` tüm modüllerdeki tüm yöntemleri araması ve bu yöntemlerin her birinde `ICorProfilerInfo5::RequestRejit` kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="13a04-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="13a04-129">Yöntemler yeniden derlenirse, eski davranış yerine `Simple.Add` yeni davranışı olur.</span><span class="sxs-lookup"><span data-stu-id="13a04-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="13a04-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13a04-130">Requirements</span></span>

<span data-ttu-id="13a04-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a04-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="13a04-132">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="13a04-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="13a04-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="13a04-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="13a04-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a04-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="13a04-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13a04-135">See also</span></span>

- [<span data-ttu-id="13a04-136">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13a04-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
