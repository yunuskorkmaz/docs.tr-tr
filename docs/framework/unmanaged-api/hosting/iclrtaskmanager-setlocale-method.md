---
title: ICLRTaskManager::SetLocale Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad9e07e76d39ce25dc339eb5fb02635866966093
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612131"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="2716a-102">ICLRTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2716a-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="2716a-103">Ortak dil çalışma zamanı (CLR), ana bilgisayar (hangi coğrafi kültür ve dil eşlemelerini) yerel ayar tanımlayıcısı şu anda yürütülen görevde değerini değiştirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="2716a-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2716a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2716a-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2716a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2716a-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="2716a-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="2716a-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2716a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2716a-107">Return Value</span></span>  
  
|<span data-ttu-id="2716a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2716a-108">HRESULT</span></span>|<span data-ttu-id="2716a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2716a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2716a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2716a-110">S_OK</span></span>|<span data-ttu-id="2716a-111">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2716a-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="2716a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2716a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2716a-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2716a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2716a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2716a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2716a-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2716a-115">The call timed out.</span></span>|  
|<span data-ttu-id="2716a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2716a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2716a-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2716a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2716a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2716a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2716a-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2716a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2716a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2716a-120">E_FAIL</span></span>|<span data-ttu-id="2716a-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2716a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2716a-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2716a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2716a-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2716a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2716a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2716a-124">Remarks</span></span>  
 <span data-ttu-id="2716a-125">`SetLocale` konak bulunması bir mekanizmasını eşitlemesine gezinin yürütmek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="2716a-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2716a-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2716a-126">Requirements</span></span>  
 <span data-ttu-id="2716a-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2716a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2716a-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2716a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2716a-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2716a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2716a-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2716a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2716a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2716a-131">See also</span></span>
- [<span data-ttu-id="2716a-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2716a-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2716a-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2716a-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2716a-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2716a-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2716a-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2716a-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
