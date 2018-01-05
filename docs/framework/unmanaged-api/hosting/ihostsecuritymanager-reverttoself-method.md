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
ms.workload: dotnet
ms.openlocfilehash: 765d40cc99269031093e9241ed1bba6c82b9a042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="fcbd6-102">IHostSecurityManager::RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcbd6-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="fcbd6-103">Geçerli kullanıcı kimliği kimliğe bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcbd6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcbd6-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fcbd6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fcbd6-105">Return Value</span></span>  
  
|<span data-ttu-id="fcbd6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fcbd6-106">HRESULT</span></span>|<span data-ttu-id="fcbd6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcbd6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fcbd6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fcbd6-108">S_OK</span></span>|<span data-ttu-id="fcbd6-109">`RevertToSelf`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="fcbd6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fcbd6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fcbd6-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fcbd6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fcbd6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fcbd6-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-113">The call timed out.</span></span>|  
|<span data-ttu-id="fcbd6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fcbd6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fcbd6-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fcbd6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fcbd6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fcbd6-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fcbd6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fcbd6-118">E_FAIL</span></span>|<span data-ttu-id="fcbd6-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fcbd6-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fcbd6-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcbd6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcbd6-122">Remarks</span></span>  
 <span data-ttu-id="fcbd6-123">`RevertToSelf`önceki bir çağrı sonra özgün iş parçacığı belirteci döndürülecek adlı [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbd6-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcbd6-124">Requirements</span></span>  
 <span data-ttu-id="fcbd6-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcbd6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbd6-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fcbd6-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fcbd6-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fcbd6-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcbd6-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbd6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbd6-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcbd6-129">See Also</span></span>  
 [<span data-ttu-id="fcbd6-130">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcbd6-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="fcbd6-131">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcbd6-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="fcbd6-132">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcbd6-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
