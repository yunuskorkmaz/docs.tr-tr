---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: SetMinThreads yöntemi'
title: IHostIoCompletionManager::SetMinThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: aade5ebb9e318d51296e52e7cf1c31c6ea9e4f6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708248"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="f0406-103">IHostIoCompletionManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0406-103">IHostIoCompletionManager::SetMinThreads Method</span></span>

<span data-ttu-id="f0406-104">Ana bilgisayarın g/ç tamamlama için en az sayıda iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0406-104">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0406-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0406-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0406-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0406-106">Parameters</span></span>  

 `dwMinIoCompletionThreads`  
 <span data-ttu-id="f0406-107">'ndaki Konağın oluşturması gereken en düşük g/ç Tamamlama iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="f0406-107">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0406-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f0406-108">Return Value</span></span>  
  
|<span data-ttu-id="f0406-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0406-109">HRESULT</span></span>|<span data-ttu-id="f0406-110">Description</span><span class="sxs-lookup"><span data-stu-id="f0406-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0406-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0406-111">S_OK</span></span>|<span data-ttu-id="f0406-112">`SetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f0406-112">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f0406-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0406-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0406-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f0406-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0406-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0406-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0406-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f0406-116">The call timed out.</span></span>|  
|<span data-ttu-id="f0406-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0406-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0406-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0406-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0406-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0406-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0406-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f0406-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0406-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0406-121">E_FAIL</span></span>|<span data-ttu-id="f0406-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f0406-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0406-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f0406-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0406-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0406-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f0406-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f0406-125">E_NOTIMPL</span></span>|<span data-ttu-id="f0406-126">Konak, uygulamasının bir uygulamasını sağlamaz `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="f0406-126">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0406-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0406-127">Remarks</span></span>  

 <span data-ttu-id="f0406-128">Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerini işlemek için ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0406-128">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="f0406-129">Bu nedenle, konağın uygulanması gerekmez `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="f0406-129">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="f0406-130">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f0406-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0406-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0406-131">Requirements</span></span>  

 <span data-ttu-id="f0406-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0406-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0406-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0406-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0406-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f0406-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0406-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0406-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0406-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0406-136">See also</span></span>

- [<span data-ttu-id="f0406-137">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0406-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f0406-138">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0406-138">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="f0406-139">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0406-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
