---
description: 'Şu konuda daha fazla bilgi edinin: IHostSecurityManager arabirimi'
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
ms.openlocfilehash: 76ba26443fa2a4e65459dd073eb6d22031548112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671549"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="5249d-103">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5249d-103">IHostSecurityManager Interface</span></span>

<span data-ttu-id="5249d-104">Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamı üzerinde erişime ve denetime izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5249d-104">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5249d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5249d-105">Methods</span></span>  
  
|<span data-ttu-id="5249d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5249d-106">Method</span></span>|<span data-ttu-id="5249d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5249d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5249d-108">GetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5249d-108">GetSecurityContext Method</span></span>](ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="5249d-109">Konaktan istenen [IHostSecurityContext](ihostsecuritycontext-interface.md) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="5249d-109">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="5249d-110">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5249d-110">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="5249d-111">Geçerli Kullanıcı kimliğinin kimlik bilgileri kullanılarak kodun yürütülmesini ister.</span><span class="sxs-lookup"><span data-stu-id="5249d-111">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="5249d-112">OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5249d-112">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="5249d-113">Geçerli iş parçacığıyla ilişkili isteğe bağlı erişim belirtecini açar.</span><span class="sxs-lookup"><span data-stu-id="5249d-113">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="5249d-114">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5249d-114">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="5249d-115">Geçerli Kullanıcı kimliğini kimliğe bürünme işlemini sonlandırır ve özgün iş parçacığı belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5249d-115">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="5249d-116">SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5249d-116">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="5249d-117">Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5249d-117">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="5249d-118">SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5249d-118">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="5249d-119">Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5249d-119">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5249d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5249d-120">Remarks</span></span>  

 <span data-ttu-id="5249d-121">Bir konak, ortak dil çalışma zamanı (CLR) ve Kullanıcı kodu tarafından iş parçacığı belirteçlerine yönelik tüm kod erişimini denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5249d-121">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="5249d-122">Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5249d-122">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="5249d-123">`IHostSecurityContext` CLR için donuk olan bu güvenlik bağlamı bilgilerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="5249d-123">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="5249d-124">CLR yönetilen iş parçacığı bağlamını dahili olarak işler.</span><span class="sxs-lookup"><span data-stu-id="5249d-124">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="5249d-125">Aşağıdaki durumlarda işlemi özel olarak sorgular `IHostSecurityManager` :</span><span class="sxs-lookup"><span data-stu-id="5249d-125">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="5249d-126">Sonlandırıcısı iş parçacığında, sonlandırıcısı yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="5249d-126">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="5249d-127">Sınıf ve modül Oluşturucu yürütme sırasında.</span><span class="sxs-lookup"><span data-stu-id="5249d-127">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="5249d-128">Çalışan iş parçacığındaki zaman uyumsuz noktalarında [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) metoduna çağrılar.</span><span class="sxs-lookup"><span data-stu-id="5249d-128">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="5249d-129">G/ç tamamlama bağlantı noktalarıyla bakım yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="5249d-129">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5249d-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5249d-130">Requirements</span></span>  

 <span data-ttu-id="5249d-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5249d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5249d-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5249d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5249d-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5249d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5249d-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5249d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5249d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5249d-135">See also</span></span>

- [<span data-ttu-id="5249d-136">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5249d-136">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="5249d-137">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5249d-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
