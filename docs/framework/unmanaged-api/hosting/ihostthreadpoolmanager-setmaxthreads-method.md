---
title: "IHostThreadPoolManager::SetMaxThreads Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69465029deb1db191c28313fb9a260d3c5ba5289
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="0d4e1-102">IHostThreadPoolManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d4e1-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="0d4e1-103">Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d4e1-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d4e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d4e1-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="0d4e1-106">İş parçacığı havuzu çalışan iş parçacıkları sayısı.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d4e1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d4e1-107">Return Value</span></span>  
  
|<span data-ttu-id="0d4e1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d4e1-108">HRESULT</span></span>|<span data-ttu-id="0d4e1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d4e1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d4e1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d4e1-110">S_OK</span></span>|<span data-ttu-id="0d4e1-111">`SetMaxThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0d4e1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0d4e1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0d4e1-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0d4e1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0d4e1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0d4e1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-115">The call timed out.</span></span>|  
|<span data-ttu-id="0d4e1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0d4e1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0d4e1-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0d4e1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0d4e1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0d4e1-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0d4e1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0d4e1-120">E_FAIL</span></span>|<span data-ttu-id="0d4e1-121">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0d4e1-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0d4e1-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0d4e1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0d4e1-124">E_NOTIMPL</span></span>|<span data-ttu-id="0d4e1-125">Ana bilgisayar uygulaması sağlamaz `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d4e1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d4e1-126">Remarks</span></span>  
 <span data-ttu-id="0d4e1-127">Bir ana iş parçacığı havuzunun boyutunu yapılandırmak CLR izin vermek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="0d4e1-128">Bazı ana bilgisayarlar, uygulama, performans ve ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzu üzerinde özel denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0d4e1-129">Bu durumda, bir konak E_NOTIMPL HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d4e1-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d4e1-130">Requirements</span></span>  
 <span data-ttu-id="0d4e1-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d4e1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d4e1-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d4e1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d4e1-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0d4e1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d4e1-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d4e1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4e1-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d4e1-135">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="0d4e1-136">GetMaxThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d4e1-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="0d4e1-137">SetMinThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d4e1-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="0d4e1-138">Ihostthreadpoolmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d4e1-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
