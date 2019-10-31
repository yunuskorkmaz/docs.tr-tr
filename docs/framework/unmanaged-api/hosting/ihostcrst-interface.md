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
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130518"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="7491a-102">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7491a-102">IHostCrst Interface</span></span>
<span data-ttu-id="7491a-103">İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="7491a-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7491a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7491a-104">Methods</span></span>  
  
|<span data-ttu-id="7491a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7491a-105">Method</span></span>|<span data-ttu-id="7491a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7491a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7491a-107">Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7491a-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="7491a-108">Kritik bölümüne girer.</span><span class="sxs-lookup"><span data-stu-id="7491a-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="7491a-109">Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7491a-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="7491a-110">Kritik bölümünü bırakır.</span><span class="sxs-lookup"><span data-stu-id="7491a-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="7491a-111">SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7491a-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="7491a-112">Kritik bölüm için döngü sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7491a-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="7491a-113">TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7491a-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="7491a-114">Kritik bölümü girmeye çalışır ve başarılı veya başarısız olarak anında rapor verebilir.</span><span class="sxs-lookup"><span data-stu-id="7491a-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7491a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7491a-115">Remarks</span></span>  
 <span data-ttu-id="7491a-116">`IHostCrst`, ortak dil çalışma zamanının (CLR), `EnterCriticalSection` veya `LeaveCriticalSection`gibi Win32 işlevleri yerine ana bilgisayarın kritik bir bölümün temsili ile doğrudan iletişim kurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7491a-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7491a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7491a-117">Requirements</span></span>  
 <span data-ttu-id="7491a-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7491a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7491a-119">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7491a-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7491a-120">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7491a-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7491a-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7491a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7491a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7491a-122">See also</span></span>

- [<span data-ttu-id="7491a-123">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7491a-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="7491a-124">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7491a-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="7491a-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7491a-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
