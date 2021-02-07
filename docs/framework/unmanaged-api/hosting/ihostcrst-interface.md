---
description: 'Daha fazla bilgi edinin: IHostCrst arabirimi'
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
ms.openlocfilehash: 7945f0087667c1d610a1a2370528b055af74d579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708885"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="bab70-103">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bab70-103">IHostCrst Interface</span></span>

<span data-ttu-id="bab70-104">İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="bab70-104">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bab70-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bab70-105">Methods</span></span>  
  
|<span data-ttu-id="bab70-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bab70-106">Method</span></span>|<span data-ttu-id="bab70-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bab70-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bab70-108">Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bab70-108">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="bab70-109">Kritik bölümüne girer.</span><span class="sxs-lookup"><span data-stu-id="bab70-109">Enters the critical section.</span></span>|  
|[<span data-ttu-id="bab70-110">Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bab70-110">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="bab70-111">Kritik bölümünü bırakır.</span><span class="sxs-lookup"><span data-stu-id="bab70-111">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="bab70-112">SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bab70-112">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="bab70-113">Kritik bölüm için döngü sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bab70-113">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="bab70-114">TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bab70-114">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="bab70-115">Kritik bölümü girmeye çalışır ve başarılı veya başarısız olarak anında rapor verebilir.</span><span class="sxs-lookup"><span data-stu-id="bab70-115">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bab70-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bab70-116">Remarks</span></span>  

 <span data-ttu-id="bab70-117">`IHostCrst` ortak dil çalışma zamanının (CLR), veya gibi Win32 işlevlerini kullanmak yerine, kritik bir bölümün temsili ile doğrudan iletişim kurmasına izin verir `EnterCriticalSection` `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="bab70-117">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab70-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bab70-118">Requirements</span></span>  

 <span data-ttu-id="bab70-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bab70-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab70-120">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bab70-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bab70-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bab70-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bab70-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bab70-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab70-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bab70-123">See also</span></span>

- [<span data-ttu-id="bab70-124">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bab70-124">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="bab70-125">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bab70-125">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="bab70-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bab70-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
