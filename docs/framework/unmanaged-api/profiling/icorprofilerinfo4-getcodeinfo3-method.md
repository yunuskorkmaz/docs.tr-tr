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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb067d16ef7f8177f979a083707f8c6ef36750c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61685634"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="d11a6-102">ICorProfilerInfo4::GetCodeInfo3 Metodu</span><span class="sxs-lookup"><span data-stu-id="d11a6-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="d11a6-103">Belirtilen işlev JIT yeniden derlenen sürümü ile ilişkili yerel kod kapsam alır.</span><span class="sxs-lookup"><span data-stu-id="d11a6-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d11a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d11a6-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d11a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d11a6-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="d11a6-106">[in] Yerel kod ilişkilendirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="d11a6-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="d11a6-107">[in] JIT yeniden derlenen işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="d11a6-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="d11a6-108">[in] Boyutu `codeInfos` dizisi.</span><span class="sxs-lookup"><span data-stu-id="d11a6-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="d11a6-109">[out] Toplam sayısı için bir işaretçi [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d11a6-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="d11a6-110">[out] Çağıran tarafından sağlanan arabellek.</span><span class="sxs-lookup"><span data-stu-id="d11a6-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="d11a6-111">Yöntemin dönüşünün ardından bir dizi içerdiği `COR_PRF_CODE_INFO` yapıları, yerel kod bloğunun her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d11a6-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d11a6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d11a6-112">Remarks</span></span>  
 <span data-ttu-id="d11a6-113">`GetCodeInfo3` Yöntemi benzer [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)dışında belirtilen IP adresi içeren işlev JIT yeniden derlenen Kimliğini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d11a6-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d11a6-114">`GetCodeInfo3` bir çöp toplama ise tetikleyebilirsiniz [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) erişemez.</span><span class="sxs-lookup"><span data-stu-id="d11a6-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="d11a6-115">Daha fazla bilgi için [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d11a6-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="d11a6-116">Kapsam, ortak Ara dil (CIL) uzaklığı artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="d11a6-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="d11a6-117">Sonra `GetCodeInfo3` döndürür, doğrulamalısınız `codeInfos` arabellek tüm içerecek şekilde büyük [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="d11a6-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="d11a6-118">Bunu yapmak için değeri ile karşılaştırmak `cCodeInfos` değeriyle `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d11a6-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="d11a6-119">Varsa `cCodeInfos` boyutu tarafından ayrılmış bir [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısıdır küçük `pcCodeInfos`, daha büyük bir ayırma `codeInfos` arabellek, güncelleştirme `cCodeInfos` yeni, daha büyük bir boyut ve çağrı `GetCodeInfo3` yeniden.</span><span class="sxs-lookup"><span data-stu-id="d11a6-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="d11a6-120">Alternatif olarak, ilk çağırabilirsiniz `GetCodeInfo3` sıfır uzunluklu ile `codeInfos` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="d11a6-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d11a6-121">Ardından ayarlayabilirsiniz `codeInfos` arabellek boyutu döndürülen değere `pcCodeInfos`, boyutuna göre çarpılan bir [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısı ve çağrı `GetCodeInfo3` yeniden.</span><span class="sxs-lookup"><span data-stu-id="d11a6-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d11a6-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d11a6-122">Requirements</span></span>  
 <span data-ttu-id="d11a6-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d11a6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d11a6-124">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d11a6-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d11a6-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d11a6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d11a6-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d11a6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11a6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d11a6-127">See also</span></span>

- [<span data-ttu-id="d11a6-128">GetCodeInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d11a6-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="d11a6-129">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d11a6-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d11a6-130">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d11a6-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d11a6-131">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d11a6-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
