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
ms.openlocfilehash: 1953a3e0492e4cfcdaea761b68ea22cf5a4a8ed7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205526"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="f73fa-102">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f73fa-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="f73fa-103">Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel yerel görüntü önbelleğinden görüntü yükleyip yüklememeyeceğini anlamak için ICorDebugProcess arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="f73fa-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f73fa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f73fa-104">Methods</span></span>  
  
|<span data-ttu-id="f73fa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f73fa-105">Method</span></span>|<span data-ttu-id="f73fa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f73fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f73fa-107">EnableNGenPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-107">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="f73fa-108">Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f73fa-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="f73fa-109">EnumerateGCReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-109">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="f73fa-110">Bir işlemde çöp toplanabilecek tüm nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="f73fa-111">EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-111">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="f73fa-112">İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="f73fa-113">EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-113">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="f73fa-114">Yönetilen yığında nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="f73fa-115">EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-115">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="f73fa-116">Yönetilen yığının bölgeleri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="f73fa-117">GetArrayLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-117">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="f73fa-118">Bellekteki bir dizinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="f73fa-119">GetGCHeapInformation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-119">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="f73fa-120">Yönetilen yığında atık olarak toplanabilecek nesneler hakkında bilgi içeren [COR_HEAPINFO](cor-heapinfo-structure.md) yapısına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-120">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="f73fa-121">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="f73fa-121">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="f73fa-122">Yönetilen yığında bir nesneye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="f73fa-123">GetTypeFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-123">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="f73fa-124">Tür tanımlayıcısına dayanan bir tür için alan bilgilerini içeren bir diziye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="f73fa-125">GetTypeForTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-125">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="f73fa-126">Tür tanımlayıcılarına göre bir nesne hakkında bilgi sağlayan bir tür nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="f73fa-127">GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-127">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="f73fa-128">Belirtilen adresteki nesnenin tür tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="f73fa-129">GetTypeLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f73fa-129">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="f73fa-130">Bir nesnenin tür tanımlayıcısına göre bellek içindeki düzeni hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="f73fa-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f73fa-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f73fa-131">Remarks</span></span>  
 <span data-ttu-id="f73fa-132">Bu arabirim, ICorDebugProcess, ICorDebugProcess2 ve [ICorDebugProcess3](icordebugprocess3-interface.md) arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="f73fa-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f73fa-133">Bu arabirim, başka bir makineden ya da başka bir işlemden uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f73fa-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f73fa-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f73fa-134">Requirements</span></span>  
 <span data-ttu-id="f73fa-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f73fa-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f73fa-136">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f73fa-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f73fa-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f73fa-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f73fa-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f73fa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f73fa-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f73fa-139">See also</span></span>

- [<span data-ttu-id="f73fa-140">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f73fa-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f73fa-141">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f73fa-141">Debugging</span></span>](index.md)
