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
ms.openlocfilehash: 7eedf052b6f2285799940b394d9891975230cb72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132923"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="e4f11-102">IHostTaskManager::Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4f11-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="e4f11-103">Ana bilgisayara geçerli görevin uykuya geçmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="e4f11-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f11-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4f11-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f11-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4f11-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="e4f11-106">'ndaki İş parçacığının uyku moduna alacağı zaman aralığı (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="e4f11-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="e4f11-107">'ndaki [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) sabit listesi değerlerinden biri, bu eylem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4f11-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4f11-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4f11-108">Return Value</span></span>  
  
|<span data-ttu-id="e4f11-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4f11-109">HRESULT</span></span>|<span data-ttu-id="e4f11-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4f11-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4f11-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4f11-111">S_OK</span></span>|<span data-ttu-id="e4f11-112">`Sleep` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e4f11-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="e4f11-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4f11-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4f11-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e4f11-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4f11-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4f11-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4f11-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e4f11-116">The call timed out.</span></span>|  
|<span data-ttu-id="e4f11-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4f11-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4f11-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e4f11-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4f11-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4f11-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4f11-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e4f11-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4f11-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="e4f11-121">E_FAIL</span></span>|<span data-ttu-id="e4f11-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e4f11-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4f11-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e4f11-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4f11-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4f11-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f11-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4f11-125">Remarks</span></span>  
 <span data-ttu-id="e4f11-126">CLR genellikle <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> kullanıcı kodundan çağrıldığında `IHostTaskManager::Sleep` çağırır.</span><span class="sxs-lookup"><span data-stu-id="e4f11-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f11-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4f11-127">Requirements</span></span>  
 <span data-ttu-id="e4f11-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f11-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f11-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4f11-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4f11-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e4f11-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4f11-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f11-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f11-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f11-132">See also</span></span>

- [<span data-ttu-id="e4f11-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f11-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e4f11-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f11-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e4f11-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f11-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e4f11-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f11-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
