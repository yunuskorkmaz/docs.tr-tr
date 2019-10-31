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
ms.openlocfilehash: a8642235cda359b849c49a35ab565397402c37d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130510"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="83ce1-102">IHostCrst::SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83ce1-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="83ce1-103">Geçerli [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği için döngü sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="83ce1-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ce1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83ce1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83ce1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83ce1-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="83ce1-106">'ndaki Geçerli `IHostCrst` örneği için yeni döndürme sayısı.</span><span class="sxs-lookup"><span data-stu-id="83ce1-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83ce1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="83ce1-107">Return Value</span></span>  
  
|<span data-ttu-id="83ce1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83ce1-108">HRESULT</span></span>|<span data-ttu-id="83ce1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83ce1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83ce1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83ce1-110">S_OK</span></span>|<span data-ttu-id="83ce1-111">`SetSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="83ce1-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="83ce1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83ce1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83ce1-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="83ce1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83ce1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83ce1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83ce1-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="83ce1-115">The call timed out.</span></span>|  
|<span data-ttu-id="83ce1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83ce1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83ce1-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="83ce1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83ce1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83ce1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83ce1-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="83ce1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83ce1-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="83ce1-120">E_FAIL</span></span>|<span data-ttu-id="83ce1-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="83ce1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83ce1-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="83ce1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83ce1-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="83ce1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83ce1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83ce1-124">Remarks</span></span>  
 <span data-ttu-id="83ce1-125">Çok işlemcili sistemlerde, geçerli `IHostCrst` örneği tarafından temsil edilen kritik bölüm kullanılamaz durumdaysa, çağıran bir iş parçacığı [ıhostsemaforu](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) çağrılmadan önce `dwSpinCount` zaman alır:: kritik bölümüyle ilişkili bir Semaforda bekleyin.</span><span class="sxs-lookup"><span data-stu-id="83ce1-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="83ce1-126">Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler.</span><span class="sxs-lookup"><span data-stu-id="83ce1-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="83ce1-127">`dwSpinCount` kullanımı, Win32 `InitializeCriticalSectionAndSpinCount` işlevindeki aynı ada sahip parametrenin kullanımıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="83ce1-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83ce1-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83ce1-128">Requirements</span></span>  
 <span data-ttu-id="83ce1-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83ce1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83ce1-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83ce1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83ce1-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="83ce1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83ce1-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83ce1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ce1-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83ce1-133">See also</span></span>

- [<span data-ttu-id="83ce1-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83ce1-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="83ce1-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83ce1-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="83ce1-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83ce1-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
