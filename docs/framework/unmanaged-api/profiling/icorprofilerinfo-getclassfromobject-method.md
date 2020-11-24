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
ms.openlocfilehash: 5a7edc6045969861679d1b80c0563e99f48932cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680256"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="b13f4-102">ICorProfilerInfo::GetClassFromObject Metodu</span><span class="sxs-lookup"><span data-stu-id="b13f4-102">ICorProfilerInfo::GetClassFromObject Method</span></span>

<span data-ttu-id="b13f4-103">`ClassID`Bir nesnesini alır `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="b13f4-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b13f4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b13f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b13f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b13f4-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="b13f4-106">'ndaki Alınacak nesnenin KIMLIĞI `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="b13f4-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="b13f4-107">dışı Döndürülen işaretçisine yönelik bir işaretçi `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="b13f4-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b13f4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b13f4-108">Remarks</span></span>  

 <span data-ttu-id="b13f4-109">Null değeri, `pClassId` `objectId` kaldırılması gereken bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b13f4-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b13f4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b13f4-110">Requirements</span></span>  

 <span data-ttu-id="b13f4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b13f4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b13f4-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b13f4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b13f4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b13f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b13f4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b13f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b13f4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b13f4-115">See also</span></span>

- [<span data-ttu-id="b13f4-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b13f4-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
