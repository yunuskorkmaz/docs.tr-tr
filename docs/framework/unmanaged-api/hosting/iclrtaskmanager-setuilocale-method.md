---
title: ICLRTaskManager::SetUILocale Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ef939f915062368d74a0c48bdaee47cbec7b56f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491470"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="bc5f0-102">ICLRTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc5f0-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="bc5f0-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar kullanıcı arabirimi (UI) yerel ayar veya kültür değiştirildi, o anda yürütülen görevde bildirir.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc5f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc5f0-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc5f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc5f0-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="bc5f0-106">[in] Yeni atanan coğrafi kültür ve dil kullanıcı arabirimi için eşlenen yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc5f0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc5f0-107">Return Value</span></span>  
  
|<span data-ttu-id="bc5f0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc5f0-108">HRESULT</span></span>|<span data-ttu-id="bc5f0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc5f0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc5f0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc5f0-110">S_OK</span></span>|<span data-ttu-id="bc5f0-111">`SetUILocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="bc5f0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc5f0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc5f0-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bc5f0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc5f0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc5f0-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-115">The call timed out.</span></span>|  
|<span data-ttu-id="bc5f0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc5f0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc5f0-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc5f0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc5f0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc5f0-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc5f0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc5f0-120">E_FAIL</span></span>|<span data-ttu-id="bc5f0-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc5f0-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc5f0-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc5f0-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc5f0-124">Remarks</span></span>  
 <span data-ttu-id="bc5f0-125">`SetUILocale` bulunması bir mekanizmasını eşitlemesine gezinin yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc5f0-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc5f0-126">Requirements</span></span>  
 <span data-ttu-id="bc5f0-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc5f0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc5f0-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc5f0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc5f0-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bc5f0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc5f0-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc5f0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc5f0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc5f0-131">See also</span></span>
- [<span data-ttu-id="bc5f0-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc5f0-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bc5f0-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc5f0-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bc5f0-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc5f0-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bc5f0-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc5f0-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
