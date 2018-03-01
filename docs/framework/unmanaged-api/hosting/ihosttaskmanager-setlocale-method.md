---
title: "IHostTaskManager::SetLocale Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eeb5e7510c6de882233ec1fa8fa1b8f501a00685
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="8808d-102">IHostTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8808d-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="8808d-103">Ortak dil çalışma zamanı (CLR) yerel ya da şu anda yürütülen görevde kültürü değişti konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="8808d-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8808d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8808d-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8808d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8808d-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="8808d-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="8808d-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8808d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8808d-107">Return Value</span></span>  
  
|<span data-ttu-id="8808d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8808d-108">HRESULT</span></span>|<span data-ttu-id="8808d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8808d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8808d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8808d-110">S_OK</span></span>|<span data-ttu-id="8808d-111">`SetLocale`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8808d-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="8808d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8808d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8808d-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8808d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8808d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8808d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8808d-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8808d-115">The call timed out.</span></span>|  
|<span data-ttu-id="8808d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8808d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8808d-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="8808d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8808d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8808d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8808d-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="8808d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8808d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8808d-120">E_FAIL</span></span>|<span data-ttu-id="8808d-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8808d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8808d-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8808d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8808d-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8808d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8808d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8808d-124">E_NOTIMPL</span></span>|<span data-ttu-id="8808d-125">Ana bilgisayarın yerel ayarı değiştirmek yönetilen kullanıcı kodu izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="8808d-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8808d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8808d-126">Remarks</span></span>  
 <span data-ttu-id="8808d-127">Çalışma zamanı çağrıları `SetLocale` zaman değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından yönetilen kod değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="8808d-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="8808d-128">Bu yöntem, sahip olabilirsiniz herhangi bir mekanizması yerel ayarlar eşitlenmesi için yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="8808d-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="8808d-129">Bir konak yerel yönetilen koddan değiştirilmesine izin vermez veya yerel ayarlar eşitlemek için bir mekanizma uygulamaz, bu yöntemle E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="8808d-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8808d-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8808d-130">Requirements</span></span>  
 <span data-ttu-id="8808d-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8808d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8808d-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8808d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8808d-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8808d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8808d-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8808d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8808d-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8808d-135">See Also</span></span>  
 [<span data-ttu-id="8808d-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8808d-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="8808d-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8808d-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="8808d-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8808d-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="8808d-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8808d-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="8808d-140">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8808d-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
