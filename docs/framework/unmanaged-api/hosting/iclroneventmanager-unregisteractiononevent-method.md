---
title: "ICLROnEventManager::UnregisterActionOnEvent Yöntemi"
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
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d295817a7c6f8a177de3ff251904beeaf8ca828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="d1511-102">ICLROnEventManager::UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1511-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="d1511-103">Belirtilen olay için daha önce kaydedilmiş geri işaretçi kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="d1511-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1511-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1511-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1511-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1511-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="d1511-106">[in] Aşağıdakilerden birini [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) tarafından açıklanan geri işaretçi kaydını kaldırmak istediğiniz olay belirten değerleri `pAction`.</span><span class="sxs-lookup"><span data-stu-id="d1511-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="d1511-107">[in] Bir işaretçi bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) bir parametre olarak geçirilen nesne [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1511-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1511-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1511-108">Return Value</span></span>  
  
|<span data-ttu-id="d1511-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1511-109">HRESULT</span></span>|<span data-ttu-id="d1511-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1511-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1511-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1511-111">S_OK</span></span>|<span data-ttu-id="d1511-112">`UnregisterActionOnEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d1511-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="d1511-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1511-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1511-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d1511-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1511-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1511-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1511-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d1511-116">The call timed out.</span></span>|  
|<span data-ttu-id="d1511-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1511-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1511-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="d1511-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1511-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1511-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1511-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="d1511-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1511-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1511-121">E_FAIL</span></span>|<span data-ttu-id="d1511-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d1511-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1511-123">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d1511-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1511-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1511-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1511-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1511-125">Requirements</span></span>  
 <span data-ttu-id="d1511-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1511-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1511-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1511-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1511-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d1511-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1511-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1511-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1511-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1511-130">See Also</span></span>  
 [<span data-ttu-id="d1511-131">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d1511-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="d1511-132">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1511-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="d1511-133">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1511-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="d1511-134">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1511-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
