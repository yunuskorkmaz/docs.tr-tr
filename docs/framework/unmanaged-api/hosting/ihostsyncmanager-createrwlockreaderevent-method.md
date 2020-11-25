---
title: IHostSyncManager::CreateRWLockReaderEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
ms.openlocfilehash: 7c9bf2186d3dc4500694225ea4023df3609b9010
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704389"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="63b34-102">IHostSyncManager::CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63b34-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>

<span data-ttu-id="63b34-103">Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63b34-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b34-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="63b34-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63b34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63b34-105">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="63b34-106">[in] `true` , `ppEvent` sinyal alınmalıdır; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="63b34-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="63b34-107">'ndaki Okuyucu kilidi ile ilişkilendirilecek tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="63b34-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="63b34-108">dışı Bir [IHostManualEvent](ihostmanualevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturuoluşturulamadığı null.</span><span class="sxs-lookup"><span data-stu-id="63b34-108">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63b34-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63b34-109">Return Value</span></span>  
  
|<span data-ttu-id="63b34-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63b34-110">HRESULT</span></span>|<span data-ttu-id="63b34-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63b34-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63b34-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="63b34-112">S_OK</span></span>|<span data-ttu-id="63b34-113">`CreateRWLockReaderEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="63b34-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="63b34-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="63b34-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="63b34-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="63b34-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="63b34-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="63b34-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="63b34-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="63b34-117">The call timed out.</span></span>|  
|<span data-ttu-id="63b34-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="63b34-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="63b34-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="63b34-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="63b34-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="63b34-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="63b34-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="63b34-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="63b34-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63b34-122">E_FAIL</span></span>|<span data-ttu-id="63b34-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="63b34-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63b34-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="63b34-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="63b34-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="63b34-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="63b34-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="63b34-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="63b34-127">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="63b34-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63b34-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63b34-128">Remarks</span></span>  

 <span data-ttu-id="63b34-129">CLR, `CreateRWLockReaderEvent` `IHostManualEvent` bir okuyucu kilidi uygulamasında kullanmak üzere bir örneğe başvuru almak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="63b34-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="63b34-130">Ana bilgisayar, [ICLRSyncManager](iclrsyncmanager-interface.md) arabirimini sorgulayarak okuyucu kilidinde hangi görevlerin beklediğini belirleyen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="63b34-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63b34-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63b34-131">Requirements</span></span>  

 <span data-ttu-id="63b34-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63b34-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63b34-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63b34-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63b34-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="63b34-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63b34-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b34-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b34-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63b34-136">See also</span></span>

- [<span data-ttu-id="63b34-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63b34-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="63b34-138">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63b34-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="63b34-139">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63b34-139">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="63b34-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63b34-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
