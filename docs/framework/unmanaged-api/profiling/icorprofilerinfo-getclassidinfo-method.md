---
title: ICorProfilerInfo::GetClassIDInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97465b5d39b3f6adbb6bccfc7b478ddad97066fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563736"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="08a0e-102">ICorProfilerInfo::GetClassIDInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="08a0e-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="08a0e-103">Üst için belirtilen sınıf modülü ve meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="08a0e-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08a0e-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08a0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08a0e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="08a0e-106">[in] Bilgilerin alınacağı sınıfın Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="08a0e-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="08a0e-107">[out] Üst modülünün sınıf kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08a0e-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="08a0e-108">[out] Meta veri belirteci sınıfı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08a0e-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08a0e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08a0e-109">Remarks</span></span>  
 <span data-ttu-id="08a0e-110">Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) belirli bir modül için bir meta veri arabirimi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="08a0e-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="08a0e-111">Tarafından başvurulan konuma döndürülen meta veri belirteci `pTypeDefToken` sınıfı için meta veriler erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08a0e-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="08a0e-112">Genel türler için daha fazla bilgi almak için kullanın [Icorprofilerınfo2::getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="08a0e-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08a0e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08a0e-113">Requirements</span></span>  
 <span data-ttu-id="08a0e-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08a0e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08a0e-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08a0e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08a0e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08a0e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08a0e-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a0e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a0e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08a0e-118">See also</span></span>
- [<span data-ttu-id="08a0e-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08a0e-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
