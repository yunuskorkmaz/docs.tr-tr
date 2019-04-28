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
ms.openlocfilehash: 12a114ea65aca544d653704cdfb01ed15d19c581
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609275"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="850e3-102">CorDebugBlockingObject Yapısı</span><span class="sxs-lookup"><span data-stu-id="850e3-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="850e3-103">Bir iş parçacığı ve iş parçacığı engellenir belirli bir nedenle engelleyen bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="850e3-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="850e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="850e3-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="850e3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="850e3-105">Members</span></span>  
  
|<span data-ttu-id="850e3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="850e3-106">Member</span></span>|<span data-ttu-id="850e3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="850e3-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="850e3-108">Nesne üzerinde iş parçacığını engelliyor.</span><span class="sxs-lookup"><span data-stu-id="850e3-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="850e3-109">Bu nesne yalnızca geçerli eşitleme durumunun süresi boyunca geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="850e3-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="850e3-110">İki iş parçacığı aynı eşitlenmiş durum içinde'aynı nesne üzerinde engelliyorsanız bekleyebilir [Icordebugvalue::getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) aynı değeri döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="850e3-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="850e3-111">Ancak, arabirimler olabilir veya eşdeğer bir işaretçi olabilir.</span><span class="sxs-lookup"><span data-stu-id="850e3-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="850e3-112">Engelleme işleminden önce milisaniye sayısını, zaman aşımı veya onu olacağı zaman aşımına gösteren SONSUZ değer olur. Zaman aşımı değerini durdurma işlemi, yine de kalan saat için toplam süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="850e3-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="850e3-113">Neden iş parçacığı bu nesne üzerinde engellenir.</span><span class="sxs-lookup"><span data-stu-id="850e3-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="850e3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="850e3-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="850e3-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="850e3-115">Requirements</span></span>  
 <span data-ttu-id="850e3-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="850e3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="850e3-117">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="850e3-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="850e3-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="850e3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="850e3-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="850e3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850e3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="850e3-120">See also</span></span>

- [<span data-ttu-id="850e3-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="850e3-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="850e3-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="850e3-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
