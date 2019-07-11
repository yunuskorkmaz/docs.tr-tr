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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c79f18c1deec4183a5a736c5acf88e9a1fd8021
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749100"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="5ed0f-102">IHostThreadPoolManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ed0f-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="5ed0f-103">En az sayıda konak korumalıdır boşta iş parçacıkları istekleri olasılığına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ed0f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ed0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ed0f-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="5ed0f-106">[in] Yeni en düşük, konak korumalıdır iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ed0f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ed0f-107">Return Value</span></span>  
  
|<span data-ttu-id="5ed0f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ed0f-108">HRESULT</span></span>|<span data-ttu-id="5ed0f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ed0f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ed0f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ed0f-110">S_OK</span></span>|<span data-ttu-id="5ed0f-111">`SetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5ed0f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ed0f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ed0f-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ed0f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ed0f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ed0f-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-115">The call timed out.</span></span>|  
|<span data-ttu-id="5ed0f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ed0f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ed0f-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ed0f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ed0f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ed0f-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ed0f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ed0f-120">E_FAIL</span></span>|<span data-ttu-id="5ed0f-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ed0f-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ed0f-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5ed0f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5ed0f-124">E_NOTIMPL</span></span>|<span data-ttu-id="5ed0f-125">Ana bilgisayar uygulaması sağlamaz `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ed0f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ed0f-126">Remarks</span></span>  
 <span data-ttu-id="5ed0f-127">Bir konağa bir uygulamasını sağlamak için gerekli olmayan `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="5ed0f-128">Bu durumda, bir E_NOTIMPL HRESULT değerini döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed0f-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ed0f-129">Requirements</span></span>  
 <span data-ttu-id="5ed0f-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed0f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed0f-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ed0f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ed0f-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5ed0f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ed0f-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed0f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed0f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ed0f-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="5ed0f-135">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ed0f-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="5ed0f-136">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ed0f-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="5ed0f-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ed0f-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
