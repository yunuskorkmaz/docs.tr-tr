---
title: "ICLROnEventManager::RegisterActionOnEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager.RegisterActionOnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 008bdc856c9fbede7398f467674ac191c1860128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="50e90-102">ICLROnEventManager::RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e90-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="50e90-103">Belirtilen olay için bir geri çağırma işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="50e90-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e90-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50e90-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50e90-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50e90-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="50e90-106">[in] Aşağıdakilerden birini [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) kendisi tarafından açıklanan geri işaretçi kaydetmek olay belirten değerleri `pAction`.</span><span class="sxs-lookup"><span data-stu-id="50e90-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="50e90-107">[in] Bir işaretçi bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) kayıtlı olay başlatıldığında çağrılan nesne.</span><span class="sxs-lookup"><span data-stu-id="50e90-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50e90-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50e90-108">Return Value</span></span>  
  
|<span data-ttu-id="50e90-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50e90-109">HRESULT</span></span>|<span data-ttu-id="50e90-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e90-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50e90-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="50e90-111">S_OK</span></span>|<span data-ttu-id="50e90-112">`RegisterActionOnEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="50e90-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="50e90-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50e90-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50e90-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="50e90-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50e90-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50e90-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50e90-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="50e90-116">The call timed out.</span></span>|  
|<span data-ttu-id="50e90-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50e90-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50e90-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="50e90-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50e90-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50e90-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50e90-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="50e90-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50e90-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50e90-121">E_FAIL</span></span>|<span data-ttu-id="50e90-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="50e90-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50e90-123">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="50e90-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50e90-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="50e90-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e90-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50e90-125">Remarks</span></span>  
 <span data-ttu-id="50e90-126">Ana bilgisayar veya her ikisini tarafından açıklanan iki olay türleri için geri aramaları kaydetme `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="50e90-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="50e90-127">Ana bilgisayar alır `ICLROnEventManager` çağırarak arabirim [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50e90-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50e90-128">Olaylar, `RegisterActionOnEvent` kayıtları harekete birden çok kez ve bir kaldırma veya CLR devre dışı bırakma sinyal için farklı iş parçacıklarından.</span><span class="sxs-lookup"><span data-stu-id="50e90-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e90-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50e90-129">Requirements</span></span>  
 <span data-ttu-id="50e90-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e90-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e90-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50e90-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50e90-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="50e90-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50e90-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e90-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e90-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50e90-134">See Also</span></span>  
 [<span data-ttu-id="50e90-135">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="50e90-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="50e90-136">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e90-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="50e90-137">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e90-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="50e90-138">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e90-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
