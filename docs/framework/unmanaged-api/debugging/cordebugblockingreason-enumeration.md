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
ms.openlocfilehash: 3ea71439c9a6c494c218a7cfc18508f4f8173b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740377"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="fd6a5-102">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fd6a5-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="fd6a5-103">Belirli bir nesne üzerinde bir iş parçacığı neden engellenmiş duruma nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd6a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd6a5-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="fd6a5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fd6a5-105">Members</span></span>  
  
|<span data-ttu-id="fd6a5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fd6a5-106">Member</span></span>|<span data-ttu-id="fd6a5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd6a5-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="fd6a5-108">Yalnızca iç kullanım.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="fd6a5-109">Bir iş parçacığı, bir nesne izleme kilidi ile ilişkili olan kritik bölümü almaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="fd6a5-110">Biri çağırdığınızda genelde böyle <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> veya <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="fd6a5-111">Bir iş parçacığı, bir nesne için İzleyici kilit ile ilişkili olay bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="fd6a5-112">Biri çağırdığınızda genelde böyle <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd6a5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd6a5-113">Remarks</span></span>  
 <span data-ttu-id="fd6a5-114">Zaman `BLOCKING_MONITOR_CRITICAL_SECTION` veya `BLOCKING_MONITOR_EVENT` üyesi kullanılan bir [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısını `pBlockingObject` yapısı noktalarına giriliyor nesnesini temsil eden bir "ICorDebugValue" arabirim üyesi .</span><span class="sxs-lookup"><span data-stu-id="fd6a5-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="fd6a5-115">Uygulamak için de garanti [Icordebugheapvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd6a5-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd6a5-116">Requirements</span></span>  
 <span data-ttu-id="fd6a5-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd6a5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd6a5-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd6a5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd6a5-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd6a5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd6a5-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd6a5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6a5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6a5-121">See also</span></span>

- [<span data-ttu-id="fd6a5-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fd6a5-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="fd6a5-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fd6a5-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
