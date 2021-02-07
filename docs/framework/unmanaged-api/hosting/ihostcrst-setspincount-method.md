---
description: ': IHostCrst:: SetSpinCount metodu hakkında daha fazla bilgi edinin'
title: IHostCrst::SetSpinCount Yöntemi
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: f04281d2649f210e64fc4c0585eb7d52be3e8ec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721235"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="e1c65-103">IHostCrst::SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1c65-103">IHostCrst::SetSpinCount Method</span></span>

<span data-ttu-id="e1c65-104">Geçerli [IHostCrst](ihostcrst-interface.md) örneği için döngü sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e1c65-104">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c65-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1c65-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c65-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1c65-106">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="e1c65-107">'ndaki Geçerli örnek için yeni döndürme sayısı `IHostCrst` .</span><span class="sxs-lookup"><span data-stu-id="e1c65-107">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1c65-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1c65-108">Return Value</span></span>  
  
|<span data-ttu-id="e1c65-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1c65-109">HRESULT</span></span>|<span data-ttu-id="e1c65-110">Description</span><span class="sxs-lookup"><span data-stu-id="e1c65-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1c65-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1c65-111">S_OK</span></span>|<span data-ttu-id="e1c65-112">`SetSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e1c65-112">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="e1c65-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1c65-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1c65-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e1c65-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e1c65-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e1c65-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e1c65-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e1c65-116">The call timed out.</span></span>|  
|<span data-ttu-id="e1c65-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e1c65-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e1c65-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e1c65-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e1c65-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e1c65-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e1c65-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e1c65-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e1c65-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1c65-121">E_FAIL</span></span>|<span data-ttu-id="e1c65-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e1c65-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e1c65-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e1c65-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e1c65-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1c65-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1c65-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1c65-125">Remarks</span></span>  

 <span data-ttu-id="e1c65-126">Çok işlemcili sistemlerde, geçerli örnek tarafından temsil edilen kritik bölüm `IHostCrst` kullanılamaz durumdaysa, `dwSpinCount` [ıhostsemaforu](ihostsemaphore-wait-method.md) çağrılmadan önce bir çağıran iş parçacığı zaman alır:: kritik bölümüyle Ilişkili bir semafor üzerinde bekleyin.</span><span class="sxs-lookup"><span data-stu-id="e1c65-126">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="e1c65-127">Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler.</span><span class="sxs-lookup"><span data-stu-id="e1c65-127">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="e1c65-128">Öğesinin kullanımı, `dwSpinCount` Win32 işlevindeki aynı ada sahip parametresinin kullanımı ile aynıdır `InitializeCriticalSectionAndSpinCount` .</span><span class="sxs-lookup"><span data-stu-id="e1c65-128">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c65-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1c65-129">Requirements</span></span>  

 <span data-ttu-id="e1c65-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c65-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c65-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e1c65-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1c65-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e1c65-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1c65-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c65-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c65-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1c65-134">See also</span></span>

- [<span data-ttu-id="e1c65-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c65-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e1c65-136">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c65-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="e1c65-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c65-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
