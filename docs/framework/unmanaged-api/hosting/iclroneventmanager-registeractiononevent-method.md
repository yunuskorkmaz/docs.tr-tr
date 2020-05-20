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
ms.openlocfilehash: e634b3876d51d461446ed3f5ae537ac1db1545bd
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703510"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="7291d-102">ICLROnEventManager::RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7291d-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="7291d-103">Belirtilen olay için bir geri çağırma işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7291d-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7291d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7291d-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7291d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7291d-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="7291d-106">'ndaki Tarafından tanımlanan geri çağırma işaretçisinin kaydedileceği olayı gösteren [EClrEvent](eclrevent-enumeration.md) değerlerinden biri `pAction` .</span><span class="sxs-lookup"><span data-stu-id="7291d-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="7291d-107">'ndaki Kayıtlı olay tetiklendiğinde çağrılan bir [IActionOnCLREvent](iactiononclrevent-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7291d-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7291d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7291d-108">Return Value</span></span>  
  
|<span data-ttu-id="7291d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7291d-109">HRESULT</span></span>|<span data-ttu-id="7291d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7291d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7291d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7291d-111">S_OK</span></span>|<span data-ttu-id="7291d-112">`RegisterActionOnEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7291d-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="7291d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7291d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7291d-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7291d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7291d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7291d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7291d-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7291d-116">The call timed out.</span></span>|  
|<span data-ttu-id="7291d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7291d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7291d-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7291d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7291d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7291d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7291d-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7291d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7291d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7291d-121">E_FAIL</span></span>|<span data-ttu-id="7291d-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7291d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7291d-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7291d-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7291d-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7291d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7291d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7291d-125">Remarks</span></span>  
 <span data-ttu-id="7291d-126">Konak, tarafından açıklanan iki olay türünün biri veya her ikisi için geri çağırmaları kaydedebilir `EClrEvent` .</span><span class="sxs-lookup"><span data-stu-id="7291d-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="7291d-127">Konak, `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="7291d-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7291d-128">Kaydeden olaylar birden `RegisterActionOnEvent` çok kez tetiklenebilir ve farklı iş parçacıklarından clr 'nin kaldırılmasına veya devre dışı bırakılmasına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="7291d-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7291d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7291d-129">Requirements</span></span>  
 <span data-ttu-id="7291d-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7291d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7291d-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7291d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7291d-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7291d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7291d-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7291d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7291d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7291d-134">See also</span></span>

- [<span data-ttu-id="7291d-135">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7291d-135">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="7291d-136">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7291d-136">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="7291d-137">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7291d-137">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7291d-138">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7291d-138">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
