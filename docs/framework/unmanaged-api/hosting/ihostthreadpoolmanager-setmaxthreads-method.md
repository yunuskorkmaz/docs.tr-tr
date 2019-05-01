---
title: IHostThreadPoolManager::SetMaxThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0df8d11bba870dfec880401064ec3f78f5f04e1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961284"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="febb6-102">IHostThreadPoolManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="febb6-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="febb6-103">Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="febb6-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febb6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="febb6-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="febb6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="febb6-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="febb6-106">İş parçacığı havuzundaki çalışan iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="febb6-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="febb6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="febb6-107">Return Value</span></span>  
  
|<span data-ttu-id="febb6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="febb6-108">HRESULT</span></span>|<span data-ttu-id="febb6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="febb6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="febb6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="febb6-110">S_OK</span></span>|<span data-ttu-id="febb6-111">`SetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="febb6-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="febb6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="febb6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="febb6-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="febb6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="febb6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="febb6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="febb6-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="febb6-115">The call timed out.</span></span>|  
|<span data-ttu-id="febb6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="febb6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="febb6-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="febb6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="febb6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="febb6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="febb6-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="febb6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="febb6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="febb6-120">E_FAIL</span></span>|<span data-ttu-id="febb6-121">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="febb6-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="febb6-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="febb6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="febb6-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="febb6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="febb6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="febb6-124">E_NOTIMPL</span></span>|<span data-ttu-id="febb6-125">Ana bilgisayar uygulaması sağlamaz `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="febb6-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="febb6-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="febb6-126">Remarks</span></span>  
 <span data-ttu-id="febb6-127">Bir ana iş parçacığı havuzunun boyutunu yapılandırmak CLR izin vermek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="febb6-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="febb6-128">Bazı konakların, uygulama, performans ve ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzu üzerinde tek denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="febb6-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="febb6-129">Bu durumda, bir konak E_NOTIMPL bir HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="febb6-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="febb6-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="febb6-130">Requirements</span></span>  
 <span data-ttu-id="febb6-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="febb6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="febb6-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="febb6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="febb6-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="febb6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="febb6-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="febb6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febb6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="febb6-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="febb6-136">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="febb6-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="febb6-137">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="febb6-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="febb6-138">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="febb6-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
