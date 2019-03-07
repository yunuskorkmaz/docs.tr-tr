---
title: IHostThreadPoolManager::GetMaxThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8758bd416b721a95f48b8c8edb933cf617e13455
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466507"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="2b152-102">IHostThreadPoolManager::GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b152-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="2b152-103">Konak tutan iş parçacığı sayısı, iş parçacığı havuzundaki eşzamanlı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2b152-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b152-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b152-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b152-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b152-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="2b152-106">[out] Ana iş parçacığı havuzundaki tutan iş parçacığı sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b152-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b152-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b152-107">Return Value</span></span>  
  
|<span data-ttu-id="2b152-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b152-108">HRESULT</span></span>|<span data-ttu-id="2b152-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b152-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b152-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b152-110">S_OK</span></span>|<span data-ttu-id="2b152-111">`GetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2b152-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2b152-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b152-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b152-113">Ortak dil çalışma zamanı (CLR (bir işleme, yüklenmemiş veya CLR bir durumda, BT başarıyla yönetilen kod veya çağrı işlemi çalıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2b152-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b152-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b152-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b152-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2b152-115">The call timed out.</span></span>|  
|<span data-ttu-id="2b152-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b152-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b152-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2b152-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b152-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b152-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b152-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2b152-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b152-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b152-120">E_FAIL</span></span>|<span data-ttu-id="2b152-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2b152-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b152-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2b152-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b152-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b152-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2b152-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2b152-124">E_NOTIMPL</span></span>|<span data-ttu-id="2b152-125">Ana bilgisayar uygulaması sağlamaz `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="2b152-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b152-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b152-126">Remarks</span></span>  
 <span data-ttu-id="2b152-127">CLR çağrıları `GetMaxThreads` toplam iş parçacığı havuzundaki iş parçacığı sayısını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="2b152-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="2b152-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) yöntemi iş öğeleri şu anda işleme değil iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2b152-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="2b152-129">Tüm istekleri yukarıda döndürülen değeri `pdwMaxWorkerThreads` iş parçacığı kullanılabilir hale kadar parametre sıraya alınan kalır.</span><span class="sxs-lookup"><span data-stu-id="2b152-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="2b152-130">Ana bilgisayar uygulaması sağlamıyorsa `GetMaxThreads`, E_NOTIMPL bir HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="2b152-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b152-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b152-131">Requirements</span></span>  
 <span data-ttu-id="2b152-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b152-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b152-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b152-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b152-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2b152-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b152-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b152-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b152-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b152-136">See also</span></span>
- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="2b152-137">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b152-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="2b152-138">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b152-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="2b152-139">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b152-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
