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
ms.openlocfilehash: 4068166438c524ad1c0ed4efe455b1f66b6641d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140833"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="f451b-102">ICLROnEventManager::RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f451b-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="f451b-103">Belirtilen olay için bir geri çağırma işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f451b-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f451b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f451b-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f451b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f451b-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="f451b-106">'ndaki `pAction`tarafından tanımlanan geri arama işaretçisinin kaydedileceği olayı belirten [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="f451b-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="f451b-107">'ndaki Kayıtlı olay tetiklendiğinde çağrılan bir [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f451b-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f451b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f451b-108">Return Value</span></span>  
  
|<span data-ttu-id="f451b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f451b-109">HRESULT</span></span>|<span data-ttu-id="f451b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f451b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f451b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f451b-111">S_OK</span></span>|<span data-ttu-id="f451b-112">`RegisterActionOnEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f451b-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="f451b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f451b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f451b-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f451b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f451b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f451b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f451b-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f451b-116">The call timed out.</span></span>|  
|<span data-ttu-id="f451b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f451b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f451b-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f451b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f451b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f451b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f451b-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f451b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f451b-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="f451b-121">E_FAIL</span></span>|<span data-ttu-id="f451b-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f451b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f451b-123">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f451b-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f451b-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f451b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f451b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f451b-125">Remarks</span></span>  
 <span data-ttu-id="f451b-126">Konak, `EClrEvent`tarafından tanımlanan iki olay türünün biri veya her ikisi için geri çağırmaları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="f451b-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="f451b-127">Ana bilgisayar [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodunu çağırarak `ICLROnEventManager` arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="f451b-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f451b-128">`RegisterActionOnEvent` yazmaçların birden çok kez tetiklenebilir ve farklı iş parçacıklarından CLR 'nin kaldırılmasına veya devre dışı bırakılmasına sinyal verebilir.</span><span class="sxs-lookup"><span data-stu-id="f451b-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f451b-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f451b-129">Requirements</span></span>  
 <span data-ttu-id="f451b-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f451b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f451b-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f451b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f451b-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f451b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f451b-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f451b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f451b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f451b-134">See also</span></span>

- [<span data-ttu-id="f451b-135">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f451b-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="f451b-136">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f451b-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="f451b-137">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f451b-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f451b-138">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f451b-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
