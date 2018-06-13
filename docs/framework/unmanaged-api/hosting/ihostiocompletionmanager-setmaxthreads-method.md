---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a810f3a25dc90ddb234c70ca3fa5130039350136
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438827"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="1ff27-102">IHostIoCompletionManager::SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ff27-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="1ff27-103">G/ç istekleri konak allots iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1ff27-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ff27-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ff27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ff27-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="1ff27-106">[in] G/ç istekleri paylaştırmak için iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1ff27-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ff27-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ff27-107">Return Value</span></span>  
  
|<span data-ttu-id="1ff27-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ff27-108">HRESULT</span></span>|<span data-ttu-id="1ff27-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ff27-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ff27-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ff27-110">S_OK</span></span>|<span data-ttu-id="1ff27-111">`SetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1ff27-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="1ff27-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ff27-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ff27-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1ff27-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ff27-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ff27-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ff27-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1ff27-115">The call timed out.</span></span>|  
|<span data-ttu-id="1ff27-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ff27-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ff27-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="1ff27-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ff27-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ff27-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ff27-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="1ff27-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ff27-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ff27-120">E_FAIL</span></span>|<span data-ttu-id="1ff27-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1ff27-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ff27-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1ff27-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ff27-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ff27-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ff27-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1ff27-124">E_NOTIMPL</span></span>|<span data-ttu-id="1ff27-125">Ana bilgisayar uygulaması sağlamaz `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="1ff27-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff27-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ff27-126">Remarks</span></span>  
 <span data-ttu-id="1ff27-127">`SetMaxThreads` CLR g/ç bağlantı noktasındaki isteklere hizmet kullanılabilir iş parçacıklarının sayısını ayarlamak için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="1ff27-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="1ff27-128">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzunun boyutunu özel denetime gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1ff27-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="1ff27-129">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="1ff27-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="1ff27-130">Bu durumda, bir konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="1ff27-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff27-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ff27-131">Requirements</span></span>  
 <span data-ttu-id="1ff27-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ff27-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff27-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ff27-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ff27-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1ff27-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ff27-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff27-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff27-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ff27-136">See Also</span></span>  
 [<span data-ttu-id="1ff27-137">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ff27-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="1ff27-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ff27-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
