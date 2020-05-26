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
ms.openlocfilehash: 8fa59e065042565b4a543106fff714558cef42ec
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842250"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="733bc-102">IHostTask::Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="733bc-102">IHostTask::Join Method</span></span>
<span data-ttu-id="733bc-103">Geçerli [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tarafından temsil edilen görev tamamlanıncaya kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](ihosttask-alert-method.md) çağrıldığında, çağıran görevi engeller.</span><span class="sxs-lookup"><span data-stu-id="733bc-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733bc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="733bc-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="733bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="733bc-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="733bc-106">'ndaki Görevin sonlanmasını beklemek için milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="733bc-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="733bc-107">Bu Aralık görev sonlandırılmadan önce sona erdiğinde, çağıran görev engellemeleri.</span><span class="sxs-lookup"><span data-stu-id="733bc-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="733bc-108">'ndaki [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="733bc-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="733bc-109">WAIT_ALERTABLE değeri, `Alert` sona erdiğinde çağrıldığında, ana bilgisayarı görevi uyandırmasını söyler `milliseconds` .</span><span class="sxs-lookup"><span data-stu-id="733bc-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="733bc-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="733bc-110">Return Value</span></span>  
  
|<span data-ttu-id="733bc-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="733bc-111">HRESULT</span></span>|<span data-ttu-id="733bc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="733bc-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="733bc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="733bc-113">S_OK</span></span>|<span data-ttu-id="733bc-114">`Join`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="733bc-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="733bc-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="733bc-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="733bc-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="733bc-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="733bc-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="733bc-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="733bc-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="733bc-118">The call timed out.</span></span>|  
|<span data-ttu-id="733bc-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="733bc-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="733bc-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="733bc-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="733bc-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="733bc-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="733bc-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi veya geçerli `IHostTask` örnek bir görevle ilişkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="733bc-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="733bc-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="733bc-123">E_FAIL</span></span>|<span data-ttu-id="733bc-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="733bc-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="733bc-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="733bc-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="733bc-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="733bc-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="733bc-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="733bc-127">Requirements</span></span>  
 <span data-ttu-id="733bc-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="733bc-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="733bc-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="733bc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="733bc-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="733bc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="733bc-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="733bc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733bc-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="733bc-132">See also</span></span>

- [<span data-ttu-id="733bc-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="733bc-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="733bc-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="733bc-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="733bc-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="733bc-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="733bc-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="733bc-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="733bc-137">WAIT_OPTION Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="733bc-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
