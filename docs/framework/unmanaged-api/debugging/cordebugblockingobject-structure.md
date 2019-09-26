---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273965"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="02ad8-102">CorDebugBlockingObject Yapısı</span><span class="sxs-lookup"><span data-stu-id="02ad8-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="02ad8-103">Bir iş parçacığını engelleyen bir nesne ve iş parçacığının engellediği belirli bir nedeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02ad8-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ad8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02ad8-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="02ad8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="02ad8-105">Members</span></span>  
  
|<span data-ttu-id="02ad8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="02ad8-106">Member</span></span>|<span data-ttu-id="02ad8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02ad8-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="02ad8-108">İş parçacığının engellediği nesne.</span><span class="sxs-lookup"><span data-stu-id="02ad8-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="02ad8-109">Bu nesne yalnızca geçerli eşitlenmiş durumun süresi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="02ad8-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="02ad8-110">Aynı eşitlenmiş durum içindeki aynı nesnede iki iş parçacığı engellenirse, [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) yönteminin aynı değeri döndürmesini beklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="02ad8-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="02ad8-111">Ancak, arabirimler işaretçi eşdeğeri olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="02ad8-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="02ad8-112">Engelleme işlemi zaman aşımına geçmeden önce geçen milisaniye sayısı veya sonsuz değeri, zaman aşımına gerekmediğini gösterir. Zaman aşımı değeri, hala kalan süre değil, engelleyici işlem için geçen sürenin toplam uzunluğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02ad8-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="02ad8-113">Bu nesne üzerinde iş parçacığının engellendiği neden.</span><span class="sxs-lookup"><span data-stu-id="02ad8-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02ad8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02ad8-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02ad8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02ad8-115">Requirements</span></span>  
 <span data-ttu-id="02ad8-116">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02ad8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02ad8-117">**Üst bilgi** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="02ad8-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="02ad8-118">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="02ad8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02ad8-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ad8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ad8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02ad8-120">See also</span></span>

- [<span data-ttu-id="02ad8-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="02ad8-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="02ad8-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="02ad8-122">Debugging</span></span>](index.md)
