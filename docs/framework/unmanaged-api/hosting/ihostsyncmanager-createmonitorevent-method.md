---
description: ': IHostSyncManager:: CreateMonitorEvent yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b48d0417e614cf04c3ab150f0bdda73408b7a273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784788"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="db8c7-103">IHostSyncManager::CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db8c7-103">IHostSyncManager::CreateMonitorEvent Method</span></span>

<span data-ttu-id="db8c7-104">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db8c7-104">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db8c7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db8c7-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db8c7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db8c7-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="db8c7-107">'ndaki Olay nesnesiyle ilişkilendirmek için bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="db8c7-107">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="db8c7-108">dışı [IHostAutoEvent](ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="db8c7-108">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db8c7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="db8c7-109">Return Value</span></span>  
  
|<span data-ttu-id="db8c7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db8c7-110">HRESULT</span></span>|<span data-ttu-id="db8c7-111">Description</span><span class="sxs-lookup"><span data-stu-id="db8c7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db8c7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="db8c7-112">S_OK</span></span>|<span data-ttu-id="db8c7-113">`CreateMonitorEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="db8c7-113">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="db8c7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db8c7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db8c7-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="db8c7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db8c7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db8c7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db8c7-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="db8c7-117">The call timed out.</span></span>|  
|<span data-ttu-id="db8c7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db8c7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db8c7-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="db8c7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db8c7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db8c7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db8c7-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="db8c7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db8c7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db8c7-122">E_FAIL</span></span>|<span data-ttu-id="db8c7-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="db8c7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db8c7-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="db8c7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db8c7-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="db8c7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="db8c7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="db8c7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="db8c7-127">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="db8c7-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db8c7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db8c7-128">Remarks</span></span>  

 <span data-ttu-id="db8c7-129">`CreateMonitorEvent``IHostAutoEvent`clr 'nin yönetilen türün uygulamasında kullandığı bir döndürür <xref:System.Threading.Monitor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="db8c7-129">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="db8c7-130">Bu yöntem, Win32 `CreateEvent` işlevini, `false` parametresi için belirtilen bir değerle yansıtır `bManualReset` .</span><span class="sxs-lookup"><span data-stu-id="db8c7-130">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="db8c7-131">Ana bilgisayar, [ICLRSyncManager:: Getmonitortorowner](iclrsyncmanager-getmonitorowner-method.md) yöntemini çağırarak monitörde hangi görevin beklediğini belirleyen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="db8c7-131">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db8c7-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db8c7-132">Requirements</span></span>  

 <span data-ttu-id="db8c7-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db8c7-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db8c7-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db8c7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db8c7-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="db8c7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db8c7-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db8c7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db8c7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db8c7-137">See also</span></span>

- [<span data-ttu-id="db8c7-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db8c7-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="db8c7-139">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db8c7-139">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="db8c7-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db8c7-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
