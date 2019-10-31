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
ms.openlocfilehash: e9679029cd54ac44832add9bc4f47f8c8e9a26a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138458"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="002ef-102">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="002ef-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="002ef-103">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="002ef-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="002ef-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="002ef-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="002ef-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="002ef-105">Methods</span></span>  
  
|<span data-ttu-id="002ef-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="002ef-106">Method</span></span>|<span data-ttu-id="002ef-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="002ef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="002ef-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ef-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="002ef-109">Yönetilen yığının bölgeleri hakkında bilgi içeren, belirtilen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="002ef-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="002ef-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="002ef-110">Remarks</span></span>  
 <span data-ttu-id="002ef-111">`ICorDebugHeapSegmentEnum` arabirimi ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="002ef-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="002ef-112">`ICorDebugHeapSegmentEnum` örneği, [ICorDebugProcess5:: Enumerateheapregion](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="002ef-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="002ef-113">Koleksiyondaki [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri [ICorDebugHeapSegmentEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) yöntemi çağırarak listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="002ef-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="002ef-114">`ICorDebugHeapSegmentEnum` bir koleksiyon nesnesi, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırır, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="002ef-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="002ef-115">Boş veya ayrılmış bellek bölgeleri hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="002ef-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002ef-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="002ef-116">Requirements</span></span>  
 <span data-ttu-id="002ef-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002ef-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002ef-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="002ef-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="002ef-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="002ef-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="002ef-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="002ef-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002ef-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="002ef-121">See also</span></span>

- [<span data-ttu-id="002ef-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="002ef-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
