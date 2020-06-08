---
title: ICorProfilerInfo4::GetCodeInfo3 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
ms.openlocfilehash: 54e522aaaf23ae81b96b6be7168a9a13f28a16d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496145"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="a509a-102">ICorProfilerInfo4::GetCodeInfo3 Metodu</span><span class="sxs-lookup"><span data-stu-id="a509a-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="a509a-103">Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.</span><span class="sxs-lookup"><span data-stu-id="a509a-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a509a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a509a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a509a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a509a-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="a509a-106">'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a509a-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="a509a-107">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="a509a-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="a509a-108">'ndaki `codeInfos`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a509a-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="a509a-109">dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a509a-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="a509a-110">dışı Arayan tarafından sağlanmış arabellek.</span><span class="sxs-lookup"><span data-stu-id="a509a-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="a509a-111">Yöntem çağrıldıktan sonra, `COR_PRF_CODE_INFO` her biri yerel kod bloğunu açıklayan bir yapı dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="a509a-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a509a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a509a-112">Remarks</span></span>  
 <span data-ttu-id="a509a-113">`GetCodeInfo3`Yöntemi, [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)ile benzerdir, ancak belirtilen IP ADRESINI içeren işlevin JıT yeniden derlenmesi kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="a509a-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a509a-114">`GetCodeInfo3`bir çöp toplama tetiklenebilir, ancak [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="a509a-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="a509a-115">Daha fazla bilgi için bkz. HRESULT [corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md) .</span><span class="sxs-lookup"><span data-stu-id="a509a-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="a509a-116">Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="a509a-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="a509a-117">`GetCodeInfo3`Geri döndüğünde, `codeInfos` arabelleğin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a509a-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="a509a-118">Bunu yapmak için değerini `cCodeInfos` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="a509a-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a509a-119">`cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuna göre ayrılmışsa `pcCodeInfos` , daha büyük bir arabellek ayırarak, `codeInfos` `cCodeInfos` Yeni, daha büyük boyutla güncelleştirin ve `GetCodeInfo3` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="a509a-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="a509a-120">Alternatif olarak, `GetCodeInfo3` `codeInfos` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a509a-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a509a-121">Daha sonra `codeInfos` arabellek boyutunu ' de döndürülen değere ayarlayabilir `pcCodeInfos` , [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo3` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a509a-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a509a-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a509a-122">Requirements</span></span>  
 <span data-ttu-id="a509a-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a509a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a509a-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a509a-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a509a-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a509a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a509a-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a509a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a509a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a509a-127">See also</span></span>

- [<span data-ttu-id="a509a-128">GetCodeInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a509a-128">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="a509a-129">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a509a-129">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="a509a-130">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a509a-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a509a-131">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a509a-131">Profiling</span></span>](index.md)
