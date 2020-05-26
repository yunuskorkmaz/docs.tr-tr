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
ms.openlocfilehash: bb12547155383bb410f592018232ca6f688bab8a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841913"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="9e713-102">IHostTaskManager::Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e713-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="9e713-103">Ana bilgisayara geçerli görevin uykuya geçmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="9e713-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e713-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9e713-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e713-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e713-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="9e713-106">'ndaki İş parçacığının uyku moduna alacağı zaman aralığı (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="9e713-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="9e713-107">'ndaki [WAIT_OPTION](wait-option-enumeration.md) sabit listesi değerlerinden biri, bu eylem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e713-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e713-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e713-108">Return Value</span></span>  
  
|<span data-ttu-id="9e713-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e713-109">HRESULT</span></span>|<span data-ttu-id="9e713-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e713-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e713-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e713-111">S_OK</span></span>|<span data-ttu-id="9e713-112">`Sleep`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9e713-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="9e713-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e713-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e713-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9e713-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e713-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e713-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e713-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9e713-116">The call timed out.</span></span>|  
|<span data-ttu-id="9e713-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e713-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e713-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9e713-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e713-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e713-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e713-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9e713-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e713-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e713-121">E_FAIL</span></span>|<span data-ttu-id="9e713-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e713-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e713-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e713-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e713-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e713-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e713-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e713-125">Remarks</span></span>  
 <span data-ttu-id="9e713-126">CLR genellikle `IHostTaskManager::Sleep` <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> kullanıcı kodundan çağrıldığında ' i çağırır.</span><span class="sxs-lookup"><span data-stu-id="9e713-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e713-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e713-127">Requirements</span></span>  
 <span data-ttu-id="9e713-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e713-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e713-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e713-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e713-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9e713-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e713-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e713-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e713-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e713-132">See also</span></span>

- [<span data-ttu-id="9e713-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e713-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9e713-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e713-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9e713-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e713-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9e713-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e713-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
