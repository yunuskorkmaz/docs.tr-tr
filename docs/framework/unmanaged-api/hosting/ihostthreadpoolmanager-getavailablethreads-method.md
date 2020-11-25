---
title: IHostThreadPoolManager::GetAvailableThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: 64d5ba9ad5557f99b175c277d48003529d77861c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730818"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="f24fd-102">IHostThreadPoolManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f24fd-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="f24fd-103">İş öğelerini işlemeyen iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f24fd-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f24fd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f24fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f24fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f24fd-105">Parameters</span></span>  

 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="f24fd-106">dışı İş öğelerinin Şu anda işlemeyen iş parçacığı havuzundaki iş parçacığı sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f24fd-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f24fd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f24fd-107">Return Value</span></span>  
  
|<span data-ttu-id="f24fd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f24fd-108">HRESULT</span></span>|<span data-ttu-id="f24fd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f24fd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f24fd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f24fd-110">S_OK</span></span>|<span data-ttu-id="f24fd-111">`GetAvailableThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f24fd-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f24fd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f24fd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f24fd-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f24fd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f24fd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f24fd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f24fd-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f24fd-115">The call timed out.</span></span>|  
|<span data-ttu-id="f24fd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f24fd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f24fd-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f24fd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f24fd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f24fd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f24fd-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f24fd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f24fd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f24fd-120">E_FAIL</span></span>|<span data-ttu-id="f24fd-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f24fd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f24fd-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f24fd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f24fd-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f24fd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f24fd-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f24fd-124">E_NOTIMPL</span></span>|<span data-ttu-id="f24fd-125">Konak, uygulamasının bir uygulamasını sağlamaz `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="f24fd-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f24fd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f24fd-126">Remarks</span></span>  

 <span data-ttu-id="f24fd-127">Konak uygulamasının bir uygulamasını sağlamıyorsa `GetAvailableThreads` , E_NOTIMPL BIR HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f24fd-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f24fd-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f24fd-128">Requirements</span></span>  

 <span data-ttu-id="f24fd-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f24fd-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f24fd-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f24fd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f24fd-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f24fd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f24fd-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f24fd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24fd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f24fd-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="f24fd-134">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f24fd-134">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
