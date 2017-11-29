---
title: ICorDebugHeapSegmentEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHealRegionEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum
helpviewer_keywords: ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ca82e888ba078fcb8b855f5286bc14f970d64ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="a493d-102">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a493d-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="a493d-103">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a493d-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="a493d-104">Bu arabirim Icordebugenum arabirimi sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="a493d-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a493d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a493d-105">Methods</span></span>  
  
|<span data-ttu-id="a493d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a493d-106">Method</span></span>|<span data-ttu-id="a493d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a493d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a493d-108">Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="a493d-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="a493d-109">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Yönetilen yığın bölgeler hakkında bilgiler içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a493d-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a493d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a493d-110">Remarks</span></span>  
 <span data-ttu-id="a493d-111">`ICorDebugHeapSegmentEnum` Arabirimini uygulayan Icordebugenum arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a493d-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a493d-112">Bir `ICorDebugHeapSegmentEnum` örneği ile doldurulur [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a493d-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="a493d-113">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) koleksiyonundaki nesneleri numaralandırılan çağırarak [Icordebugheapsegmentenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a493d-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="a493d-114">Bir `ICorDebugHeapSegmentEnum` koleksiyon nesnesi numaralandırır yönetilen nesneleri içerebilir tüm bellek bölgeler, ancak bunu yönetilen nesneler gerçekte bu bölgede bulunan garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="a493d-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="a493d-115">Boş veya ayrılmış bellek bölgeler hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a493d-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a493d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a493d-116">Requirements</span></span>  
 <span data-ttu-id="a493d-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a493d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a493d-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a493d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a493d-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a493d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a493d-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a493d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a493d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a493d-121">See Also</span></span>  
 [<span data-ttu-id="a493d-122">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a493d-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
