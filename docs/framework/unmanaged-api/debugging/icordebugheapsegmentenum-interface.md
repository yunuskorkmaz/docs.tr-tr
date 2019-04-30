---
title: ICorDebugHeapSegmentEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73036d1c12c46cbfda8031073a005bc9b376040e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756218"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="93cf2-102">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93cf2-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="93cf2-103">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="93cf2-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="93cf2-104">Icordebugenum arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="93cf2-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93cf2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="93cf2-105">Methods</span></span>  
  
|<span data-ttu-id="93cf2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="93cf2-106">Method</span></span>|<span data-ttu-id="93cf2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93cf2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93cf2-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93cf2-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="93cf2-109">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığının bölgeler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="93cf2-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93cf2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93cf2-110">Remarks</span></span>  
 <span data-ttu-id="93cf2-111">`ICorDebugHeapSegmentEnum` Arabirimi uygulayan Icordebugenum arabirimi.</span><span class="sxs-lookup"><span data-stu-id="93cf2-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="93cf2-112">Bir `ICorDebugHeapSegmentEnum` örneği ile doldurulur [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93cf2-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="93cf2-113">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) koleksiyonundaki nesneleri numaralandırılan çağırarak [Icordebugheapsegmentenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93cf2-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="93cf2-114">Bir `ICorDebugHeapSegmentEnum` koleksiyon nesnesini numaralandırır yönetilen nesneleri içerebilir tüm bellek bölgeler, ancak yönetilen nesneleri aslında bu bölgelerde bulunan garantilemez.</span><span class="sxs-lookup"><span data-stu-id="93cf2-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="93cf2-115">Bu işlem, boş veya ayrılmış bellek bölgeleri hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="93cf2-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93cf2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93cf2-116">Requirements</span></span>  
 <span data-ttu-id="93cf2-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93cf2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93cf2-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93cf2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93cf2-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93cf2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93cf2-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93cf2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93cf2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93cf2-121">See also</span></span>

- [<span data-ttu-id="93cf2-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="93cf2-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
