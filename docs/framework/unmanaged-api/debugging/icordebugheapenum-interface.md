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
ms.openlocfilehash: e8d1948a7d0ff23410ba8670628424a4067fb47d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138494"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="f663a-102">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f663a-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="f663a-103">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f663a-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="f663a-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="f663a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f663a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f663a-105">Methods</span></span>  
  
|<span data-ttu-id="f663a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f663a-106">Method</span></span>|<span data-ttu-id="f663a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f663a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f663a-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f663a-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="f663a-109">Yönetilen yığında nesneler hakkında bilgi içeren, belirtilen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f663a-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f663a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f663a-110">Remarks</span></span>  
 <span data-ttu-id="f663a-111">`ICorDebugHeapEnum` arabirimi ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="f663a-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f663a-112">`ICorDebugHeapEnum` örneği, [ICorDebugProcess5:: EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="f663a-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="f663a-113">Koleksiyondaki her bir [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örneği, yığında canlı bir nesneyi veya herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmayan bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f663a-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="f663a-114">Koleksiyondaki [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri [ICorDebugHeapEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f663a-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f663a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f663a-115">Requirements</span></span>  
 <span data-ttu-id="f663a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f663a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f663a-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f663a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f663a-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f663a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f663a-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f663a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f663a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f663a-120">See also</span></span>

- [<span data-ttu-id="f663a-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f663a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
