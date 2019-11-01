---
title: IHostSyncManager::CreateRWLockWriterEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: 13eb23c530a4fe1b491f41cc65cc94dacc9d34f4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192002"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="6b497-102">IHostSyncManager::CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b497-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="6b497-103">Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b497-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b497-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b497-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b497-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b497-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="6b497-106">'ndaki Otomatik sıfırlama olayı ile ilişkilendirilecek tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="6b497-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="6b497-107">dışı [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="6b497-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b497-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b497-108">Return Value</span></span>  
  
|<span data-ttu-id="6b497-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b497-109">HRESULT</span></span>|<span data-ttu-id="6b497-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b497-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b497-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b497-111">S_OK</span></span>|<span data-ttu-id="6b497-112">`CreateRWLockWriterEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6b497-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="6b497-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b497-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b497-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6b497-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b497-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b497-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b497-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6b497-116">The call timed out.</span></span>|  
|<span data-ttu-id="6b497-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b497-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b497-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6b497-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b497-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b497-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b497-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6b497-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b497-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="6b497-121">E_FAIL</span></span>|<span data-ttu-id="6b497-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6b497-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b497-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6b497-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b497-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b497-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6b497-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6b497-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6b497-126">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="6b497-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b497-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b497-127">Remarks</span></span>  
 <span data-ttu-id="6b497-128">CLR, bir yazıcı kilidi uygulamasında kullanmak üzere bir `IHostAutoEvent` örneğine başvuru almak için `CreateRWLockWriterEvent` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6b497-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="6b497-129">Konak, [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) arabiriminin yineleme yöntemlerini çağırarak hangi görevlerin kilit üzerinde beklediğini belirleyebilmek için belirtilen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="6b497-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b497-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b497-130">Requirements</span></span>  
 <span data-ttu-id="6b497-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b497-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b497-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6b497-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b497-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6b497-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b497-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b497-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b497-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b497-135">See also</span></span>

- [<span data-ttu-id="6b497-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b497-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6b497-137">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b497-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="6b497-138">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b497-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="6b497-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b497-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
