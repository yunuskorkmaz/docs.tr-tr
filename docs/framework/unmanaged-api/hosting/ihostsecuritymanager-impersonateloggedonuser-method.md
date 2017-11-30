---
title: "IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.ImpersonateLoggedOnUser
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c5956dcad6908f0117de7f5ff0c6632ad3bb925
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="0aea7-102">IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0aea7-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="0aea7-103">İstek, kod geçerli kullanıcı kimlik bilgilerini kullanarak yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="0aea7-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aea7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0aea7-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0aea7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0aea7-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="0aea7-106">[in] Taklit için kullanıcının kimlik bilgilerini temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="0aea7-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0aea7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0aea7-107">Return Value</span></span>  
  
|<span data-ttu-id="0aea7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0aea7-108">HRESULT</span></span>|<span data-ttu-id="0aea7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0aea7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0aea7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0aea7-110">S_OK</span></span>|<span data-ttu-id="0aea7-111">`ImpersonateLoggedOnUser`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0aea7-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="0aea7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0aea7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0aea7-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0aea7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0aea7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0aea7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0aea7-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0aea7-115">The call timed out.</span></span>|  
|<span data-ttu-id="0aea7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0aea7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0aea7-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="0aea7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0aea7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0aea7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0aea7-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="0aea7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0aea7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0aea7-120">E_FAIL</span></span>|<span data-ttu-id="0aea7-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0aea7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0aea7-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0aea7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0aea7-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0aea7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aea7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0aea7-124">Remarks</span></span>  
 <span data-ttu-id="0aea7-125">Çağrı `LogonUser` veya kimlik bilgileri geçerli kullanıcı kimliği için bir tanıtıcı almak için ilgili bir Win32 işlevi.</span><span class="sxs-lookup"><span data-stu-id="0aea7-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="0aea7-126">`HANDLE` Türü COM uyumlu değil, diğer bir deyişle, boyutuna bir işletim sistemine özeldir ve özel hazırlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0aea7-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="0aea7-127">Bu nedenle, bu belirteç CLR ve ana bilgisayar arasında yalnızca işlemdeki kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0aea7-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aea7-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0aea7-128">Requirements</span></span>  
 <span data-ttu-id="0aea7-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aea7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aea7-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0aea7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0aea7-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0aea7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0aea7-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aea7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aea7-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0aea7-133">See Also</span></span>  
 [<span data-ttu-id="0aea7-134">Ihostsecuritycontext arabirimi</span><span class="sxs-lookup"><span data-stu-id="0aea7-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="0aea7-135">Ihostsecuritymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="0aea7-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="0aea7-136">RevertToSelf yöntemi</span><span class="sxs-lookup"><span data-stu-id="0aea7-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
