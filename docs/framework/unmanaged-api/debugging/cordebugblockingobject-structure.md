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
ms.openlocfilehash: ed7db321b32657087b791758096c692f25f3d7f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407842"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="83290-102">CorDebugBlockingObject Yapısı</span><span class="sxs-lookup"><span data-stu-id="83290-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="83290-103">Bir iş parçacığı ve iş parçacığı engellendi belirli bir nedenle engelleyen bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83290-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83290-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83290-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="83290-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="83290-105">Members</span></span>  
  
|<span data-ttu-id="83290-106">Üye</span><span class="sxs-lookup"><span data-stu-id="83290-106">Member</span></span>|<span data-ttu-id="83290-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83290-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="83290-108">İş parçacığı engelleyen nesnesi.</span><span class="sxs-lookup"><span data-stu-id="83290-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="83290-109">Bu nesne yalnızca geçerli eşitlenmiş durumuna süre için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="83290-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="83290-110">İki iş parçacığı aynı eşitlenmiş durumuna içinde aynı nesne üzerinde engelliyorsanız bekleyebilir [Icordebugvalue::getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) yöntemi aynı değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="83290-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="83290-111">Ancak, arabirimler olabilir veya eşdeğer işaretçisi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="83290-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="83290-112">Engelleme işleminden önce milisaniye sayısını zaman aşımı ya da onu olacağı zaman aşımına gösterir SONSUZ değeri görüntüler. Zaman aşımı değerini değil hala kalan zaman engelleme işlemi için toplam süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="83290-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="83290-113">İş parçacığı bu nesne üzerinde engellendi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="83290-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83290-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83290-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83290-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83290-115">Requirements</span></span>  
 <span data-ttu-id="83290-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83290-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83290-117">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="83290-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="83290-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83290-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83290-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83290-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83290-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83290-120">See Also</span></span>  
 [<span data-ttu-id="83290-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="83290-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="83290-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="83290-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
