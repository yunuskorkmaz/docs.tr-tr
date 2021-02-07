---
description: 'Şu konuda daha fazla bilgi edinin: IHostThreadPoolManager:: SetMinThreads yöntemi'
title: IHostThreadPoolManager::SetMinThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: 00d6bd8212ee95318bbe546da80ca34bff7d1324
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753763"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="602de-103">IHostThreadPoolManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="602de-103">IHostThreadPoolManager::SetMinThreads Method</span></span>

<span data-ttu-id="602de-104">Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="602de-104">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="602de-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="602de-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="602de-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="602de-106">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="602de-107">'ndaki Konağın saklanması gereken yeni iş parçacığı sayısı alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="602de-107">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="602de-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="602de-108">Return Value</span></span>  
  
|<span data-ttu-id="602de-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="602de-109">HRESULT</span></span>|<span data-ttu-id="602de-110">Description</span><span class="sxs-lookup"><span data-stu-id="602de-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="602de-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="602de-111">S_OK</span></span>|<span data-ttu-id="602de-112">`SetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="602de-112">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="602de-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="602de-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="602de-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="602de-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="602de-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="602de-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="602de-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="602de-116">The call timed out.</span></span>|  
|<span data-ttu-id="602de-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="602de-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="602de-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="602de-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="602de-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="602de-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="602de-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="602de-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="602de-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="602de-121">E_FAIL</span></span>|<span data-ttu-id="602de-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="602de-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="602de-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="602de-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="602de-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="602de-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="602de-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="602de-125">E_NOTIMPL</span></span>|<span data-ttu-id="602de-126">Konak, uygulamasının bir uygulamasını sağlamaz `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="602de-126">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="602de-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="602de-127">Remarks</span></span>  

 <span data-ttu-id="602de-128">Uygulamasının uygulamasını sağlaması için bir konak gerekli değildir `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="602de-128">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="602de-129">Bu durumda, E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="602de-129">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="602de-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="602de-130">Requirements</span></span>  

 <span data-ttu-id="602de-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="602de-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="602de-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="602de-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="602de-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="602de-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="602de-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="602de-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602de-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="602de-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="602de-136">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="602de-136">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="602de-137">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="602de-137">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="602de-138">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="602de-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
