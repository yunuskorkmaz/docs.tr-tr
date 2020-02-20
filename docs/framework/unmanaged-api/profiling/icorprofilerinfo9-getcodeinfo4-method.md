---
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
ms.openlocfilehash: f65cebff912adeb7afc34434467cf7be72f9be32
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449770"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="99934-102">ICorProfilerInfo9:: GetCodeInfo4 yöntemi</span><span class="sxs-lookup"><span data-stu-id="99934-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="99934-103">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="99934-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="99934-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99934-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="99934-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99934-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="99934-106">\[, yerel bir işlevin başlangıcına yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="99934-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="99934-107">`codeInfos` dizisinin boyutu \[.</span><span class="sxs-lookup"><span data-stu-id="99934-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="99934-108">\[out] kullanılabilen toplam [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="99934-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="99934-109">\[out] arayan tarafından sağlanmış bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="99934-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="99934-110">Yöntemi çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` yapıları dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="99934-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="99934-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99934-111">Remarks</span></span>

<span data-ttu-id="99934-112">`GetCodeInfo4` yöntemi [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)ile benzerdir, ancak yöntemin farklı yerel sürümleri için kod bilgilerini arayabilir.</span><span class="sxs-lookup"><span data-stu-id="99934-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="99934-113">`GetCodeInfo4` bir çöp toplama tetikleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="99934-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="99934-114">Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="99934-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="99934-115">`GetCodeInfo4` çağrıldıktan sonra, `codeInfos` arabelleğinin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99934-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="99934-116">Bunu yapmak için `cCodeInfos` değerini `cchName` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="99934-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="99934-117">[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısına bölünen `cCodeInfos`, `pcCodeInfos`daha küçüktür, daha büyük bir `codeInfos` arabelleği ayırın, yeni, daha büyük boyutlu `cCodeInfos` güncelleştirin ve `GetCodeInfo4` çağırın.</span><span class="sxs-lookup"><span data-stu-id="99934-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="99934-118">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetCodeInfo4` sıfır uzunluklu `codeInfos` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99934-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="99934-119">Daha sonra `codeInfos` arabellek boyutunu `pcCodeInfos`döndürülen değere ayarlayabilirsiniz, bir [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo4` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99934-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="99934-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99934-120">Requirements</span></span>

<span data-ttu-id="99934-121">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="99934-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="99934-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="99934-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="99934-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="99934-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="99934-124">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99934-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="99934-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99934-125">See also</span></span>

- [<span data-ttu-id="99934-126">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="99934-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
