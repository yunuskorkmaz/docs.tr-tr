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
ms.openlocfilehash: ec323daf7c0d612d84c86c950c0c7235c7f9ebe7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485258"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="d16dc-102">IHostThreadPoolManager::GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d16dc-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="d16dc-103">İş parçacığı havuzundaki istekleri olasılığına konak tutar boşta iş parçacıkları en az sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d16dc-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d16dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d16dc-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d16dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d16dc-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="d16dc-106">[out] En az sayıda konak şu anda tutar boşta çalışan iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d16dc-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d16dc-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d16dc-107">Return Value</span></span>  
  
|<span data-ttu-id="d16dc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d16dc-108">HRESULT</span></span>|<span data-ttu-id="d16dc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d16dc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d16dc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d16dc-110">S_OK</span></span>|<span data-ttu-id="d16dc-111">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d16dc-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d16dc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d16dc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d16dc-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="d16dc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d16dc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d16dc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d16dc-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d16dc-115">The call timed out.</span></span>|  
|<span data-ttu-id="d16dc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d16dc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d16dc-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d16dc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d16dc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d16dc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d16dc-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d16dc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d16dc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d16dc-120">E_FAIL</span></span>|<span data-ttu-id="d16dc-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d16dc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d16dc-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d16dc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d16dc-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d16dc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d16dc-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d16dc-124">E_NOTIMPL</span></span>|<span data-ttu-id="d16dc-125">Ana bilgisayar uygulaması sağlamaz `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="d16dc-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d16dc-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d16dc-126">Remarks</span></span>  
 <span data-ttu-id="d16dc-127">Konak bir uygulamasını sağlamak için gerekli olmayan `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="d16dc-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="d16dc-128">Bu durumda, bir E_NOTIMPL HRESULT değerini döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d16dc-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d16dc-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d16dc-129">Requirements</span></span>  
 <span data-ttu-id="d16dc-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d16dc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d16dc-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d16dc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d16dc-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d16dc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d16dc-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d16dc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d16dc-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d16dc-134">See also</span></span>
- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="d16dc-135">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d16dc-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="d16dc-136">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d16dc-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="d16dc-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d16dc-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
