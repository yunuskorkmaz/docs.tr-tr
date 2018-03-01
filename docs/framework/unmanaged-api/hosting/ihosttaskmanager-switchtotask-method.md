---
title: "IHostTaskManager::SwitchToTask Yöntemi"
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
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03578a6a9579a807323d54308347f16f24ae90dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="086e4-102">IHostTaskManager::SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="086e4-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="086e4-103">Geçerli görev moduna geçirmelisiniz konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="086e4-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="086e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="086e4-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="086e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="086e4-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="086e4-106">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) ana bilgisayar varsa almalıdır eylemini belirten numaralandırma değerlerinin istenen işlem engeller.</span><span class="sxs-lookup"><span data-stu-id="086e4-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="086e4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="086e4-107">Return Value</span></span>  
  
|<span data-ttu-id="086e4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="086e4-108">HRESULT</span></span>|<span data-ttu-id="086e4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="086e4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="086e4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="086e4-110">S_OK</span></span>|<span data-ttu-id="086e4-111">`SwitchToTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="086e4-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="086e4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="086e4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="086e4-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="086e4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="086e4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="086e4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="086e4-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="086e4-115">The call timed out.</span></span>|  
|<span data-ttu-id="086e4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="086e4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="086e4-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="086e4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="086e4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="086e4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="086e4-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="086e4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="086e4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="086e4-120">E_FAIL</span></span>|<span data-ttu-id="086e4-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="086e4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="086e4-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="086e4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="086e4-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="086e4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="086e4-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="086e4-124">Remarks</span></span>  
 <span data-ttu-id="086e4-125">Ana bilgisayar, istenen ya da gerekli olarak başka bir görevde geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="086e4-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="086e4-126">`SwitchToTask`ana bilgisayar için geçmelisiniz hangi görev belirtmez; yalnızca gelen moduna geçirmelisiniz görev belirtir.</span><span class="sxs-lookup"><span data-stu-id="086e4-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="086e4-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="086e4-127">Requirements</span></span>  
 <span data-ttu-id="086e4-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="086e4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="086e4-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="086e4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="086e4-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="086e4-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="086e4-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="086e4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="086e4-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="086e4-132">See Also</span></span>  
 [<span data-ttu-id="086e4-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="086e4-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="086e4-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="086e4-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="086e4-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="086e4-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="086e4-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="086e4-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
