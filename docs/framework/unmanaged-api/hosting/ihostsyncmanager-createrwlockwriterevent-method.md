---
description: ': IHostSyncManager:: CreateRWLockWriterEvent Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 509f18ff49966e5da3a25e39258d33caf69249a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784762"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="0a874-103">IHostSyncManager::CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a874-103">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>

<span data-ttu-id="0a874-104">Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a874-104">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a874-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a874-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a874-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a874-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="0a874-107">'ndaki Otomatik sıfırlama olayı ile ilişkilendirilecek tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="0a874-107">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="0a874-108">dışı [IHostAutoEvent](ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="0a874-108">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a874-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a874-109">Return Value</span></span>  
  
|<span data-ttu-id="0a874-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a874-110">HRESULT</span></span>|<span data-ttu-id="0a874-111">Description</span><span class="sxs-lookup"><span data-stu-id="0a874-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a874-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a874-112">S_OK</span></span>|<span data-ttu-id="0a874-113">`CreateRWLockWriterEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0a874-113">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0a874-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a874-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a874-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0a874-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a874-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a874-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a874-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0a874-117">The call timed out.</span></span>|  
|<span data-ttu-id="0a874-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a874-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a874-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0a874-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a874-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a874-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a874-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0a874-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a874-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a874-122">E_FAIL</span></span>|<span data-ttu-id="0a874-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0a874-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a874-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0a874-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a874-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a874-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0a874-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0a874-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0a874-127">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="0a874-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a874-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a874-128">Remarks</span></span>  

 <span data-ttu-id="0a874-129">CLR, `CreateRWLockWriterEvent` `IHostAutoEvent` bir yazıcı kilidi uygulamasında kullanmak üzere bir örneğe başvuru almak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0a874-129">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="0a874-130">Konak, [ICLRSyncManager](iclrsyncmanager-interface.md) arabiriminin yineleme yöntemlerini çağırarak hangi görevlerin kilit üzerinde beklediğini belirleyebilmek için belirtilen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0a874-130">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a874-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a874-131">Requirements</span></span>  

 <span data-ttu-id="0a874-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a874-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a874-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a874-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a874-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0a874-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a874-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a874-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a874-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a874-136">See also</span></span>

- [<span data-ttu-id="0a874-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a874-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0a874-138">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a874-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="0a874-139">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a874-139">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="0a874-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a874-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
