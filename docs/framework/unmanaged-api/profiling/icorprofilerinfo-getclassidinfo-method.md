---
title: ICorProfilerInfo::GetClassIDInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassIDInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d8cf1f82ce6df8eed7b0f914003d1b13bf65685
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="9b53c-102">ICorProfilerInfo::GetClassIDInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="9b53c-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="9b53c-103">Üst modülü ve meta veri simgesi için belirtilen sınıf alır.</span><span class="sxs-lookup"><span data-stu-id="9b53c-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b53c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b53c-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b53c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b53c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9b53c-106">[in] Bilgi almak sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="9b53c-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="9b53c-107">[out] Sınıfın üst modülünün kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b53c-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="9b53c-108">[out] Sınıfı için meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b53c-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b53c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b53c-109">Remarks</span></span>  
 <span data-ttu-id="9b53c-110">Profil Oluşturucu kod çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) belirli bir modül için bir meta veri arabirimi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="9b53c-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="9b53c-111">Tarafından başvurulan konuma döndürülen meta veri simgesi `pTypeDefToken` sınıfı için meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b53c-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="9b53c-112">Genel türler için daha fazla bilgi almak için [Icorprofilerınfo2::getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="9b53c-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b53c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b53c-113">Requirements</span></span>  
 <span data-ttu-id="9b53c-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b53c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b53c-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b53c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b53c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b53c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b53c-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b53c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b53c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b53c-118">See Also</span></span>  
 [<span data-ttu-id="9b53c-119">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b53c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
