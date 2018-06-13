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
ms.openlocfilehash: 8f34fee19c796f65d315fcbd26d55e1d5322303a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453034"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="5a216-102">ICorProfilerInfo::IsArrayClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a216-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="5a216-103">Belirtilen sınıf bir dizi sınıf olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5a216-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a216-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a216-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a216-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a216-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5a216-106">[in] İncelenmesi için sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a216-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="5a216-107">[out] Dizi öğeleri türünü gösterir CorElementType numaralandırması değerini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5a216-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="5a216-108">[out] Dizi öğeleri, kullanılabilir olduğunda sınıf kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5a216-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="5a216-109">[out] Dizi derecesini (diğer bir deyişle, Boyutlar sayısı) belirten bir tamsayı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5a216-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a216-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a216-110">Remarks</span></span>  
 <span data-ttu-id="5a216-111">Belirtilen sınıf bir dizi sınıf ise `IsArrayClass` yöntemi S_OK HRESULT ve null olmayan çıktı parametreleri için değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a216-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="5a216-112">Aksi takdirde, S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a216-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a216-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a216-113">Requirements</span></span>  
 <span data-ttu-id="5a216-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a216-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a216-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a216-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a216-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a216-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a216-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a216-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a216-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a216-118">See Also</span></span>  
 [<span data-ttu-id="5a216-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a216-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
