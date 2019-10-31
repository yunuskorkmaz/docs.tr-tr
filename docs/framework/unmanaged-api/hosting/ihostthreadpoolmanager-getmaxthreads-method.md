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
ms.openlocfilehash: e53265556de026e84af7ca345a5f82be3c5ff812
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122051"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="42572-102">IHostThreadPoolManager::GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42572-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="42572-103">Konağın iş parçacığı havuzunda eşzamanlı olarak tuttuğu en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="42572-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42572-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42572-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42572-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42572-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="42572-106">dışı Konağın iş parçacığı havuzunda sakladığı en fazla iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="42572-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42572-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="42572-107">Return Value</span></span>  
  
|<span data-ttu-id="42572-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42572-108">HRESULT</span></span>|<span data-ttu-id="42572-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42572-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42572-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="42572-110">S_OK</span></span>|<span data-ttu-id="42572-111">`GetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="42572-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="42572-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42572-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42572-113">Ortak dil çalışma zamanı (CLR (bir işleme yüklenmemiş) veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="42572-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42572-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42572-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42572-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="42572-115">The call timed out.</span></span>|  
|<span data-ttu-id="42572-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42572-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42572-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="42572-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42572-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42572-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42572-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="42572-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42572-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="42572-120">E_FAIL</span></span>|<span data-ttu-id="42572-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="42572-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42572-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="42572-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42572-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="42572-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="42572-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="42572-124">E_NOTIMPL</span></span>|<span data-ttu-id="42572-125">Ana bilgisayar `GetMaxThreads`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="42572-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42572-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42572-126">Remarks</span></span>  
 <span data-ttu-id="42572-127">CLR, iş parçacığı havuzundaki toplam iş parçacığı sayısını belirlemede `GetMaxThreads` çağırır.</span><span class="sxs-lookup"><span data-stu-id="42572-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="42572-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) yöntemi şu anda iş öğelerini işlemeyen iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="42572-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="42572-129">`pdwMaxWorkerThreads` parametresinin döndürülen değeri üzerindeki tüm istekler, iş parçacıkları kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="42572-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="42572-130">Ana bilgisayar bir `GetMaxThreads`uygulamasını sağlamıyorsa, E_NOTIMPL bir HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="42572-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42572-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42572-131">Requirements</span></span>  
 <span data-ttu-id="42572-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42572-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42572-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="42572-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42572-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="42572-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42572-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42572-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42572-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42572-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="42572-137">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42572-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="42572-138">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42572-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="42572-139">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42572-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
