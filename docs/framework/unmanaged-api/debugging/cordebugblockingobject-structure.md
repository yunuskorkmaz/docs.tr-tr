---
description: 'Daha fazla bilgi edinin: CorDebugBlockingObject yapısı'
title: CorDebugBlockingObject Yapısı
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
ms.openlocfilehash: 2b16af5eecb01067c2ee6811613f964af391f345
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712226"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="2a400-103">CorDebugBlockingObject Yapısı</span><span class="sxs-lookup"><span data-stu-id="2a400-103">CorDebugBlockingObject Structure</span></span>

<span data-ttu-id="2a400-104">Bir iş parçacığını engelleyen bir nesne ve iş parçacığının engellediği belirli bir nedeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a400-104">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a400-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a400-105">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="2a400-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2a400-106">Members</span></span>  
  
|<span data-ttu-id="2a400-107">Üye</span><span class="sxs-lookup"><span data-stu-id="2a400-107">Member</span></span>|<span data-ttu-id="2a400-108">Description</span><span class="sxs-lookup"><span data-stu-id="2a400-108">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="2a400-109">İş parçacığının engellediği nesne.</span><span class="sxs-lookup"><span data-stu-id="2a400-109">The object on which the thread is blocking.</span></span> <span data-ttu-id="2a400-110">Bu nesne yalnızca geçerli eşitlenmiş durumun süresi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2a400-110">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="2a400-111">Aynı eşitlenmiş durum içindeki aynı nesnede iki iş parçacığı engellenirse, [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) yönteminin aynı değeri döndürmesini beklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2a400-111">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="2a400-112">Ancak, arabirimler işaretçi eşdeğeri olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2a400-112">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="2a400-113">Engelleme işlemi zaman aşımına geçmeden önce geçen milisaniye sayısı veya sonsuz değeri, zaman aşımına gerekmediğini gösterir. Zaman aşımı değeri, hala kalan süre değil, engelleyici işlem için geçen sürenin toplam uzunluğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a400-113">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="2a400-114">Bu nesne üzerinde iş parçacığının engellendiği neden.</span><span class="sxs-lookup"><span data-stu-id="2a400-114">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a400-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a400-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a400-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a400-116">Requirements</span></span>  

 <span data-ttu-id="2a400-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a400-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a400-118">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="2a400-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="2a400-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a400-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a400-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a400-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a400-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a400-121">See also</span></span>

- [<span data-ttu-id="2a400-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="2a400-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="2a400-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2a400-123">Debugging</span></span>](index.md)
