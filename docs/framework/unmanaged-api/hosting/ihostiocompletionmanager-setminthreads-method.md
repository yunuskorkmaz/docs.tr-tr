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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55570050a4053eac6327f9d7887c2fcd08eceab7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780732"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="5737f-102">IHostIoCompletionManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5737f-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="5737f-103">En az sayıda konak paylaştırmak iş parçacıkları için g/ç tamamlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5737f-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5737f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5737f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5737f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5737f-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="5737f-106">[in] Konak oluşturmalısınız g/ç Tamamlama iş parçacıklarını en küçük sayısı.</span><span class="sxs-lookup"><span data-stu-id="5737f-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5737f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5737f-107">Return Value</span></span>  
  
|<span data-ttu-id="5737f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5737f-108">HRESULT</span></span>|<span data-ttu-id="5737f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5737f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5737f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5737f-110">S_OK</span></span>|<span data-ttu-id="5737f-111">`SetMinThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5737f-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5737f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5737f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5737f-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="5737f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5737f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5737f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5737f-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5737f-115">The call timed out.</span></span>|  
|<span data-ttu-id="5737f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5737f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5737f-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5737f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5737f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5737f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5737f-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="5737f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5737f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5737f-120">E_FAIL</span></span>|<span data-ttu-id="5737f-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5737f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5737f-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5737f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5737f-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5737f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5737f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5737f-124">E_NOTIMPL</span></span>|<span data-ttu-id="5737f-125">Ana bilgisayar uygulaması sağlamaz `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5737f-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5737f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5737f-126">Remarks</span></span>  
 <span data-ttu-id="5737f-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç istekleri işlemek için ayrılan iş parçacığı sayısı üzerinde tek denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5737f-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="5737f-128">Bu nedenle, konak uygulamak için gerekli değildir `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5737f-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="5737f-129">Bu durumda, konak Bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="5737f-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5737f-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5737f-130">Requirements</span></span>  
 <span data-ttu-id="5737f-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5737f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5737f-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5737f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5737f-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5737f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5737f-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5737f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5737f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5737f-135">See also</span></span>

- [<span data-ttu-id="5737f-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5737f-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="5737f-137">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5737f-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="5737f-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5737f-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
