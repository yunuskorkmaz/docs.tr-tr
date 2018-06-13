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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f2ef8299911905d651ad5c3076dc9c74f397f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438925"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="80c2d-102">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c2d-102">IHostCrst Interface</span></span>
<span data-ttu-id="80c2d-103">İş parçacığı oluşturma için önemli bir bölümü ana bilgisayarın gösterimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="80c2d-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80c2d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="80c2d-104">Methods</span></span>  
  
|<span data-ttu-id="80c2d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="80c2d-105">Method</span></span>|<span data-ttu-id="80c2d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80c2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80c2d-107">Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80c2d-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="80c2d-108">Kritik bölüm girer.</span><span class="sxs-lookup"><span data-stu-id="80c2d-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="80c2d-109">Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80c2d-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="80c2d-110">Kritik bölüm bırakır.</span><span class="sxs-lookup"><span data-stu-id="80c2d-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="80c2d-111">SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80c2d-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="80c2d-112">Kritik Bölümü için dönüş sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="80c2d-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="80c2d-113">TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80c2d-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="80c2d-114">Kritik bölüm ve raporları başarı veya başarısızlık hemen girmek çalışır.</span><span class="sxs-lookup"><span data-stu-id="80c2d-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80c2d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80c2d-115">Remarks</span></span>  
 <span data-ttu-id="80c2d-116">`IHostCrst` Ortak dil çalışma zamanı (CLR) önemli bir bölümü doğrudan ana bilgisayarın gösterimi ile iletişim kurmak için Win32 işlevleri gibi kullanmak yerine sağlar `EnterCriticalSection` veya `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="80c2d-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80c2d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80c2d-117">Requirements</span></span>  
 <span data-ttu-id="80c2d-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c2d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c2d-119">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80c2d-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80c2d-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="80c2d-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80c2d-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c2d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c2d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80c2d-122">See Also</span></span>  
 [<span data-ttu-id="80c2d-123">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c2d-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="80c2d-124">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c2d-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="80c2d-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="80c2d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
