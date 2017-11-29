---
title: "IHostTaskManager::SetLocale Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetLocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 885dd41a3bc5afb156d1f338fb3564731d5a742a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="f4790-102">IHostTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4790-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="f4790-103">Ortak dil çalışma zamanı (CLR) yerel ya da şu anda yürütülen görevde kültürü değişti konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="f4790-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4790-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4790-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4790-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4790-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f4790-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="f4790-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4790-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f4790-107">Return Value</span></span>  
  
|<span data-ttu-id="f4790-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4790-108">HRESULT</span></span>|<span data-ttu-id="f4790-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4790-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4790-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4790-110">S_OK</span></span>|<span data-ttu-id="f4790-111">`SetLocale`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f4790-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="f4790-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4790-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4790-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f4790-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4790-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4790-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4790-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f4790-115">The call timed out.</span></span>|  
|<span data-ttu-id="f4790-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4790-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4790-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="f4790-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4790-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4790-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4790-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="f4790-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4790-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4790-120">E_FAIL</span></span>|<span data-ttu-id="f4790-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f4790-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4790-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f4790-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4790-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4790-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f4790-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f4790-124">E_NOTIMPL</span></span>|<span data-ttu-id="f4790-125">Ana bilgisayarın yerel ayarı değiştirmek yönetilen kullanıcı kodu izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="f4790-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4790-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4790-126">Remarks</span></span>  
 <span data-ttu-id="f4790-127">Çalışma zamanı çağrıları `SetLocale` zaman değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından yönetilen kod değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f4790-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="f4790-128">Bu yöntem, sahip olabilirsiniz herhangi bir mekanizması yerel ayarlar eşitlenmesi için yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4790-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="f4790-129">Bir konak yerel yönetilen koddan değiştirilmesine izin vermez veya yerel ayarlar eşitlemek için bir mekanizma uygulamaz, bu yöntemle E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4790-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4790-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4790-130">Requirements</span></span>  
 <span data-ttu-id="f4790-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4790-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4790-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4790-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4790-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f4790-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4790-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4790-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4790-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4790-135">See Also</span></span>  
 [<span data-ttu-id="f4790-136">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4790-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f4790-137">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4790-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f4790-138">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4790-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f4790-139">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4790-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="f4790-140">Setuılocale yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4790-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
