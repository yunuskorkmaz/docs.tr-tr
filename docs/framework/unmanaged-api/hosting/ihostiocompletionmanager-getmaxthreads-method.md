---
title: IHostIoCompletionManager::GetMaxThreads Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e7df4acd435c767a1d0c3ae4484a236359cfb38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="092de-102">IHostIoCompletionManager::GetMaxThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="092de-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="092de-103">G/ç istekleri konak paylaştırmak iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="092de-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="092de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="092de-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="092de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="092de-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="092de-106">[out] Ana bilgisayar g/ç istekleri paylaştırmak iş parçacığı havuzu iş parçacıkları sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="092de-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="092de-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="092de-107">Return Value</span></span>  
  
|<span data-ttu-id="092de-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="092de-108">HRESULT</span></span>|<span data-ttu-id="092de-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="092de-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="092de-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="092de-110">S_OK</span></span>|<span data-ttu-id="092de-111">`GetMaxThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="092de-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="092de-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="092de-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="092de-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="092de-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="092de-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="092de-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="092de-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="092de-115">The call timed out.</span></span>|  
|<span data-ttu-id="092de-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="092de-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="092de-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="092de-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="092de-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="092de-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="092de-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="092de-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="092de-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="092de-120">E_FAIL</span></span>|<span data-ttu-id="092de-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="092de-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="092de-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="092de-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="092de-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="092de-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="092de-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="092de-124">E_NOTIMPL</span></span>|<span data-ttu-id="092de-125">Ana bilgisayar uygulaması sağlamaz `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="092de-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="092de-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="092de-126">Remarks</span></span>  
 <span data-ttu-id="092de-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç istekleri işlemek için ayrılan iş parçacığı sayısını özel denetime isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="092de-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="092de-128">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="092de-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="092de-129">Bu durumda, konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="092de-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="092de-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="092de-130">Requirements</span></span>  
 <span data-ttu-id="092de-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="092de-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="092de-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="092de-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="092de-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="092de-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="092de-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="092de-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092de-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="092de-135">See Also</span></span>  
 [<span data-ttu-id="092de-136">Iclrıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="092de-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="092de-137">Ihostıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="092de-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
