---
title: IHostCrst Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst
helpviewer_keywords: IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59485d7a642ba8b3233d5d077062e89fb2ac9b14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="d8023-102">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8023-102">IHostCrst Interface</span></span>
<span data-ttu-id="d8023-103">İş parçacığı oluşturma için önemli bir bölümü ana bilgisayarın gösterimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="d8023-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8023-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d8023-104">Methods</span></span>  
  
|<span data-ttu-id="d8023-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d8023-105">Method</span></span>|<span data-ttu-id="d8023-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8023-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8023-107">Enter yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8023-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="d8023-108">Kritik bölüm girer.</span><span class="sxs-lookup"><span data-stu-id="d8023-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="d8023-109">Leave yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8023-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="d8023-110">Kritik bölüm bırakır.</span><span class="sxs-lookup"><span data-stu-id="d8023-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="d8023-111">SetSpinCount yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8023-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="d8023-112">Kritik Bölümü için dönüş sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d8023-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="d8023-113">TryEnter yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8023-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="d8023-114">Kritik bölüm ve raporları başarı veya başarısızlık hemen girmek çalışır.</span><span class="sxs-lookup"><span data-stu-id="d8023-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8023-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8023-115">Remarks</span></span>  
 <span data-ttu-id="d8023-116">`IHostCrst`Ortak dil çalışma zamanı (CLR) önemli bir bölümü doğrudan ana bilgisayarın gösterimi ile iletişim kurmak için Win32 işlevleri gibi kullanmak yerine sağlar `EnterCriticalSection` veya `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="d8023-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8023-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8023-117">Requirements</span></span>  
 <span data-ttu-id="d8023-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8023-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8023-119">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8023-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8023-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d8023-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8023-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8023-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8023-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8023-122">See Also</span></span>  
 [<span data-ttu-id="d8023-123">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8023-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d8023-124">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8023-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="d8023-125">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d8023-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
