---
title: "IHostTask::Join Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Join
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5dbfcfc87a520925f36e09d4f2d21dbffadfe1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="cccdd-102">IHostTask::Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cccdd-102">IHostTask::Join Method</span></span>
<span data-ttu-id="cccdd-103">Geçerli tarafından temsil edilen görev kadar arama görev engeller [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tamamlandıktan, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="cccdd-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cccdd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cccdd-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cccdd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cccdd-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="cccdd-106">[in] Görev sonlandırmak beklenecek milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="cccdd-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="cccdd-107">Görev sona erdirmeden önce bu aralığı sona erdiğinde, arama görev kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cccdd-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="cccdd-108">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="cccdd-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="cccdd-109">WAIT_ALERTABLE değerini, görev uyandırmak için ana bilgisayar bildirir `Alert` önce adlı `milliseconds` sona erdiğinde.</span><span class="sxs-lookup"><span data-stu-id="cccdd-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cccdd-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cccdd-110">Return Value</span></span>  
  
|<span data-ttu-id="cccdd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cccdd-111">HRESULT</span></span>|<span data-ttu-id="cccdd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cccdd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cccdd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cccdd-113">S_OK</span></span>|<span data-ttu-id="cccdd-114">`Join`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cccdd-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="cccdd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cccdd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cccdd-116">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cccdd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cccdd-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cccdd-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cccdd-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cccdd-118">The call timed out.</span></span>|  
|<span data-ttu-id="cccdd-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cccdd-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cccdd-120">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="cccdd-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cccdd-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cccdd-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cccdd-122">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber veya geçerli üzerinde beklerken `IHostTask` örneği bir görev ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="cccdd-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="cccdd-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cccdd-123">E_FAIL</span></span>|<span data-ttu-id="cccdd-124">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cccdd-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cccdd-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cccdd-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cccdd-126">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cccdd-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cccdd-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cccdd-127">Requirements</span></span>  
 <span data-ttu-id="cccdd-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cccdd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cccdd-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cccdd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cccdd-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cccdd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cccdd-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cccdd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccdd-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cccdd-132">See Also</span></span>  
 [<span data-ttu-id="cccdd-133">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccdd-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cccdd-134">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccdd-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cccdd-135">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccdd-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="cccdd-136">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccdd-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="cccdd-137">Waıt_optıon numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cccdd-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
