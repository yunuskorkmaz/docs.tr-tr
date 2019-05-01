---
title: IHostSecurityManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957592"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="950e7-102">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="950e7-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="950e7-103">Erişim ve güvenlik bağlamı şu anda yürütülen iş parçacığının denetime izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="950e7-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="950e7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="950e7-104">Methods</span></span>  
  
|<span data-ttu-id="950e7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="950e7-105">Method</span></span>|<span data-ttu-id="950e7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="950e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="950e7-107">GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="950e7-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="950e7-108">İstenen alır [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) konaktan.</span><span class="sxs-lookup"><span data-stu-id="950e7-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="950e7-109">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="950e7-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="950e7-110">İstek, kod, geçerli kullanıcı kimliğinin kimlik bilgilerini kullanarak yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="950e7-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="950e7-111">OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="950e7-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="950e7-112">Geçerli iş parçacığıyla ilişkilendirilmiş isteğe bağlı erişim belirteci açılır.</span><span class="sxs-lookup"><span data-stu-id="950e7-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="950e7-113">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="950e7-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="950e7-114">Geçerli kullanıcı kimliğine bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="950e7-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="950e7-115">SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="950e7-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="950e7-116">Şu anda çalışan bir iş parçacığı için güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="950e7-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="950e7-117">SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="950e7-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="950e7-118">Şu anda çalışan bir iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="950e7-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="950e7-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="950e7-119">Remarks</span></span>  
 <span data-ttu-id="950e7-120">Bir konak ortak dil çalışma zamanı (CLR) ve kullanıcı kodu tarafından iş parçacığı belirteçleri tüm kod erişimi denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="950e7-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="950e7-121">Bu eksiksiz güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemler veya kod noktaları kod kısıtlı erişimle üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="950e7-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="950e7-122">`IHostSecurityContext` CLR için donuktur bu güvenlik bağlamı bilgileri yalıtır.</span><span class="sxs-lookup"><span data-stu-id="950e7-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="950e7-123">CLR, yönetilen iş parçacığı bağlamı dahili olarak işler.</span><span class="sxs-lookup"><span data-stu-id="950e7-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="950e7-124">İşleme özel sorgular `IHostSecurityManager` aşağıdaki durumlarda:</span><span class="sxs-lookup"><span data-stu-id="950e7-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="950e7-125">Sonlandırıcı iş parçacığında, sonlandırıcı yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="950e7-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="950e7-126">Sınıf ve modül Oluşturucu yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="950e7-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="950e7-127">Zaman uyumsuz noktalarda yapılan çağrıda çalışan iş parçacığı üzerinde [Ihostthreadpoolmanager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="950e7-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="950e7-128">G/ç tamamlama bağlantı noktaları Bakım.</span><span class="sxs-lookup"><span data-stu-id="950e7-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="950e7-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="950e7-129">Requirements</span></span>  
 <span data-ttu-id="950e7-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="950e7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="950e7-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="950e7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="950e7-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="950e7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="950e7-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="950e7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950e7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="950e7-134">See also</span></span>

- [<span data-ttu-id="950e7-135">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="950e7-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="950e7-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="950e7-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
