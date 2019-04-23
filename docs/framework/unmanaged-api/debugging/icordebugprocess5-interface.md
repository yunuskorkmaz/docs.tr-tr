---
title: ICorDebugProcess5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089244"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="0cad7-102">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cad7-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="0cad7-103">Icordebugprocess arabirimi, yönetilen nesnelerin Çöp toplaması hakkında bilgi sağlamak için yönetilen yığına erişimi desteklemek için genişletir ve bir hata ayıklayıcı olup olmadığını belirlemek için uygulama yerel görüntü önbelleğinden görüntüleri yükler.</span><span class="sxs-lookup"><span data-stu-id="0cad7-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0cad7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0cad7-104">Methods</span></span>  
  
|<span data-ttu-id="0cad7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0cad7-105">Method</span></span>|<span data-ttu-id="0cad7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cad7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0cad7-107">EnableNGenPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="0cad7-108">Nasıl bir uygulama yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri yükler belirleyen değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0cad7-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="0cad7-109">EnumerateGCReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="0cad7-110">Bir işlemde atık olarak toplanmış olacak olan tüm nesneler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="0cad7-111">EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="0cad7-112">Numaralandırıcı nesnesi tanıtıcıları için bir işlem olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="0cad7-113">EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="0cad7-114">Bir numaralandırıcı, yönetilen yığındaki nesneler için alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="0cad7-115">EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="0cad7-116">Yönetilen yığının bölgeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="0cad7-117">GetArrayLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="0cad7-118">Bellekte bir dizinin düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="0cad7-119">GetGCHeapInformation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="0cad7-120">Bir işaretçi alır bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) yönetilen yığında atık olarak toplanmış olacak nesneler hakkında bilgi içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="0cad7-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="0cad7-121">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="0cad7-122">Bir işaretçi, yönetilen yığındaki bir nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="0cad7-123">GetTypeFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="0cad7-124">Kendi tür tanımlayıcısına göre bir türü için alan bilgileri içeren bir dizi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="0cad7-125">GetTypeForTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="0cad7-126">Kendi tür tanımlayıcıları hakkında temel bir nesne hakkında bilgi sağlayan bir tür nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="0cad7-127">GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="0cad7-128">Tür tanımlayıcı nesne için belirli bir adreste alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="0cad7-129">GetTypeLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cad7-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="0cad7-130">Kendi tür tanımlayıcısına göre bellekte bir nesne düzeni bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="0cad7-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cad7-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cad7-131">Remarks</span></span>  
 <span data-ttu-id="0cad7-132">Bu arabirim Icordebugprocess Icordebugprocess2, mantıksal olarak genişletir ve [Icordebugprocess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="0cad7-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cad7-133">Bu arabirim, başka bir makineden ya da başka bir işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0cad7-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cad7-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cad7-134">Requirements</span></span>  
 <span data-ttu-id="0cad7-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cad7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cad7-136">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cad7-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cad7-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cad7-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cad7-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cad7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cad7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cad7-139">See also</span></span>

- [<span data-ttu-id="0cad7-140">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0cad7-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0cad7-141">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0cad7-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
