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
ms.openlocfilehash: dda68041dbf4efa82a35c48702d83aa231462fef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121380"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="2c61b-102">IHostTask::Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c61b-102">IHostTask::Join Method</span></span>
<span data-ttu-id="2c61b-103">Geçerli [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tarafından temsil edilen görev tamamlanıncaya kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) çağrıldığında, çağıran görevi engeller.</span><span class="sxs-lookup"><span data-stu-id="2c61b-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c61b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c61b-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c61b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c61b-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="2c61b-106">'ndaki Görevin sonlanmasını beklemek için milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="2c61b-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="2c61b-107">Bu Aralık görev sonlandırılmadan önce sona erdiğinde, çağıran görev engellemeleri.</span><span class="sxs-lookup"><span data-stu-id="2c61b-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="2c61b-108">'ndaki [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="2c61b-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="2c61b-109">WAIT_ALERTABLE değeri, `Alert` `milliseconds` bitmeden önce çağrılırsa, ana bilgisayara görevi uyandırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="2c61b-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c61b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2c61b-110">Return Value</span></span>  
  
|<span data-ttu-id="2c61b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c61b-111">HRESULT</span></span>|<span data-ttu-id="2c61b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c61b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c61b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c61b-113">S_OK</span></span>|<span data-ttu-id="2c61b-114">`Join` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2c61b-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="2c61b-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c61b-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c61b-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2c61b-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c61b-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c61b-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c61b-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2c61b-118">The call timed out.</span></span>|  
|<span data-ttu-id="2c61b-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c61b-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c61b-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2c61b-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c61b-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c61b-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c61b-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi veya geçerli `IHostTask` örneği bir görevle ilişkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="2c61b-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="2c61b-123">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="2c61b-123">E_FAIL</span></span>|<span data-ttu-id="2c61b-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2c61b-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c61b-125">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2c61b-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c61b-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c61b-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c61b-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c61b-127">Requirements</span></span>  
 <span data-ttu-id="2c61b-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c61b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c61b-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2c61b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c61b-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2c61b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c61b-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c61b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c61b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c61b-132">See also</span></span>

- [<span data-ttu-id="2c61b-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c61b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2c61b-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c61b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2c61b-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c61b-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2c61b-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c61b-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="2c61b-137">WAIT_OPTION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2c61b-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
