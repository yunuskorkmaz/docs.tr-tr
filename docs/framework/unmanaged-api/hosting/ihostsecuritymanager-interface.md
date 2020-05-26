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
ms.openlocfilehash: b2c334c7a757c2f4044d08787bdae93ffc2804e4
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803892"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="f0964-102">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0964-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="f0964-103">Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamı üzerinde erişime ve denetime izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0964-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0964-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0964-104">Methods</span></span>  
  
|<span data-ttu-id="f0964-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f0964-105">Method</span></span>|<span data-ttu-id="f0964-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0964-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0964-107">GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0964-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="f0964-108">Konaktan istenen [IHostSecurityContext](ihostsecuritycontext-interface.md) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="f0964-108">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="f0964-109">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0964-109">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="f0964-110">Geçerli Kullanıcı kimliğinin kimlik bilgileri kullanılarak kodun yürütülmesini ister.</span><span class="sxs-lookup"><span data-stu-id="f0964-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="f0964-111">OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0964-111">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="f0964-112">Geçerli iş parçacığıyla ilişkili isteğe bağlı erişim belirtecini açar.</span><span class="sxs-lookup"><span data-stu-id="f0964-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="f0964-113">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0964-113">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="f0964-114">Geçerli Kullanıcı kimliğini kimliğe bürünme işlemini sonlandırır ve özgün iş parçacığı belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0964-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="f0964-115">SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0964-115">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="f0964-116">Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0964-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="f0964-117">SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0964-117">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="f0964-118">Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0964-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0964-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0964-119">Remarks</span></span>  
 <span data-ttu-id="f0964-120">Bir konak, ortak dil çalışma zamanı (CLR) ve Kullanıcı kodu tarafından iş parçacığı belirteçlerine yönelik tüm kod erişimini denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f0964-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="f0964-121">Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0964-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="f0964-122">`IHostSecurityContext`CLR için donuk olan bu güvenlik bağlamı bilgilerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="f0964-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="f0964-123">CLR yönetilen iş parçacığı bağlamını dahili olarak işler.</span><span class="sxs-lookup"><span data-stu-id="f0964-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="f0964-124">Aşağıdaki durumlarda işlemi özel olarak sorgular `IHostSecurityManager` :</span><span class="sxs-lookup"><span data-stu-id="f0964-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="f0964-125">Sonlandırıcısı iş parçacığında, sonlandırıcısı yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="f0964-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="f0964-126">Sınıf ve modül Oluşturucu yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="f0964-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="f0964-127">Çalışan iş parçacığındaki zaman uyumsuz noktalarında [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) metoduna çağrılar.</span><span class="sxs-lookup"><span data-stu-id="f0964-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="f0964-128">G/ç tamamlama bağlantı noktalarıyla bakım yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="f0964-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0964-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0964-129">Requirements</span></span>  
 <span data-ttu-id="f0964-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0964-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0964-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0964-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0964-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f0964-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0964-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0964-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0964-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0964-134">See also</span></span>

- [<span data-ttu-id="f0964-135">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0964-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="f0964-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0964-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
