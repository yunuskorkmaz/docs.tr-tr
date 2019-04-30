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
ms.openlocfilehash: 03c5c9d04567832951062fe1512a292f9b32a94b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763340"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="3501c-102">ICLRTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3501c-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="3501c-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar kullanıcı arabirimi (UI) yerel ayar veya kültür değiştirildi, o anda yürütülen görevde bildirir.</span><span class="sxs-lookup"><span data-stu-id="3501c-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3501c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3501c-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3501c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3501c-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="3501c-106">[in] Yeni atanan coğrafi kültür ve dil kullanıcı arabirimi için eşlenen yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="3501c-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3501c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3501c-107">Return Value</span></span>  
  
|<span data-ttu-id="3501c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3501c-108">HRESULT</span></span>|<span data-ttu-id="3501c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3501c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3501c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3501c-110">S_OK</span></span>|<span data-ttu-id="3501c-111">`SetUILocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3501c-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="3501c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3501c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3501c-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3501c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3501c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3501c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3501c-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3501c-115">The call timed out.</span></span>|  
|<span data-ttu-id="3501c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3501c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3501c-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3501c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3501c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3501c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3501c-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3501c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3501c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3501c-120">E_FAIL</span></span>|<span data-ttu-id="3501c-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3501c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3501c-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3501c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3501c-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3501c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3501c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3501c-124">Remarks</span></span>  
 <span data-ttu-id="3501c-125">`SetUILocale` bulunması bir mekanizmasını eşitlemesine gezinin yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="3501c-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3501c-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3501c-126">Requirements</span></span>  
 <span data-ttu-id="3501c-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3501c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3501c-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3501c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3501c-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3501c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3501c-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3501c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3501c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3501c-131">See also</span></span>

- [<span data-ttu-id="3501c-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3501c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3501c-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3501c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3501c-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3501c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3501c-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3501c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
