---
title: IHostThreadPoolManager::GetMinThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: 54dfa2741d3b4c1b2eada75ee8d214a2d0b250a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730779"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="a7479-102">IHostThreadPoolManager::GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7479-102">IHostThreadPoolManager::GetMinThreads Method</span></span>

<span data-ttu-id="a7479-103">Olasılığına of istekleri içinde, konağın iş parçacığı havuzunda sakladığı en az boş iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a7479-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7479-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7479-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7479-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7479-105">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="a7479-106">dışı Konağın Şu anda koruduğu en az sayıda boştaki çalışan iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7479-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7479-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7479-107">Return Value</span></span>  
  
|<span data-ttu-id="a7479-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7479-108">HRESULT</span></span>|<span data-ttu-id="a7479-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7479-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7479-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7479-110">S_OK</span></span>|<span data-ttu-id="a7479-111">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a7479-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="a7479-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7479-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7479-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a7479-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7479-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7479-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7479-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a7479-115">The call timed out.</span></span>|  
|<span data-ttu-id="a7479-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7479-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7479-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7479-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7479-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7479-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7479-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a7479-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7479-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7479-120">E_FAIL</span></span>|<span data-ttu-id="a7479-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7479-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7479-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a7479-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7479-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7479-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a7479-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a7479-124">E_NOTIMPL</span></span>|<span data-ttu-id="a7479-125">Konak, uygulamasının bir uygulamasını sağlamaz `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="a7479-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7479-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7479-126">Remarks</span></span>  

 <span data-ttu-id="a7479-127">Uygulamasının uygulamasını sağlaması için konak gerekli değildir `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="a7479-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="a7479-128">Bu durumda, E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="a7479-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7479-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7479-129">Requirements</span></span>  

 <span data-ttu-id="a7479-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7479-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7479-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7479-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7479-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a7479-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7479-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7479-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7479-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7479-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="a7479-135">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7479-135">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="a7479-136">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7479-136">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="a7479-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7479-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
