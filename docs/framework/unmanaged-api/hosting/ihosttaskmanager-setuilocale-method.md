---
title: "IHostTaskManager::SetUILocale Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetUILocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 099c3d4878e7dd83be9240e121777c71c2890c88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="08dc9-102">IHostTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08dc9-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="08dc9-103">Ortak dil çalışma zamanı (CLR) kullanıcı arabirimini (UI) yerel ya da şu anda yürütülen görevde kültürü değişti konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="08dc9-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08dc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08dc9-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08dc9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08dc9-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="08dc9-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="08dc9-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08dc9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08dc9-107">Return Value</span></span>  
  
|<span data-ttu-id="08dc9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08dc9-108">HRESULT</span></span>|<span data-ttu-id="08dc9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08dc9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08dc9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="08dc9-110">S_OK</span></span>|<span data-ttu-id="08dc9-111">`SetUILocale`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="08dc9-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="08dc9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08dc9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08dc9-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="08dc9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08dc9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08dc9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08dc9-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="08dc9-115">The call timed out.</span></span>|  
|<span data-ttu-id="08dc9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08dc9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08dc9-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="08dc9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08dc9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08dc9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08dc9-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="08dc9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08dc9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08dc9-120">E_FAIL</span></span>|<span data-ttu-id="08dc9-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="08dc9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08dc9-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="08dc9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08dc9-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="08dc9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="08dc9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="08dc9-124">E_NOTIMPL</span></span>|<span data-ttu-id="08dc9-125">Ana bilgisayar UI kültürü değiştirmek için yönetilen kullanıcı kodu izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="08dc9-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08dc9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08dc9-126">Remarks</span></span>  
 <span data-ttu-id="08dc9-127">Çalışma zamanı çağrıları `SetUILocale` zaman değerini <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliği tarafından yönetilen kod değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="08dc9-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="08dc9-128">Bu yöntem, sahip olabilirsiniz herhangi bir mekanizması yerel ayarlar eşitlenmesi için yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="08dc9-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="08dc9-129">Bir konak UI yerel yönetilen koddan değiştirilmesine izin vermez veya yerel ayarlar eşitlemek için bir mekanizma uygulamaz, bu yöntemle E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="08dc9-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08dc9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08dc9-130">Requirements</span></span>  
 <span data-ttu-id="08dc9-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08dc9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08dc9-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08dc9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08dc9-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="08dc9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08dc9-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08dc9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dc9-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08dc9-135">See Also</span></span>  
 [<span data-ttu-id="08dc9-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08dc9-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="08dc9-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08dc9-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="08dc9-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08dc9-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="08dc9-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08dc9-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="08dc9-140">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08dc9-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
