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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf83c7755bc099275c02ff0049f663573c582faf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469567"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="1b6cb-102">IHostCrst::SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b6cb-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="1b6cb-103">Döngü sayısı için geçerli ayarlar [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b6cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b6cb-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b6cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b6cb-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="1b6cb-106">[in] Yeni sayaç sayısı geçerli `IHostCrst` örneği.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b6cb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1b6cb-107">Return Value</span></span>  
  
|<span data-ttu-id="1b6cb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b6cb-108">HRESULT</span></span>|<span data-ttu-id="1b6cb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b6cb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b6cb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b6cb-110">S_OK</span></span>|<span data-ttu-id="1b6cb-111">`SetSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="1b6cb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b6cb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b6cb-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b6cb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b6cb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b6cb-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b6cb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b6cb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b6cb-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b6cb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b6cb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b6cb-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b6cb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b6cb-120">E_FAIL</span></span>|<span data-ttu-id="1b6cb-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b6cb-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b6cb-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b6cb-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b6cb-124">Remarks</span></span>  
 <span data-ttu-id="1b6cb-125">Birden çok işlemcili sistemlerde, kritik bölüm geçerli tarafından temsil edilen `IHostCrst` örneği kullanılamıyorsa, çağıran iş parçacığı dönerek `dwSpinCount` çağırmadan önce kez [Ihostsemaphore::wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) ilişkili semafor üzerinde Kritik Bölümü.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="1b6cb-126">Kritik bölüm döndürme işlemi sırasında boş hale gelirse, çağıran iş parçacığını bekleme işlemi önler.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="1b6cb-127">Kullanımını `dwSpinCount` Win32'de aynı ada sahip parametre kullanımı aynıdır `InitializeCriticalSectionAndSpinCount` işlevi.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b6cb-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b6cb-128">Requirements</span></span>  
 <span data-ttu-id="1b6cb-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b6cb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b6cb-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b6cb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b6cb-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1b6cb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b6cb-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b6cb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b6cb-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b6cb-133">See also</span></span>
- [<span data-ttu-id="1b6cb-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b6cb-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="1b6cb-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b6cb-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="1b6cb-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b6cb-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
