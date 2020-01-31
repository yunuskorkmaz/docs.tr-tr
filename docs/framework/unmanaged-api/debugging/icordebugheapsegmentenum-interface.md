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
ms.openlocfilehash: 98e3351c9c86961d11b0985117259d0ff3b609ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794413"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="49571-102">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49571-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="49571-103">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="49571-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="49571-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="49571-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49571-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="49571-105">Methods</span></span>  
  
|<span data-ttu-id="49571-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="49571-106">Method</span></span>|<span data-ttu-id="49571-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49571-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49571-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49571-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="49571-109">Yönetilen yığının bölgeleri hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="49571-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49571-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49571-110">Remarks</span></span>  
 <span data-ttu-id="49571-111">`ICorDebugHeapSegmentEnum` arabirimi ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="49571-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="49571-112">Bir `ICorDebugHeapSegmentEnum` örnek, [ICorDebugProcess5:: Enumerateheapregion](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak [cor_heapobject](cor-heapobject-structure.md) örneklerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="49571-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="49571-113">Koleksiyondaki [cor_heapobject](cor-heapobject-structure.md) nesneleri [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="49571-113">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="49571-114">`ICorDebugHeapSegmentEnum` bir koleksiyon nesnesi, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırır, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="49571-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="49571-115">Boş veya ayrılmış bellek bölgeleri hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="49571-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49571-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49571-116">Requirements</span></span>  
 <span data-ttu-id="49571-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49571-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49571-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49571-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49571-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="49571-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49571-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49571-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49571-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49571-121">See also</span></span>

- [<span data-ttu-id="49571-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="49571-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
