---
title: ICorProfilerInfo4::GetObjectSize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f72984da8f75eec35517da6ec1f8a73bc96c4609
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780815"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="837af-102">ICorProfilerInfo4::GetObjectSize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="837af-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="837af-103">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="837af-103">Returns the size of a specified object.</span></span> <span data-ttu-id="837af-104">Değiştirir [Icorprofilerınfo::getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) ne de ifade edilebilir daha büyük nesnelerin boyutunu raporlama yöntemi bir `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="837af-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="837af-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="837af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="837af-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="837af-107">[in] Nesnenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="837af-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="837af-108">[out] Nesnenin boyutu, bayt için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="837af-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="837af-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="837af-109">Remarks</span></span>  
 <span data-ttu-id="837af-110">Aynı türden farklı nesneler genellikle aynı boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="837af-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="837af-111">Ancak, diziler veya dizeler gibi bazı türleri her nesne için başka bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="837af-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="837af-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="837af-112">Requirements</span></span>  
 <span data-ttu-id="837af-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="837af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="837af-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="837af-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="837af-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="837af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="837af-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="837af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837af-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="837af-117">See also</span></span>

- [<span data-ttu-id="837af-118">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="837af-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
