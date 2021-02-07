---
description: 'Şu konuda daha fazla bilgi edinin: IHostThreadPoolManager:: SetMaxThreads yöntemi'
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
ms.openlocfilehash: 83266b05f639c0aa63e492bca525cbbf09a30775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671249"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="5491e-103">IHostThreadPoolManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5491e-103">IHostThreadPoolManager::SetMaxThreads Method</span></span>

<span data-ttu-id="5491e-104">Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5491e-104">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5491e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5491e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5491e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5491e-106">Parameters</span></span>  

 `MaxThreads`  
 <span data-ttu-id="5491e-107">İş parçacığı havuzundaki çalışan iş parçacığı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="5491e-107">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5491e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5491e-108">Return Value</span></span>  
  
|<span data-ttu-id="5491e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5491e-109">HRESULT</span></span>|<span data-ttu-id="5491e-110">Description</span><span class="sxs-lookup"><span data-stu-id="5491e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5491e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5491e-111">S_OK</span></span>|<span data-ttu-id="5491e-112">`SetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5491e-112">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5491e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5491e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5491e-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5491e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5491e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5491e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5491e-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5491e-116">The call timed out.</span></span>|  
|<span data-ttu-id="5491e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5491e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5491e-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5491e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5491e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5491e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5491e-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5491e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5491e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5491e-121">E_FAIL</span></span>|<span data-ttu-id="5491e-122">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5491e-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5491e-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5491e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5491e-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5491e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5491e-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5491e-125">E_NOTIMPL</span></span>|<span data-ttu-id="5491e-126">Konak, uygulamasının bir uygulamasını sağlamaz `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="5491e-126">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5491e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5491e-127">Remarks</span></span>  

 <span data-ttu-id="5491e-128">CLR 'nin iş parçacığı havuzunun boyutunu yapılandırmasına izin vermek için bir konak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5491e-128">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="5491e-129">Bazı konaklar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzu üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5491e-129">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="5491e-130">Bu durumda, bir ana bilgisayar E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="5491e-130">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5491e-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5491e-131">Requirements</span></span>  

 <span data-ttu-id="5491e-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5491e-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5491e-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5491e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5491e-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5491e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5491e-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5491e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5491e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5491e-136">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="5491e-137">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5491e-137">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="5491e-138">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5491e-138">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="5491e-139">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5491e-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
