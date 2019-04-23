---
title: IHostTask::Join Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4373fc4e8a4c414c40e8d3c5547b5998b9300348
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170778"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="adabe-102">IHostTask::Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="adabe-102">IHostTask::Join Method</span></span>
<span data-ttu-id="adabe-103">Geçerli tarafından temsil edilen bir görev kadar çağırma göreviyle engeller [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tamamlanana, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="adabe-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adabe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adabe-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adabe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="adabe-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="adabe-106">[in] Görevin sonlandırmak için beklenecek milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="adabe-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="adabe-107">Görev sonlandırılmadan önce bu aralığı aşılırsa, çağırma göreviyle engellemesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="adabe-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="adabe-108">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="adabe-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="adabe-109">Görev durumunda Uyanma için ana WAIT_ALERTABLE değerini bildirir `Alert` önce çağrılır `milliseconds` geçen.</span><span class="sxs-lookup"><span data-stu-id="adabe-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adabe-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="adabe-110">Return Value</span></span>  
  
|<span data-ttu-id="adabe-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="adabe-111">HRESULT</span></span>|<span data-ttu-id="adabe-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adabe-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adabe-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="adabe-113">S_OK</span></span>|<span data-ttu-id="adabe-114">`Join` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="adabe-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="adabe-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="adabe-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="adabe-116">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="adabe-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="adabe-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="adabe-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="adabe-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="adabe-118">The call timed out.</span></span>|  
|<span data-ttu-id="adabe-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="adabe-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="adabe-120">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="adabe-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="adabe-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="adabe-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="adabe-122">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber beklerken veya geçerli üzerinde `IHostTask` örneği, bir görev ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="adabe-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="adabe-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="adabe-123">E_FAIL</span></span>|<span data-ttu-id="adabe-124">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="adabe-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="adabe-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="adabe-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="adabe-126">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="adabe-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adabe-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="adabe-127">Requirements</span></span>  
 <span data-ttu-id="adabe-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adabe-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adabe-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="adabe-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adabe-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="adabe-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adabe-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adabe-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adabe-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adabe-132">See also</span></span>

- [<span data-ttu-id="adabe-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adabe-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="adabe-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adabe-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="adabe-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adabe-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="adabe-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adabe-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="adabe-137">WAIT_OPTION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="adabe-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
