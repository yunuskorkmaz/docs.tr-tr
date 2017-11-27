---
title: IHostThreadPoolManager::GetMaxThreads Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd15b1448c23785437b3dc62562b5d96abb3601c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="2e3c7-102">IHostThreadPoolManager::GetMaxThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="2e3c7-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="2e3c7-103">Konak tutar iş parçacığı sayısı, iş parçacığı havuzundaki eşzamanlı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e3c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e3c7-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e3c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e3c7-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="2e3c7-106">[out] İş parçacığı havuzundaki konak tutar iş parçacığı sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e3c7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e3c7-107">Return Value</span></span>  
  
|<span data-ttu-id="2e3c7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e3c7-108">HRESULT</span></span>|<span data-ttu-id="2e3c7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e3c7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e3c7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e3c7-110">S_OK</span></span>|<span data-ttu-id="2e3c7-111">`GetMaxThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2e3c7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e3c7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e3c7-113">Ortak dil çalışma zamanı (CLR (bir işlemine yüklendi değil veya CLR bir kapsamda başarıyla yönetilen kod veya işlem çağrısı çalışamaz durumda.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e3c7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e3c7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e3c7-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-115">The call timed out.</span></span>|  
|<span data-ttu-id="2e3c7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e3c7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e3c7-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e3c7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e3c7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e3c7-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e3c7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e3c7-120">E_FAIL</span></span>|<span data-ttu-id="2e3c7-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e3c7-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e3c7-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2e3c7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2e3c7-124">E_NOTIMPL</span></span>|<span data-ttu-id="2e3c7-125">Ana bilgisayar uygulaması sağlamaz `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e3c7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e3c7-126">Remarks</span></span>  
 <span data-ttu-id="2e3c7-127">CLR çağrıları `GetMaxThreads` toplam iş parçacığı havuzu iş parçacığı sayısını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="2e3c7-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) yöntemi iş öğeleri şu anda işlenmiyor iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="2e3c7-129">Döndürülen değerini yukarıdaki tüm istekleri `pdwMaxWorkerThreads` iş parçacıkları kullanılabilir duruma kadar parametre sıraya alınan kalır.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="2e3c7-130">Ana bilgisayar uygulaması sağlamıyorsa `GetMaxThreads`, E_NOTIMPL HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e3c7-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e3c7-131">Requirements</span></span>  
 <span data-ttu-id="2e3c7-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e3c7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e3c7-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e3c7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e3c7-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2e3c7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e3c7-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e3c7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3c7-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="2e3c7-137">GetMinThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e3c7-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="2e3c7-138">SetMaxThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e3c7-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="2e3c7-139">Ihostthreadpoolmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e3c7-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
