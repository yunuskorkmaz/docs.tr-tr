---
title: "IHostTaskManager::SetCLRTaskManager Yöntemi"
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
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f009fee3f9bc439ce61d859759870f9cbb54f09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="92bbf-102">IHostTaskManager::SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92bbf-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="92bbf-103">Ana bilgisayar için bir arabirim işaretçisi sağlayan bir [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) ortak dil çalışma zamanı tarafından (CLR) uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="92bbf-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92bbf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92bbf-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92bbf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92bbf-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="92bbf-106">[in] Bir işaretçi bir `ICLRTaskManager` ortak dil çalışma zamanı tarafından uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="92bbf-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92bbf-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92bbf-107">Return Value</span></span>  
  
|<span data-ttu-id="92bbf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92bbf-108">HRESULT</span></span>|<span data-ttu-id="92bbf-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92bbf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92bbf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="92bbf-110">S_OK</span></span>|<span data-ttu-id="92bbf-111">`SetCLRTaskManager`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="92bbf-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="92bbf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92bbf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92bbf-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="92bbf-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92bbf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92bbf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92bbf-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="92bbf-115">The call timed out.</span></span>|  
|<span data-ttu-id="92bbf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92bbf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92bbf-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="92bbf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92bbf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92bbf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92bbf-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="92bbf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92bbf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92bbf-120">E_FAIL</span></span>|<span data-ttu-id="92bbf-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="92bbf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92bbf-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92bbf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92bbf-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="92bbf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92bbf-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92bbf-124">Remarks</span></span>  
 <span data-ttu-id="92bbf-125">Çalışma zamanı çağrıları `SetCLRTaskManager` ana bilgisayar için bir arabirim işaretçisi sağlamak için bir `ICLRTaskManager` örneği.</span><span class="sxs-lookup"><span data-stu-id="92bbf-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92bbf-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92bbf-126">Requirements</span></span>  
 <span data-ttu-id="92bbf-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92bbf-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92bbf-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92bbf-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92bbf-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="92bbf-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92bbf-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92bbf-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92bbf-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92bbf-131">See Also</span></span>  
 [<span data-ttu-id="92bbf-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92bbf-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="92bbf-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92bbf-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="92bbf-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92bbf-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="92bbf-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92bbf-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
