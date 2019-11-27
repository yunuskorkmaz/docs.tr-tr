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
ms.openlocfilehash: 460162f0fbc9993635d1bce0c5b130358ced4fa7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448152"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="b7c30-102">ICorProfilerInfo::GetClassFromObject Metodu</span><span class="sxs-lookup"><span data-stu-id="b7c30-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="b7c30-103">Bir nesnenin `ObjectID`verilen `ClassID` alır.</span><span class="sxs-lookup"><span data-stu-id="b7c30-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7c30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7c30-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7c30-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b7c30-106">'ndaki `ClassID`alınacak nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7c30-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="b7c30-107">dışı Döndürülen `ClassID`işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b7c30-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7c30-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7c30-108">Remarks</span></span>  
 <span data-ttu-id="b7c30-109">Null `pClassId`, `objectId`, kaldırma işlemi için bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7c30-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c30-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7c30-110">Requirements</span></span>  
 <span data-ttu-id="b7c30-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7c30-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c30-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b7c30-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7c30-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b7c30-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7c30-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7c30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c30-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7c30-115">See also</span></span>

- [<span data-ttu-id="b7c30-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7c30-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
