---
title: "IHostIoCompletionManager::CreateIoCompletionPort Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CreateIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 230d6446460af92dbc4356977c0df4556d0229a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="df44d-102">IHostIoCompletionManager::CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df44d-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="df44d-103">Ana bilgisayar yeni bir g/ç tamamlama bağlantı noktasını oluşturmak istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="df44d-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df44d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df44d-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df44d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df44d-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="df44d-106">[out] Yeni oluşturulan g/ç tamamlama bağlantı noktasını ya da 0 (sıfır), bağlantı noktası oluşturulamadı, işleyici için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="df44d-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df44d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="df44d-107">Return Value</span></span>  
  
|<span data-ttu-id="df44d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df44d-108">HRESULT</span></span>|<span data-ttu-id="df44d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df44d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df44d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="df44d-110">S_OK</span></span>|<span data-ttu-id="df44d-111">`CreateIoCompletionPort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="df44d-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="df44d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df44d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df44d-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="df44d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="df44d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="df44d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="df44d-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="df44d-115">The call timed out.</span></span>|  
|<span data-ttu-id="df44d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="df44d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="df44d-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="df44d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="df44d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="df44d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="df44d-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="df44d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="df44d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df44d-120">E_FAIL</span></span>|<span data-ttu-id="df44d-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="df44d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="df44d-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="df44d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="df44d-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="df44d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="df44d-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="df44d-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="df44d-125">İstenen kaynak ayırmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="df44d-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df44d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df44d-126">Remarks</span></span>  
 <span data-ttu-id="df44d-127">CLR çağrıları `CreateIoCompletionPort` ana bilgisayar yeni bir g/ç tamamlama bağlantı noktasını oluşturmak istemeniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df44d-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="df44d-128">Bu bağlantı noktası üzerinden yapılan bir çağrı g/ç işlemleri bağlar [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df44d-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="df44d-129">Ana bilgisayar raporları durumu geri CLR çağırarak [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="df44d-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df44d-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df44d-130">Requirements</span></span>  
 <span data-ttu-id="df44d-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df44d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df44d-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df44d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df44d-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="df44d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df44d-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df44d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df44d-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df44d-135">See Also</span></span>  
 [<span data-ttu-id="df44d-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df44d-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="df44d-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df44d-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
