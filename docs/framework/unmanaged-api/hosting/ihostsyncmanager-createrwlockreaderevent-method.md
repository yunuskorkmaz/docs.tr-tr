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
ms.openlocfilehash: 64cf6c80ab1cf4b3ca52c60d6e72b54c438f9f4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195846"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="1aac2-102">IHostSyncManager::CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aac2-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="1aac2-103">Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1aac2-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aac2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1aac2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aac2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1aac2-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="1aac2-106">[in] `ppEvent` sinyal alınmalıdır `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="1aac2-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="1aac2-107">'ndaki Okuyucu kilidi ile ilişkilendirilecek tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="1aac2-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="1aac2-108">dışı Bir [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturuoluşturulamadığı null.</span><span class="sxs-lookup"><span data-stu-id="1aac2-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aac2-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1aac2-109">Return Value</span></span>  
  
|<span data-ttu-id="1aac2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1aac2-110">HRESULT</span></span>|<span data-ttu-id="1aac2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1aac2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1aac2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1aac2-112">S_OK</span></span>|<span data-ttu-id="1aac2-113">`CreateRWLockReaderEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1aac2-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="1aac2-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1aac2-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1aac2-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1aac2-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1aac2-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1aac2-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1aac2-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1aac2-117">The call timed out.</span></span>|  
|<span data-ttu-id="1aac2-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1aac2-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1aac2-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1aac2-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1aac2-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1aac2-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1aac2-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1aac2-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1aac2-122">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="1aac2-122">E_FAIL</span></span>|<span data-ttu-id="1aac2-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1aac2-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1aac2-124">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1aac2-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1aac2-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1aac2-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1aac2-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1aac2-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1aac2-127">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="1aac2-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aac2-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1aac2-128">Remarks</span></span>  
 <span data-ttu-id="1aac2-129">CLR, bir okuyucu kilidi uygulamasında kullanmak üzere bir `IHostManualEvent` örneğine başvuru almak için `CreateRWLockReaderEvent` çağırır.</span><span class="sxs-lookup"><span data-stu-id="1aac2-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="1aac2-130">Ana bilgisayar, [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) arabirimini sorgulayarak okuyucu kilidinde hangi görevlerin beklediğini belirleyen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1aac2-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aac2-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1aac2-131">Requirements</span></span>  
 <span data-ttu-id="1aac2-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aac2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aac2-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1aac2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1aac2-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1aac2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1aac2-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aac2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aac2-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1aac2-136">See also</span></span>

- [<span data-ttu-id="1aac2-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aac2-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="1aac2-138">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aac2-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="1aac2-139">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aac2-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="1aac2-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aac2-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
