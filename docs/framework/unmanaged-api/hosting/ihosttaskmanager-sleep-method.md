---
description: 'Şu konuda daha fazla bilgi edinin: IHostTaskManager:: Sleep yöntemi'
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
ms.openlocfilehash: fedb87c6bd4558a2aa6158299551327cb2271d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789378"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="76d45-103">IHostTaskManager::Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76d45-103">IHostTaskManager::Sleep Method</span></span>

<span data-ttu-id="76d45-104">Ana bilgisayara geçerli görevin uykuya geçmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="76d45-104">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d45-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76d45-105">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76d45-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76d45-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="76d45-107">'ndaki İş parçacığının uyku moduna alacağı zaman aralığı (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="76d45-107">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="76d45-108">'ndaki [WAIT_OPTION](wait-option-enumeration.md) sabit listesi değerlerinden biri, bu eylem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="76d45-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76d45-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="76d45-109">Return Value</span></span>  
  
|<span data-ttu-id="76d45-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76d45-110">HRESULT</span></span>|<span data-ttu-id="76d45-111">Description</span><span class="sxs-lookup"><span data-stu-id="76d45-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76d45-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="76d45-112">S_OK</span></span>|<span data-ttu-id="76d45-113">`Sleep` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="76d45-113">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="76d45-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76d45-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76d45-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="76d45-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76d45-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76d45-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76d45-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="76d45-117">The call timed out.</span></span>|  
|<span data-ttu-id="76d45-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76d45-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76d45-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="76d45-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76d45-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76d45-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76d45-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="76d45-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76d45-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76d45-122">E_FAIL</span></span>|<span data-ttu-id="76d45-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="76d45-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76d45-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="76d45-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76d45-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="76d45-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76d45-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76d45-126">Remarks</span></span>  

 <span data-ttu-id="76d45-127">CLR genellikle `IHostTaskManager::Sleep` <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> kullanıcı kodundan çağrıldığında ' i çağırır.</span><span class="sxs-lookup"><span data-stu-id="76d45-127">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76d45-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76d45-128">Requirements</span></span>  

 <span data-ttu-id="76d45-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76d45-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76d45-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="76d45-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76d45-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="76d45-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76d45-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76d45-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d45-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76d45-133">See also</span></span>

- [<span data-ttu-id="76d45-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76d45-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="76d45-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76d45-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="76d45-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76d45-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="76d45-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76d45-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
