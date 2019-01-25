---
title: ICorProfilerInfo4::GetObjectSize2 Metodu
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
ms.openlocfilehash: 9a3b0ddc804e8eefdf90b3b0f17f4575b4d92bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502656"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="a1f1b-102">ICorProfilerInfo4::GetObjectSize2 Metodu</span><span class="sxs-lookup"><span data-stu-id="a1f1b-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="a1f1b-103">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1f1b-103">Returns the size of a specified object.</span></span> <span data-ttu-id="a1f1b-104">Değiştirir [Icorprofilerınfo::getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) ne de ifade edilebilir daha büyük nesnelerin boyutunu raporlama yöntemi bir `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="a1f1b-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f1b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1f1b-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1f1b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1f1b-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a1f1b-107">[in] Nesnenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="a1f1b-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="a1f1b-108">[out] Nesnenin boyutu, bayt için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a1f1b-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1f1b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1f1b-109">Remarks</span></span>  
 <span data-ttu-id="a1f1b-110">Aynı türden farklı nesneler genellikle aynı boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="a1f1b-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="a1f1b-111">Ancak, diziler veya dizeler gibi bazı türleri her nesne için başka bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1f1b-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f1b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1f1b-112">Requirements</span></span>  
 <span data-ttu-id="a1f1b-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f1b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f1b-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1f1b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1f1b-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1f1b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1f1b-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f1b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f1b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f1b-117">See also</span></span>
- [<span data-ttu-id="a1f1b-118">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1f1b-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
