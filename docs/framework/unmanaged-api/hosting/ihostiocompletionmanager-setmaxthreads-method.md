---
title: "IHostIoCompletionManager::SetMaxThreads Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 084cbf5509583a45f09bcf903e833f4890c5651e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="4f807-102">IHostIoCompletionManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f807-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="4f807-103">G/ç istekleri konak allots iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f807-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f807-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f807-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f807-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f807-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="4f807-106">[in] G/ç istekleri paylaştırmak için iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="4f807-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f807-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4f807-107">Return Value</span></span>  
  
|<span data-ttu-id="4f807-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f807-108">HRESULT</span></span>|<span data-ttu-id="4f807-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f807-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f807-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f807-110">S_OK</span></span>|<span data-ttu-id="4f807-111">`SetMaxThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4f807-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4f807-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f807-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f807-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4f807-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4f807-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4f807-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4f807-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4f807-115">The call timed out.</span></span>|  
|<span data-ttu-id="4f807-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4f807-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4f807-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4f807-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4f807-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4f807-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4f807-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4f807-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4f807-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f807-120">E_FAIL</span></span>|<span data-ttu-id="4f807-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4f807-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4f807-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4f807-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4f807-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f807-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4f807-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4f807-124">E_NOTIMPL</span></span>|<span data-ttu-id="4f807-125">Ana bilgisayar uygulaması sağlamaz `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="4f807-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f807-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f807-126">Remarks</span></span>  
 <span data-ttu-id="4f807-127">`SetMaxThreads`CLR g/ç bağlantı noktasındaki isteklere hizmet kullanılabilir iş parçacıklarının sayısını ayarlamak için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="4f807-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="4f807-128">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzunun boyutunu özel denetime gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4f807-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="4f807-129">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="4f807-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="4f807-130">Bu durumda, bir konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="4f807-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f807-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f807-131">Requirements</span></span>  
 <span data-ttu-id="4f807-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f807-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f807-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f807-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f807-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4f807-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f807-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f807-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f807-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f807-136">See Also</span></span>  
 [<span data-ttu-id="4f807-137">Iclrıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f807-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="4f807-138">Ihostıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f807-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
