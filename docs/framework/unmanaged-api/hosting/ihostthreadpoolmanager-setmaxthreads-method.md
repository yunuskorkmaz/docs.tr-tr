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
ms.openlocfilehash: 30c4ff93688396dd9a6a8086fbb53ad1c763ead0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141306"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="9f6b8-102">IHostThreadPoolManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f6b8-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="9f6b8-103">Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f6b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f6b8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f6b8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f6b8-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="9f6b8-106">İş parçacığı havuzundaki çalışan iş parçacığı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f6b8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9f6b8-107">Return Value</span></span>  
  
|<span data-ttu-id="9f6b8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f6b8-108">HRESULT</span></span>|<span data-ttu-id="9f6b8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f6b8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f6b8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f6b8-110">S_OK</span></span>|<span data-ttu-id="9f6b8-111">`SetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9f6b8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f6b8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f6b8-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9f6b8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f6b8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9f6b8-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-115">The call timed out.</span></span>|  
|<span data-ttu-id="9f6b8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9f6b8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9f6b8-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9f6b8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9f6b8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9f6b8-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9f6b8-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="9f6b8-120">E_FAIL</span></span>|<span data-ttu-id="9f6b8-121">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9f6b8-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9f6b8-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9f6b8-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9f6b8-124">E_NOTIMPL</span></span>|<span data-ttu-id="9f6b8-125">Ana bilgisayar `SetMaxThreads`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f6b8-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f6b8-126">Remarks</span></span>  
 <span data-ttu-id="9f6b8-127">CLR 'nin iş parçacığı havuzunun boyutunu yapılandırmasına izin vermek için bir konak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="9f6b8-128">Bazı konaklar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzu üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="9f6b8-129">Bu durumda, bir ana bilgisayar bir E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f6b8-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f6b8-130">Requirements</span></span>  
 <span data-ttu-id="9f6b8-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f6b8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f6b8-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9f6b8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f6b8-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9f6b8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f6b8-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f6b8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6b8-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f6b8-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="9f6b8-136">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f6b8-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="9f6b8-137">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f6b8-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="9f6b8-138">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f6b8-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
