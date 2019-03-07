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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0ac90729e4885f0b76e1cd78ec31a0e2e251452
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497814"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="10b54-102">IHostIoCompletionManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="10b54-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="10b54-103">En düşük g/ç istekleri işlemek için ana sağlayan iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="10b54-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10b54-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10b54-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10b54-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="10b54-106">[out] En düşük işlem g/ç istekleri konak sağlayan iş parçacığı sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="10b54-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10b54-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10b54-107">Return Value</span></span>  
  
|<span data-ttu-id="10b54-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10b54-108">HRESULT</span></span>|<span data-ttu-id="10b54-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10b54-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10b54-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10b54-110">S_OK</span></span>|<span data-ttu-id="10b54-111">`GetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="10b54-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="10b54-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10b54-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10b54-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="10b54-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10b54-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10b54-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10b54-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="10b54-115">The call timed out.</span></span>|  
|<span data-ttu-id="10b54-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10b54-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10b54-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="10b54-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10b54-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10b54-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10b54-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="10b54-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10b54-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10b54-120">E_FAIL</span></span>|<span data-ttu-id="10b54-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="10b54-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10b54-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="10b54-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10b54-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="10b54-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="10b54-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="10b54-124">E_NOTIMPL</span></span>|<span data-ttu-id="10b54-125">Ana bilgisayar uygulaması sağlamaz `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="10b54-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10b54-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10b54-126">Remarks</span></span>  
 <span data-ttu-id="10b54-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle hizmet g/ç istekleri için ayrılan iş parçacığı sayısı üzerinde tek denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10b54-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="10b54-128">Bu nedenle, konak uygulamak için gerekli değildir `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="10b54-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="10b54-129">Bu durumda, konak Bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="10b54-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10b54-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10b54-130">Requirements</span></span>  
 <span data-ttu-id="10b54-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10b54-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10b54-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10b54-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10b54-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="10b54-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10b54-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10b54-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b54-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10b54-135">See also</span></span>
- [<span data-ttu-id="10b54-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10b54-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="10b54-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10b54-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
