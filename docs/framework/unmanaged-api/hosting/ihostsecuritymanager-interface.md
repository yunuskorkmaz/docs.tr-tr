---
title: IHostSecurityManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager
helpviewer_keywords: IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44f2272c0f4e1423c222a004559d7bbd58237d82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="1267b-102">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1267b-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="1267b-103">Erişim ve güvenlik bağlamı şu anda yürütülen iş parçacığı üzerinde denetime izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1267b-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1267b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1267b-104">Methods</span></span>  
  
|<span data-ttu-id="1267b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1267b-105">Method</span></span>|<span data-ttu-id="1267b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1267b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1267b-107">GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1267b-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="1267b-108">İstenen alır [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) ana bilgisayardan.</span><span class="sxs-lookup"><span data-stu-id="1267b-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="1267b-109">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1267b-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="1267b-110">İstek, kod geçerli kullanıcı kimlik bilgilerini kullanarak yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="1267b-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="1267b-111">OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1267b-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="1267b-112">Geçerli iş parçacığı ile ilişkili isteğe bağlı erişim belirteci açar.</span><span class="sxs-lookup"><span data-stu-id="1267b-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="1267b-113">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1267b-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="1267b-114">Geçerli kullanıcı kimliği kimliğe bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="1267b-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="1267b-115">SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1267b-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="1267b-116">Şu anda yürütülen iş parçacığı için güvenlik bağlamı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1267b-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="1267b-117">SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1267b-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="1267b-118">Şu anda yürütülen iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1267b-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1267b-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1267b-119">Remarks</span></span>  
 <span data-ttu-id="1267b-120">Bir ana iş parçacığı belirteçleri tüm kod erişimi ortak dil çalışma zamanı (CLR) ve kullanıcı kodu tarafından kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1267b-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="1267b-121">Bu tam güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemleri veya kısıtlı kod erişimi olan kod noktaları üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1267b-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="1267b-122">`IHostSecurityContext`CLR opak bu güvenlik bağlamı bilgileri yalıtır.</span><span class="sxs-lookup"><span data-stu-id="1267b-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="1267b-123">CLR yönetilen iş parçacığı içeriği dahili olarak işler.</span><span class="sxs-lookup"><span data-stu-id="1267b-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="1267b-124">İşlem özel sorgular `IHostSecurityManager` aşağıdaki durumlarda:</span><span class="sxs-lookup"><span data-stu-id="1267b-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="1267b-125">Sonlandırıcı parçacığında sonlandırıcıyı yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="1267b-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="1267b-126">Sınıf ve modül Oluşturucusu yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="1267b-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="1267b-127">Zaman uyumsuz noktalarında çağrılarında çalışan iş parçacığı üzerinde [Ihostthreadpoolmanager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1267b-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="1267b-128">G/ç tamamlama bağlantı noktaları Bakım.</span><span class="sxs-lookup"><span data-stu-id="1267b-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1267b-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1267b-129">Requirements</span></span>  
 <span data-ttu-id="1267b-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1267b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1267b-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1267b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1267b-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1267b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1267b-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1267b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1267b-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1267b-134">See Also</span></span>  
 [<span data-ttu-id="1267b-135">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1267b-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="1267b-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1267b-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
