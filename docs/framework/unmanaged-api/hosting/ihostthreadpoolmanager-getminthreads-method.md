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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f4c2ea6deadeb0e9e1869a4ab064f2a948a74f4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749210"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="14ccc-102">IHostThreadPoolManager::GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14ccc-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="14ccc-103">İş parçacığı havuzundaki istekleri olasılığına konak tutar boşta iş parçacıkları en az sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="14ccc-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ccc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14ccc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14ccc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14ccc-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="14ccc-106">[out] En az sayıda konak şu anda tutar boşta çalışan iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="14ccc-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14ccc-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="14ccc-107">Return Value</span></span>  
  
|<span data-ttu-id="14ccc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14ccc-108">HRESULT</span></span>|<span data-ttu-id="14ccc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14ccc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14ccc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="14ccc-110">S_OK</span></span>|<span data-ttu-id="14ccc-111">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="14ccc-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="14ccc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14ccc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14ccc-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="14ccc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="14ccc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="14ccc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="14ccc-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="14ccc-115">The call timed out.</span></span>|  
|<span data-ttu-id="14ccc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="14ccc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="14ccc-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="14ccc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="14ccc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="14ccc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="14ccc-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="14ccc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="14ccc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14ccc-120">E_FAIL</span></span>|<span data-ttu-id="14ccc-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="14ccc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="14ccc-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="14ccc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="14ccc-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="14ccc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="14ccc-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="14ccc-124">E_NOTIMPL</span></span>|<span data-ttu-id="14ccc-125">Ana bilgisayar uygulaması sağlamaz `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="14ccc-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14ccc-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14ccc-126">Remarks</span></span>  
 <span data-ttu-id="14ccc-127">Konak bir uygulamasını sağlamak için gerekli olmayan `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="14ccc-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="14ccc-128">Bu durumda, bir E_NOTIMPL HRESULT değerini döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="14ccc-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14ccc-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14ccc-129">Requirements</span></span>  
 <span data-ttu-id="14ccc-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14ccc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14ccc-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="14ccc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14ccc-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="14ccc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14ccc-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14ccc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ccc-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14ccc-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="14ccc-135">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14ccc-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="14ccc-136">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14ccc-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="14ccc-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14ccc-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
