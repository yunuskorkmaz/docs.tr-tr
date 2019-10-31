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
ms.openlocfilehash: 897fb56cacb51e98cf8f1778c3529617decb5ecb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138436"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="dee35-102">ICorDebugHeapSegmentEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dee35-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="dee35-103">Yönetilen yığının bellek bölgeleri hakkında bilgi içeren, belirtilen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="dee35-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dee35-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dee35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dee35-105">Parameters</span></span>  
 <span data-ttu-id="dee35-106">celt</span><span class="sxs-lookup"><span data-stu-id="dee35-106">celt</span></span>  
 <span data-ttu-id="dee35-107">'ndaki Alınacak parçaların sayısı.</span><span class="sxs-lookup"><span data-stu-id="dee35-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="dee35-108">segmentler</span><span class="sxs-lookup"><span data-stu-id="dee35-108">segments</span></span>  
 <span data-ttu-id="dee35-109">dışı Her biri, yönetilen yığında bir bellek bölgesi hakkında bilgi sağlayan bir [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="dee35-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="dee35-110">Pceltfettiz</span><span class="sxs-lookup"><span data-stu-id="dee35-110">pceltFetched</span></span>  
 <span data-ttu-id="dee35-111">dışı Gerçekten `segments`döndürülen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesne sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dee35-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="dee35-112">Bu değer, `celt` 1 ise `null` olabilir.</span><span class="sxs-lookup"><span data-stu-id="dee35-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dee35-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dee35-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee35-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dee35-114">Requirements</span></span>  
 <span data-ttu-id="dee35-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee35-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee35-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dee35-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dee35-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dee35-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dee35-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee35-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee35-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dee35-119">See also</span></span>

- [<span data-ttu-id="dee35-120">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dee35-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="dee35-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dee35-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
