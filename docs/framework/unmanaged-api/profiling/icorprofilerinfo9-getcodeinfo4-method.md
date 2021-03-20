---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo9:: GetCodeInfo4 yöntemi'
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c7897e266fbb84d44df719c127e24bd375b560bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759097"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="44ef6-103">ICorProfilerInfo9:: GetCodeInfo4 yöntemi</span><span class="sxs-lookup"><span data-stu-id="44ef6-103">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="44ef6-104">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="44ef6-104">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="44ef6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44ef6-105">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="44ef6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44ef6-106">Parameters</span></span>

<span data-ttu-id="44ef6-107">`pNativeCodeStartAddress` 'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44ef6-107">`pNativeCodeStartAddress` [in] A pointer to the start of a native function.</span></span>

<span data-ttu-id="44ef6-108">`cCodeInfos` 'ndaki `codeInfos` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="44ef6-108">`cCodeInfos` [in] The size of the `codeInfos` array.</span></span>

<span data-ttu-id="44ef6-109">`pcCodeInfos` dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44ef6-109">`pcCodeInfos` [out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

<span data-ttu-id="44ef6-110">`codeInfos` dışı Arayan tarafından sağlanmış arabellek.</span><span class="sxs-lookup"><span data-stu-id="44ef6-110">`codeInfos` [out] A caller-provided buffer.</span></span> <span data-ttu-id="44ef6-111">Yöntem çağrıldıktan sonra, `COR_PRF_CODE_INFO` her biri yerel kod bloğunu açıklayan bir yapı dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="44ef6-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="44ef6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44ef6-112">Remarks</span></span>

<span data-ttu-id="44ef6-113">`GetCodeInfo4`Yöntemi, bir yöntemin farklı yerel sürümleri için kod bilgilerini aramak dışında, [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="44ef6-113">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="44ef6-114">`GetCodeInfo4` bir çöp toplama tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="44ef6-114">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="44ef6-115">Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="44ef6-115">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="44ef6-116">`GetCodeInfo4`Geri döndüğünde, `codeInfos` arabelleğin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44ef6-116">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="44ef6-117">Bunu yapmak için değerini `cCodeInfos` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="44ef6-117">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="44ef6-118">`cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuna göre ayrılmışsa `pcCodeInfos` , daha büyük bir arabellek ayırarak, `codeInfos` `cCodeInfos` Yeni, daha büyük boyutla güncelleştirin ve `GetCodeInfo4` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="44ef6-118">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="44ef6-119">Alternatif olarak, `GetCodeInfo4` `codeInfos` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ef6-119">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="44ef6-120">Daha sonra `codeInfos` arabellek boyutunu ' de döndürülen değere ayarlayabilir `pcCodeInfos` , [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo4` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ef6-120">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="44ef6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44ef6-121">Requirements</span></span>

<span data-ttu-id="44ef6-122">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="44ef6-122">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="44ef6-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="44ef6-123">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="44ef6-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="44ef6-124">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="44ef6-125">**.NET sürümleri:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44ef6-125">**.NET Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="44ef6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44ef6-126">See also</span></span>

- [<span data-ttu-id="44ef6-127">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44ef6-127">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
