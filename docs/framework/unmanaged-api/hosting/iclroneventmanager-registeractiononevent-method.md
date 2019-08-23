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
ms.openlocfilehash: 36d4b0692b112a66fea3dd878c7054a083fb68ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951142"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="81acb-102">ICLROnEventManager::RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81acb-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="81acb-103">Belirtilen olay için bir geri çağırma işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="81acb-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81acb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81acb-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81acb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81acb-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="81acb-106">'ndaki Tarafından`pAction`tanımlanan geri çağırma işaretçisinin kaydedileceği olayı gösteren [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="81acb-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="81acb-107">'ndaki Kayıtlı olay tetiklendiğinde çağrılan bir [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="81acb-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81acb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="81acb-108">Return Value</span></span>  
  
|<span data-ttu-id="81acb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81acb-109">HRESULT</span></span>|<span data-ttu-id="81acb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81acb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81acb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="81acb-111">S_OK</span></span>|<span data-ttu-id="81acb-112">`RegisterActionOnEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="81acb-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="81acb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81acb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81acb-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="81acb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81acb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81acb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81acb-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="81acb-116">The call timed out.</span></span>|  
|<span data-ttu-id="81acb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81acb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81acb-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="81acb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81acb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81acb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81acb-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="81acb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81acb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81acb-121">E_FAIL</span></span>|<span data-ttu-id="81acb-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="81acb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81acb-123">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="81acb-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81acb-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="81acb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81acb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81acb-125">Remarks</span></span>  
 <span data-ttu-id="81acb-126">Konak, tarafından `EClrEvent`açıklanan iki olay türünün biri veya her ikisi için geri çağırmaları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="81acb-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="81acb-127">Konak, `ICLROnEventManager` [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodunu çağırarak arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="81acb-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81acb-128">`RegisterActionOnEvent` Kaydeden olaylar birden çok kez tetiklenebilir ve farklı iş parçacıklarından clr 'nin kaldırılmasına veya devre dışı bırakılmasına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="81acb-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81acb-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81acb-129">Requirements</span></span>  
 <span data-ttu-id="81acb-130">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81acb-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81acb-131">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81acb-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81acb-132">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="81acb-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81acb-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81acb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81acb-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81acb-134">See also</span></span>

- [<span data-ttu-id="81acb-135">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="81acb-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="81acb-136">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81acb-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="81acb-137">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81acb-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="81acb-138">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81acb-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
