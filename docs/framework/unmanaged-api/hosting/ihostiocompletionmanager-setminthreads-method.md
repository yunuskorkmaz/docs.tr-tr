---
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
ms.openlocfilehash: 8b1fc936b601d327ce6306f22dbec2c1078718da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133728"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="9406b-102">IHostIoCompletionManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9406b-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="9406b-103">Ana bilgisayarın g/ç tamamlama için en az sayıda iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9406b-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9406b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9406b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9406b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9406b-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="9406b-106">'ndaki Konağın oluşturması gereken en düşük g/ç Tamamlama iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="9406b-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9406b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9406b-107">Return Value</span></span>  
  
|<span data-ttu-id="9406b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9406b-108">HRESULT</span></span>|<span data-ttu-id="9406b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9406b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9406b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9406b-110">S_OK</span></span>|<span data-ttu-id="9406b-111">`SetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9406b-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9406b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9406b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9406b-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9406b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9406b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9406b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9406b-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9406b-115">The call timed out.</span></span>|  
|<span data-ttu-id="9406b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9406b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9406b-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9406b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9406b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9406b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9406b-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9406b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9406b-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="9406b-120">E_FAIL</span></span>|<span data-ttu-id="9406b-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9406b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9406b-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9406b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9406b-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9406b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9406b-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9406b-124">E_NOTIMPL</span></span>|<span data-ttu-id="9406b-125">Ana bilgisayar `SetMinThreads`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="9406b-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9406b-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9406b-126">Remarks</span></span>  
 <span data-ttu-id="9406b-127">Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerini işlemek için ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9406b-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="9406b-128">Bu nedenle, konağın `SetMinThreads`uygulamak için konak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9406b-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="9406b-129">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="9406b-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9406b-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9406b-130">Requirements</span></span>  
 <span data-ttu-id="9406b-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9406b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9406b-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9406b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9406b-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9406b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9406b-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9406b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9406b-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9406b-135">See also</span></span>

- [<span data-ttu-id="9406b-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9406b-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="9406b-137">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9406b-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="9406b-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9406b-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
