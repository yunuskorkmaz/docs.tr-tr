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
ms.openlocfilehash: b605419a291f7bee76ecad7e07be9a7a989f9fe9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496015"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="a6f56-102">ICorProfilerInfo4::GetObjectSize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6f56-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="a6f56-103">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6f56-103">Returns the size of a specified object.</span></span> <span data-ttu-id="a6f56-104">[ICorProfilerInfo:: GetObjectSize](icorprofilerinfo-getobjectsize-method.md) yöntemini, içinde belirtilebilenden daha büyük nesnelerin raporlama boyutlarına göre değiştirir `ULONG` .</span><span class="sxs-lookup"><span data-stu-id="a6f56-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f56-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a6f56-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6f56-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6f56-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a6f56-107">'ndaki Nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a6f56-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="a6f56-108">dışı Nesnenin boyutunun bayt cinsinden işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a6f56-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6f56-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6f56-109">Remarks</span></span>  
 <span data-ttu-id="a6f56-110">Aynı türdeki farklı nesneler genellikle aynı boyutta olur.</span><span class="sxs-lookup"><span data-stu-id="a6f56-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="a6f56-111">Ancak, diziler veya dizeler gibi bazı türlerin her nesne için farklı boyutta bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6f56-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6f56-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6f56-112">Requirements</span></span>  
 <span data-ttu-id="a6f56-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6f56-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f56-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a6f56-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6f56-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a6f56-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6f56-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f56-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f56-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6f56-117">See also</span></span>

- [<span data-ttu-id="a6f56-118">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6f56-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
