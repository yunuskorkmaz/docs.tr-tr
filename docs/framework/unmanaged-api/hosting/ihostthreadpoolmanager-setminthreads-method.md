---
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
ms.openlocfilehash: f2d2665382559596563d9b155d2afa4d99c91ee7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141262"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="6605d-102">IHostThreadPoolManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6605d-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="6605d-103">Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6605d-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6605d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6605d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6605d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6605d-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="6605d-106">'ndaki Konağın saklanması gereken yeni iş parçacığı sayısı alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="6605d-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6605d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6605d-107">Return Value</span></span>  
  
|<span data-ttu-id="6605d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6605d-108">HRESULT</span></span>|<span data-ttu-id="6605d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6605d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6605d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6605d-110">S_OK</span></span>|<span data-ttu-id="6605d-111">`SetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6605d-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="6605d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6605d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6605d-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6605d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6605d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6605d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6605d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6605d-115">The call timed out.</span></span>|  
|<span data-ttu-id="6605d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6605d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6605d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6605d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6605d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6605d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6605d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6605d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6605d-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="6605d-120">E_FAIL</span></span>|<span data-ttu-id="6605d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6605d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6605d-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6605d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6605d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6605d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6605d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="6605d-124">E_NOTIMPL</span></span>|<span data-ttu-id="6605d-125">Ana bilgisayar `SetMinThreads`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="6605d-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6605d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6605d-126">Remarks</span></span>  
 <span data-ttu-id="6605d-127">`SetMinThreads`uygulanmasını sağlamak için konağın gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6605d-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="6605d-128">Bu durumda, E_NOTIMPL bir HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="6605d-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6605d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6605d-129">Requirements</span></span>  
 <span data-ttu-id="6605d-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6605d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6605d-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6605d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6605d-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6605d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6605d-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6605d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6605d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6605d-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="6605d-135">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6605d-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="6605d-136">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6605d-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="6605d-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6605d-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
