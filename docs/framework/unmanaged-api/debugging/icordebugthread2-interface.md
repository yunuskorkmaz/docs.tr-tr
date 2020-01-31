---
title: ICorDebugThread2 Arabirimi
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
ms.openlocfilehash: fdaad46b739721ff95b712d4b6461a793ae0a480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791426"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="6bf1b-102">ICorDebugThread2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bf1b-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="6bf1b-103">ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bf1b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6bf1b-104">Methods</span></span>  
  
|<span data-ttu-id="6bf1b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6bf1b-105">Method</span></span>|<span data-ttu-id="6bf1b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bf1b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bf1b-107">GetActiveFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bf1b-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="6bf1b-108">Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="6bf1b-109">GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bf1b-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="6bf1b-110">Bu `ICorDebugThread2`yönelik bir bağlantı tanımlayıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="6bf1b-111">GetTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bf1b-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="6bf1b-112">Bu `ICorDebugThread2`yönelik bir görev tanımlayıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="6bf1b-113">GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bf1b-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="6bf1b-114">Bu `ICorDebugThread2`işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="6bf1b-115">InterceptCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bf1b-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="6bf1b-116">Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bf1b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bf1b-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bf1b-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bf1b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bf1b-119">Requirements</span></span>  
 <span data-ttu-id="6bf1b-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bf1b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bf1b-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bf1b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bf1b-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6bf1b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bf1b-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bf1b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf1b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-124">See also</span></span>

- [<span data-ttu-id="6bf1b-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6bf1b-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
