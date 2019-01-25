---
title: Icordebugthread2 arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3826bfd16d3cf7534a6e920c516987908547b419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716158"
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="f5670-102">Icordebugthread2 arabirimi1</span><span class="sxs-lookup"><span data-stu-id="f5670-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="f5670-103">Icordebugthread arabirimi mantıksal uzantısı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="f5670-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5670-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f5670-104">Methods</span></span>  
  
|<span data-ttu-id="f5670-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f5670-105">Method</span></span>|<span data-ttu-id="f5670-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5670-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5670-107">GetActiveFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5670-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="f5670-108">Bir iş parçacığının çerçeveler etkin işlevler hakkında veri içeren cor_actıve_functıon örnekleri dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="f5670-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="f5670-109">GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5670-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="f5670-110">Bunun için bir bağlantı tanımlayıcısını alır `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="f5670-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f5670-111">GetTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5670-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="f5670-112">Bunun için bir görev tanımlayıcısını alır `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="f5670-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f5670-113">GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5670-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="f5670-114">Bu işletim sistemi iş parçacığı tanıtıcısını alır `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="f5670-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f5670-115">InterceptCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5670-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="f5670-116">Bir hata ayıklayıcı bir iş parçacığında geçerli özel durumun izlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f5670-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5670-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5670-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5670-118">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f5670-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5670-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5670-119">Requirements</span></span>  
 <span data-ttu-id="f5670-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5670-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5670-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5670-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5670-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5670-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5670-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5670-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5670-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5670-124">See also</span></span>
- [<span data-ttu-id="f5670-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f5670-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
