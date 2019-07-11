---
title: ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c933389e1398d294d79f82a69a609a77aa820f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779829"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="1b6f1-102">ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b6f1-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="1b6f1-103">Bellek Yükü bilgisayarda ortak dil çalışma zamanı (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b6f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b6f1-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b6f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b6f1-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="1b6f1-106">[in] Aşağıdakilerden birini [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) değerleri, bilgisayarın bellek baskısı belirten şu anda karşılaşılan.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b6f1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1b6f1-107">Return Value</span></span>  
  
|<span data-ttu-id="1b6f1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b6f1-108">HRESULT</span></span>|<span data-ttu-id="1b6f1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b6f1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b6f1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b6f1-110">S_OK</span></span>|<span data-ttu-id="1b6f1-111">`OnMemoryNotification` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="1b6f1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b6f1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b6f1-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b6f1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b6f1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b6f1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b6f1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b6f1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b6f1-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b6f1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b6f1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b6f1-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b6f1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b6f1-120">E_FAIL</span></span>|<span data-ttu-id="1b6f1-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b6f1-122">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b6f1-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b6f1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b6f1-124">Remarks</span></span>  
 <span data-ttu-id="1b6f1-125">CLR için bir geri çağırma kaydeder `OnMemoryNotification` bir çağrı kullanılarak [Ihostmemorymanager::registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="1b6f1-126">Çalışma zamanı ana bilgisayar kaynakları düşük çalıştırıyorsanız bu bellek bildirdiğinde ek bellek boşaltmak için geri döndürülen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b6f1-127">Çağrılar `OnMemoryNotification` hiçbir zaman engellememe.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="1b6f1-128">Bunlar her zaman hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b6f1-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b6f1-129">Requirements</span></span>  
 <span data-ttu-id="1b6f1-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b6f1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b6f1-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b6f1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b6f1-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1b6f1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b6f1-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b6f1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b6f1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b6f1-134">See also</span></span>

- [<span data-ttu-id="1b6f1-135">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b6f1-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="1b6f1-136">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b6f1-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="1b6f1-137">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b6f1-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
