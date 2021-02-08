---
description: 'Şu konuda daha fazla bilgi edinin: IHostTask:: JOIN yöntemi'
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
ms.openlocfilehash: 8231401ab01ee040f225b78a52b61eb7d59af1d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784658"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="8549e-103">IHostTask::Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8549e-103">IHostTask::Join Method</span></span>

<span data-ttu-id="8549e-104">Geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görev tamamlanıncaya kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](ihosttask-alert-method.md) çağrıldığında, çağıran görevi engeller.</span><span class="sxs-lookup"><span data-stu-id="8549e-104">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8549e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8549e-105">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8549e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8549e-106">Parameters</span></span>  

 `milliseconds`  
 <span data-ttu-id="8549e-107">'ndaki Görevin sonlanmasını beklemek için milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="8549e-107">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="8549e-108">Bu Aralık görev sonlandırılmadan önce sona erdiğinde, çağıran görev engellemeleri.</span><span class="sxs-lookup"><span data-stu-id="8549e-108">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="8549e-109">'ndaki [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="8549e-109">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="8549e-110">WAIT_ALERTABLE değeri, `Alert` sona erdiğinde çağrıldığında, ana bilgisayarı görevi uyandırmasını söyler `milliseconds` .</span><span class="sxs-lookup"><span data-stu-id="8549e-110">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8549e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8549e-111">Return Value</span></span>  
  
|<span data-ttu-id="8549e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8549e-112">HRESULT</span></span>|<span data-ttu-id="8549e-113">Description</span><span class="sxs-lookup"><span data-stu-id="8549e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8549e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8549e-114">S_OK</span></span>|<span data-ttu-id="8549e-115">`Join` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8549e-115">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="8549e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8549e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8549e-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8549e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8549e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8549e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8549e-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8549e-119">The call timed out.</span></span>|  
|<span data-ttu-id="8549e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8549e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8549e-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8549e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8549e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8549e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8549e-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi veya geçerli `IHostTask` örnek bir görevle ilişkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="8549e-123">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="8549e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8549e-124">E_FAIL</span></span>|<span data-ttu-id="8549e-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8549e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8549e-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8549e-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8549e-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8549e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8549e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8549e-128">Requirements</span></span>  

 <span data-ttu-id="8549e-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8549e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8549e-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8549e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8549e-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8549e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8549e-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8549e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8549e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8549e-133">See also</span></span>

- [<span data-ttu-id="8549e-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8549e-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8549e-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8549e-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8549e-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8549e-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8549e-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8549e-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="8549e-138">WAIT_OPTION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8549e-138">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
