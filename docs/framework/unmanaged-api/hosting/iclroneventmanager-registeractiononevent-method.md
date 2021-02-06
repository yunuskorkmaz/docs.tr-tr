---
description: ': ICLROnEventManager:: RegisterActionOnEvent Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b13209aed6a169185b42c6b9520f21f59f6be3bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637436"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="4ca9a-103">ICLROnEventManager::RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ca9a-103">ICLROnEventManager::RegisterActionOnEvent Method</span></span>

<span data-ttu-id="4ca9a-104">Belirtilen olay için bir geri çağırma işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-104">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca9a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ca9a-105">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ca9a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ca9a-106">Parameters</span></span>  

 `event`  
 <span data-ttu-id="4ca9a-107">'ndaki Tarafından tanımlanan geri çağırma işaretçisinin kaydedileceği olayı gösteren [EClrEvent](eclrevent-enumeration.md) değerlerinden biri `pAction` .</span><span class="sxs-lookup"><span data-stu-id="4ca9a-107">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="4ca9a-108">'ndaki Kayıtlı olay tetiklendiğinde çağrılan bir [IActionOnCLREvent](iactiononclrevent-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-108">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ca9a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4ca9a-109">Return Value</span></span>  
  
|<span data-ttu-id="4ca9a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ca9a-110">HRESULT</span></span>|<span data-ttu-id="4ca9a-111">Description</span><span class="sxs-lookup"><span data-stu-id="4ca9a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ca9a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ca9a-112">S_OK</span></span>|<span data-ttu-id="4ca9a-113">`RegisterActionOnEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-113">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="4ca9a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ca9a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ca9a-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ca9a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ca9a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ca9a-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-117">The call timed out.</span></span>|  
|<span data-ttu-id="4ca9a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ca9a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ca9a-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ca9a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ca9a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ca9a-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ca9a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ca9a-122">E_FAIL</span></span>|<span data-ttu-id="4ca9a-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ca9a-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ca9a-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ca9a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ca9a-126">Remarks</span></span>  

 <span data-ttu-id="4ca9a-127">Konak, tarafından açıklanan iki olay türünün biri veya her ikisi için geri çağırmaları kaydedebilir `EClrEvent` .</span><span class="sxs-lookup"><span data-stu-id="4ca9a-127">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="4ca9a-128">Konak, `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-128">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ca9a-129">Kaydeden olaylar birden `RegisterActionOnEvent` çok kez tetiklenebilir ve farklı iş parçacıklarından clr 'nin kaldırılmasına veya devre dışı bırakılmasına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-129">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ca9a-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ca9a-130">Requirements</span></span>  

 <span data-ttu-id="4ca9a-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ca9a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ca9a-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ca9a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ca9a-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4ca9a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ca9a-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ca9a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca9a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ca9a-135">See also</span></span>

- [<span data-ttu-id="4ca9a-136">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4ca9a-136">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="4ca9a-137">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ca9a-137">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="4ca9a-138">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ca9a-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4ca9a-139">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ca9a-139">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
