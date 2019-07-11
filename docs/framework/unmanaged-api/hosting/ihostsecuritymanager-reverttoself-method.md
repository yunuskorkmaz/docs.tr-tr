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
ms.openlocfilehash: f098d8462229a405d5775203368478c7ee7e9f3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769394"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="77407-102">IHostSecurityManager::RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77407-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="77407-103">Geçerli kullanıcı kimliğine bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="77407-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77407-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77407-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="77407-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77407-105">Return Value</span></span>  
  
|<span data-ttu-id="77407-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77407-106">HRESULT</span></span>|<span data-ttu-id="77407-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77407-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77407-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="77407-108">S_OK</span></span>|<span data-ttu-id="77407-109">`RevertToSelf` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="77407-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="77407-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77407-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77407-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="77407-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77407-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77407-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77407-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="77407-113">The call timed out.</span></span>|  
|<span data-ttu-id="77407-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77407-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77407-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="77407-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77407-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77407-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77407-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="77407-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77407-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77407-118">E_FAIL</span></span>|<span data-ttu-id="77407-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="77407-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77407-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77407-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77407-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="77407-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77407-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77407-122">Remarks</span></span>  
 <span data-ttu-id="77407-123">`RevertToSelf` çağrısında sonra özgün iş parçacığı belirteci döndürmek için çağrılan [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77407-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77407-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77407-124">Requirements</span></span>  
 <span data-ttu-id="77407-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77407-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77407-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77407-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77407-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="77407-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77407-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77407-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77407-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77407-129">See also</span></span>

- [<span data-ttu-id="77407-130">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77407-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="77407-131">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77407-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="77407-132">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77407-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
