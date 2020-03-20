---
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
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178889"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="7d8a2-102">ICorDebugHeapSegmentEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d8a2-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="7d8a2-103">Yönetilen [yığının](cor-heapobject-structure.md) bellek bölgeleri hakkında bilgi içeren COR_HEAPOBJECT örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7d8a2-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d8a2-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d8a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d8a2-105">Parameters</span></span>  
 <span data-ttu-id="7d8a2-106">Celt</span><span class="sxs-lookup"><span data-stu-id="7d8a2-106">celt</span></span>  
 <span data-ttu-id="7d8a2-107">[içinde] Alınacak segment sayısı.</span><span class="sxs-lookup"><span data-stu-id="7d8a2-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="7d8a2-108">segmentler</span><span class="sxs-lookup"><span data-stu-id="7d8a2-108">segments</span></span>  
 <span data-ttu-id="7d8a2-109">[çıkış] Her biri yönetilen yığındaki bellek bölgesi hakkında bilgi sağlayan [bir COR_HEAPOBJECT](cor-heapobject-structure.md) nesneyi işaret eden bir dizi işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d8a2-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="7d8a2-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="7d8a2-110">pceltFetched</span></span>  
 <span data-ttu-id="7d8a2-111">[çıkış] Gerçekte döndürülen [COR_HEAPOBJECT](cor-heapobject-structure.md) nesne sayısına `segments`işaretçi</span><span class="sxs-lookup"><span data-stu-id="7d8a2-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="7d8a2-112">Bu değer `null` 1 `celt` ise olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d8a2-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d8a2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d8a2-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d8a2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d8a2-114">Requirements</span></span>  
 <span data-ttu-id="7d8a2-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d8a2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d8a2-116">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d8a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d8a2-117">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d8a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d8a2-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d8a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d8a2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d8a2-119">See also</span></span>

- [<span data-ttu-id="7d8a2-120">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d8a2-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="7d8a2-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d8a2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
