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
ms.openlocfilehash: 164e042ab0f1a275ff07b917658024e22c2d7b0b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862042"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="fdcc2-102">ICorProfilerInfo4::GetCodeInfo3 Metodu</span><span class="sxs-lookup"><span data-stu-id="fdcc2-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="fdcc2-103">Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdcc2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdcc2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdcc2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdcc2-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="fdcc2-106">'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="fdcc2-107">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="fdcc2-108">'ndaki `codeInfos` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="fdcc2-109">dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="fdcc2-110">dışı Arayan tarafından sağlanmış arabellek.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="fdcc2-111">Yöntemi çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` yapıları dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdcc2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdcc2-112">Remarks</span></span>  
 <span data-ttu-id="fdcc2-113">`GetCodeInfo3` yöntemi [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)ile benzerdir, ancak belirtilen IP adresini IÇEREN işlevin JIT YENIDEN derlenmesi kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fdcc2-114">`GetCodeInfo3` bir çöp toplamayı tetikleyebilir, ancak [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="fdcc2-115">Daha fazla bilgi için bkz. HRESULT [corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md) .</span><span class="sxs-lookup"><span data-stu-id="fdcc2-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="fdcc2-116">Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="fdcc2-117">`GetCodeInfo3` çağrıldıktan sonra, `codeInfos` arabelleğinin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="fdcc2-118">Bunu yapmak için `cCodeInfos` değerini `cchName` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="fdcc2-119">[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısına bölünen `cCodeInfos`, `pcCodeInfos`daha küçüktür, daha büyük bir `codeInfos` arabelleği ayırın, yeni, daha büyük boyutlu `cCodeInfos` güncelleştirin ve `GetCodeInfo3` çağırın.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="fdcc2-120">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetCodeInfo3` sıfır uzunluklu `codeInfos` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="fdcc2-121">Daha sonra `codeInfos` arabellek boyutunu `pcCodeInfos`döndürülen değere ayarlayabilirsiniz, bir [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo3` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdcc2-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdcc2-122">Requirements</span></span>  
 <span data-ttu-id="fdcc2-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdcc2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdcc2-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fdcc2-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdcc2-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fdcc2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdcc2-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdcc2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdcc2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdcc2-127">See also</span></span>

- [<span data-ttu-id="fdcc2-128">GetCodeInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdcc2-128">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="fdcc2-129">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdcc2-129">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="fdcc2-130">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fdcc2-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="fdcc2-131">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdcc2-131">Profiling</span></span>](index.md)
