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
ms.openlocfilehash: 5b5faf14337f78d9b176787528ae8947f5810ba6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704376"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="c4d1a-102">IHostSyncManager::CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4d1a-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>

<span data-ttu-id="c4d1a-103">Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d1a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c4d1a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4d1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4d1a-105">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="c4d1a-106">'ndaki Otomatik sıfırlama olayı ile ilişkilendirilecek tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="c4d1a-107">dışı [IHostAutoEvent](ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4d1a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c4d1a-108">Return Value</span></span>  
  
|<span data-ttu-id="c4d1a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4d1a-109">HRESULT</span></span>|<span data-ttu-id="c4d1a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4d1a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4d1a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4d1a-111">S_OK</span></span>|<span data-ttu-id="c4d1a-112">`CreateRWLockWriterEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c4d1a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4d1a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4d1a-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4d1a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4d1a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4d1a-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-116">The call timed out.</span></span>|  
|<span data-ttu-id="c4d1a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4d1a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4d1a-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4d1a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4d1a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4d1a-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4d1a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4d1a-121">E_FAIL</span></span>|<span data-ttu-id="c4d1a-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4d1a-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4d1a-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c4d1a-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c4d1a-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c4d1a-126">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4d1a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4d1a-127">Remarks</span></span>  

 <span data-ttu-id="c4d1a-128">CLR, `CreateRWLockWriterEvent` `IHostAutoEvent` bir yazıcı kilidi uygulamasında kullanmak üzere bir örneğe başvuru almak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="c4d1a-129">Konak, [ICLRSyncManager](iclrsyncmanager-interface.md) arabiriminin yineleme yöntemlerini çağırarak hangi görevlerin kilit üzerinde beklediğini belirleyebilmek için belirtilen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d1a-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4d1a-130">Requirements</span></span>  

 <span data-ttu-id="c4d1a-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4d1a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d1a-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4d1a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4d1a-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c4d1a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4d1a-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d1a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d1a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d1a-135">See also</span></span>

- [<span data-ttu-id="c4d1a-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d1a-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c4d1a-137">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d1a-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="c4d1a-138">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d1a-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="c4d1a-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d1a-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
