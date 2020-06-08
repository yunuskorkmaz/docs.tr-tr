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
ms.openlocfilehash: 613267549329d2f48dcd18ae341e47538e414ac0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498537"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="6e237-102">ICorProfilerInfo::GetClassFromObject Metodu</span><span class="sxs-lookup"><span data-stu-id="6e237-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="6e237-103">`ClassID`Bir nesnesini alır `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="6e237-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e237-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6e237-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e237-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e237-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="6e237-106">'ndaki Alınacak nesnenin KIMLIĞI `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="6e237-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="6e237-107">dışı Döndürülen işaretçisine yönelik bir işaretçi `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="6e237-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e237-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e237-108">Remarks</span></span>  
 <span data-ttu-id="6e237-109">Null değeri, `pClassId` `objectId` kaldırılması gereken bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e237-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e237-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e237-110">Requirements</span></span>  
 <span data-ttu-id="6e237-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e237-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e237-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6e237-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e237-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e237-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e237-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e237-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e237-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e237-115">See also</span></span>

- [<span data-ttu-id="6e237-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e237-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
