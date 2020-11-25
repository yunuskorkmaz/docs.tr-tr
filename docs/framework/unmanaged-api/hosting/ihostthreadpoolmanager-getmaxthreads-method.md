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
ms.openlocfilehash: 3aecebe2803d3a795db801491d0f60a5eb7c00ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730792"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="bc0ea-102">IHostThreadPoolManager::GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc0ea-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>

<span data-ttu-id="bc0ea-103">Konağın iş parçacığı havuzunda eşzamanlı olarak tuttuğu en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0ea-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bc0ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc0ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc0ea-105">Parameters</span></span>  

 `pdwMaxWorkerThreads`  
 <span data-ttu-id="bc0ea-106">dışı Konağın iş parçacığı havuzunda sakladığı en fazla iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc0ea-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc0ea-107">Return Value</span></span>  
  
|<span data-ttu-id="bc0ea-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc0ea-108">HRESULT</span></span>|<span data-ttu-id="bc0ea-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc0ea-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc0ea-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc0ea-110">S_OK</span></span>|<span data-ttu-id="bc0ea-111">`GetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="bc0ea-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc0ea-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc0ea-113">Ortak dil çalışma zamanı (CLR (bir işleme yüklenmemiş) veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bc0ea-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc0ea-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc0ea-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-115">The call timed out.</span></span>|  
|<span data-ttu-id="bc0ea-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc0ea-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc0ea-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc0ea-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc0ea-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc0ea-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc0ea-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc0ea-120">E_FAIL</span></span>|<span data-ttu-id="bc0ea-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc0ea-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc0ea-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bc0ea-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="bc0ea-124">E_NOTIMPL</span></span>|<span data-ttu-id="bc0ea-125">Konak, uygulamasının bir uygulamasını sağlamaz `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="bc0ea-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc0ea-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc0ea-126">Remarks</span></span>  

 <span data-ttu-id="bc0ea-127">CLR, `GetMaxThreads` iş parçacığı havuzundaki toplam iş parçacığı sayısını belirlemede çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="bc0ea-128">[GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) yöntemi şu anda iş öğelerini işlemeyen iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-128">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="bc0ea-129">Parametrenin döndürülen değerinin üzerindeki tüm istekler, `pdwMaxWorkerThreads` iş parçacıkları kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="bc0ea-130">Konak uygulamasının bir uygulamasını sağlamıyorsa `GetMaxThreads` , E_NOTIMPL BIR HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0ea-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc0ea-131">Requirements</span></span>  

 <span data-ttu-id="bc0ea-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc0ea-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc0ea-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc0ea-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc0ea-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bc0ea-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc0ea-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0ea-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0ea-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc0ea-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="bc0ea-137">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc0ea-137">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="bc0ea-138">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc0ea-138">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="bc0ea-139">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc0ea-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
