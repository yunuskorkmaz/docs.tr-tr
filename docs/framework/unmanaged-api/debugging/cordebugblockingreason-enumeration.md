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
ms.openlocfilehash: 99fcf160b3e3b2b238520e3db5ba2e74b270380a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274137"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="b0199-102">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b0199-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="b0199-103">Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0199-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0199-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0199-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="b0199-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b0199-105">Members</span></span>  
  
|<span data-ttu-id="b0199-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b0199-106">Member</span></span>|<span data-ttu-id="b0199-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0199-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="b0199-108">Yalnızca iç kullanım.</span><span class="sxs-lookup"><span data-stu-id="b0199-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="b0199-109">Bir iş parçacığı, bir nesne üzerindeki izleyici kilidi ile ilişkili kritik bölümü almaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="b0199-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="b0199-110">Genellikle, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> veya <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> yöntemlerinden birini çağırdığınızda bu durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="b0199-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="b0199-111">Bir iş parçacığı bir nesne için izleyici kilidi ile ilişkili olayı bekliyor.</span><span class="sxs-lookup"><span data-stu-id="b0199-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="b0199-112">Genellikle, bu <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` yöntemlerden birini çağırdığınızda oluşur.</span><span class="sxs-lookup"><span data-stu-id="b0199-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0199-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0199-113">Remarks</span></span>  
 <span data-ttu-id="b0199-114">Veya üyesi bir [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapısında kullanıldığında, yapının üyesi,girilmekteolannesneyitemsiledenbir"ICorDebugValue"arabirimineişareteder.`pBlockingObject` `BLOCKING_MONITOR_EVENT` `BLOCKING_MONITOR_CRITICAL_SECTION`</span><span class="sxs-lookup"><span data-stu-id="b0199-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="b0199-115">Ayrıca, [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) arabirimini uygulamak da garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="b0199-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0199-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0199-116">Requirements</span></span>  
 <span data-ttu-id="b0199-117">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0199-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0199-118">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0199-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0199-119">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0199-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0199-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0199-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0199-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0199-121">See also</span></span>

- [<span data-ttu-id="b0199-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b0199-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="b0199-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b0199-123">Debugging</span></span>](index.md)
