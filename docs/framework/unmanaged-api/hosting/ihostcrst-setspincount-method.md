---
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
ms.openlocfilehash: 2436809f35d5c46416f48987cc92feb51d291a6a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804877"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="bd4c2-102">IHostCrst::SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd4c2-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="bd4c2-103">Geçerli [IHostCrst](ihostcrst-interface.md) örneği için döngü sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-103">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd4c2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bd4c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd4c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd4c2-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="bd4c2-106">'ndaki Geçerli örnek için yeni döndürme sayısı `IHostCrst` .</span><span class="sxs-lookup"><span data-stu-id="bd4c2-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd4c2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bd4c2-107">Return Value</span></span>  
  
|<span data-ttu-id="bd4c2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd4c2-108">HRESULT</span></span>|<span data-ttu-id="bd4c2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd4c2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd4c2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd4c2-110">S_OK</span></span>|<span data-ttu-id="bd4c2-111">`SetSpinCount`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="bd4c2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd4c2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd4c2-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bd4c2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bd4c2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bd4c2-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-115">The call timed out.</span></span>|  
|<span data-ttu-id="bd4c2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bd4c2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bd4c2-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bd4c2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bd4c2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bd4c2-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bd4c2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd4c2-120">E_FAIL</span></span>|<span data-ttu-id="bd4c2-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bd4c2-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bd4c2-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd4c2-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd4c2-124">Remarks</span></span>  
 <span data-ttu-id="bd4c2-125">Çok işlemcili sistemlerde, geçerli örnek tarafından temsil edilen kritik bölüm `IHostCrst` kullanılamaz durumdaysa, `dwSpinCount` [ıhostsemaforu](ihostsemaphore-wait-method.md) çağrılmadan önce bir çağıran iş parçacığı zaman alır:: kritik bölümüyle Ilişkili bir semafor üzerinde bekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="bd4c2-126">Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="bd4c2-127">Öğesinin kullanımı, `dwSpinCount` Win32 işlevindeki aynı ada sahip parametresinin kullanımı ile aynıdır `InitializeCriticalSectionAndSpinCount` .</span><span class="sxs-lookup"><span data-stu-id="bd4c2-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd4c2-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd4c2-128">Requirements</span></span>  
 <span data-ttu-id="bd4c2-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd4c2-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd4c2-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bd4c2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd4c2-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="bd4c2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd4c2-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd4c2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd4c2-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd4c2-133">See also</span></span>

- [<span data-ttu-id="bd4c2-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd4c2-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="bd4c2-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd4c2-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="bd4c2-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd4c2-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
