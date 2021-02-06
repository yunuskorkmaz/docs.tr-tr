---
description: 'Daha fazla bilgi edinin: ICorDebugHeapSegmentEnum Interface'
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
ms.openlocfilehash: 614bae0ea5e3eb7816fdeec23a0dc7aa6e44801d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660888"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="f40ea-103">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f40ea-103">ICorDebugHeapSegmentEnum Interface</span></span>

<span data-ttu-id="f40ea-104">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f40ea-104">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="f40ea-105">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="f40ea-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f40ea-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f40ea-106">Methods</span></span>  
  
|<span data-ttu-id="f40ea-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f40ea-107">Method</span></span>|<span data-ttu-id="f40ea-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f40ea-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f40ea-109">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f40ea-109">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="f40ea-110">Yönetilen yığının bölgeleri hakkında bilgi içeren [cor_segment](cor-segment-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f40ea-110">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f40ea-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f40ea-111">Remarks</span></span>  

 <span data-ttu-id="f40ea-112">`ICorDebugHeapSegmentEnum`Arabirim ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="f40ea-112">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f40ea-113">`ICorDebugHeapSegmentEnum` [ICorDebugProcess5:: Enumerateheapregion](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak bir örnek [cor_segment](cor-segment-structure.md) örneklerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="f40ea-113">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="f40ea-114">Koleksiyondaki [cor_segment](cor-segment-structure.md) nesneleri [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f40ea-114">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="f40ea-115">Bir `ICorDebugHeapSegmentEnum` koleksiyon nesnesi, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırır, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="f40ea-115">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="f40ea-116">Boş veya ayrılmış bellek bölgeleri hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f40ea-116">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40ea-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f40ea-117">Requirements</span></span>  

 <span data-ttu-id="f40ea-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f40ea-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f40ea-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f40ea-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f40ea-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f40ea-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f40ea-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f40ea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40ea-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f40ea-122">See also</span></span>

- [<span data-ttu-id="f40ea-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f40ea-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
