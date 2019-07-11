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
ms.openlocfilehash: e88b7bd647fe46ba98e4396d1836293647f2faa4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764413"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="ac616-102">IHostTask::Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac616-102">IHostTask::Join Method</span></span>
<span data-ttu-id="ac616-103">Geçerli tarafından temsil edilen bir görev kadar çağırma göreviyle engeller [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tamamlanana, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ac616-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac616-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac616-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac616-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac616-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="ac616-106">[in] Görevin sonlandırmak için beklenecek milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="ac616-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="ac616-107">Görev sonlandırılmadan önce bu aralığı aşılırsa, çağırma göreviyle engellemesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac616-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="ac616-108">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="ac616-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="ac616-109">Görev durumunda Uyanma için ana WAIT_ALERTABLE değerini bildirir `Alert` önce çağrılır `milliseconds` geçen.</span><span class="sxs-lookup"><span data-stu-id="ac616-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac616-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac616-110">Return Value</span></span>  
  
|<span data-ttu-id="ac616-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac616-111">HRESULT</span></span>|<span data-ttu-id="ac616-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac616-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac616-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac616-113">S_OK</span></span>|<span data-ttu-id="ac616-114">`Join` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ac616-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="ac616-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac616-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac616-116">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="ac616-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac616-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac616-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac616-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ac616-118">The call timed out.</span></span>|  
|<span data-ttu-id="ac616-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac616-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac616-120">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ac616-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac616-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac616-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac616-122">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber beklerken veya geçerli üzerinde `IHostTask` örneği, bir görev ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="ac616-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="ac616-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac616-123">E_FAIL</span></span>|<span data-ttu-id="ac616-124">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ac616-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac616-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac616-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac616-126">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac616-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac616-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac616-127">Requirements</span></span>  
 <span data-ttu-id="ac616-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac616-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac616-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac616-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac616-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ac616-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac616-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac616-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac616-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac616-132">See also</span></span>

- [<span data-ttu-id="ac616-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac616-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ac616-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac616-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ac616-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac616-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ac616-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac616-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="ac616-137">WAIT_OPTION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ac616-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
