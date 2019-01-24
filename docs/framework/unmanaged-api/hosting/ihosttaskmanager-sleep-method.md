---
title: IHostTaskManager::Sleep Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e9661d1cd6994acf2c622350593ede502929f3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510656"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="3deba-102">IHostTaskManager::Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3deba-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="3deba-103">Konak, geçerli görev, uyku durumuna geçiyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="3deba-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3deba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3deba-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3deba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3deba-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="3deba-106">[in] İş parçacığı uyku milisaniye cinsinden zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="3deba-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="3deba-107">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) bu konak sürecektir hangi eylemini belirten numaralandırma değerlerinin eylem engeller.</span><span class="sxs-lookup"><span data-stu-id="3deba-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3deba-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3deba-108">Return Value</span></span>  
  
|<span data-ttu-id="3deba-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3deba-109">HRESULT</span></span>|<span data-ttu-id="3deba-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3deba-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3deba-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3deba-111">S_OK</span></span>|<span data-ttu-id="3deba-112">`Sleep` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3deba-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="3deba-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3deba-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3deba-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="3deba-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3deba-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3deba-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3deba-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3deba-116">The call timed out.</span></span>|  
|<span data-ttu-id="3deba-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3deba-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3deba-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3deba-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3deba-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3deba-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3deba-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3deba-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3deba-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3deba-121">E_FAIL</span></span>|<span data-ttu-id="3deba-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3deba-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3deba-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3deba-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3deba-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3deba-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3deba-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3deba-125">Remarks</span></span>  
 <span data-ttu-id="3deba-126">CLR genellikle çağrıları `IHostTaskManager::Sleep` olduğunda <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> kullanıcı kodundan çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3deba-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3deba-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3deba-127">Requirements</span></span>  
 <span data-ttu-id="3deba-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3deba-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3deba-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3deba-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3deba-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3deba-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3deba-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3deba-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3deba-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3deba-132">See also</span></span>
- [<span data-ttu-id="3deba-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3deba-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3deba-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3deba-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3deba-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3deba-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3deba-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3deba-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
