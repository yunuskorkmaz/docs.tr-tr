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
ms.openlocfilehash: cebf5f1101abed29bc325cec2390b4fd13056e4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459976"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="ff940-102">ICorProfilerInfo4::GetCodeInfo3 Metodu</span><span class="sxs-lookup"><span data-stu-id="ff940-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="ff940-103">Belirtilen işlev JIT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsam alır.</span><span class="sxs-lookup"><span data-stu-id="ff940-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff940-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff940-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff940-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff940-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="ff940-106">[in] Yerel kod ilişkilendirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="ff940-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="ff940-107">[in] JIT yeniden derlenmesi işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="ff940-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="ff940-108">[in] Boyutunu `codeInfos` dizi.</span><span class="sxs-lookup"><span data-stu-id="ff940-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="ff940-109">[out] Toplam sayısını gösteren bir işaretçi [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff940-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="ff940-110">[out] Çağıran tarafından sağlanan arabellek.</span><span class="sxs-lookup"><span data-stu-id="ff940-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="ff940-111">Metodu döndükten sonra bir dizi içerir `COR_PRF_CODE_INFO` yapıları, yerel kod bloğunu her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff940-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff940-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff940-112">Remarks</span></span>  
 <span data-ttu-id="ff940-113">`GetCodeInfo3` Yöntemi benzer [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)dışında belirtilen IP adresi içeren işlevi JIT yeniden derlenmesi Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="ff940-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff940-114">`GetCodeInfo3` Çöp toplama, ancak tetikleyebilir [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) almayacak.</span><span class="sxs-lookup"><span data-stu-id="ff940-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="ff940-115">Daha fazla bilgi için bkz: [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ff940-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="ff940-116">Kapsam, ortak Ara dili (CIL) uzaklığı artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="ff940-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="ff940-117">Sonra `GetCodeInfo3` döndürür, doğrulamalısınız `codeInfos` arabellek tüm içerecek şekilde büyük [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="ff940-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="ff940-118">Bunu yapmak için değeri ile karşılaştırın `cCodeInfos` değeriyle `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="ff940-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ff940-119">Varsa `cCodeInfos` boyutu tarafından ayrılmış bir [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısıdır küçüktür `pcCodeInfos`, daha geniş bir ayırma `codeInfos` arabellek, güncelleştirme `cCodeInfos` yeni, büyük boyutu ve arama `GetCodeInfo3` yeniden.</span><span class="sxs-lookup"><span data-stu-id="ff940-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="ff940-120">Alternatif olarak, ilk çağırabilirsiniz `GetCodeInfo3` sıfır uzunluklu ile `codeInfos` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ff940-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ff940-121">Ardından ayarlayabilirsiniz `codeInfos` arabellek boyutu için döndürülen değer `pcCodeInfos`, boyutuna çarpılan bir [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısı ve çağrı `GetCodeInfo3` yeniden.</span><span class="sxs-lookup"><span data-stu-id="ff940-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff940-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff940-122">Requirements</span></span>  
 <span data-ttu-id="ff940-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff940-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff940-124">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff940-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff940-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff940-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff940-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff940-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff940-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff940-127">See Also</span></span>  
 [<span data-ttu-id="ff940-128">GetCodeInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff940-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [<span data-ttu-id="ff940-129">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff940-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="ff940-130">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff940-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ff940-131">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff940-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
