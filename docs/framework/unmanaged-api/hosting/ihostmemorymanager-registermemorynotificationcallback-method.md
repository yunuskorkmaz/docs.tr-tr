---
title: IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87dfbe85d279aa191253857887c1d9b5b5f8c7cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088528"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="389dd-102">IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="389dd-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="389dd-103">Bilgisayarda geçerli bellek yükü bir işaretçiye ortak dil çalışma zamanı (CLR) bildirmek için konak çağıran bir geri çağırma işlevini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="389dd-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="389dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="389dd-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="389dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="389dd-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="389dd-106">[in] Bir arabirim işaretçisi için bir [Iclrmemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) CLR tarafından uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="389dd-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="389dd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="389dd-107">Return Value</span></span>  
  
|<span data-ttu-id="389dd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="389dd-108">HRESULT</span></span>|<span data-ttu-id="389dd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="389dd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="389dd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="389dd-110">S_OK</span></span>|`RegisterMemoryNotificationCallback` <span data-ttu-id="389dd-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="389dd-111">returned successfully.</span></span>|  
|<span data-ttu-id="389dd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="389dd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="389dd-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="389dd-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="389dd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="389dd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="389dd-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="389dd-115">The call timed out.</span></span>|  
|<span data-ttu-id="389dd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="389dd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="389dd-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="389dd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="389dd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="389dd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="389dd-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="389dd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="389dd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="389dd-120">E_FAIL</span></span>|<span data-ttu-id="389dd-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="389dd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="389dd-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="389dd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="389dd-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="389dd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="389dd-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="389dd-124">Remarks</span></span>  
 <span data-ttu-id="389dd-125">Çünkü `ICLRMemoryNotificationCallback` arabirimi yalnızca bir yöntem tanımlar ([Iclrmemorynotificationcallback::onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) ve çünkü `pCallback` işaretçisidir bir `ICLRMemoryNotificationCallback` CLR tarafından sağlanan örneği etkili bir şekilde geri çağırma işlevi için kendisini kayıttır.</span><span class="sxs-lookup"><span data-stu-id="389dd-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="389dd-126">Konak çağırır `OnMemoryNotification` standart Win32 kullanarak yerine rapor bellek baskısı koşullarını `CreateMemoryResourceNotification` işlevi.</span><span class="sxs-lookup"><span data-stu-id="389dd-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="389dd-127">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="389dd-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="389dd-128">Çağrılar `OnMemoryNotification` hiçbir zaman engellememe.</span><span class="sxs-lookup"><span data-stu-id="389dd-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="389dd-129">Bunlar her zaman hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="389dd-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="389dd-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="389dd-130">Requirements</span></span>  
 <span data-ttu-id="389dd-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="389dd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="389dd-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="389dd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="389dd-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="389dd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="389dd-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="389dd-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="389dd-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="389dd-135">See also</span></span>

- [<span data-ttu-id="389dd-136">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="389dd-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="389dd-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="389dd-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
