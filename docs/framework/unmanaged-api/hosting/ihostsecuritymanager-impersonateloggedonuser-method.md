---
title: IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ebf9ad72f7a1b0dd7ac54afa104089182f122ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109895"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="6c99b-102">IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c99b-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="6c99b-103">İstek, kod, geçerli kullanıcı kimliğinin kimlik bilgilerini kullanarak yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="6c99b-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c99b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c99b-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c99b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c99b-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="6c99b-106">[in] Veritabanının özellikleri için kullanıcı kimlik bilgilerini temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="6c99b-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c99b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c99b-107">Return Value</span></span>  
  
|<span data-ttu-id="6c99b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c99b-108">HRESULT</span></span>|<span data-ttu-id="6c99b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c99b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c99b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c99b-110">S_OK</span></span>|`ImpersonateLoggedOnUser` <span data-ttu-id="6c99b-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6c99b-111">returned successfully.</span></span>|  
|<span data-ttu-id="6c99b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c99b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c99b-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6c99b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c99b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c99b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c99b-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6c99b-115">The call timed out.</span></span>|  
|<span data-ttu-id="6c99b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c99b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c99b-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6c99b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c99b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c99b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c99b-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6c99b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c99b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c99b-120">E_FAIL</span></span>|<span data-ttu-id="6c99b-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6c99b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c99b-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c99b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c99b-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c99b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c99b-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c99b-124">Remarks</span></span>  
 <span data-ttu-id="6c99b-125">Çağrı `LogonUser` veya kimlik bilgileri geçerli kullanıcı kimliği için bir tanıtıcı almak için ilgili bir Win32 işlevi.</span><span class="sxs-lookup"><span data-stu-id="6c99b-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="6c99b-126">`HANDLE` Tür COM uyumlu değil, diğer bir deyişle, bir işletim sistemine özgü boyutuna ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6c99b-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="6c99b-127">Bu nedenle, bu belirteci yalnızca CLR ile konak arasındaki işlemin içinde kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6c99b-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c99b-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c99b-128">Requirements</span></span>  
 <span data-ttu-id="6c99b-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c99b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c99b-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c99b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c99b-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6c99b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6c99b-132">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6c99b-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6c99b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c99b-133">See also</span></span>

- [<span data-ttu-id="6c99b-134">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c99b-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6c99b-135">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c99b-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="6c99b-136">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c99b-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
