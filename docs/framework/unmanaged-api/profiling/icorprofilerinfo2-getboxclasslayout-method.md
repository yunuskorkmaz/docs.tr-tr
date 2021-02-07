---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo2:: GetBoxClassLayout yöntemi'
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
ms.openlocfilehash: 0bc9ccc80da8bcc89cfe73eaa240310c01e6ca8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760527"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="070d5-103">ICorProfilerInfo2::GetBoxClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="070d5-103">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>

<span data-ttu-id="070d5-104">Belirtilen değer türünün paketleniyorsa nerede bulunduğu hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="070d5-104">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="070d5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="070d5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="070d5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="070d5-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="070d5-107">'ndaki Kutulanmış değer türünü tanımlayan sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="070d5-107">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="070d5-108">dışı Değer türünün kutulanmış nesne KIMLIĞI işaretçisine göre göreli bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="070d5-108">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="070d5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="070d5-109">Remarks</span></span>  

 <span data-ttu-id="070d5-110">`pBufferOffset`Değer, bir kutu içindeki değer türünün konumudur.</span><span class="sxs-lookup"><span data-stu-id="070d5-110">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="070d5-111">`pBufferOffset`Kutulanmış bir nesneye uygulandıktan sonra, nesnenin değerini yorumlamak için değer türünün sınıf düzeni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="070d5-111">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="070d5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="070d5-112">Requirements</span></span>  

 <span data-ttu-id="070d5-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="070d5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="070d5-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="070d5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="070d5-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="070d5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="070d5-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="070d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="070d5-117">See also</span></span>

- [<span data-ttu-id="070d5-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="070d5-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="070d5-119">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="070d5-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
