---
description: 'Daha fazla bilgi edinin: CorDebugBlockingReason numaralandırması'
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
ms.openlocfilehash: c2d9c805549d046fe40ab5ea00f30e2fd0a680a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747119"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="6bd6c-103">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6bd6c-103">CorDebugBlockingReason Enumeration</span></span>

<span data-ttu-id="6bd6c-104">Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bd6c-104">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd6c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6bd6c-105">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="6bd6c-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6bd6c-106">Members</span></span>  
  
|<span data-ttu-id="6bd6c-107">Üye</span><span class="sxs-lookup"><span data-stu-id="6bd6c-107">Member</span></span>|<span data-ttu-id="6bd6c-108">Description</span><span class="sxs-lookup"><span data-stu-id="6bd6c-108">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="6bd6c-109">Yalnızca iç kullanım.</span><span class="sxs-lookup"><span data-stu-id="6bd6c-109">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="6bd6c-110">Bir iş parçacığı, bir nesne üzerindeki izleyici kilidi ile ilişkili kritik bölümü almaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="6bd6c-110">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="6bd6c-111">Genellikle, veya yöntemlerinden birini çağırdığınızda bu durum oluşur <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6bd6c-111">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="6bd6c-112">Bir iş parçacığı bir nesne için izleyici kilidi ile ilişkili olayı bekliyor.</span><span class="sxs-lookup"><span data-stu-id="6bd6c-112">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="6bd6c-113">Genellikle, bu yöntemlerden birini çağırdığınızda oluşur <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` .</span><span class="sxs-lookup"><span data-stu-id="6bd6c-113">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bd6c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bd6c-114">Remarks</span></span>  

 <span data-ttu-id="6bd6c-115">`BLOCKING_MONITOR_CRITICAL_SECTION`Veya `BLOCKING_MONITOR_EVENT` üyesi bir [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapısında kullanıldığında, `pBlockingObject` yapının üyesi, girilmekte olan nesneyi temsil eden bir "ICorDebugValue" arabirimine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6bd6c-115">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="6bd6c-116">Ayrıca, [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) arabirimini uygulamak da garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="6bd6c-116">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bd6c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bd6c-117">Requirements</span></span>  

 <span data-ttu-id="6bd6c-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bd6c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd6c-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bd6c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bd6c-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6bd6c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bd6c-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd6c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd6c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bd6c-122">See also</span></span>

- [<span data-ttu-id="6bd6c-123">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="6bd6c-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="6bd6c-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6bd6c-124">Debugging</span></span>](index.md)
