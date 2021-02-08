---
description: 'Daha fazla bilgi edinin: ICorDebugHeapSegmentEnum:: Next yöntemi'
title: ICorDebugHeapSegmentEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 8d2ddfb4df82969fa9cf580ed8a7f903f9d6c260
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803683"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="c7967-103">ICorDebugHeapSegmentEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7967-103">ICorDebugHeapSegmentEnum::Next Method</span></span>

<span data-ttu-id="c7967-104">Yönetilen yığının bellek bölgeleri hakkında bilgi içeren [cor_segment](cor-segment-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c7967-104">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7967-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7967-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7967-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7967-106">Parameters</span></span>  

 <span data-ttu-id="c7967-107">celt</span><span class="sxs-lookup"><span data-stu-id="c7967-107">celt</span></span>  
 <span data-ttu-id="c7967-108">'ndaki Alınacak parçaların sayısı.</span><span class="sxs-lookup"><span data-stu-id="c7967-108">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="c7967-109">segmentler</span><span class="sxs-lookup"><span data-stu-id="c7967-109">segments</span></span>  
 <span data-ttu-id="c7967-110">dışı Her biri yönetilen yığında bir bellek bölgesi hakkında bilgi sağlayan bir [cor_segment](cor-segment-structure.md) nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="c7967-110">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="c7967-111">Pceltfettiz</span><span class="sxs-lookup"><span data-stu-id="c7967-111">pceltFetched</span></span>  
 <span data-ttu-id="c7967-112">dışı Aslında ' de döndürülen [cor_segment](cor-segment-structure.md) nesnelerinin sayısına yönelik bir işaretçi `segments` .</span><span class="sxs-lookup"><span data-stu-id="c7967-112">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="c7967-113">Bu değer 1 ise `null` olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="c7967-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7967-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7967-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7967-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7967-115">Requirements</span></span>  

 <span data-ttu-id="c7967-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7967-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7967-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c7967-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7967-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c7967-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7967-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7967-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7967-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7967-120">See also</span></span>

- [<span data-ttu-id="c7967-121">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7967-121">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="c7967-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c7967-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
