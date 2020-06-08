---
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
ms.openlocfilehash: a3018d8477d5abd7d03ad8675503624d2e44e8f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504140"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="b1b0a-102">ICLROnEventManager::UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1b0a-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="b1b0a-103">Belirtilen olay için önceden kaydedilmiş bir geri çağırma işaretçisinin kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b0a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b1b0a-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1b0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1b0a-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="b1b0a-106">'ndaki [EClrEvent](eclrevent-enumeration.md) değerlerinden biri, tarafından tanımlanan geri çağırma işaretçisinin kaydını silmek için olayı belirtir `pAction` .</span><span class="sxs-lookup"><span data-stu-id="b1b0a-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="b1b0a-107">'ndaki [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) metoduna parametre olarak geçirilmiş bir [IActionOnCLREvent](iactiononclrevent-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1b0a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1b0a-108">Return Value</span></span>  
  
|<span data-ttu-id="b1b0a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1b0a-109">HRESULT</span></span>|<span data-ttu-id="b1b0a-110">Description</span><span class="sxs-lookup"><span data-stu-id="b1b0a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1b0a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1b0a-111">S_OK</span></span>|<span data-ttu-id="b1b0a-112">`UnregisterActionOnEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="b1b0a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1b0a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1b0a-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1b0a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1b0a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1b0a-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-116">The call timed out.</span></span>|  
|<span data-ttu-id="b1b0a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1b0a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1b0a-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1b0a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1b0a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1b0a-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1b0a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1b0a-121">E_FAIL</span></span>|<span data-ttu-id="b1b0a-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1b0a-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1b0a-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1b0a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1b0a-125">Requirements</span></span>  
 <span data-ttu-id="b1b0a-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1b0a-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b0a-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1b0a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1b0a-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b1b0a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1b0a-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b0a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b0a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1b0a-130">See also</span></span>

- [<span data-ttu-id="b1b0a-131">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b1b0a-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="b1b0a-132">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1b0a-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="b1b0a-133">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1b0a-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b1b0a-134">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1b0a-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
