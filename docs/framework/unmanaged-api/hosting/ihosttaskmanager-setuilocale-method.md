---
title: IHostTaskManager::SetUILocale Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e110f1f5ea326c232c7c96bb05913080e950083d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158905"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="cb8ab-102">IHostTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb8ab-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="cb8ab-103">Konak, ortak dil çalışma zamanı (CLR) kullanıcı arabirimini (UI) yerel ayar veya kültür, şu anda yürütülmekte olan görevi üzerinde değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb8ab-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb8ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb8ab-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="cb8ab-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb8ab-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb8ab-107">Return Value</span></span>  
  
|<span data-ttu-id="cb8ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb8ab-108">HRESULT</span></span>|<span data-ttu-id="cb8ab-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb8ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb8ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb8ab-110">S_OK</span></span>|`SetUILocale` <span data-ttu-id="cb8ab-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-111">returned successfully.</span></span>|  
|<span data-ttu-id="cb8ab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb8ab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb8ab-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb8ab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb8ab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb8ab-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-115">The call timed out.</span></span>|  
|<span data-ttu-id="cb8ab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb8ab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb8ab-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb8ab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb8ab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb8ab-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb8ab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb8ab-120">E_FAIL</span></span>|<span data-ttu-id="cb8ab-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb8ab-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb8ab-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cb8ab-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="cb8ab-124">E_NOTIMPL</span></span>|<span data-ttu-id="cb8ab-125">Konak yönetilen kullanıcı kodu UI kültürü değiştirmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb8ab-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb8ab-126">Remarks</span></span>  
 <span data-ttu-id="cb8ab-127">Çalışma zamanı çağrıları `SetUILocale` zaman değerini <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliği, yönetilen kod tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="cb8ab-128">Bu yöntem, sahip olabilir bir mekanizmasını gezinin eşitleme yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="cb8ab-129">Bir konak kullanıcı Arabirimi yerel ayarını, yönetilen koddan değiştirilmesine izin vermiyor veya yerel eşitlemek için bir mekanizma uygulamıyor, bu yöntemden E_NOTIMPL döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb8ab-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb8ab-130">Requirements</span></span>  
 <span data-ttu-id="cb8ab-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb8ab-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb8ab-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb8ab-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb8ab-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cb8ab-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cb8ab-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="cb8ab-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb8ab-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb8ab-135">See also</span></span>

- [<span data-ttu-id="cb8ab-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb8ab-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="cb8ab-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb8ab-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="cb8ab-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb8ab-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="cb8ab-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb8ab-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="cb8ab-140">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb8ab-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
