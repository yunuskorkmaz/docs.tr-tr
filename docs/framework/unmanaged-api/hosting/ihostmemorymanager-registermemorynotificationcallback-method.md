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
ms.openlocfilehash: d68790cdb671efdd0761ceef59196e8646654d5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439616"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="57c01-102">IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c01-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="57c01-103">Bilgisayarda geçerli bellek yükünün bir işaretçi ortak dil çalışma zamanı (CLR) bilgilendirmek için ana bilgisayar çağıran bir geri çağırma işlevini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="57c01-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c01-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57c01-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57c01-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57c01-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="57c01-106">[in] Bir arabirim işaretçisi bir [Iclrmemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) CLR tarafından uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="57c01-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57c01-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57c01-107">Return Value</span></span>  
  
|<span data-ttu-id="57c01-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57c01-108">HRESULT</span></span>|<span data-ttu-id="57c01-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57c01-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57c01-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57c01-110">S_OK</span></span>|<span data-ttu-id="57c01-111">`RegisterMemoryNotificationCallback` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="57c01-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="57c01-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57c01-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57c01-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="57c01-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57c01-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57c01-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57c01-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="57c01-115">The call timed out.</span></span>|  
|<span data-ttu-id="57c01-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57c01-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57c01-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="57c01-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57c01-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57c01-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57c01-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="57c01-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57c01-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57c01-120">E_FAIL</span></span>|<span data-ttu-id="57c01-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="57c01-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57c01-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="57c01-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57c01-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="57c01-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c01-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57c01-124">Remarks</span></span>  
 <span data-ttu-id="57c01-125">Çünkü `ICLRMemoryNotificationCallback` arabirimi tanımlar tek bir yöntem ([Iclrmemorynotificationcallback::onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) ve çünkü `pCallback` gösteren bir işaretçidir bir `ICLRMemoryNotificationCallback` CLR tarafından sağlanan örneği Kayıt, geri çağırma işlevi kendisi için etkin değil.</span><span class="sxs-lookup"><span data-stu-id="57c01-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="57c01-126">Ana bilgisayar çağırır `OnMemoryNotification` standart Win32 kullanarak yerine rapor bellek baskısı koşullarını `CreateMemoryResourceNotification` işlevi.</span><span class="sxs-lookup"><span data-stu-id="57c01-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="57c01-127">Daha fazla bilgi için Windows platformu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="57c01-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57c01-128">Çağrılar `OnMemoryNotification` hiçbir zaman engelleyin.</span><span class="sxs-lookup"><span data-stu-id="57c01-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="57c01-129">Bunlar her zaman hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="57c01-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c01-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57c01-130">Requirements</span></span>  
 <span data-ttu-id="57c01-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57c01-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c01-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57c01-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57c01-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="57c01-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57c01-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c01-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c01-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57c01-135">See Also</span></span>  
 [<span data-ttu-id="57c01-136">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c01-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="57c01-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c01-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
