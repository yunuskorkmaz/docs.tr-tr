---
description: ': ICLROnEventManager:: UnregisterActionOnEvent yöntemi hakkında daha fazla bilgi edinin'
title: ICLROnEventManager::UnregisterActionOnEvent Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 8131c58669ff7be0fdc2b2e063c70d3b370921e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789820"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="7cd6f-103">ICLROnEventManager::UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cd6f-103">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>

<span data-ttu-id="7cd6f-104">Belirtilen olay için önceden kaydedilmiş bir geri çağırma işaretçisinin kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-104">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cd6f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cd6f-105">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cd6f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cd6f-106">Parameters</span></span>  

 `event`  
 <span data-ttu-id="7cd6f-107">'ndaki [EClrEvent](eclrevent-enumeration.md) değerlerinden biri, tarafından tanımlanan geri çağırma işaretçisinin kaydını silmek için olayı belirtir `pAction` .</span><span class="sxs-lookup"><span data-stu-id="7cd6f-107">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="7cd6f-108">'ndaki [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) metoduna parametre olarak geçirilmiş bir [IActionOnCLREvent](iactiononclrevent-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-108">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cd6f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7cd6f-109">Return Value</span></span>  
  
|<span data-ttu-id="7cd6f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7cd6f-110">HRESULT</span></span>|<span data-ttu-id="7cd6f-111">Description</span><span class="sxs-lookup"><span data-stu-id="7cd6f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cd6f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cd6f-112">S_OK</span></span>|<span data-ttu-id="7cd6f-113">`UnregisterActionOnEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-113">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="7cd6f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7cd6f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7cd6f-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7cd6f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7cd6f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7cd6f-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-117">The call timed out.</span></span>|  
|<span data-ttu-id="7cd6f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7cd6f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7cd6f-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7cd6f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7cd6f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7cd6f-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7cd6f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7cd6f-122">E_FAIL</span></span>|<span data-ttu-id="7cd6f-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7cd6f-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7cd6f-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cd6f-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cd6f-126">Requirements</span></span>  

 <span data-ttu-id="7cd6f-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cd6f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cd6f-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7cd6f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cd6f-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7cd6f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cd6f-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cd6f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd6f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cd6f-131">See also</span></span>

- [<span data-ttu-id="7cd6f-132">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7cd6f-132">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="7cd6f-133">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cd6f-133">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="7cd6f-134">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cd6f-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7cd6f-135">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cd6f-135">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
