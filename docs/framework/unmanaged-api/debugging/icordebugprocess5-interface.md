---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5 Interface'
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
ms.openlocfilehash: 880c305c1d9786f87d9727836a973696aa686ecf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649776"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="d61cf-103">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d61cf-103">ICorDebugProcess5 Interface</span></span>

<span data-ttu-id="d61cf-104">Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel yerel görüntü önbelleğinden görüntü yükleyip yüklememeyeceğini anlamak için ICorDebugProcess arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="d61cf-104">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d61cf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d61cf-105">Methods</span></span>  
  
|<span data-ttu-id="d61cf-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d61cf-106">Method</span></span>|<span data-ttu-id="d61cf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d61cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d61cf-108">EnableNGenPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-108">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="d61cf-109">Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d61cf-109">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="d61cf-110">EnumerateGCReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-110">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="d61cf-111">Bir işlemde çöp toplanabilecek tüm nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-111">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="d61cf-112">EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-112">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="d61cf-113">İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-113">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="d61cf-114">EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-114">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="d61cf-115">Yönetilen yığında nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-115">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="d61cf-116">EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-116">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="d61cf-117">Yönetilen yığının bölgeleri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-117">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="d61cf-118">GetArrayLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-118">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="d61cf-119">Bellekteki bir dizinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-119">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="d61cf-120">GetGCHeapInformation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-120">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="d61cf-121">Yönetilen yığında atık olarak toplanabilecek nesneler hakkında bilgi içeren [COR_HEAPINFO](cor-heapinfo-structure.md) yapısına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-121">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="d61cf-122">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="d61cf-122">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="d61cf-123">Yönetilen yığında bir nesneye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-123">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="d61cf-124">GetTypeFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-124">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="d61cf-125">Tür tanımlayıcısına dayanan bir tür için alan bilgilerini içeren bir diziye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-125">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="d61cf-126">GetTypeForTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-126">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="d61cf-127">Tür tanımlayıcılarına göre bir nesne hakkında bilgi sağlayan bir tür nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-127">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="d61cf-128">GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-128">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="d61cf-129">Belirtilen adresteki nesnenin tür tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-129">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="d61cf-130">GetTypeLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d61cf-130">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="d61cf-131">Bir nesnenin tür tanımlayıcısına göre bellek içindeki düzeni hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="d61cf-131">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d61cf-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d61cf-132">Remarks</span></span>  

 <span data-ttu-id="d61cf-133">Bu arabirim, ICorDebugProcess, ICorDebugProcess2 ve [ICorDebugProcess3](icordebugprocess3-interface.md) arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="d61cf-133">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d61cf-134">Bu arabirim, başka bir makineden ya da başka bir işlemden uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d61cf-134">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d61cf-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d61cf-135">Requirements</span></span>  

 <span data-ttu-id="d61cf-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d61cf-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d61cf-137">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d61cf-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d61cf-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d61cf-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d61cf-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d61cf-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d61cf-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d61cf-140">See also</span></span>

- [<span data-ttu-id="d61cf-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d61cf-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d61cf-142">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d61cf-142">Debugging</span></span>](index.md)
