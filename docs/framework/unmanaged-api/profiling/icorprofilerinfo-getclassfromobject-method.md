---
title: ICorProfilerInfo::GetClassFromObject Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9031ae9b4870c182922baaa41883de4cddb469d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676685"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="fff9e-102">ICorProfilerInfo::GetClassFromObject Metodu</span><span class="sxs-lookup"><span data-stu-id="fff9e-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="fff9e-103">Alır `ClassID` verilen bir nesnenin kendi `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="fff9e-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fff9e-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fff9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fff9e-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="fff9e-106">[in] Alınacağı nesnesinin Kimliğini `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="fff9e-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="fff9e-107">[out] Döndürülen işaretçi `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="fff9e-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fff9e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fff9e-108">Remarks</span></span>  
 <span data-ttu-id="fff9e-109">Bir null `pClassId` belirten `objectId` kaldırılıyor türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="fff9e-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff9e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fff9e-110">Requirements</span></span>  
 <span data-ttu-id="fff9e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fff9e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff9e-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fff9e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fff9e-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fff9e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fff9e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff9e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fff9e-115">See also</span></span>
- [<span data-ttu-id="fff9e-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fff9e-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
