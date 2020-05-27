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
ms.openlocfilehash: 53d42afda6668acc6462c419fcefd6bc1435a34c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842458"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="fdf33-102">IHostThreadPoolManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdf33-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="fdf33-103">Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fdf33-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf33-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fdf33-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdf33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdf33-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="fdf33-106">İş parçacığı havuzundaki çalışan iş parçacığı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="fdf33-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdf33-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fdf33-107">Return Value</span></span>  
  
|<span data-ttu-id="fdf33-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdf33-108">HRESULT</span></span>|<span data-ttu-id="fdf33-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdf33-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdf33-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdf33-110">S_OK</span></span>|<span data-ttu-id="fdf33-111">`SetMaxThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fdf33-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="fdf33-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fdf33-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fdf33-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fdf33-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fdf33-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fdf33-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fdf33-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fdf33-115">The call timed out.</span></span>|  
|<span data-ttu-id="fdf33-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fdf33-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fdf33-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fdf33-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fdf33-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fdf33-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fdf33-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fdf33-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fdf33-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdf33-120">E_FAIL</span></span>|<span data-ttu-id="fdf33-121">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fdf33-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="fdf33-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fdf33-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fdf33-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdf33-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fdf33-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fdf33-124">E_NOTIMPL</span></span>|<span data-ttu-id="fdf33-125">Konak, uygulamasının bir uygulamasını sağlamaz `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="fdf33-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdf33-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdf33-126">Remarks</span></span>  
 <span data-ttu-id="fdf33-127">CLR 'nin iş parçacığı havuzunun boyutunu yapılandırmasına izin vermek için bir konak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fdf33-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="fdf33-128">Bazı konaklar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzu üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf33-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="fdf33-129">Bu durumda, bir ana bilgisayar E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="fdf33-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdf33-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdf33-130">Requirements</span></span>  
 <span data-ttu-id="fdf33-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdf33-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdf33-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fdf33-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdf33-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fdf33-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdf33-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdf33-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf33-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdf33-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="fdf33-136">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdf33-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="fdf33-137">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdf33-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="fdf33-138">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdf33-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
