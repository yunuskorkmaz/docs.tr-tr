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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081482"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="13e18-102">IHostThreadPoolManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e18-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="13e18-103">Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13e18-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13e18-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13e18-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13e18-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="13e18-106">İş parçacığı havuzundaki çalışan iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="13e18-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13e18-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13e18-107">Return Value</span></span>  
  
|<span data-ttu-id="13e18-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13e18-108">HRESULT</span></span>|<span data-ttu-id="13e18-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13e18-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13e18-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="13e18-110">S_OK</span></span>|`SetMaxThreads` <span data-ttu-id="13e18-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13e18-111">returned successfully.</span></span>|  
|<span data-ttu-id="13e18-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13e18-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13e18-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="13e18-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13e18-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13e18-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13e18-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="13e18-115">The call timed out.</span></span>|  
|<span data-ttu-id="13e18-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13e18-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13e18-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="13e18-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13e18-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13e18-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13e18-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="13e18-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13e18-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13e18-120">E_FAIL</span></span>|<span data-ttu-id="13e18-121">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="13e18-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="13e18-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="13e18-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13e18-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="13e18-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="13e18-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="13e18-124">E_NOTIMPL</span></span>|<span data-ttu-id="13e18-125">Ana bilgisayar uygulaması sağlamaz `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="13e18-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13e18-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13e18-126">Remarks</span></span>  
 <span data-ttu-id="13e18-127">Bir ana iş parçacığı havuzunun boyutunu yapılandırmak CLR izin vermek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="13e18-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="13e18-128">Bazı konakların, uygulama, performans ve ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzu üzerinde tek denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13e18-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="13e18-129">Bu durumda, bir konak E_NOTIMPL bir HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="13e18-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e18-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13e18-130">Requirements</span></span>  
 <span data-ttu-id="13e18-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e18-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e18-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13e18-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13e18-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13e18-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="13e18-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="13e18-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13e18-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13e18-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="13e18-136">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e18-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="13e18-137">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e18-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="13e18-138">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13e18-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
