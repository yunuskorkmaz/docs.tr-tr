---
title: ICorDebugGCReferenceEnum Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f83d2ac9ca96145fa89b283fec42c71858097f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080838"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="523b9-102">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="523b9-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="523b9-103">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="523b9-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="523b9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="523b9-104">Methods</span></span>  
  
|<span data-ttu-id="523b9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="523b9-105">Method</span></span>|<span data-ttu-id="523b9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="523b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="523b9-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="523b9-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="523b9-108">Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) atık olarak toplanmış olan nesneler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="523b9-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="523b9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="523b9-109">Remarks</span></span>  
 <span data-ttu-id="523b9-110">`ICorDebugGCReferenceEnum` Arabirimi uygulayan "ICorDebugEnum" arabirimi.</span><span class="sxs-lookup"><span data-stu-id="523b9-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="523b9-111">Bir `ICorDebugGCReferenceEnum` örneği ile doldurulur [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="523b9-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="523b9-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri numaralandırılan çağırarak [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="523b9-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="523b9-113">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) bu yöntem tarafından doldurulan koleksiyonundaki nesneleri temsil eden üç nesne türleri:</span><span class="sxs-lookup"><span data-stu-id="523b9-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="523b9-114">Tüm yönetilen yığında nesneleri.</span><span class="sxs-lookup"><span data-stu-id="523b9-114">Objects from all managed stacks.</span></span> <span data-ttu-id="523b9-115">Bu, ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra, yönetilen kod kullanarak canlı başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="523b9-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="523b9-116">Nesne işleyicisi tablosundan.</span><span class="sxs-lookup"><span data-stu-id="523b9-116">Objects from the handle table.</span></span> <span data-ttu-id="523b9-117">Bu güçlü atıflar içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve Modül içindeki statik değişkenler.</span><span class="sxs-lookup"><span data-stu-id="523b9-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="523b9-118">Sonlandırma sırasından nesneleri.</span><span class="sxs-lookup"><span data-stu-id="523b9-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="523b9-119">Sonlandırıcı çalıştırılana dek Sonlandırıcı kuyruğunda nesneleri kökleri.</span><span class="sxs-lookup"><span data-stu-id="523b9-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="523b9-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="523b9-120">Requirements</span></span>  
 <span data-ttu-id="523b9-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="523b9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="523b9-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="523b9-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="523b9-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="523b9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="523b9-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="523b9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523b9-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="523b9-125">See also</span></span>

- [<span data-ttu-id="523b9-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="523b9-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
