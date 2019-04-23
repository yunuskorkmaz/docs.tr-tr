---
title: IHostIoCompletionManager::GetAvailableThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e96a12bbf9c4fdc8a0bc79661070eb7fec1a593
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123986"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="2f351-102">IHostIoCompletionManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f351-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="2f351-103">Şu anda isteklere hizmet değil, konak tarafından yönetilen iş parçacıkları toplam sayısı g/ç Tamamlama iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2f351-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f351-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f351-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f351-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f351-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="2f351-106">[out] Hizmet istekleri için şu anda kullanılabilir olan ana bilgisayar tarafından yönetilen g/ç Tamamlama iş parçacığı sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f351-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f351-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2f351-107">Return Value</span></span>  
  
|<span data-ttu-id="2f351-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f351-108">HRESULT</span></span>|<span data-ttu-id="2f351-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f351-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f351-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f351-110">S_OK</span></span>|<span data-ttu-id="2f351-111">`GetAvailableThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2f351-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2f351-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f351-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f351-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="2f351-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f351-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f351-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f351-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2f351-115">The call timed out.</span></span>|  
|<span data-ttu-id="2f351-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f351-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f351-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2f351-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f351-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f351-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f351-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2f351-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f351-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f351-120">E_FAIL</span></span>|<span data-ttu-id="2f351-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2f351-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f351-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2f351-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f351-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2f351-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2f351-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2f351-124">E_NOTIMPL</span></span>|<span data-ttu-id="2f351-125">Ana bilgisayar uygulaması sağlamaz `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="2f351-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f351-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f351-126">Remarks</span></span>  
 <span data-ttu-id="2f351-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç Tamamlama iş parçacığı havuzunun boyutunu üzerinde tek denetim isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f351-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="2f351-128">Bu nedenle, konak uygulamak için gerekli değildir `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="2f351-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="2f351-129">Bu durumda, konak Bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="2f351-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f351-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f351-130">Requirements</span></span>  
 <span data-ttu-id="2f351-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f351-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f351-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2f351-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f351-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2f351-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f351-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f351-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f351-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f351-135">See also</span></span>

- [<span data-ttu-id="2f351-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f351-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="2f351-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f351-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
