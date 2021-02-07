---
description: ': IHostMemoryManager:: RegisterMemoryNotificationCallback Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 26a7468aba4f473eebff78a8c67eeb5b3e866e9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707773"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="f5c4a-103">IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5c4a-103">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>

<span data-ttu-id="f5c4a-104">Bilgisayarın, bilgisayardaki geçerli bellek yükünün ortak dil çalışma zamanını (CLR) bilgilendirmek için çağırdığı bir geri çağırma işlevine bir işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-104">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c4a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5c4a-105">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5c4a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5c4a-106">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="f5c4a-107">'ndaki CLR tarafından uygulanan [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) örneğine yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-107">[in] An interface pointer to an [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5c4a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f5c4a-108">Return Value</span></span>  
  
|<span data-ttu-id="f5c4a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5c4a-109">HRESULT</span></span>|<span data-ttu-id="f5c4a-110">Description</span><span class="sxs-lookup"><span data-stu-id="f5c4a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5c4a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5c4a-111">S_OK</span></span>|<span data-ttu-id="f5c4a-112">`RegisterMemoryNotificationCallback` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-112">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="f5c4a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5c4a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5c4a-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5c4a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5c4a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5c4a-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-116">The call timed out.</span></span>|  
|<span data-ttu-id="f5c4a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5c4a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5c4a-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5c4a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5c4a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5c4a-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5c4a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5c4a-121">E_FAIL</span></span>|<span data-ttu-id="f5c4a-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5c4a-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5c4a-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5c4a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5c4a-125">Remarks</span></span>  

 <span data-ttu-id="f5c4a-126">`ICLRMemoryNotificationCallback`Arabirim yalnızca bir yöntemi ([ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)) TANıMLADıĞıNDAN ve, `pCallback` clr tarafından sağlanmış bir örneğe yönelik bir işaretçi olduğundan `ICLRMemoryNotificationCallback` , geri çağırma işlevinin kendisi için kayıt etkin olur.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-126">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="f5c4a-127">Ana bilgisayar `OnMemoryNotification` , standart Win32 işlevini kullanmak yerine bellek baskısı koşullarını raporlamak için çağırır `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="f5c4a-127">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="f5c4a-128">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-128">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5c4a-129">Hiçbir şekilde `OnMemoryNotification` engellenmemek için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-129">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="f5c4a-130">Her zaman hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-130">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c4a-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5c4a-131">Requirements</span></span>  

 <span data-ttu-id="f5c4a-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c4a-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c4a-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5c4a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5c4a-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f5c4a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5c4a-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c4a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c4a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5c4a-136">See also</span></span>

- [<span data-ttu-id="f5c4a-137">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5c4a-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="f5c4a-138">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5c4a-138">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
