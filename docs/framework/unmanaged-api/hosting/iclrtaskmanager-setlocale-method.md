---
title: "ICLRTaskManager::SetLocale Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.SetLocale
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbed6bff52d7ccad38eb45d12a31d08dc8b1b774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="0ba50-102">ICLRTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ba50-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="0ba50-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar (coğrafi kültür ve dil eşler) yerel ayar tanımlayıcısı şu anda yürütülen görevde değerini değiştirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="0ba50-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ba50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ba50-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ba50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ba50-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="0ba50-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="0ba50-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ba50-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ba50-107">Return Value</span></span>  
  
|<span data-ttu-id="0ba50-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ba50-108">HRESULT</span></span>|<span data-ttu-id="0ba50-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ba50-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ba50-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ba50-110">S_OK</span></span>|<span data-ttu-id="0ba50-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0ba50-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="0ba50-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ba50-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ba50-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0ba50-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ba50-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ba50-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ba50-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0ba50-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ba50-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ba50-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ba50-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="0ba50-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ba50-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ba50-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ba50-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="0ba50-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ba50-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ba50-120">E_FAIL</span></span>|<span data-ttu-id="0ba50-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0ba50-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ba50-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ba50-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ba50-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ba50-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ba50-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ba50-124">Remarks</span></span>  
 <span data-ttu-id="0ba50-125">`SetLocale`ana bilgisayar sahip olabilirsiniz herhangi bir mekanizması yerel ayarlar eşitlemesine yürütmek için fırsatı sunar.</span><span class="sxs-lookup"><span data-stu-id="0ba50-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ba50-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ba50-126">Requirements</span></span>  
 <span data-ttu-id="0ba50-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ba50-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ba50-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ba50-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ba50-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0ba50-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ba50-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ba50-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba50-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba50-131">See Also</span></span>  
 [<span data-ttu-id="0ba50-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ba50-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0ba50-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ba50-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0ba50-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ba50-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0ba50-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ba50-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
