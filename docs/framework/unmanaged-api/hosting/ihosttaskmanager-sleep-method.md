---
title: "IHostTaskManager::Sleep Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.Sleep
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc26ca7d226c4529b0bc702567e774f2f98b085d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="150e8-102">IHostTaskManager::Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="150e8-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="150e8-103">Geçerli görev uyku gittiği konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="150e8-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="150e8-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="150e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="150e8-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="150e8-106">[in] İş parçacığı uyku milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="150e8-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="150e8-107">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) bu konak almalıdır hangi eylemini belirten numaralandırma değerlerinin eylem engeller.</span><span class="sxs-lookup"><span data-stu-id="150e8-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="150e8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="150e8-108">Return Value</span></span>  
  
|<span data-ttu-id="150e8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="150e8-109">HRESULT</span></span>|<span data-ttu-id="150e8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="150e8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="150e8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="150e8-111">S_OK</span></span>|<span data-ttu-id="150e8-112">`Sleep`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="150e8-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="150e8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="150e8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="150e8-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="150e8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="150e8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="150e8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="150e8-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="150e8-116">The call timed out.</span></span>|  
|<span data-ttu-id="150e8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="150e8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="150e8-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="150e8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="150e8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="150e8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="150e8-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="150e8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="150e8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="150e8-121">E_FAIL</span></span>|<span data-ttu-id="150e8-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="150e8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="150e8-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="150e8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="150e8-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="150e8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="150e8-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="150e8-125">Remarks</span></span>  
 <span data-ttu-id="150e8-126">CLR genellikle çağırır `IHostTaskManager::Sleep` zaman <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> kullanıcı kodundan olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="150e8-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="150e8-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="150e8-127">Requirements</span></span>  
 <span data-ttu-id="150e8-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="150e8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="150e8-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="150e8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="150e8-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="150e8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="150e8-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="150e8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="150e8-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="150e8-132">See Also</span></span>  
 [<span data-ttu-id="150e8-133">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="150e8-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="150e8-134">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="150e8-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="150e8-135">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="150e8-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="150e8-136">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="150e8-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
