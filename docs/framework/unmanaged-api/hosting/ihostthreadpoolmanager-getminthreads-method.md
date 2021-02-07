---
description: 'Şu konuda daha fazla bilgi edinin: IHostThreadPoolManager:: GetMinThreads Yöntemi'
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
ms.openlocfilehash: 2ebb828f9bc6230b4b0237aa1494f428a1834139
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728403"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="f0178-103">IHostThreadPoolManager::GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0178-103">IHostThreadPoolManager::GetMinThreads Method</span></span>

<span data-ttu-id="f0178-104">Olasılığına of istekleri içinde, konağın iş parçacığı havuzunda sakladığı en az boş iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f0178-104">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0178-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0178-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0178-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0178-106">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="f0178-107">dışı Konağın Şu anda koruduğu en az sayıda boştaki çalışan iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f0178-107">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0178-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f0178-108">Return Value</span></span>  
  
|<span data-ttu-id="f0178-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0178-109">HRESULT</span></span>|<span data-ttu-id="f0178-110">Description</span><span class="sxs-lookup"><span data-stu-id="f0178-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0178-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0178-111">S_OK</span></span>|<span data-ttu-id="f0178-112">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f0178-112">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f0178-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0178-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0178-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f0178-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0178-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0178-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0178-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f0178-116">The call timed out.</span></span>|  
|<span data-ttu-id="f0178-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0178-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0178-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0178-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0178-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0178-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0178-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f0178-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0178-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0178-121">E_FAIL</span></span>|<span data-ttu-id="f0178-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f0178-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0178-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f0178-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0178-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0178-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f0178-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f0178-125">E_NOTIMPL</span></span>|<span data-ttu-id="f0178-126">Konak, uygulamasının bir uygulamasını sağlamaz `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="f0178-126">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0178-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0178-127">Remarks</span></span>  

 <span data-ttu-id="f0178-128">Uygulamasının uygulamasını sağlaması için konak gerekli değildir `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="f0178-128">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="f0178-129">Bu durumda, E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f0178-129">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0178-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0178-130">Requirements</span></span>  

 <span data-ttu-id="f0178-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0178-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0178-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0178-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0178-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f0178-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0178-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0178-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0178-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0178-135">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="f0178-136">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0178-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="f0178-137">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0178-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="f0178-138">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0178-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
