---
title: IHostCrst Arabirimi
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 350af708456914c73929d2b8887173cf784d4294
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680566"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="761b6-102">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="761b6-102">IHostCrst Interface</span></span>

<span data-ttu-id="761b6-103">İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="761b6-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="761b6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="761b6-104">Methods</span></span>  
  
|<span data-ttu-id="761b6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="761b6-105">Method</span></span>|<span data-ttu-id="761b6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="761b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="761b6-107">Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761b6-107">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="761b6-108">Kritik bölümüne girer.</span><span class="sxs-lookup"><span data-stu-id="761b6-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="761b6-109">Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761b6-109">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="761b6-110">Kritik bölümünü bırakır.</span><span class="sxs-lookup"><span data-stu-id="761b6-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="761b6-111">SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761b6-111">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="761b6-112">Kritik bölüm için döngü sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="761b6-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="761b6-113">TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761b6-113">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="761b6-114">Kritik bölümü girmeye çalışır ve başarılı veya başarısız olarak anında rapor verebilir.</span><span class="sxs-lookup"><span data-stu-id="761b6-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="761b6-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="761b6-115">Remarks</span></span>  

 <span data-ttu-id="761b6-116">`IHostCrst` ortak dil çalışma zamanının (CLR), veya gibi Win32 işlevlerini kullanmak yerine, kritik bir bölümün temsili ile doğrudan iletişim kurmasına izin verir `EnterCriticalSection` `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="761b6-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="761b6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="761b6-117">Requirements</span></span>  

 <span data-ttu-id="761b6-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="761b6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="761b6-119">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="761b6-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="761b6-120">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="761b6-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="761b6-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="761b6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761b6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="761b6-122">See also</span></span>

- [<span data-ttu-id="761b6-123">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="761b6-123">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="761b6-124">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="761b6-124">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="761b6-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="761b6-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
