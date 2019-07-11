---
title: IHostIoCompletionManager::GetMaxThreads Metodu
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fcd66914448fa63c892f7285b8cd364d4cacc5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779212"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="878f9-102">IHostIoCompletionManager::GetMaxThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="878f9-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="878f9-103">G/ç isteklerine hizmet konağı paylaştırmak iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="878f9-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="878f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="878f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="878f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="878f9-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="878f9-106">[out] Ana bilgisayar hizmeti g/ç istekleri paylaştırmak iş parçacığı havuzundaki iş parçacığı sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="878f9-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="878f9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="878f9-107">Return Value</span></span>  
  
|<span data-ttu-id="878f9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="878f9-108">HRESULT</span></span>|<span data-ttu-id="878f9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="878f9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="878f9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="878f9-110">S_OK</span></span>|<span data-ttu-id="878f9-111">`GetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="878f9-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="878f9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="878f9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="878f9-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="878f9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="878f9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="878f9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="878f9-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="878f9-115">The call timed out.</span></span>|  
|<span data-ttu-id="878f9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="878f9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="878f9-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="878f9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="878f9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="878f9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="878f9-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="878f9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="878f9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="878f9-120">E_FAIL</span></span>|<span data-ttu-id="878f9-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="878f9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="878f9-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="878f9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="878f9-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="878f9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="878f9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="878f9-124">E_NOTIMPL</span></span>|<span data-ttu-id="878f9-125">Ana bilgisayar uygulaması sağlamaz `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="878f9-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="878f9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="878f9-126">Remarks</span></span>  
 <span data-ttu-id="878f9-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç istekleri işlemek için ayrılan iş parçacığı sayısı üzerinde tek denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="878f9-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="878f9-128">Bu nedenle, konak uygulamak için gerekli değildir `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="878f9-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="878f9-129">Bu durumda, konak Bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="878f9-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="878f9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="878f9-130">Requirements</span></span>  
 <span data-ttu-id="878f9-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="878f9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="878f9-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="878f9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="878f9-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="878f9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="878f9-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="878f9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878f9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="878f9-135">See also</span></span>

- [<span data-ttu-id="878f9-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="878f9-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="878f9-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="878f9-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
