---
title: "IHostTask::Join Yöntemi"
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
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 85ee44fe9185364a6870b996ca98cfe6cc297bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="7ff01-102">IHostTask::Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ff01-102">IHostTask::Join Method</span></span>
<span data-ttu-id="7ff01-103">Geçerli tarafından temsil edilen görev kadar arama görev engeller [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tamamlandıktan, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7ff01-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff01-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ff01-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ff01-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ff01-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="7ff01-106">[in] Görev sonlandırmak beklenecek milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="7ff01-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="7ff01-107">Görev sona erdirmeden önce bu aralığı sona erdiğinde, arama görev kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ff01-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="7ff01-108">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="7ff01-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="7ff01-109">WAIT_ALERTABLE değerini, görev uyandırmak için ana bilgisayar bildirir `Alert` önce adlı `milliseconds` sona erdiğinde.</span><span class="sxs-lookup"><span data-stu-id="7ff01-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ff01-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7ff01-110">Return Value</span></span>  
  
|<span data-ttu-id="7ff01-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ff01-111">HRESULT</span></span>|<span data-ttu-id="7ff01-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ff01-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ff01-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ff01-113">S_OK</span></span>|<span data-ttu-id="7ff01-114">`Join`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7ff01-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="7ff01-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ff01-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ff01-116">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7ff01-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ff01-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ff01-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ff01-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7ff01-118">The call timed out.</span></span>|  
|<span data-ttu-id="7ff01-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ff01-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ff01-120">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7ff01-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ff01-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ff01-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ff01-122">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber veya geçerli üzerinde beklerken `IHostTask` örneği bir görev ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="7ff01-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="7ff01-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ff01-123">E_FAIL</span></span>|<span data-ttu-id="7ff01-124">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7ff01-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ff01-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7ff01-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ff01-126">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ff01-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ff01-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff01-127">Requirements</span></span>  
 <span data-ttu-id="7ff01-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff01-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff01-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ff01-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ff01-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7ff01-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ff01-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff01-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff01-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff01-132">See Also</span></span>  
 [<span data-ttu-id="7ff01-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ff01-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7ff01-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ff01-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7ff01-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ff01-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7ff01-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ff01-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="7ff01-137">WAIT_OPTION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7ff01-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
