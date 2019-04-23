---
title: ICorProfilerInfo::IsArrayClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 350221ae205636cef82581f3fe11367006dd8b2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072178"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="6b234-102">ICorProfilerInfo::IsArrayClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b234-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="6b234-103">Array sınıfı belirtilen sınıf olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6b234-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b234-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b234-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b234-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b234-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="6b234-106">[in] İncelenecek sınıfın Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="6b234-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="6b234-107">[out] Dizi öğelerin türünü belirten CorElementType sabit değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6b234-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="6b234-108">[out] Kullanılabilir olduğunda, dizi öğelerinin sınıf kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6b234-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="6b234-109">[out] (Diğer bir deyişle, boyut sayısı) dizi boyut sayısını belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6b234-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b234-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b234-110">Remarks</span></span>  
 <span data-ttu-id="6b234-111">Bir dizi sınıfı belirtilen sınıf ise `IsArrayClass` yöntemi bir S_OK HRESULT ve null olmayan çıkış parametreleri için değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b234-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="6b234-112">Aksi takdirde S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b234-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b234-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b234-113">Requirements</span></span>  
 <span data-ttu-id="6b234-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b234-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b234-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b234-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b234-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b234-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b234-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b234-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b234-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b234-118">See also</span></span>

- [<span data-ttu-id="6b234-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b234-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
