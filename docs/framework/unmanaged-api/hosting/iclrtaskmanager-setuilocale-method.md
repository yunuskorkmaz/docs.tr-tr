---
title: "ICLRTaskManager::SetUILocale Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fab9da8f7e63ad000595378f5bc36f3aadc2ac3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="9e908-102">ICLRTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e908-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="9e908-103">Ortak dil çalışma zamanı (CLR ana kullanıcı arabirimi (UI) yerel ya da kültür değiştirdi) şu anda yürütülen görevde bildirir.</span><span class="sxs-lookup"><span data-stu-id="9e908-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e908-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e908-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e908-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e908-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="9e908-106">[in] Yeni atanan coğrafi kültür ve kullanıcı arabirimi dili eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="9e908-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e908-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e908-107">Return Value</span></span>  
  
|<span data-ttu-id="9e908-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e908-108">HRESULT</span></span>|<span data-ttu-id="9e908-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e908-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e908-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e908-110">S_OK</span></span>|<span data-ttu-id="9e908-111">`SetUILocale`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9e908-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="9e908-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e908-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e908-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9e908-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e908-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e908-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e908-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9e908-115">The call timed out.</span></span>|  
|<span data-ttu-id="9e908-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e908-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e908-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9e908-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e908-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e908-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e908-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9e908-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e908-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e908-120">E_FAIL</span></span>|<span data-ttu-id="9e908-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e908-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e908-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e908-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e908-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e908-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e908-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e908-124">Remarks</span></span>  
 <span data-ttu-id="9e908-125">`SetUILocale`yerel ayarlar eşitlenmesi için sahip olabilirsiniz herhangi mekanizmaları yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e908-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e908-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e908-126">Requirements</span></span>  
 <span data-ttu-id="9e908-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e908-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e908-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e908-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e908-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9e908-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e908-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e908-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e908-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e908-131">See Also</span></span>  
 [<span data-ttu-id="9e908-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e908-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9e908-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e908-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9e908-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e908-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9e908-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e908-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
