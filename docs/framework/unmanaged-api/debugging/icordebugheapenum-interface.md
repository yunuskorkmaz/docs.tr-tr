---
title: ICorDebugHeapEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e9f58a0bc51e8a22672df6ab9bd94009c00f9bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688086"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="6df70-102">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df70-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="6df70-103">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6df70-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="6df70-104">Icordebugenum arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="6df70-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6df70-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6df70-105">Methods</span></span>  
  
|<span data-ttu-id="6df70-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6df70-106">Method</span></span>|<span data-ttu-id="6df70-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6df70-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6df70-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6df70-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="6df70-109">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığındaki nesneler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6df70-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6df70-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6df70-110">Remarks</span></span>  
 <span data-ttu-id="6df70-111">`ICorDebugHeapEnum` Arabirimi uygulayan Icordebugenum arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6df70-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="6df70-112">Bir `ICorDebugHeapEnum` örneği ile doldurulur [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6df70-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="6df70-113">Her [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) canlı bir nesne yığını üzerindeki veya herhangi bir nesne tarafından kökü belirtilmemiş ancak henüz çöp toplayıcısı tarafından toplanmış değil bir nesne koleksiyonundaki örneği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6df70-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="6df70-114">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) koleksiyonundaki nesneleri numaralandırılan çağırarak [Icordebugheapenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6df70-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df70-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6df70-115">Requirements</span></span>  
 <span data-ttu-id="6df70-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df70-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df70-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6df70-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6df70-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6df70-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6df70-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df70-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df70-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6df70-120">See also</span></span>
- [<span data-ttu-id="6df70-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6df70-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
