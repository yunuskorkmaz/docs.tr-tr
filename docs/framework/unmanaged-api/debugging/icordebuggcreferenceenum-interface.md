---
title: ICorDebugGCReferenceEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1afe52c3df8f61b234b3c68ee819ba8389593c82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="e65cc-102">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e65cc-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="e65cc-103">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e65cc-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e65cc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e65cc-104">Methods</span></span>  
  
|<span data-ttu-id="e65cc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e65cc-105">Method</span></span>|<span data-ttu-id="e65cc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e65cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e65cc-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e65cc-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="e65cc-108">Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olacak nesneleri hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e65cc-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e65cc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e65cc-109">Remarks</span></span>  
 <span data-ttu-id="e65cc-110">`ICorDebugGCReferenceEnum` Arabirimini uygulayan "ICorDebugEnum" arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e65cc-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="e65cc-111">Bir `ICorDebugGCReferenceEnum` örneği ile doldurulur [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e65cc-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="e65cc-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri numaralandırılan çağırarak [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e65cc-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="e65cc-113">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) bu yöntem tarafından doldurulmuş koleksiyonundaki nesneleri temsil eden nesneler üç tür:</span><span class="sxs-lookup"><span data-stu-id="e65cc-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="e65cc-114">Tüm yönetilen yığınları nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e65cc-114">Objects from all managed stacks.</span></span> <span data-ttu-id="e65cc-115">Bu ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra, yönetilen kod Canlı başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="e65cc-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="e65cc-116">Tanıtıcı tablosunu nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e65cc-116">Objects from the handle table.</span></span> <span data-ttu-id="e65cc-117">Bu güçlü başvurular içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve bir modüldeki statik değişkenler.</span><span class="sxs-lookup"><span data-stu-id="e65cc-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="e65cc-118">Nesneleri sonlandırıcıyı sırasından.</span><span class="sxs-lookup"><span data-stu-id="e65cc-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="e65cc-119">Sonlandırıcıyı çalıştırılana dek sonlandırıcıyı sıranın nesneleri kökleri.</span><span class="sxs-lookup"><span data-stu-id="e65cc-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65cc-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e65cc-120">Requirements</span></span>  
 <span data-ttu-id="e65cc-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e65cc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65cc-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e65cc-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e65cc-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e65cc-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e65cc-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e65cc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e65cc-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e65cc-125">See Also</span></span>  
 [<span data-ttu-id="e65cc-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e65cc-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
