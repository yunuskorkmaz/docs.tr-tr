---
title: "IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fde1045fd0f15e7255a163c1f1b041800e85921
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="9500d-102">IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9500d-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="9500d-103">Bir arabirim işaretçisi ile ana bilgisayarının sağladığı [Iclrıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) ortak dil çalışma zamanı tarafından (CLR) uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="9500d-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9500d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9500d-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9500d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9500d-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="9500d-106">[in] Bir arabirim işaretçisi bir `ICLRIoCompletionManager` CLR tarafından sağlanan örneği.</span><span class="sxs-lookup"><span data-stu-id="9500d-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9500d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9500d-107">Return Value</span></span>  
  
|<span data-ttu-id="9500d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9500d-108">HRESULT</span></span>|<span data-ttu-id="9500d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9500d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9500d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9500d-110">S_OK</span></span>|<span data-ttu-id="9500d-111">`SetCLRIoCompletionManager`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9500d-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="9500d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9500d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9500d-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9500d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9500d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9500d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9500d-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9500d-115">The call timed out.</span></span>|  
|<span data-ttu-id="9500d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9500d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9500d-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9500d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9500d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9500d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9500d-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9500d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9500d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9500d-120">E_FAIL</span></span>|<span data-ttu-id="9500d-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9500d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9500d-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9500d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9500d-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9500d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9500d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9500d-124">Remarks</span></span>  
 <span data-ttu-id="9500d-125">CLR çağırdı sonra `SetCLRIoCompletionManager`, konak çağırmalıdır [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) bir g/ç isteği tamamlandığında CLR bildirir.</span><span class="sxs-lookup"><span data-stu-id="9500d-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9500d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9500d-126">Requirements</span></span>  
 <span data-ttu-id="9500d-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9500d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9500d-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9500d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9500d-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9500d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9500d-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9500d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9500d-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9500d-131">See Also</span></span>  
 [<span data-ttu-id="9500d-132">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9500d-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="9500d-133">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9500d-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
