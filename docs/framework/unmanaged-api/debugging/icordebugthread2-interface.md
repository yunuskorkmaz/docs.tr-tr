---
title: Icordebugthread2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2
helpviewer_keywords: ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3a554d075adb56294e4693b234ce22735fb982
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="1415c-102">Icordebugthread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="1415c-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="1415c-103">Icordebugthread arabirimi için mantıksal bir uzantısı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="1415c-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1415c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1415c-104">Methods</span></span>  
  
|<span data-ttu-id="1415c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1415c-105">Method</span></span>|<span data-ttu-id="1415c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1415c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1415c-107">GetActiveFunctions yöntemi</span><span class="sxs-lookup"><span data-stu-id="1415c-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="1415c-108">Bir iş parçacığının çerçeveleri etkin işlevlerde ilgili verileri içeren cor_actıve_functıon örnekleri dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="1415c-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="1415c-109">Getconnectionıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="1415c-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="1415c-110">Bunun için bir bağlantı tanımlayıcı alır `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="1415c-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="1415c-111">Gettaskıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="1415c-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="1415c-112">Bunun için bir görev tanımlayıcısı alır `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="1415c-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="1415c-113">Getvolatileosthreadıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="1415c-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="1415c-114">Bu işletim sistemi iş parçacığı tanımlayıcısını alır `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="1415c-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="1415c-115">Interceptcurrentexception yöntemi</span><span class="sxs-lookup"><span data-stu-id="1415c-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="1415c-116">Bir hata ayıklayıcısı geçerli özel durumun bir iş parçacığında izlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1415c-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1415c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1415c-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1415c-118">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1415c-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1415c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1415c-119">Requirements</span></span>  
 <span data-ttu-id="1415c-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1415c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1415c-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1415c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1415c-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1415c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1415c-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1415c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1415c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1415c-124">See Also</span></span>  
 [<span data-ttu-id="1415c-125">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1415c-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
