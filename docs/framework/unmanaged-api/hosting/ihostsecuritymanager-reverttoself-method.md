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
ms.openlocfilehash: b896c5509cc4862a6416381f89bc04a28959e091
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121461"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="bba5c-102">IHostSecurityManager::RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bba5c-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="bba5c-103">Geçerli Kullanıcı kimliğini kimliğe bürünme işlemini sonlandırır ve özgün iş parçacığı belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bba5c-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bba5c-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bba5c-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bba5c-105">Return Value</span></span>  
  
|<span data-ttu-id="bba5c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bba5c-106">HRESULT</span></span>|<span data-ttu-id="bba5c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bba5c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bba5c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bba5c-108">S_OK</span></span>|<span data-ttu-id="bba5c-109">`RevertToSelf` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bba5c-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="bba5c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bba5c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bba5c-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bba5c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bba5c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bba5c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bba5c-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bba5c-113">The call timed out.</span></span>|  
|<span data-ttu-id="bba5c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bba5c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bba5c-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bba5c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bba5c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bba5c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bba5c-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bba5c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bba5c-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="bba5c-118">E_FAIL</span></span>|<span data-ttu-id="bba5c-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bba5c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bba5c-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bba5c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bba5c-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bba5c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bba5c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bba5c-122">Remarks</span></span>  
 <span data-ttu-id="bba5c-123">`RevertToSelf`, önceki [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) metoduna yapılan bir çağrıdan sonra özgün iş parçacığı belirtecine dönmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="bba5c-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba5c-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bba5c-124">Requirements</span></span>  
 <span data-ttu-id="bba5c-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bba5c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba5c-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bba5c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bba5c-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="bba5c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bba5c-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bba5c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba5c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba5c-129">See also</span></span>

- [<span data-ttu-id="bba5c-130">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bba5c-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="bba5c-131">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bba5c-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="bba5c-132">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bba5c-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
