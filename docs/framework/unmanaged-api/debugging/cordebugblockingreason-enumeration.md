---
title: CorDebugBlockingReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe5e1267b619d5900ed9af55dd6079a8f38d6550
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406906"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="93896-102">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="93896-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="93896-103">Bir iş parçacığı neden engellenmiş duruma nedeniyle belirli bir nesne üzerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="93896-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93896-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93896-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="93896-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="93896-105">Members</span></span>  
  
|<span data-ttu-id="93896-106">Üye</span><span class="sxs-lookup"><span data-stu-id="93896-106">Member</span></span>|<span data-ttu-id="93896-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93896-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="93896-108">Yalnızca dahili kullanım.</span><span class="sxs-lookup"><span data-stu-id="93896-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="93896-109">Bir iş parçacığı bir nesne üzerinde İzleyici kilit ile ilişkili kritik bölüm almaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="93896-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="93896-110">Birini çağırın genellikle, bu oluşur <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> veya <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="93896-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="93896-111">Bir iş parçacığı bir nesne için İzleyici kilidi ile ilişkili olay bekliyor.</span><span class="sxs-lookup"><span data-stu-id="93896-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="93896-112">Birini çağırın genellikle, bu oluşur <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="93896-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93896-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93896-113">Remarks</span></span>  
 <span data-ttu-id="93896-114">Zaman `BLOCKING_MONITOR_CRITICAL_SECTION` veya `BLOCKING_MONITOR_EVENT` üye kullanılıyor bir [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısı, `pBlockingObject` giriliyor nesneyi temsil eden bir "ICorDebugValue" arabirim yapısı noktalarına üyesi .</span><span class="sxs-lookup"><span data-stu-id="93896-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="93896-115">Uygulamak için de garanti [Icordebugheapvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="93896-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93896-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93896-116">Requirements</span></span>  
 <span data-ttu-id="93896-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93896-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93896-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93896-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93896-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93896-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93896-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93896-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93896-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93896-121">See Also</span></span>  
 [<span data-ttu-id="93896-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="93896-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="93896-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="93896-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
