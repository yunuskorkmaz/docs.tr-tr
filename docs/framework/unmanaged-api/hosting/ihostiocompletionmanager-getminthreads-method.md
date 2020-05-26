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
ms.openlocfilehash: e748a731f2c6934f58a1cd838cc40ce4fd0e4652
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804729"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="8a31c-102">IHostIoCompletionManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="8a31c-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="8a31c-103">Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8a31c-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a31c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8a31c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a31c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a31c-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="8a31c-106">dışı Ana bilgisayarın g/ç isteklerini işlemek için sağladığı en az iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8a31c-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a31c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8a31c-107">Return Value</span></span>  
  
|<span data-ttu-id="8a31c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a31c-108">HRESULT</span></span>|<span data-ttu-id="8a31c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a31c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a31c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a31c-110">S_OK</span></span>|<span data-ttu-id="8a31c-111">`GetMinThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8a31c-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8a31c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8a31c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8a31c-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8a31c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8a31c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8a31c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8a31c-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8a31c-115">The call timed out.</span></span>|  
|<span data-ttu-id="8a31c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a31c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8a31c-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8a31c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8a31c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8a31c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8a31c-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8a31c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8a31c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a31c-120">E_FAIL</span></span>|<span data-ttu-id="8a31c-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8a31c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8a31c-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8a31c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8a31c-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a31c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8a31c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8a31c-124">E_NOTIMPL</span></span>|<span data-ttu-id="8a31c-125">Konak, uygulamasının bir uygulamasını sağlamaz `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="8a31c-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a31c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a31c-126">Remarks</span></span>  
 <span data-ttu-id="8a31c-127">Ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerine ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a31c-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="8a31c-128">Bu nedenle, konağın uygulanması gerekmez `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="8a31c-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="8a31c-129">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="8a31c-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a31c-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a31c-130">Requirements</span></span>  
 <span data-ttu-id="8a31c-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a31c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a31c-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8a31c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a31c-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8a31c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a31c-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a31c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a31c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a31c-135">See also</span></span>

- [<span data-ttu-id="8a31c-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a31c-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="8a31c-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a31c-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
