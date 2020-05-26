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
ms.openlocfilehash: a05cfb43b5b4a328d22c4df04049a7fa156ca080
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841938"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="d0753-102">IHostThreadPoolManager::GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0753-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="d0753-103">Olasılığına of istekleri içinde, konağın iş parçacığı havuzunda sakladığı en az boş iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d0753-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0753-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d0753-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0753-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0753-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="d0753-106">dışı Konağın Şu anda koruduğu en az sayıda boştaki çalışan iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0753-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0753-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0753-107">Return Value</span></span>  
  
|<span data-ttu-id="d0753-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0753-108">HRESULT</span></span>|<span data-ttu-id="d0753-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0753-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0753-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0753-110">S_OK</span></span>|<span data-ttu-id="d0753-111">`GetMinThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d0753-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d0753-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0753-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0753-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d0753-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0753-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0753-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0753-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d0753-115">The call timed out.</span></span>|  
|<span data-ttu-id="d0753-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0753-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0753-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d0753-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0753-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0753-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0753-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d0753-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0753-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0753-120">E_FAIL</span></span>|<span data-ttu-id="d0753-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d0753-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0753-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d0753-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0753-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0753-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d0753-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d0753-124">E_NOTIMPL</span></span>|<span data-ttu-id="d0753-125">Konak, uygulamasının bir uygulamasını sağlamaz `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="d0753-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0753-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0753-126">Remarks</span></span>  
 <span data-ttu-id="d0753-127">Uygulamasının uygulamasını sağlaması için konak gerekli değildir `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="d0753-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="d0753-128">Bu durumda, E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0753-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0753-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0753-129">Requirements</span></span>  
 <span data-ttu-id="d0753-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0753-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0753-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d0753-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0753-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d0753-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0753-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0753-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0753-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0753-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="d0753-135">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0753-135">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="d0753-136">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0753-136">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="d0753-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0753-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
