---
description: ': Iclriocompletionmanager:: Ontamamlanan yöntem hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d54b189debdfc2959676b53fd3fb51b2c10dce17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789896"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="98891-103">ICLRIoCompletionManager::OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98891-103">ICLRIoCompletionManager::OnComplete Method</span></span>

<span data-ttu-id="98891-104">[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin durumunun ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="98891-104">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98891-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98891-105">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98891-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98891-106">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="98891-107">'ndaki Bağlama işleminin durumunu gösteren bir HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="98891-107">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="98891-108">S_OK işlemin başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98891-108">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="98891-109">HOST_E_INTERRUPTED, çağrının tamamlanmadan sona erdirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="98891-109">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="98891-110">E_FAIL bilinmeyen, kurtarılamaz ve çok zararlı bir hatanın oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="98891-110">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="98891-111">'ndaki G/ç isteğinin işlenmesi sırasında aktarılan baytların sayısı.</span><span class="sxs-lookup"><span data-stu-id="98891-111">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="98891-112">'ndaki `OVERLAPPED` Yöntemine yapılan çağrıya geçirilen yapıya yönelik bir işaretçi `IHostIoCompletionManager::Bind` .</span><span class="sxs-lookup"><span data-stu-id="98891-112">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98891-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="98891-113">Return Value</span></span>  
  
|<span data-ttu-id="98891-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98891-114">HRESULT</span></span>|<span data-ttu-id="98891-115">Description</span><span class="sxs-lookup"><span data-stu-id="98891-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98891-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="98891-116">S_OK</span></span>|<span data-ttu-id="98891-117">`OnComplete` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="98891-117">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="98891-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98891-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98891-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="98891-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98891-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98891-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98891-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="98891-121">The call timed out.</span></span>|  
|<span data-ttu-id="98891-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98891-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98891-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="98891-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98891-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98891-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98891-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="98891-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98891-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98891-126">E_FAIL</span></span>|<span data-ttu-id="98891-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="98891-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98891-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98891-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98891-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="98891-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98891-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98891-130">Remarks</span></span>  

 <span data-ttu-id="98891-131">Ana bilgisayar bir g/ç tamamlama soyutlama uygularsa, CLR, [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md)yöntemlerini kullanarak ana bilgisayar aracılığıyla g/ç istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="98891-131">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="98891-132">Daha sonra ana bilgisayar, `OnComplete` Bu tür isteklerin sonucunun çalışma zamanına bildirmek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="98891-132">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98891-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98891-133">Requirements</span></span>  

 <span data-ttu-id="98891-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98891-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98891-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98891-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98891-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="98891-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98891-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98891-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98891-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98891-138">See also</span></span>

- [<span data-ttu-id="98891-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98891-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="98891-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98891-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="98891-141">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98891-141">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
