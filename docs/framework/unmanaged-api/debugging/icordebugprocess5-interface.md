---
title: ICorDebugProcess5 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5
helpviewer_keywords: ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f0a46e18121a222ee62fec207dde938d1e967b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="497b4-102">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="497b4-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="497b4-103">Çöp toplama yönetilen nesnelerin hakkında bilgi sağlamak için Yönetilen yığın erişimi desteklemek için Icordebugprocess arabirimi genişletir ve bir hata ayıklayıcı olup olmadığını belirlemek için uygulama yerel yerel görüntü önbellekten görüntüleri yükler.</span><span class="sxs-lookup"><span data-stu-id="497b4-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="497b4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="497b4-104">Methods</span></span>  
  
|<span data-ttu-id="497b4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="497b4-105">Method</span></span>|<span data-ttu-id="497b4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="497b4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="497b4-107">EnableNGenPolicy yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="497b4-108">Yönetilen hata ayıklayıcı altında çalışırken yerel görüntüler nasıl bir uygulamanın yüklediği belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="497b4-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="497b4-109">EnumerateGCReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="497b4-110">Bir işlemde atık olarak toplanmış olacak tüm nesneleri için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="497b4-111">EnumerateHandles yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="497b4-112">Bir numaralandırıcı Nesne tanıtıcıları için bir işlem olarak alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="497b4-113">EnumerateHeap yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="497b4-114">Bir numaralandırıcı nesneler için yönetilen yığında alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="497b4-115">EnumerateHeapRegions yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="497b4-116">Yönetilen yığın bölgeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="497b4-117">GetArrayLayout yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="497b4-118">Bellekte bir dizi düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="497b4-119">Getgcheapınformation yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="497b4-120">Bir işaretçi alır bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) yönetilen yığında atık olarak toplanmış olacak nesneler hakkında bilgi içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="497b4-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="497b4-121">GetObject yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="497b4-122">Bir işaretçi yönetilen yığında bir nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="497b4-123">GetTypeFields yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="497b4-124">Kendi türü tanımlayıcısına göre bir türü için alan bilgilerini içeren bir dizi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="497b4-125">Gettypefortypeıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="497b4-126">Kendi türü tanımlayıcılarını dayalı bir nesne hakkında bilgi sağlayan bir türü nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="497b4-127">GetTypeId yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="497b4-128">Tür tanımlayıcısı nesne için belirtilen bir adres alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="497b4-129">GetTypeLayout yöntemi</span><span class="sxs-lookup"><span data-stu-id="497b4-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="497b4-130">Kendi türü tanımlayıcısına göre bellekte bir nesnenin düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="497b4-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="497b4-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="497b4-131">Remarks</span></span>  
 <span data-ttu-id="497b4-132">Bu arabirim Icordebugprocess Icordebugprocess2, mantıksal olarak genişletir ve [Icordebugprocess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="497b4-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="497b4-133">Bu arabirim, başka bir makineden veya başka bir işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="497b4-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="497b4-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="497b4-134">Requirements</span></span>  
 <span data-ttu-id="497b4-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497b4-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497b4-136">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="497b4-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="497b4-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="497b4-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="497b4-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497b4-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497b4-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="497b4-139">See Also</span></span>  
 [<span data-ttu-id="497b4-140">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="497b4-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="497b4-141">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="497b4-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
