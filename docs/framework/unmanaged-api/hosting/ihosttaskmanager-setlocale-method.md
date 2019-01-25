---
title: IHostTaskManager::SetLocale Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b43de32807da2478af23e52997fce2f4da1b339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674696"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="55f25-102">IHostTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55f25-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="55f25-103">Konak, ortak dil çalışma zamanı (CLR) yerel ayar veya kültür, şu anda yürütülmekte olan görevi üzerinde değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="55f25-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55f25-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55f25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55f25-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="55f25-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="55f25-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f25-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="55f25-107">Return Value</span></span>  
  
|<span data-ttu-id="55f25-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55f25-108">HRESULT</span></span>|<span data-ttu-id="55f25-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55f25-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55f25-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="55f25-110">S_OK</span></span>|<span data-ttu-id="55f25-111">`SetLocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="55f25-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="55f25-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="55f25-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="55f25-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="55f25-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="55f25-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="55f25-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="55f25-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="55f25-115">The call timed out.</span></span>|  
|<span data-ttu-id="55f25-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="55f25-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="55f25-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="55f25-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="55f25-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="55f25-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="55f25-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="55f25-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="55f25-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="55f25-120">E_FAIL</span></span>|<span data-ttu-id="55f25-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="55f25-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="55f25-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="55f25-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="55f25-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="55f25-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="55f25-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="55f25-124">E_NOTIMPL</span></span>|<span data-ttu-id="55f25-125">Ana bilgisayarın yerel ayarı değiştirmek yönetilen kullanıcı kodu izin vermez.</span><span class="sxs-lookup"><span data-stu-id="55f25-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55f25-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55f25-126">Remarks</span></span>  
 <span data-ttu-id="55f25-127">Çalışma zamanı çağrıları `SetLocale` zaman değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği, yönetilen kod tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="55f25-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="55f25-128">Bu yöntem, sahip olabilir bir mekanizmasını gezinin eşitleme yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="55f25-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="55f25-129">Bir konak yerel yönetilen koddan değiştirilmesine izin vermiyor veya yerel eşitlemek için bir mekanizma uygulamıyor, bu yöntemden E_NOTIMPL döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="55f25-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f25-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55f25-130">Requirements</span></span>  
 <span data-ttu-id="55f25-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f25-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f25-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="55f25-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55f25-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="55f25-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55f25-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f25-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f25-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55f25-135">See also</span></span>
- [<span data-ttu-id="55f25-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55f25-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="55f25-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55f25-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="55f25-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55f25-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="55f25-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55f25-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="55f25-140">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55f25-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
