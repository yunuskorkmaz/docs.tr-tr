---
title: IHostSecurityManager::RevertToSelf Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98af4c0d2e5f5930c179b4b96ffccd7ef0703211
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562407"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="6c367-102">IHostSecurityManager::RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c367-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="6c367-103">Geçerli kullanıcı kimliğine bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c367-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c367-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c367-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6c367-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c367-105">Return Value</span></span>  
  
|<span data-ttu-id="6c367-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c367-106">HRESULT</span></span>|<span data-ttu-id="6c367-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c367-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c367-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c367-108">S_OK</span></span>|<span data-ttu-id="6c367-109">`RevertToSelf` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6c367-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="6c367-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c367-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c367-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6c367-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c367-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c367-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c367-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6c367-113">The call timed out.</span></span>|  
|<span data-ttu-id="6c367-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c367-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c367-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6c367-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c367-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c367-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c367-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6c367-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c367-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c367-118">E_FAIL</span></span>|<span data-ttu-id="6c367-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6c367-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c367-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c367-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c367-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c367-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c367-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c367-122">Remarks</span></span>  
 <span data-ttu-id="6c367-123">`RevertToSelf` çağrısında sonra özgün iş parçacığı belirteci döndürmek için çağrılan [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6c367-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c367-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c367-124">Requirements</span></span>  
 <span data-ttu-id="6c367-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c367-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c367-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c367-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c367-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6c367-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c367-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c367-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c367-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c367-129">See also</span></span>
- [<span data-ttu-id="6c367-130">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c367-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6c367-131">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c367-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="6c367-132">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c367-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
