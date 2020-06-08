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
ms.openlocfilehash: 237fe23493460df77a79ba3aed9f0a809cd8aa23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501475"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="41071-102">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41071-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="41071-103">Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamı üzerinde erişime ve denetime izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="41071-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41071-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="41071-104">Methods</span></span>  
  
|<span data-ttu-id="41071-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="41071-105">Method</span></span>|<span data-ttu-id="41071-106">Description</span><span class="sxs-lookup"><span data-stu-id="41071-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41071-107">GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41071-107">GetSecurityContext Method</span></span>](ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="41071-108">Konaktan istenen [IHostSecurityContext](ihostsecuritycontext-interface.md) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="41071-108">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="41071-109">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41071-109">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="41071-110">Geçerli Kullanıcı kimliğinin kimlik bilgileri kullanılarak kodun yürütülmesini ister.</span><span class="sxs-lookup"><span data-stu-id="41071-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="41071-111">OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41071-111">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="41071-112">Geçerli iş parçacığıyla ilişkili isteğe bağlı erişim belirtecini açar.</span><span class="sxs-lookup"><span data-stu-id="41071-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="41071-113">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41071-113">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="41071-114">Geçerli Kullanıcı kimliğini kimliğe bürünme işlemini sonlandırır ve özgün iş parçacığı belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="41071-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="41071-115">SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41071-115">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="41071-116">Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="41071-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="41071-117">SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41071-117">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="41071-118">Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="41071-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41071-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41071-119">Remarks</span></span>  
 <span data-ttu-id="41071-120">Bir konak, ortak dil çalışma zamanı (CLR) ve Kullanıcı kodu tarafından iş parçacığı belirteçlerine yönelik tüm kod erişimini denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="41071-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="41071-121">Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41071-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="41071-122">`IHostSecurityContext`CLR için donuk olan bu güvenlik bağlamı bilgilerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="41071-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="41071-123">CLR yönetilen iş parçacığı bağlamını dahili olarak işler.</span><span class="sxs-lookup"><span data-stu-id="41071-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="41071-124">Aşağıdaki durumlarda işlemi özel olarak sorgular `IHostSecurityManager` :</span><span class="sxs-lookup"><span data-stu-id="41071-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="41071-125">Sonlandırıcısı iş parçacığında, sonlandırıcısı yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="41071-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="41071-126">Sınıf ve modül Oluşturucu yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="41071-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="41071-127">Çalışan iş parçacığındaki zaman uyumsuz noktalarında [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) metoduna çağrılar.</span><span class="sxs-lookup"><span data-stu-id="41071-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="41071-128">G/ç tamamlama bağlantı noktalarıyla bakım yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="41071-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41071-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41071-129">Requirements</span></span>  
 <span data-ttu-id="41071-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41071-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41071-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41071-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41071-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="41071-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41071-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41071-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41071-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41071-134">See also</span></span>

- [<span data-ttu-id="41071-135">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41071-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="41071-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="41071-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
