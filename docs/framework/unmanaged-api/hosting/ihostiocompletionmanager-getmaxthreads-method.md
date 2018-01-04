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
ms.workload: dotnet
ms.openlocfilehash: d02b0ba4802b72932ea6d23c66153c265a3d6498
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="f9838-102">IHostIoCompletionManager::GetMaxThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="f9838-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="f9838-103">G/ç istekleri konak paylaştırmak iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f9838-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9838-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9838-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9838-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9838-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="f9838-106">[out] Ana bilgisayar g/ç istekleri paylaştırmak iş parçacığı havuzu iş parçacıkları sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9838-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9838-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9838-107">Return Value</span></span>  
  
|<span data-ttu-id="f9838-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9838-108">HRESULT</span></span>|<span data-ttu-id="f9838-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9838-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9838-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9838-110">S_OK</span></span>|<span data-ttu-id="f9838-111">`GetMaxThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f9838-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f9838-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9838-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9838-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f9838-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9838-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9838-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9838-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f9838-115">The call timed out.</span></span>|  
|<span data-ttu-id="f9838-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9838-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9838-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="f9838-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9838-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9838-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9838-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="f9838-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9838-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9838-120">E_FAIL</span></span>|<span data-ttu-id="f9838-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f9838-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9838-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f9838-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9838-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9838-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f9838-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f9838-124">E_NOTIMPL</span></span>|<span data-ttu-id="f9838-125">Ana bilgisayar uygulaması sağlamaz `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="f9838-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9838-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9838-126">Remarks</span></span>  
 <span data-ttu-id="f9838-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç istekleri işlemek için ayrılan iş parçacığı sayısını özel denetime isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9838-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="f9838-128">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="f9838-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="f9838-129">Bu durumda, konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f9838-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9838-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9838-130">Requirements</span></span>  
 <span data-ttu-id="f9838-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9838-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9838-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9838-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9838-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f9838-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9838-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9838-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9838-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9838-135">See Also</span></span>  
 [<span data-ttu-id="f9838-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9838-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="f9838-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9838-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
