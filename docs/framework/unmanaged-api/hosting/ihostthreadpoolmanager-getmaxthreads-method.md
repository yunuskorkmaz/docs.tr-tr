---
description: 'Şu konuda daha fazla bilgi edinin: IHostThreadPoolManager:: GetMaxThreads yöntemi'
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
ms.openlocfilehash: e8cae2aa29a50ef58a5b87deba9e275a441d43ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728391"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="b1a21-103">IHostThreadPoolManager::GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1a21-103">IHostThreadPoolManager::GetMaxThreads Method</span></span>

<span data-ttu-id="b1a21-104">Konağın iş parçacığı havuzunda eşzamanlı olarak tuttuğu en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b1a21-104">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a21-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1a21-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a21-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1a21-106">Parameters</span></span>  

 `pdwMaxWorkerThreads`  
 <span data-ttu-id="b1a21-107">dışı Konağın iş parçacığı havuzunda sakladığı en fazla iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1a21-107">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1a21-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1a21-108">Return Value</span></span>  
  
|<span data-ttu-id="b1a21-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1a21-109">HRESULT</span></span>|<span data-ttu-id="b1a21-110">Description</span><span class="sxs-lookup"><span data-stu-id="b1a21-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1a21-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1a21-111">S_OK</span></span>|<span data-ttu-id="b1a21-112">`GetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b1a21-112">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b1a21-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1a21-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1a21-114">Ortak dil çalışma zamanı (CLR (bir işleme yüklenmemiş) veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b1a21-114">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1a21-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1a21-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1a21-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b1a21-116">The call timed out.</span></span>|  
|<span data-ttu-id="b1a21-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1a21-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1a21-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b1a21-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1a21-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1a21-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1a21-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b1a21-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1a21-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1a21-121">E_FAIL</span></span>|<span data-ttu-id="b1a21-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b1a21-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1a21-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b1a21-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1a21-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1a21-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1a21-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b1a21-125">E_NOTIMPL</span></span>|<span data-ttu-id="b1a21-126">Konak, uygulamasının bir uygulamasını sağlamaz `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="b1a21-126">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a21-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1a21-127">Remarks</span></span>  

 <span data-ttu-id="b1a21-128">CLR, `GetMaxThreads` iş parçacığı havuzundaki toplam iş parçacığı sayısını belirlemede çağırır.</span><span class="sxs-lookup"><span data-stu-id="b1a21-128">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="b1a21-129">[GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) yöntemi şu anda iş öğelerini işlemeyen iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b1a21-129">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="b1a21-130">Parametrenin döndürülen değerinin üzerindeki tüm istekler, `pdwMaxWorkerThreads` iş parçacıkları kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="b1a21-130">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="b1a21-131">Konak uygulamasının bir uygulamasını sağlamıyorsa `GetMaxThreads` , E_NOTIMPL BIR HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="b1a21-131">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a21-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1a21-132">Requirements</span></span>  

 <span data-ttu-id="b1a21-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a21-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a21-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1a21-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1a21-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b1a21-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1a21-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a21-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a21-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1a21-137">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="b1a21-138">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1a21-138">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="b1a21-139">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1a21-139">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="b1a21-140">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1a21-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
