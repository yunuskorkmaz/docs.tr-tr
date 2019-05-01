---
title: ICorProfilerInfo2::GetCodeInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1acf77c250b47bb32a83227a427dd3fe4f909a33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041034"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="5e73d-102">ICorProfilerInfo2::GetCodeInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e73d-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="5e73d-103">Yerel kod belirtilen ile ilişkili kapsam alır `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="5e73d-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e73d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e73d-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e73d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e73d-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="5e73d-106">[in] Yerel kod ilişkilendirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5e73d-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="5e73d-107">[in] Boyutu `codeInfos` dizisi.</span><span class="sxs-lookup"><span data-stu-id="5e73d-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="5e73d-108">[out] Toplam sayısı için bir işaretçi [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e73d-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="5e73d-109">[out] Çağıran tarafından sağlanan arabellek.</span><span class="sxs-lookup"><span data-stu-id="5e73d-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="5e73d-110">Yöntemin dönüşünün ardından bir dizi içerdiği `COR_PRF_CODE_INFO` yapıları, yerel kod bloğunun her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e73d-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e73d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e73d-111">Remarks</span></span>  
 <span data-ttu-id="5e73d-112">Kapsamları, Microsoft Ara dili (MSIL) uzaklığı artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="5e73d-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="5e73d-113">Sonra `GetCodeInfo2` döndürür, doğrulamalısınız `codeInfos` arabellek tüm içerecek şekilde büyük `COR_PRF_CODE_INFO` yapıları.</span><span class="sxs-lookup"><span data-stu-id="5e73d-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="5e73d-114">Bunu yapmak için değeri ile karşılaştırmak `cCodeInfos` değeriyle `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5e73d-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="5e73d-115">Varsa `cCodeInfos` boyutu tarafından ayrılmış bir `COR_PRF_CODE_INFO` yapısıdır küçük `pcCodeInfos`, daha büyük bir ayırma `codeInfos` arabellek, güncelleştirme `cCodeInfos` yeni, daha büyük bir boyut ve çağrı `GetCodeInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="5e73d-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="5e73d-116">Alternatif olarak, ilk çağırabilirsiniz `GetCodeInfo2` sıfır uzunluklu ile `codeInfos` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="5e73d-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5e73d-117">Ardından ayarlayabilirsiniz `codeInfos` arabellek boyutu döndürülen değere `pcCodeInfos`, boyutuna göre çarpılan bir `COR_PRF_CODE_INFO` yapısı ve çağrı `GetCodeInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="5e73d-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e73d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e73d-118">Requirements</span></span>  
 <span data-ttu-id="5e73d-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e73d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e73d-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e73d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e73d-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e73d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e73d-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e73d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e73d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e73d-123">See also</span></span>

- [<span data-ttu-id="5e73d-124">GetCodeInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e73d-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="5e73d-125">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e73d-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="5e73d-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5e73d-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5e73d-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5e73d-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
