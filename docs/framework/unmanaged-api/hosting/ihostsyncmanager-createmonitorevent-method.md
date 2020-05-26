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
ms.openlocfilehash: c0f7e1fd6bf4c9386300b11477df85e87899fc67
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803317"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="bbd8f-102">IHostSyncManager::CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbd8f-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="bbd8f-103">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd8f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bbd8f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbd8f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbd8f-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="bbd8f-106">'ndaki Olay nesnesiyle ilişkilendirmek için bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="bbd8f-107">dışı [IHostAutoEvent](ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbd8f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bbd8f-108">Return Value</span></span>  
  
|<span data-ttu-id="bbd8f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbd8f-109">HRESULT</span></span>|<span data-ttu-id="bbd8f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbd8f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbd8f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbd8f-111">S_OK</span></span>|<span data-ttu-id="bbd8f-112">`CreateMonitorEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="bbd8f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbd8f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbd8f-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbd8f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbd8f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbd8f-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-116">The call timed out.</span></span>|  
|<span data-ttu-id="bbd8f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbd8f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbd8f-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbd8f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbd8f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbd8f-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbd8f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbd8f-121">E_FAIL</span></span>|<span data-ttu-id="bbd8f-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbd8f-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbd8f-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bbd8f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bbd8f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bbd8f-126">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbd8f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbd8f-127">Remarks</span></span>  
 <span data-ttu-id="bbd8f-128">`CreateMonitorEvent``IHostAutoEvent`clr 'nin yönetilen türün uygulamasında kullandığı bir döndürür <xref:System.Threading.Monitor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bbd8f-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="bbd8f-129">Bu yöntem, Win32 `CreateEvent` işlevini, `false` parametresi için belirtilen bir değerle yansıtır `bManualReset` .</span><span class="sxs-lookup"><span data-stu-id="bbd8f-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="bbd8f-130">Ana bilgisayar, [ICLRSyncManager:: Getmonitortorowner](iclrsyncmanager-getmonitorowner-method.md) yöntemini çağırarak monitörde hangi görevin beklediğini belirleyen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbd8f-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbd8f-131">Requirements</span></span>  
 <span data-ttu-id="bbd8f-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbd8f-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbd8f-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bbd8f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbd8f-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="bbd8f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbd8f-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbd8f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd8f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbd8f-136">See also</span></span>

- [<span data-ttu-id="bbd8f-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbd8f-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="bbd8f-138">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbd8f-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="bbd8f-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbd8f-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
