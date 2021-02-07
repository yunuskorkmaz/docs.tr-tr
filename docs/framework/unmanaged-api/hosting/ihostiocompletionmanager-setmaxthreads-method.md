---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: SetMaxThreads yöntemi'
title: IHostIoCompletionManager::SetMaxThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 6b36523b0b0d6cefba383d324eb23debefd7c41b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708287"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="0a721-103">IHostIoCompletionManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a721-103">IHostIoCompletionManager::SetMaxThreads Method</span></span>

<span data-ttu-id="0a721-104">Ana bilgisayar tarafından g/ç isteklerine hizmet vermek için ayrılan iş parçacığı sayısı üst sınırını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0a721-104">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a721-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a721-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a721-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a721-106">Parameters</span></span>  

 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="0a721-107">'ndaki G/ç istekleri için en fazla iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0a721-107">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a721-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a721-108">Return Value</span></span>  
  
|<span data-ttu-id="0a721-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a721-109">HRESULT</span></span>|<span data-ttu-id="0a721-110">Description</span><span class="sxs-lookup"><span data-stu-id="0a721-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a721-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a721-111">S_OK</span></span>|<span data-ttu-id="0a721-112">`SetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0a721-112">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0a721-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a721-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a721-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0a721-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a721-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a721-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a721-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0a721-116">The call timed out.</span></span>|  
|<span data-ttu-id="0a721-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a721-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a721-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0a721-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a721-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a721-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a721-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0a721-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a721-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a721-121">E_FAIL</span></span>|<span data-ttu-id="0a721-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0a721-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a721-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0a721-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a721-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a721-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0a721-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0a721-125">E_NOTIMPL</span></span>|<span data-ttu-id="0a721-126">Konak, uygulamasının bir uygulamasını sağlamaz `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="0a721-126">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a721-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a721-127">Remarks</span></span>  

 <span data-ttu-id="0a721-128">`SetMaxThreads` g/ç bağlantı noktalarında hizmet istekleri için kullanılabilen en fazla iş parçacığı sayısını ayarlamaya yönelik bir fırsatla CLR sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a721-128">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="0a721-129">Ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzunun boyutu üzerinde özel denetime sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="0a721-129">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0a721-130">Bu nedenle, konağın uygulanması gerekmez `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="0a721-130">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="0a721-131">Bu durumda, bir ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0a721-131">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a721-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a721-132">Requirements</span></span>  

 <span data-ttu-id="0a721-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a721-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a721-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a721-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a721-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0a721-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a721-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a721-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a721-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a721-137">See also</span></span>

- [<span data-ttu-id="0a721-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a721-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0a721-139">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a721-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
