---
title: ICLRIoCompletionManager::OnComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d9d4336b79b60e69f980b6d5931e2994732f30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792697"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="b2fab-102">ICLRIoCompletionManager::OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2fab-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="b2fab-103">Ortak dil çalışma zamanı (CLR) için bir çağrı kullanılarak yapılan bir g/ç isteğinin durumunu bildirir [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2fab-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2fab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2fab-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2fab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2fab-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="b2fab-106">[in] Bağlama işlemi durumunu gösteren HRESULT değerini.</span><span class="sxs-lookup"><span data-stu-id="b2fab-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="b2fab-107">S_OK işleminin başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2fab-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="b2fab-108">HOST_E_INTERRUPTED, çağrı tamamlanmadan önce sona erdi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2fab-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="b2fab-109">E_FAIL bilinmeyen, kurtarılamaz, geri dönülemez bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2fab-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="b2fab-110">[in] G/ç isteğinin işlenmesi sırasında aktarılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b2fab-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="b2fab-111">[in] Bir işaretçi `OVERLAPPED` çağrısına geçirilen yapısı `IHostIoCompletionManager::Bind` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2fab-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2fab-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2fab-112">Return Value</span></span>  
  
|<span data-ttu-id="b2fab-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2fab-113">HRESULT</span></span>|<span data-ttu-id="b2fab-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2fab-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2fab-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2fab-115">S_OK</span></span>|<span data-ttu-id="b2fab-116">`OnComplete` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b2fab-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="b2fab-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2fab-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2fab-118">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b2fab-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2fab-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2fab-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2fab-120">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b2fab-120">The call timed out.</span></span>|  
|<span data-ttu-id="b2fab-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2fab-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2fab-122">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b2fab-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2fab-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2fab-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2fab-124">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b2fab-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2fab-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2fab-125">E_FAIL</span></span>|<span data-ttu-id="b2fab-126">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b2fab-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2fab-127">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b2fab-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2fab-128">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2fab-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2fab-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2fab-129">Remarks</span></span>  
 <span data-ttu-id="b2fab-130">Konak bir g/ç tamamlama Özet uygularsa, CLR konağı üzerinden g/ç isteği yöntemleri kullanılarak yapan [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b2fab-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="b2fab-131">Sonra konak çağırır `OnComplete` böyle isteklerinin sonucunu çalışma zamanını bildirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2fab-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2fab-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2fab-132">Requirements</span></span>  
 <span data-ttu-id="b2fab-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2fab-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2fab-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2fab-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2fab-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b2fab-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2fab-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2fab-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2fab-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2fab-137">See also</span></span>

- [<span data-ttu-id="b2fab-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2fab-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b2fab-139">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2fab-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="b2fab-140">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2fab-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
