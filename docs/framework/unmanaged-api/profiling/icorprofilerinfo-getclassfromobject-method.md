---
description: ': ICorProfilerInfo:: GetClassFromObject yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1c0224137c839d167263eefb17e3ae0b3ac29ef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647823"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="53000-103">ICorProfilerInfo::GetClassFromObject Metodu</span><span class="sxs-lookup"><span data-stu-id="53000-103">ICorProfilerInfo::GetClassFromObject Method</span></span>

<span data-ttu-id="53000-104">`ClassID`Bir nesnesini alır `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="53000-104">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53000-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53000-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53000-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53000-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="53000-107">'ndaki Alınacak nesnenin KIMLIĞI `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="53000-107">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="53000-108">dışı Döndürülen işaretçisine yönelik bir işaretçi `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="53000-108">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53000-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53000-109">Remarks</span></span>  

 <span data-ttu-id="53000-110">Null değeri, `pClassId` `objectId` kaldırılması gereken bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="53000-110">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53000-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53000-111">Requirements</span></span>  

 <span data-ttu-id="53000-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53000-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53000-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="53000-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53000-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="53000-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53000-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53000-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53000-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53000-116">See also</span></span>

- [<span data-ttu-id="53000-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53000-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
