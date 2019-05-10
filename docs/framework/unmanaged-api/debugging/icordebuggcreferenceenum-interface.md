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
ms.openlocfilehash: 57f09a8974dc1e8cb20185975c42c1cb3ad86a5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647164"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="3d586-102">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d586-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="3d586-103">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d586-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d586-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3d586-104">Methods</span></span>  
  
|<span data-ttu-id="3d586-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3d586-105">Method</span></span>|<span data-ttu-id="3d586-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d586-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d586-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d586-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="3d586-108">Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) atık olarak toplanmış olan nesneler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3d586-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d586-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d586-109">Remarks</span></span>  
 <span data-ttu-id="3d586-110">`ICorDebugGCReferenceEnum` Arabirimi uygulayan "ICorDebugEnum" arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3d586-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="3d586-111">Bir `ICorDebugGCReferenceEnum` örneği ile doldurulur [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3d586-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="3d586-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri numaralandırılan çağırarak [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3d586-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="3d586-113">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) bu yöntem tarafından doldurulan koleksiyonundaki nesneleri temsil eden üç nesne türleri:</span><span class="sxs-lookup"><span data-stu-id="3d586-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="3d586-114">Tüm yönetilen yığında nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3d586-114">Objects from all managed stacks.</span></span> <span data-ttu-id="3d586-115">Bu, ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra, yönetilen kod kullanarak canlı başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="3d586-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="3d586-116">Nesne işleyicisi tablosundan.</span><span class="sxs-lookup"><span data-stu-id="3d586-116">Objects from the handle table.</span></span> <span data-ttu-id="3d586-117">Bu güçlü atıflar içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve Modül içindeki statik değişkenler.</span><span class="sxs-lookup"><span data-stu-id="3d586-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="3d586-118">Sonlandırma sırasından nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3d586-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="3d586-119">Sonlandırıcı çalıştırılana dek Sonlandırıcı kuyruğunda nesneleri kökleri.</span><span class="sxs-lookup"><span data-stu-id="3d586-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d586-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d586-120">Requirements</span></span>  
 <span data-ttu-id="3d586-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d586-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d586-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d586-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d586-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d586-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d586-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d586-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d586-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d586-125">See also</span></span>

- [<span data-ttu-id="3d586-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3d586-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
