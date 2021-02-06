---
description: 'Daha fazla bilgi edinin: ICorDebugThread2 Interface'
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
ms.openlocfilehash: 81f687f6daff9ffa7298ec6d818a214b8934bcc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658509"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="d3b16-103">ICorDebugThread2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3b16-103">ICorDebugThread2 Interface</span></span>

<span data-ttu-id="d3b16-104">ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="d3b16-104">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3b16-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3b16-105">Methods</span></span>  
  
|<span data-ttu-id="d3b16-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3b16-106">Method</span></span>|<span data-ttu-id="d3b16-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3b16-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3b16-108">GetActiveFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3b16-108">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="d3b16-109">Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="d3b16-109">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="d3b16-110">GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3b16-110">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="d3b16-111">Bunun için bir bağlantı tanımlayıcısı alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="d3b16-111">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="d3b16-112">GetTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3b16-112">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="d3b16-113">Bunun için bir görev tanımlayıcısı alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="d3b16-113">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="d3b16-114">GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3b16-114">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="d3b16-115">Bunun için işletim sistemi iş parçacığı tanımlayıcısını alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="d3b16-115">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="d3b16-116">InterceptCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3b16-116">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="d3b16-117">Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="d3b16-117">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3b16-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3b16-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3b16-119">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d3b16-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3b16-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3b16-120">Requirements</span></span>  

 <span data-ttu-id="d3b16-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3b16-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b16-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3b16-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3b16-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3b16-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3b16-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3b16-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b16-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b16-125">See also</span></span>

- [<span data-ttu-id="d3b16-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3b16-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
