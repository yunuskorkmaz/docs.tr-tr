---
title: ICorProfilerInfo2::GetStaticFieldInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 36cb8d5865cdc4c1c8e34671010ede25d531bacf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782251"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="05ade-102">ICorProfilerInfo2::GetStaticFieldInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05ade-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="05ade-103">Belirtilen alan için geçerli bir statik türünü belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="05ade-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ade-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05ade-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05ade-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05ade-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="05ade-106">[in] Statik alan tanımlandığı sınıfın Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="05ade-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="05ade-107">[in] Statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="05ade-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="05ade-108">[out] Bir işaretçi değerini [cor_prf_statıc_type](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) numaralandırma belirten belirtilen alan statik olmasına ve bu nedenle, statik tür, alan için geçerli olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="05ade-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05ade-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05ade-109">Remarks</span></span>  
 <span data-ttu-id="05ade-110">Bu bilgiler, hangi işlevin adresi statik alanı alma çağrısı belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05ade-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="05ade-111">Profil Oluşturucu kodu yine de, aslında bir adresi olduğundan emin olmak statik bir alan için meta verileri denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05ade-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="05ade-112">Statik değişmez değerler (diğer bir deyişle, sabitler) yalnızca meta verilerde mevcut ve bir adresi yok.</span><span class="sxs-lookup"><span data-stu-id="05ade-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ade-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05ade-113">Requirements</span></span>  
 <span data-ttu-id="05ade-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ade-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ade-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05ade-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05ade-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05ade-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05ade-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ade-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ade-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05ade-118">See also</span></span>

- [<span data-ttu-id="05ade-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05ade-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="05ade-120">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05ade-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
