---
description: 'Bu konuda daha fazla bilgi edinin: ICorDebugHeapEnum arabirimi'
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
ms.openlocfilehash: c8a2f46bf412e2c4b2fe43d3eb50169191f40445
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660901"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="230ca-103">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="230ca-103">ICorDebugHeapEnum Interface</span></span>

<span data-ttu-id="230ca-104">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="230ca-104">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="230ca-105">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="230ca-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="230ca-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="230ca-106">Methods</span></span>  
  
|<span data-ttu-id="230ca-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="230ca-107">Method</span></span>|<span data-ttu-id="230ca-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230ca-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="230ca-109">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="230ca-109">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="230ca-110">Yönetilen yığında nesneler hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="230ca-110">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="230ca-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="230ca-111">Remarks</span></span>  

 <span data-ttu-id="230ca-112">`ICorDebugHeapEnum`Arabirim ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="230ca-112">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="230ca-113">`ICorDebugHeapEnum` [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak bir örnek [cor_heapobject](cor-heapobject-structure.md) örneklerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="230ca-113">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="230ca-114">Koleksiyondaki her bir [cor_heapobject](cor-heapobject-structure.md) örneği, yığında canlı bir nesneyi veya herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmayan bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="230ca-114">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="230ca-115">Koleksiyondaki [cor_heapobject](cor-heapobject-structure.md) nesneleri [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="230ca-115">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="230ca-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="230ca-116">Requirements</span></span>  

 <span data-ttu-id="230ca-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="230ca-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="230ca-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="230ca-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="230ca-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="230ca-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="230ca-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="230ca-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230ca-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="230ca-121">See also</span></span>

- [<span data-ttu-id="230ca-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="230ca-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
