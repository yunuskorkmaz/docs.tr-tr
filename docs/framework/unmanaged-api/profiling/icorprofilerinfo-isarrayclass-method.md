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
ms.openlocfilehash: 2608f91a7c5baa935e48fbe58ad4d14aaaad1f0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722511"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="59ef9-102">ICorProfilerInfo::IsArrayClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59ef9-102">ICorProfilerInfo::IsArrayClass Method</span></span>

<span data-ttu-id="59ef9-103">Belirtilen sınıfın bir dizi sınıfı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="59ef9-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ef9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="59ef9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59ef9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59ef9-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="59ef9-106">'ndaki İnceedilecek sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="59ef9-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="59ef9-107">dışı Dizi öğelerinin türünü gösteren CorElementType numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59ef9-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="59ef9-108">dışı Kullanılabilir olduğunda dizi öğelerinin sınıf KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59ef9-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="59ef9-109">dışı Dizinin derecesini (yani boyut sayısını) gösteren bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="59ef9-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59ef9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59ef9-110">Remarks</span></span>  

 <span data-ttu-id="59ef9-111">Belirtilen sınıf bir dizi sınıfınse, `IsArrayClass` Yöntem bir S_OK HRESULT ve null olmayan herhangi bir çıkış parametresi için değerler döndürür.</span><span class="sxs-lookup"><span data-stu-id="59ef9-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="59ef9-112">Aksi takdirde, S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="59ef9-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ef9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59ef9-113">Requirements</span></span>  

 <span data-ttu-id="59ef9-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ef9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ef9-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="59ef9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59ef9-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59ef9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ef9-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ef9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ef9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59ef9-118">See also</span></span>

- [<span data-ttu-id="59ef9-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59ef9-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
