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
ms.openlocfilehash: 5fd37546c63ef5e5f25686e105247555dfeb132a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222789"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="ac9f4-102">IHostIoCompletionManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac9f4-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="ac9f4-103">En az sayıda konak paylaştırmak iş parçacıkları için g/ç tamamlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac9f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac9f4-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac9f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac9f4-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="ac9f4-106">[in] Konak oluşturmalısınız g/ç Tamamlama iş parçacıklarını en küçük sayısı.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac9f4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac9f4-107">Return Value</span></span>  
  
|<span data-ttu-id="ac9f4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac9f4-108">HRESULT</span></span>|<span data-ttu-id="ac9f4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac9f4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac9f4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac9f4-110">S_OK</span></span>|`SetMinThreads` <span data-ttu-id="ac9f4-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-111">returned successfully.</span></span>|  
|<span data-ttu-id="ac9f4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac9f4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac9f4-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac9f4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac9f4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac9f4-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-115">The call timed out.</span></span>|  
|<span data-ttu-id="ac9f4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac9f4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac9f4-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac9f4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac9f4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac9f4-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac9f4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac9f4-120">E_FAIL</span></span>|<span data-ttu-id="ac9f4-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac9f4-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac9f4-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ac9f4-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ac9f4-124">E_NOTIMPL</span></span>|<span data-ttu-id="ac9f4-125">Ana bilgisayar uygulaması sağlamaz `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac9f4-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac9f4-126">Remarks</span></span>  
 <span data-ttu-id="ac9f4-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç istekleri işlemek için ayrılan iş parçacığı sayısı üzerinde tek denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="ac9f4-128">Bu nedenle, konak uygulamak için gerekli değildir `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="ac9f4-129">Bu durumda, konak Bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac9f4-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac9f4-130">Requirements</span></span>  
 <span data-ttu-id="ac9f4-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac9f4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac9f4-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac9f4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac9f4-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ac9f4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ac9f4-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ac9f4-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ac9f4-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac9f4-135">See also</span></span>

- [<span data-ttu-id="ac9f4-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac9f4-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="ac9f4-137">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac9f4-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="ac9f4-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac9f4-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
