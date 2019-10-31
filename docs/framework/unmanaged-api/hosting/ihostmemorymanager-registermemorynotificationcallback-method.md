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
ms.openlocfilehash: 4400fab27ed82e540230ce4196844285e8e37d16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128643"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="0a906-102">IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a906-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="0a906-103">Bilgisayarın, bilgisayardaki geçerli bellek yükünün ortak dil çalışma zamanını (CLR) bilgilendirmek için çağırdığı bir geri çağırma işlevine bir işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0a906-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a906-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a906-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a906-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a906-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="0a906-106">'ndaki CLR tarafından uygulanan [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) örneğine yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0a906-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a906-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a906-107">Return Value</span></span>  
  
|<span data-ttu-id="0a906-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a906-108">HRESULT</span></span>|<span data-ttu-id="0a906-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a906-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a906-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a906-110">S_OK</span></span>|<span data-ttu-id="0a906-111">`RegisterMemoryNotificationCallback` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0a906-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="0a906-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a906-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a906-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0a906-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a906-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a906-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a906-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0a906-115">The call timed out.</span></span>|  
|<span data-ttu-id="0a906-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a906-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a906-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0a906-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a906-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a906-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a906-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0a906-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a906-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="0a906-120">E_FAIL</span></span>|<span data-ttu-id="0a906-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0a906-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a906-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0a906-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a906-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a906-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a906-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a906-124">Remarks</span></span>  
 <span data-ttu-id="0a906-125">`ICLRMemoryNotificationCallback` arabirimi yalnızca bir yöntemi ([ICLRMemoryNotificationCallback:: OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) tanımladığından ve `pCallback` CLR tarafından sağlanmış bir `ICLRMemoryNotificationCallback` örneğine yönelik bir işaretçi olduğundan, geri çağırma için kayıt etkin olur işlevin kendisini.</span><span class="sxs-lookup"><span data-stu-id="0a906-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="0a906-126">Ana bilgisayar, standart Win32 `CreateMemoryResourceNotification` işlevini kullanmak yerine bellek baskısı koşullarını raporlamak için `OnMemoryNotification` çağırır.</span><span class="sxs-lookup"><span data-stu-id="0a906-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="0a906-127">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="0a906-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a906-128">`OnMemoryNotification` hiçbir şekilde engellenmemek için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="0a906-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="0a906-129">Her zaman hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0a906-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a906-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a906-130">Requirements</span></span>  
 <span data-ttu-id="0a906-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a906-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a906-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a906-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a906-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0a906-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a906-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a906-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a906-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a906-135">See also</span></span>

- [<span data-ttu-id="0a906-136">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a906-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="0a906-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a906-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
