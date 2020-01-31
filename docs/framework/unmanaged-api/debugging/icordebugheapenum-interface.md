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
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794435"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="1866d-102">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1866d-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="1866d-103">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1866d-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="1866d-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="1866d-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1866d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1866d-105">Methods</span></span>  
  
|<span data-ttu-id="1866d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1866d-106">Method</span></span>|<span data-ttu-id="1866d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1866d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1866d-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1866d-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="1866d-109">Yönetilen yığında nesneler hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1866d-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1866d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1866d-110">Remarks</span></span>  
 <span data-ttu-id="1866d-111">`ICorDebugHeapEnum` arabirimi ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="1866d-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="1866d-112">[ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak bir `ICorDebugHeapEnum` örneği [cor_heapobject](cor-heapobject-structure.md) örneklerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1866d-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="1866d-113">Koleksiyondaki her bir [cor_heapobject](cor-heapobject-structure.md) örneği, yığında canlı bir nesneyi veya herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmayan bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1866d-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="1866d-114">Koleksiyondaki [cor_heapobject](cor-heapobject-structure.md) nesneleri [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1866d-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1866d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1866d-115">Requirements</span></span>  
 <span data-ttu-id="1866d-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1866d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1866d-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1866d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1866d-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1866d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1866d-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1866d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1866d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1866d-120">See also</span></span>

- [<span data-ttu-id="1866d-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1866d-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
