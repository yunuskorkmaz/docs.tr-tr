---
title: IHostThreadPoolManager::GetMinThreads Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8ee8adfb93a3e098bb6df69ad00202118bc1731e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="7865c-102">IHostThreadPoolManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="7865c-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="7865c-103">İş parçacığı havuzundaki istekleri kapatıldığını konak tutar boş iş parçacığı minimum sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7865c-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7865c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7865c-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7865c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7865c-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="7865c-106">[out] Konak şu anda tutar boşta çalışan iş parçacığı minimum sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7865c-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7865c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7865c-107">Return Value</span></span>  
  
|<span data-ttu-id="7865c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7865c-108">HRESULT</span></span>|<span data-ttu-id="7865c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7865c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7865c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7865c-110">S_OK</span></span>|<span data-ttu-id="7865c-111">`GetMinThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7865c-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="7865c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7865c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7865c-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7865c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7865c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7865c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7865c-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7865c-115">The call timed out.</span></span>|  
|<span data-ttu-id="7865c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7865c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7865c-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7865c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7865c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7865c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7865c-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7865c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7865c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7865c-120">E_FAIL</span></span>|<span data-ttu-id="7865c-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7865c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7865c-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7865c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7865c-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7865c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7865c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="7865c-124">E_NOTIMPL</span></span>|<span data-ttu-id="7865c-125">Ana bilgisayar uygulaması sağlamaz `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="7865c-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7865c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7865c-126">Remarks</span></span>  
 <span data-ttu-id="7865c-127">Ana bilgisayar uygulaması sağlamak için gerekli olmayan `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="7865c-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="7865c-128">Bu durumda, E_NOTIMPL HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="7865c-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7865c-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7865c-129">Requirements</span></span>  
 <span data-ttu-id="7865c-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7865c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7865c-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7865c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7865c-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7865c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7865c-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7865c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7865c-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7865c-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="7865c-135">GetMaxThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="7865c-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="7865c-136">SetMinThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="7865c-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="7865c-137">Ihostthreadpoolmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="7865c-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
