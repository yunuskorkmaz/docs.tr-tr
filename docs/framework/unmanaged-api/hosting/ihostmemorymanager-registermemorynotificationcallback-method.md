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
ms.openlocfilehash: 0c20df85560f715e829fe02be599788854fcb0f1
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804476"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="99fb5-102">IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99fb5-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="99fb5-103">Bilgisayarın, bilgisayardaki geçerli bellek yükünün ortak dil çalışma zamanını (CLR) bilgilendirmek için çağırdığı bir geri çağırma işlevine bir işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="99fb5-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fb5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="99fb5-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99fb5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99fb5-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="99fb5-106">'ndaki CLR tarafından uygulanan [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) örneğine yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="99fb5-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99fb5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99fb5-107">Return Value</span></span>  
  
|<span data-ttu-id="99fb5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99fb5-108">HRESULT</span></span>|<span data-ttu-id="99fb5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99fb5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99fb5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="99fb5-110">S_OK</span></span>|<span data-ttu-id="99fb5-111">`RegisterMemoryNotificationCallback`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="99fb5-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="99fb5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99fb5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99fb5-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="99fb5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99fb5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99fb5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99fb5-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="99fb5-115">The call timed out.</span></span>|  
|<span data-ttu-id="99fb5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99fb5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99fb5-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="99fb5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99fb5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99fb5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99fb5-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="99fb5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99fb5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99fb5-120">E_FAIL</span></span>|<span data-ttu-id="99fb5-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="99fb5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99fb5-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99fb5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99fb5-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="99fb5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99fb5-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99fb5-124">Remarks</span></span>  
 <span data-ttu-id="99fb5-125">`ICLRMemoryNotificationCallback`Arabirim yalnızca bir yöntemi ([ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)) TANıMLADıĞıNDAN ve, `pCallback` clr tarafından sağlanmış bir örneğe yönelik bir işaretçi olduğundan `ICLRMemoryNotificationCallback` , geri çağırma işlevinin kendisi için kayıt etkin olur.</span><span class="sxs-lookup"><span data-stu-id="99fb5-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="99fb5-126">Ana bilgisayar `OnMemoryNotification` , standart Win32 işlevini kullanmak yerine bellek baskısı koşullarını raporlamak için çağırır `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="99fb5-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="99fb5-127">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="99fb5-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99fb5-128">Hiçbir şekilde `OnMemoryNotification` engellenmemek için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="99fb5-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="99fb5-129">Her zaman hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="99fb5-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fb5-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99fb5-130">Requirements</span></span>  
 <span data-ttu-id="99fb5-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99fb5-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fb5-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99fb5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99fb5-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="99fb5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99fb5-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fb5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fb5-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99fb5-135">See also</span></span>

- [<span data-ttu-id="99fb5-136">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99fb5-136">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="99fb5-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99fb5-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
