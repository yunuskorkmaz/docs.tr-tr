---
title: ICorProfilerInfo2::GetBoxClassLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 630b67a64716f26577bbc376970e4f76216f4da5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497362"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="21e66-102">ICorProfilerInfo2::GetBoxClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e66-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="21e66-103">Belirtilen değer türünün paketleniyorsa nerede bulunduğu hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="21e66-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e66-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="21e66-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e66-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21e66-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="21e66-106">'ndaki Kutulanmış değer türünü tanımlayan sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="21e66-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="21e66-107">dışı Değer türünün kutulanmış nesne KIMLIĞI işaretçisine göre göreli bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="21e66-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21e66-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21e66-108">Remarks</span></span>  
 <span data-ttu-id="21e66-109">`pBufferOffset`Değer, bir kutu içindeki değer türünün konumudur.</span><span class="sxs-lookup"><span data-stu-id="21e66-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="21e66-110">`pBufferOffset`Kutulanmış bir nesneye uygulandıktan sonra, nesnenin değerini yorumlamak için değer türünün sınıf düzeni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21e66-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e66-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21e66-111">Requirements</span></span>  
 <span data-ttu-id="21e66-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e66-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e66-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21e66-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21e66-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21e66-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e66-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e66-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21e66-116">See also</span></span>

- [<span data-ttu-id="21e66-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e66-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="21e66-118">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e66-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
