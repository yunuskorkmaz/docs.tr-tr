---
title: "ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback.OnMemoryNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3683b77db6a1a8be2d5c5ccf6c1865d5d6bdb94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="03afe-102">ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03afe-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="03afe-103">Ortak dil çalışma zamanı (CLR) bilgisayardaki Bellek Yükü bildirir.</span><span class="sxs-lookup"><span data-stu-id="03afe-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03afe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03afe-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03afe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03afe-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="03afe-106">[in] Aşağıdakilerden birini [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) değerleri, bellek baskısı bilgisayar belirten şu anda karşılaşılan.</span><span class="sxs-lookup"><span data-stu-id="03afe-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03afe-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="03afe-107">Return Value</span></span>  
  
|<span data-ttu-id="03afe-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03afe-108">HRESULT</span></span>|<span data-ttu-id="03afe-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03afe-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03afe-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="03afe-110">S_OK</span></span>|<span data-ttu-id="03afe-111">`OnMemoryNotification`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="03afe-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="03afe-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03afe-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03afe-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="03afe-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03afe-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03afe-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03afe-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="03afe-115">The call timed out.</span></span>|  
|<span data-ttu-id="03afe-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03afe-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03afe-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="03afe-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03afe-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03afe-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03afe-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="03afe-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03afe-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03afe-120">E_FAIL</span></span>|<span data-ttu-id="03afe-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="03afe-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03afe-122">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="03afe-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03afe-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="03afe-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03afe-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03afe-124">Remarks</span></span>  
 <span data-ttu-id="03afe-125">CLR için bir geri çağırma kaydeder `OnMemoryNotification` yapılan bir çağrı kullanılarak [Ihostmemorymanager::registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03afe-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="03afe-126">Çalışma zamanı ana bilgisayarın bu bellek kaynakları düşük çalıştıran bildirdiğinde ek bellek boşaltmak için geri döndürülen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="03afe-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03afe-127">Çağrılar `OnMemoryNotification` hiçbir zaman engelleyin.</span><span class="sxs-lookup"><span data-stu-id="03afe-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="03afe-128">Bunlar her zaman hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="03afe-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03afe-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03afe-129">Requirements</span></span>  
 <span data-ttu-id="03afe-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03afe-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03afe-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03afe-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03afe-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="03afe-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03afe-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03afe-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03afe-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03afe-134">See Also</span></span>  
 [<span data-ttu-id="03afe-135">Ihostmemorymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="03afe-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="03afe-136">RegisterMemoryNotificationCallback yöntemi</span><span class="sxs-lookup"><span data-stu-id="03afe-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="03afe-137">Iclrmemorynotificationcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="03afe-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
