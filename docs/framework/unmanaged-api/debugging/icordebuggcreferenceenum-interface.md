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
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134625"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="e6972-102">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6972-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="e6972-103">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6972-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6972-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e6972-104">Methods</span></span>  
  
|<span data-ttu-id="e6972-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e6972-105">Method</span></span>|<span data-ttu-id="e6972-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6972-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6972-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6972-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="e6972-108">Atık olarak toplanabilecek nesneler hakkında bilgi içeren, belirtilen [cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e6972-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6972-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6972-109">Remarks</span></span>  
 <span data-ttu-id="e6972-110">`ICorDebugGCReferenceEnum` arabirimi "ıcorhata ayıklama Genum" arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="e6972-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="e6972-111">[ICorDebugProcess5:: EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemini çağırarak bir `ICorDebugGCReferenceEnum` örneği [cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) örneklerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e6972-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="e6972-112">[Cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri [ıcorıtcggcreference:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6972-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="e6972-113">Bu yöntem tarafından doldurulan koleksiyondaki [cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri üç tür nesneyi temsil eder:</span><span class="sxs-lookup"><span data-stu-id="e6972-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="e6972-114">Tüm yönetilen yığınlardan nesneler.</span><span class="sxs-lookup"><span data-stu-id="e6972-114">Objects from all managed stacks.</span></span> <span data-ttu-id="e6972-115">Bu, Yönetilen koddaki canlı başvuruları ve ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e6972-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="e6972-116">Tanıtıcı tablodaki nesneler.</span><span class="sxs-lookup"><span data-stu-id="e6972-116">Objects from the handle table.</span></span> <span data-ttu-id="e6972-117">Bu, bir modülde tanımlayıcı başvuruları (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve statik değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e6972-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="e6972-118">Sonlandırıcı sırasından nesneler.</span><span class="sxs-lookup"><span data-stu-id="e6972-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="e6972-119">Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.</span><span class="sxs-lookup"><span data-stu-id="e6972-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6972-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6972-120">Requirements</span></span>  
 <span data-ttu-id="e6972-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6972-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6972-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e6972-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6972-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6972-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6972-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6972-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6972-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6972-125">See also</span></span>

- [<span data-ttu-id="e6972-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e6972-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
