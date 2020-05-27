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
ms.openlocfilehash: c5b150b161acba3820ced367049f08153dd091aa
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842445"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="fd0a3-102">IHostThreadPoolManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd0a3-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="fd0a3-103">Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd0a3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd0a3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd0a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd0a3-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="fd0a3-106">'ndaki Konağın saklanması gereken yeni iş parçacığı sayısı alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd0a3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd0a3-107">Return Value</span></span>  
  
|<span data-ttu-id="fd0a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd0a3-108">HRESULT</span></span>|<span data-ttu-id="fd0a3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd0a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd0a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd0a3-110">S_OK</span></span>|<span data-ttu-id="fd0a3-111">`SetMinThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="fd0a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd0a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd0a3-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd0a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd0a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd0a3-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="fd0a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd0a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd0a3-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd0a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd0a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd0a3-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd0a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd0a3-120">E_FAIL</span></span>|<span data-ttu-id="fd0a3-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd0a3-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd0a3-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fd0a3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fd0a3-124">E_NOTIMPL</span></span>|<span data-ttu-id="fd0a3-125">Konak, uygulamasının bir uygulamasını sağlamaz `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="fd0a3-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd0a3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd0a3-126">Remarks</span></span>  
 <span data-ttu-id="fd0a3-127">Uygulamasının uygulamasını sağlaması için bir konak gerekli değildir `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="fd0a3-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="fd0a3-128">Bu durumda, E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd0a3-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd0a3-129">Requirements</span></span>  
 <span data-ttu-id="fd0a3-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd0a3-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd0a3-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fd0a3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd0a3-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fd0a3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd0a3-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd0a3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0a3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd0a3-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="fd0a3-135">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd0a3-135">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="fd0a3-136">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd0a3-136">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="fd0a3-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd0a3-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
