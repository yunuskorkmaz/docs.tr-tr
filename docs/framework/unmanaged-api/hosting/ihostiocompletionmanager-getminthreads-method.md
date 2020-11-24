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
ms.openlocfilehash: d321ce08edf4780fc5f26ac627849b9129c2f283
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673234"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="0ab85-102">IHostIoCompletionManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="0ab85-102">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="0ab85-103">Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0ab85-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab85-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0ab85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ab85-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ab85-105">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="0ab85-106">dışı Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0ab85-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ab85-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ab85-107">Return Value</span></span>  
  
|<span data-ttu-id="0ab85-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ab85-108">HRESULT</span></span>|<span data-ttu-id="0ab85-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ab85-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ab85-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ab85-110">S_OK</span></span>|<span data-ttu-id="0ab85-111">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0ab85-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0ab85-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ab85-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ab85-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0ab85-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ab85-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ab85-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ab85-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0ab85-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ab85-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ab85-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ab85-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ab85-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ab85-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ab85-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ab85-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0ab85-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ab85-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ab85-120">E_FAIL</span></span>|<span data-ttu-id="0ab85-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0ab85-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ab85-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ab85-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ab85-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ab85-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ab85-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0ab85-124">E_NOTIMPL</span></span>|<span data-ttu-id="0ab85-125">Konak, uygulamasının bir uygulamasını sağlamaz `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="0ab85-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ab85-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ab85-126">Remarks</span></span>  

 <span data-ttu-id="0ab85-127">Ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerine ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ab85-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0ab85-128">Bu nedenle, konağın uygulanması gerekmez `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="0ab85-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="0ab85-129">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0ab85-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ab85-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ab85-130">Requirements</span></span>  

 <span data-ttu-id="0ab85-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ab85-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ab85-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ab85-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ab85-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0ab85-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ab85-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ab85-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab85-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ab85-135">See also</span></span>

- [<span data-ttu-id="0ab85-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ab85-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0ab85-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ab85-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
