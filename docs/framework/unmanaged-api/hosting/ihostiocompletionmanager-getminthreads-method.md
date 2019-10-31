---
title: IHostIoCompletionManager::GetMinThreads Metodu
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: 2506de5f04840f130fab28518f9db7b58eb6e9ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133827"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="fb778-102">IHostIoCompletionManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="fb778-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="fb778-103">Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fb778-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb778-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb778-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb778-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb778-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="fb778-106">dışı Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb778-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb778-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb778-107">Return Value</span></span>  
  
|<span data-ttu-id="fb778-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb778-108">HRESULT</span></span>|<span data-ttu-id="fb778-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb778-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb778-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb778-110">S_OK</span></span>|<span data-ttu-id="fb778-111">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fb778-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="fb778-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb778-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb778-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fb778-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb778-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb778-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb778-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fb778-115">The call timed out.</span></span>|  
|<span data-ttu-id="fb778-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb778-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb778-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fb778-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb778-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb778-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb778-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fb778-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb778-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="fb778-120">E_FAIL</span></span>|<span data-ttu-id="fb778-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fb778-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb778-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fb778-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb778-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb778-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fb778-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fb778-124">E_NOTIMPL</span></span>|<span data-ttu-id="fb778-125">Ana bilgisayar `GetMinThreads`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="fb778-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb778-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb778-126">Remarks</span></span>  
 <span data-ttu-id="fb778-127">Ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerine ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fb778-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="fb778-128">Bu nedenle, konağın `GetMinThreads`uygulamak için konak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fb778-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="fb778-129">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="fb778-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb778-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb778-130">Requirements</span></span>  
 <span data-ttu-id="fb778-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb778-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb778-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb778-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb778-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fb778-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb778-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb778-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb778-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb778-135">See also</span></span>

- [<span data-ttu-id="fb778-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb778-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="fb778-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb778-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
