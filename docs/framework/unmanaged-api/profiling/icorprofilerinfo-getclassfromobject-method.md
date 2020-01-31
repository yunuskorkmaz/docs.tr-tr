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
ms.openlocfilehash: a5573765486112a83f5ea7cc9258447692f72166
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864080"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="22e43-102">ICorProfilerInfo::GetClassFromObject Metodu</span><span class="sxs-lookup"><span data-stu-id="22e43-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="22e43-103">Bir nesnenin `ObjectID`verilen `ClassID` alır.</span><span class="sxs-lookup"><span data-stu-id="22e43-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22e43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22e43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22e43-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22e43-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="22e43-106">'ndaki `ClassID`alınacak nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="22e43-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="22e43-107">dışı Döndürülen `ClassID`işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="22e43-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22e43-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22e43-108">Remarks</span></span>  
 <span data-ttu-id="22e43-109">Null `pClassId`, `objectId`, kaldırma işlemi için bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="22e43-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22e43-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22e43-110">Requirements</span></span>  
 <span data-ttu-id="22e43-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22e43-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22e43-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="22e43-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22e43-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="22e43-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22e43-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22e43-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e43-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22e43-115">See also</span></span>

- [<span data-ttu-id="22e43-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22e43-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
