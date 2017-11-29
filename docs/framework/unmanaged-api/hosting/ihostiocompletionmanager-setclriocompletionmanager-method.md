---
title: "IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetCLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2447ba9cf3ee5968bde26b0a578cc06ef5c614c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="54ac1-102">IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54ac1-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="54ac1-103">Bir arabirim işaretçisi ile ana bilgisayarının sağladığı [Iclrıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) ortak dil çalışma zamanı tarafından (CLR) uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="54ac1-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54ac1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54ac1-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54ac1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54ac1-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="54ac1-106">[in] Bir arabirim işaretçisi bir `ICLRIoCompletionManager` CLR tarafından sağlanan örneği.</span><span class="sxs-lookup"><span data-stu-id="54ac1-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54ac1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="54ac1-107">Return Value</span></span>  
  
|<span data-ttu-id="54ac1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54ac1-108">HRESULT</span></span>|<span data-ttu-id="54ac1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54ac1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54ac1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="54ac1-110">S_OK</span></span>|<span data-ttu-id="54ac1-111">`SetCLRIoCompletionManager`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="54ac1-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="54ac1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54ac1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54ac1-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="54ac1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54ac1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54ac1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54ac1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="54ac1-115">The call timed out.</span></span>|  
|<span data-ttu-id="54ac1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54ac1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54ac1-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="54ac1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54ac1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54ac1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54ac1-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="54ac1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54ac1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54ac1-120">E_FAIL</span></span>|<span data-ttu-id="54ac1-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="54ac1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54ac1-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="54ac1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54ac1-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="54ac1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54ac1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54ac1-124">Remarks</span></span>  
 <span data-ttu-id="54ac1-125">CLR çağırdı sonra `SetCLRIoCompletionManager`, konak çağırmalıdır [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) bir g/ç isteği tamamlandığında CLR bildirir.</span><span class="sxs-lookup"><span data-stu-id="54ac1-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54ac1-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54ac1-126">Requirements</span></span>  
 <span data-ttu-id="54ac1-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54ac1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54ac1-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54ac1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54ac1-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="54ac1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54ac1-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54ac1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ac1-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54ac1-131">See Also</span></span>  
 [<span data-ttu-id="54ac1-132">Iclrıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="54ac1-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="54ac1-133">Ihostıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="54ac1-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
