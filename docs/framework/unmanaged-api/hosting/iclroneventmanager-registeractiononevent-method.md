---
title: ICLROnEventManager::RegisterActionOnEvent Yöntemi
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85c70acbdf7e5da1286f11d9962ca16f0d0ed72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569134"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="005e4-102">ICLROnEventManager::RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="005e4-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="005e4-103">Bir geri çağırma işaretçi belirtilen olay için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="005e4-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="005e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="005e4-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="005e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="005e4-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="005e4-106">[in] Aşağıdakilerden birini [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) tarafından açıklanan geri işaretçi kaydetmek istediğiniz olay belirten değerleri `pAction`.</span><span class="sxs-lookup"><span data-stu-id="005e4-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="005e4-107">[in] Bir işaretçi bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) kayıtlı olay başlatıldığında çağrılan nesne.</span><span class="sxs-lookup"><span data-stu-id="005e4-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="005e4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="005e4-108">Return Value</span></span>  
  
|<span data-ttu-id="005e4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="005e4-109">HRESULT</span></span>|<span data-ttu-id="005e4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="005e4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="005e4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="005e4-111">S_OK</span></span>|<span data-ttu-id="005e4-112">`RegisterActionOnEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="005e4-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="005e4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="005e4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="005e4-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="005e4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="005e4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="005e4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="005e4-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="005e4-116">The call timed out.</span></span>|  
|<span data-ttu-id="005e4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="005e4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="005e4-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="005e4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="005e4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="005e4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="005e4-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="005e4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="005e4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="005e4-121">E_FAIL</span></span>|<span data-ttu-id="005e4-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="005e4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="005e4-123">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="005e4-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="005e4-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="005e4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="005e4-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="005e4-125">Remarks</span></span>  
 <span data-ttu-id="005e4-126">Konak veya her ikisini tarafından açıklanan iki olay türü için geri aramaları kaydetme `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="005e4-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="005e4-127">Ana bilgisayar alır `ICLROnEventManager` çağırarak arabirim [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="005e4-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="005e4-128">Olaylar, `RegisterActionOnEvent` kayıtları tetiklenen birden çok kez ve bir kaldırma veya CLR devre dışı bırakma sinyal farklı iş parçacıkları.</span><span class="sxs-lookup"><span data-stu-id="005e4-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="005e4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="005e4-129">Requirements</span></span>  
 <span data-ttu-id="005e4-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="005e4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="005e4-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="005e4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="005e4-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="005e4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="005e4-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="005e4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005e4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="005e4-134">See also</span></span>
- [<span data-ttu-id="005e4-135">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="005e4-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="005e4-136">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="005e4-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="005e4-137">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="005e4-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="005e4-138">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="005e4-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
