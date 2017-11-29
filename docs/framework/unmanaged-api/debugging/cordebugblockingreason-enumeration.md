---
title: "CorDebugBlockingReason Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingReason
helpviewer_keywords: CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 505a83f15d5056b0280af31d372623530d6e66ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="bc0d7-102">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bc0d7-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="bc0d7-103">Bir iş parçacığı neden engellenmiş duruma nedeniyle belirli bir nesne üzerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc0d7-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="bc0d7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bc0d7-105">Members</span></span>  
  
|<span data-ttu-id="bc0d7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bc0d7-106">Member</span></span>|<span data-ttu-id="bc0d7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc0d7-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="bc0d7-108">Yalnızca dahili kullanım.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="bc0d7-109">Bir iş parçacığı bir nesne üzerinde İzleyici kilit ile ilişkili kritik bölüm almaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="bc0d7-110">Birini çağırın genellikle, bu oluşur <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> veya <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="bc0d7-111">Bir iş parçacığı bir nesne için İzleyici kilidi ile ilişkili olay bekliyor.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="bc0d7-112">Birini çağırın genellikle, bu oluşur <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc0d7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc0d7-113">Remarks</span></span>  
 <span data-ttu-id="bc0d7-114">Zaman `BLOCKING_MONITOR_CRITICAL_SECTION` veya `BLOCKING_MONITOR_EVENT` üye kullanılıyor bir [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısı, `pBlockingObject` giriliyor nesneyi temsil eden bir "ICorDebugValue" arabirim yapısı noktalarına üyesi .</span><span class="sxs-lookup"><span data-stu-id="bc0d7-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="bc0d7-115">Uygulamak için de garanti [Icordebugheapvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0d7-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc0d7-116">Requirements</span></span>  
 <span data-ttu-id="bc0d7-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc0d7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc0d7-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc0d7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc0d7-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc0d7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc0d7-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0d7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0d7-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc0d7-121">See Also</span></span>  
 [<span data-ttu-id="bc0d7-122">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="bc0d7-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="bc0d7-123">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="bc0d7-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
