---
title: IHostSyncManager::CreateMonitorEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: f7426585045c7ae81377ec9bfca9d397d6f734cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192015"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="a2d54-102">IHostSyncManager::CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2d54-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="a2d54-103">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2d54-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2d54-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2d54-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2d54-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a2d54-106">'ndaki Olay nesnesiyle ilişkilendirmek için bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="a2d54-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="a2d54-107">dışı [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="a2d54-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2d54-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2d54-108">Return Value</span></span>  
  
|<span data-ttu-id="a2d54-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2d54-109">HRESULT</span></span>|<span data-ttu-id="a2d54-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2d54-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2d54-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2d54-111">S_OK</span></span>|<span data-ttu-id="a2d54-112">`CreateMonitorEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a2d54-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="a2d54-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2d54-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2d54-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a2d54-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2d54-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2d54-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2d54-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a2d54-116">The call timed out.</span></span>|  
|<span data-ttu-id="a2d54-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2d54-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2d54-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a2d54-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2d54-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2d54-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2d54-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a2d54-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2d54-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="a2d54-121">E_FAIL</span></span>|<span data-ttu-id="a2d54-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a2d54-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2d54-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a2d54-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2d54-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2d54-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2d54-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a2d54-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a2d54-126">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="a2d54-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2d54-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2d54-127">Remarks</span></span>  
 <span data-ttu-id="a2d54-128">`CreateMonitorEvent`, CLR 'nin yönetilen <xref:System.Threading.Monitor?displayProperty=nameWithType> türü uygulamasında kullandığı bir `IHostAutoEvent` döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2d54-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="a2d54-129">Bu yöntem, `bManualReset` parametresi için belirtilen `false` bir değeri ile Win32 `CreateEvent` işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="a2d54-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="a2d54-130">Ana bilgisayar, [ICLRSyncManager:: Getmonitortorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) yöntemini çağırarak monitörde hangi görevin beklediğini belirleyen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a2d54-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d54-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2d54-131">Requirements</span></span>  
 <span data-ttu-id="a2d54-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d54-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d54-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a2d54-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2d54-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a2d54-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2d54-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d54-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d54-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2d54-136">See also</span></span>

- [<span data-ttu-id="a2d54-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d54-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a2d54-138">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d54-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="a2d54-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d54-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
