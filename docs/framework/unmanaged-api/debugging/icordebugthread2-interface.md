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
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379826"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="643f0-102">ICorDebugThread2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="643f0-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="643f0-103">ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="643f0-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="643f0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="643f0-104">Methods</span></span>  
  
|<span data-ttu-id="643f0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="643f0-105">Method</span></span>|<span data-ttu-id="643f0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="643f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="643f0-107">GetActiveFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="643f0-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="643f0-108">Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="643f0-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="643f0-109">GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="643f0-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="643f0-110">Bunun için bir bağlantı tanımlayıcısı alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="643f0-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="643f0-111">GetTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="643f0-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="643f0-112">Bunun için bir görev tanımlayıcısı alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="643f0-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="643f0-113">GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="643f0-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="643f0-114">Bunun için işletim sistemi iş parçacığı tanımlayıcısını alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="643f0-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="643f0-115">InterceptCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="643f0-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="643f0-116">Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="643f0-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="643f0-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="643f0-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="643f0-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="643f0-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="643f0-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="643f0-119">Requirements</span></span>  
 <span data-ttu-id="643f0-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="643f0-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="643f0-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="643f0-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="643f0-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="643f0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="643f0-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643f0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643f0-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="643f0-124">See also</span></span>

- [<span data-ttu-id="643f0-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="643f0-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
