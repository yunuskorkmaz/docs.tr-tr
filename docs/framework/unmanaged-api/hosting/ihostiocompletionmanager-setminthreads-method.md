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
ms.openlocfilehash: 64ea9fdd477ec005b089f451101b742278ab4266
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672415"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="d8304-102">IHostIoCompletionManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8304-102">IHostIoCompletionManager::SetMinThreads Method</span></span>

<span data-ttu-id="d8304-103">Ana bilgisayarın g/ç tamamlama için en az sayıda iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d8304-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8304-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d8304-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8304-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8304-105">Parameters</span></span>  

 `dwMinIoCompletionThreads`  
 <span data-ttu-id="d8304-106">'ndaki Konağın oluşturması gereken en düşük g/ç Tamamlama iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="d8304-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8304-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8304-107">Return Value</span></span>  
  
|<span data-ttu-id="d8304-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8304-108">HRESULT</span></span>|<span data-ttu-id="d8304-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8304-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8304-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8304-110">S_OK</span></span>|<span data-ttu-id="d8304-111">`SetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d8304-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d8304-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8304-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8304-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d8304-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8304-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8304-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8304-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d8304-115">The call timed out.</span></span>|  
|<span data-ttu-id="d8304-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8304-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8304-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d8304-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8304-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8304-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8304-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d8304-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8304-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8304-120">E_FAIL</span></span>|<span data-ttu-id="d8304-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d8304-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8304-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d8304-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8304-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8304-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d8304-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d8304-124">E_NOTIMPL</span></span>|<span data-ttu-id="d8304-125">Konak, uygulamasının bir uygulamasını sağlamaz `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="d8304-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8304-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8304-126">Remarks</span></span>  

 <span data-ttu-id="d8304-127">Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerini işlemek için ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8304-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="d8304-128">Bu nedenle, konağın uygulanması gerekmez `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="d8304-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="d8304-129">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d8304-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8304-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8304-130">Requirements</span></span>  

 <span data-ttu-id="d8304-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8304-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8304-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d8304-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8304-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d8304-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8304-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8304-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8304-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8304-135">See also</span></span>

- [<span data-ttu-id="d8304-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8304-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="d8304-137">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8304-137">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="d8304-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8304-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
