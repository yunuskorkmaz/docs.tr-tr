---
title: IHostThreadPoolManager::GetAvailableThreads Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11cd8de264a332cd553ad44a35355bf45039ab84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="292ed-102">IHostThreadPoolManager::GetAvailableThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="292ed-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="292ed-103">İş öğeleri şu anda işlenmiyor iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="292ed-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="292ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="292ed-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="292ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="292ed-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="292ed-106">[out] İş öğeleri şu anda işleme olmayan iş parçacıklarının iş parçacığı havuzundaki işaretçi.</span><span class="sxs-lookup"><span data-stu-id="292ed-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="292ed-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="292ed-107">Return Value</span></span>  
  
|<span data-ttu-id="292ed-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="292ed-108">HRESULT</span></span>|<span data-ttu-id="292ed-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="292ed-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="292ed-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="292ed-110">S_OK</span></span>|<span data-ttu-id="292ed-111">`GetAvailableThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="292ed-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="292ed-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="292ed-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="292ed-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="292ed-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="292ed-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="292ed-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="292ed-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="292ed-115">The call timed out.</span></span>|  
|<span data-ttu-id="292ed-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="292ed-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="292ed-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="292ed-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="292ed-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="292ed-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="292ed-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="292ed-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="292ed-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="292ed-120">E_FAIL</span></span>|<span data-ttu-id="292ed-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="292ed-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="292ed-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="292ed-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="292ed-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="292ed-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="292ed-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="292ed-124">E_NOTIMPL</span></span>|<span data-ttu-id="292ed-125">Ana bilgisayar uygulaması sağlamaz `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="292ed-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="292ed-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="292ed-126">Remarks</span></span>  
 <span data-ttu-id="292ed-127">Ana bilgisayar uygulaması sağlamıyorsa `GetAvailableThreads`, E_NOTIMPL HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="292ed-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="292ed-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="292ed-128">Requirements</span></span>  
 <span data-ttu-id="292ed-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="292ed-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="292ed-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="292ed-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="292ed-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="292ed-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="292ed-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="292ed-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292ed-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="292ed-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="292ed-134">Ihostthreadpoolmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="292ed-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
