---
title: "ICLRIoCompletionManager::OnComplete Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager.OnComplete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd38679d1b8d099e5eb6330e03e2333b03780dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="410ff-102">ICLRIoCompletionManager::OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="410ff-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="410ff-103">Ortak dil çalışma zamanı (CLR) için bir çağrı kullanılarak yapılan bir g/ç isteği durumunu bildirir [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="410ff-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="410ff-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="410ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="410ff-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="410ff-106">[in] Bağlama işlemi durumunu belirten bir HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="410ff-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
-   <span data-ttu-id="410ff-107">S_OK işleminin başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="410ff-107">S_OK indicates that the operation completed successfully.</span></span>  
  
-   <span data-ttu-id="410ff-108">Çağrı tamamlanmadan önce sona HOST_E_INTERRUPTED gösterir.</span><span class="sxs-lookup"><span data-stu-id="410ff-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
-   <span data-ttu-id="410ff-109">E_FAIL bilinmeyen, kurtarılamaz, geri dönülemez bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="410ff-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="410ff-110">[in] G/ç isteği işleme sırasında aktarılan toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="410ff-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="410ff-111">[in] Bir işaretçi `OVERLAPPED` çağrısına iletilen yapı `IHostIoCompletionManager::Bind` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="410ff-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="410ff-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="410ff-112">Return Value</span></span>  
  
|<span data-ttu-id="410ff-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="410ff-113">HRESULT</span></span>|<span data-ttu-id="410ff-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="410ff-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="410ff-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="410ff-115">S_OK</span></span>|<span data-ttu-id="410ff-116">`OnComplete`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="410ff-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="410ff-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="410ff-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="410ff-118">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="410ff-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="410ff-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="410ff-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="410ff-120">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="410ff-120">The call timed out.</span></span>|  
|<span data-ttu-id="410ff-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="410ff-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="410ff-122">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="410ff-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="410ff-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="410ff-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="410ff-124">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="410ff-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="410ff-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="410ff-125">E_FAIL</span></span>|<span data-ttu-id="410ff-126">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="410ff-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="410ff-127">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="410ff-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="410ff-128">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="410ff-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="410ff-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="410ff-129">Remarks</span></span>  
 <span data-ttu-id="410ff-130">Konak bir g/ç tamamlama Özet uygularsa, CLR g/ç istek ana bilgisayar üzerinden yöntemlerini kullanarak yaptığında [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="410ff-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="410ff-131">Ana bilgisayar daha sonra çağırır `OnComplete` bu tür istekleri sonucunu çalışma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="410ff-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410ff-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="410ff-132">Requirements</span></span>  
 <span data-ttu-id="410ff-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410ff-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410ff-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="410ff-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="410ff-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="410ff-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="410ff-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410ff-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410ff-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="410ff-137">See Also</span></span>  
 [<span data-ttu-id="410ff-138">Iclrıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="410ff-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="410ff-139">Ihostıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="410ff-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="410ff-140">Ihostthreadpoolmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="410ff-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
