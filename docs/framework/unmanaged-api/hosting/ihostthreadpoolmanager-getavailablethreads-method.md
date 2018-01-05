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
ms.workload: dotnet
ms.openlocfilehash: 5151b26bad08ef8e1e3c53d649f57f79eb18d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="bea02-102">IHostThreadPoolManager::GetAvailableThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="bea02-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="bea02-103">İş öğeleri şu anda işlenmiyor iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="bea02-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea02-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bea02-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bea02-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bea02-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="bea02-106">[out] İş öğeleri şu anda işleme olmayan iş parçacıklarının iş parçacığı havuzundaki işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bea02-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bea02-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bea02-107">Return Value</span></span>  
  
|<span data-ttu-id="bea02-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bea02-108">HRESULT</span></span>|<span data-ttu-id="bea02-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bea02-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bea02-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bea02-110">S_OK</span></span>|<span data-ttu-id="bea02-111">`GetAvailableThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bea02-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="bea02-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bea02-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bea02-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bea02-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bea02-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bea02-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bea02-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bea02-115">The call timed out.</span></span>|  
|<span data-ttu-id="bea02-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bea02-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bea02-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="bea02-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bea02-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bea02-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bea02-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="bea02-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bea02-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bea02-120">E_FAIL</span></span>|<span data-ttu-id="bea02-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bea02-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bea02-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bea02-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bea02-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bea02-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bea02-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="bea02-124">E_NOTIMPL</span></span>|<span data-ttu-id="bea02-125">Ana bilgisayar uygulaması sağlamaz `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="bea02-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bea02-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bea02-126">Remarks</span></span>  
 <span data-ttu-id="bea02-127">Ana bilgisayar uygulaması sağlamıyorsa `GetAvailableThreads`, E_NOTIMPL HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="bea02-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bea02-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bea02-128">Requirements</span></span>  
 <span data-ttu-id="bea02-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bea02-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bea02-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bea02-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bea02-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bea02-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bea02-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bea02-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea02-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bea02-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="bea02-134">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bea02-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
