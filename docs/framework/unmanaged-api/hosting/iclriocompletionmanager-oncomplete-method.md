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
ms.openlocfilehash: 15119974acf74b49669e5ffbee59fbff9e5c84c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714113"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="6d937-102">ICLRIoCompletionManager::OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d937-102">ICLRIoCompletionManager::OnComplete Method</span></span>

<span data-ttu-id="6d937-103">[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin durumunun ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d937-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d937-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d937-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d937-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d937-105">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="6d937-106">'ndaki Bağlama işleminin durumunu gösteren bir HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="6d937-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="6d937-107">S_OK işlemin başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d937-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="6d937-108">HOST_E_INTERRUPTED, çağrının tamamlanmadan sona erdirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d937-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="6d937-109">E_FAIL bilinmeyen, kurtarılamaz ve çok zararlı bir hatanın oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d937-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="6d937-110">'ndaki G/ç isteğinin işlenmesi sırasında aktarılan baytların sayısı.</span><span class="sxs-lookup"><span data-stu-id="6d937-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="6d937-111">'ndaki `OVERLAPPED` Yöntemine yapılan çağrıya geçirilen yapıya yönelik bir işaretçi `IHostIoCompletionManager::Bind` .</span><span class="sxs-lookup"><span data-stu-id="6d937-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d937-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6d937-112">Return Value</span></span>  
  
|<span data-ttu-id="6d937-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d937-113">HRESULT</span></span>|<span data-ttu-id="6d937-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d937-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d937-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d937-115">S_OK</span></span>|<span data-ttu-id="6d937-116">`OnComplete` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6d937-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="6d937-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d937-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d937-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6d937-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6d937-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6d937-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6d937-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6d937-120">The call timed out.</span></span>|  
|<span data-ttu-id="6d937-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6d937-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6d937-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6d937-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6d937-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6d937-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6d937-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6d937-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6d937-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d937-125">E_FAIL</span></span>|<span data-ttu-id="6d937-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6d937-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6d937-127">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6d937-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6d937-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d937-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d937-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d937-129">Remarks</span></span>  

 <span data-ttu-id="6d937-130">Ana bilgisayar bir g/ç tamamlama soyutlama uygularsa, CLR, [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md)yöntemlerini kullanarak ana bilgisayar aracılığıyla g/ç istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="6d937-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="6d937-131">Daha sonra ana bilgisayar, `OnComplete` Bu tür isteklerin sonucunun çalışma zamanına bildirmek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6d937-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d937-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d937-132">Requirements</span></span>  

 <span data-ttu-id="6d937-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d937-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d937-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6d937-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d937-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6d937-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d937-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d937-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d937-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d937-137">See also</span></span>

- [<span data-ttu-id="6d937-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d937-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="6d937-139">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d937-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="6d937-140">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d937-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
