---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: GetMinThreads Yöntemi'
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
ms.openlocfilehash: 73b8d8cbff3777fe6aa956f282d3da5d4ac1b5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708527"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="5c15d-103">IHostIoCompletionManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="5c15d-103">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="5c15d-104">Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5c15d-104">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c15d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c15d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c15d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c15d-106">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="5c15d-107">dışı Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5c15d-107">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c15d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c15d-108">Return Value</span></span>  
  
|<span data-ttu-id="5c15d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c15d-109">HRESULT</span></span>|<span data-ttu-id="5c15d-110">Description</span><span class="sxs-lookup"><span data-stu-id="5c15d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c15d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c15d-111">S_OK</span></span>|<span data-ttu-id="5c15d-112">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5c15d-112">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5c15d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c15d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c15d-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5c15d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c15d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c15d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c15d-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5c15d-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c15d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c15d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c15d-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5c15d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c15d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c15d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c15d-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5c15d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c15d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c15d-121">E_FAIL</span></span>|<span data-ttu-id="5c15d-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5c15d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c15d-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5c15d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c15d-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c15d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5c15d-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5c15d-125">E_NOTIMPL</span></span>|<span data-ttu-id="5c15d-126">Konak, uygulamasının bir uygulamasını sağlamaz `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="5c15d-126">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c15d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c15d-127">Remarks</span></span>  

 <span data-ttu-id="5c15d-128">Ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerine ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c15d-128">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="5c15d-129">Bu nedenle, konağın uygulanması gerekmez `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="5c15d-129">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="5c15d-130">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="5c15d-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c15d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c15d-131">Requirements</span></span>  

 <span data-ttu-id="5c15d-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c15d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c15d-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5c15d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c15d-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5c15d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c15d-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c15d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c15d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c15d-136">See also</span></span>

- [<span data-ttu-id="5c15d-137">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c15d-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="5c15d-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c15d-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
