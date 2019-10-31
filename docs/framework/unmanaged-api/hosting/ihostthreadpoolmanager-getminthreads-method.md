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
ms.openlocfilehash: ce1abb75c5135a9bb23f1ad2d2acbd40d9111b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122064"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="a02f6-102">IHostThreadPoolManager::GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a02f6-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="a02f6-103">Olasılığına of istekleri içinde, konağın iş parçacığı havuzunda sakladığı en az boş iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a02f6-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a02f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a02f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a02f6-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="a02f6-106">dışı Konağın Şu anda koruduğu en az sayıda boştaki çalışan iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a02f6-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a02f6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a02f6-107">Return Value</span></span>  
  
|<span data-ttu-id="a02f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a02f6-108">HRESULT</span></span>|<span data-ttu-id="a02f6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a02f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a02f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a02f6-110">S_OK</span></span>|<span data-ttu-id="a02f6-111">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a02f6-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="a02f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a02f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a02f6-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a02f6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a02f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a02f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a02f6-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a02f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="a02f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a02f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a02f6-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a02f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a02f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a02f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a02f6-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a02f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a02f6-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="a02f6-120">E_FAIL</span></span>|<span data-ttu-id="a02f6-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a02f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a02f6-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a02f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a02f6-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a02f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a02f6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a02f6-124">E_NOTIMPL</span></span>|<span data-ttu-id="a02f6-125">Ana bilgisayar `GetMinThreads`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="a02f6-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a02f6-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a02f6-126">Remarks</span></span>  
 <span data-ttu-id="a02f6-127">Konağın `GetMinThreads`uygulanmasını sağlamak için konağın gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a02f6-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="a02f6-128">Bu durumda, E_NOTIMPL bir HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="a02f6-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a02f6-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a02f6-129">Requirements</span></span>  
 <span data-ttu-id="a02f6-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a02f6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02f6-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a02f6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a02f6-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a02f6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a02f6-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02f6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02f6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a02f6-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="a02f6-135">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a02f6-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="a02f6-136">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a02f6-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="a02f6-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a02f6-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
