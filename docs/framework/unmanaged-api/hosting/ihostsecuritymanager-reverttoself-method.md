---
title: "IHostSecurityManager::RevertToSelf Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.RevertToSelf
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0fad325bc3df54f412a797e9944f5b1f38615786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="9dd2a-102">IHostSecurityManager::RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dd2a-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="9dd2a-103">Geçerli kullanıcı kimliği kimliğe bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dd2a-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9dd2a-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9dd2a-105">Return Value</span></span>  
  
|<span data-ttu-id="9dd2a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9dd2a-106">HRESULT</span></span>|<span data-ttu-id="9dd2a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dd2a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9dd2a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9dd2a-108">S_OK</span></span>|<span data-ttu-id="9dd2a-109">`RevertToSelf`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="9dd2a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9dd2a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9dd2a-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9dd2a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9dd2a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9dd2a-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-113">The call timed out.</span></span>|  
|<span data-ttu-id="9dd2a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd2a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9dd2a-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9dd2a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9dd2a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9dd2a-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9dd2a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9dd2a-118">E_FAIL</span></span>|<span data-ttu-id="9dd2a-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9dd2a-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9dd2a-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dd2a-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dd2a-122">Remarks</span></span>  
 <span data-ttu-id="9dd2a-123">`RevertToSelf`önceki bir çağrı sonra özgün iş parçacığı belirteci döndürülecek adlı [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dd2a-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dd2a-124">Requirements</span></span>  
 <span data-ttu-id="9dd2a-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dd2a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dd2a-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9dd2a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9dd2a-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9dd2a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dd2a-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dd2a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd2a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-129">See Also</span></span>  
 [<span data-ttu-id="9dd2a-130">Ihostsecuritycontext arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dd2a-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="9dd2a-131">Ihostsecuritymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dd2a-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="9dd2a-132">ImpersonateLoggedOnUser yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dd2a-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
