---
title: "IHostCrst::SetSpinCount Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76a3091102a43d17f543010be0c505157d593d2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="fd465-102">IHostCrst::SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd465-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="fd465-103">Geçerli döndürme sayısını ayarlar [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="fd465-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd465-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd465-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd465-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd465-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="fd465-106">[in] Yeni döndürme sayısı geçerli `IHostCrst` örneği.</span><span class="sxs-lookup"><span data-stu-id="fd465-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd465-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd465-107">Return Value</span></span>  
  
|<span data-ttu-id="fd465-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd465-108">HRESULT</span></span>|<span data-ttu-id="fd465-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd465-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd465-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd465-110">S_OK</span></span>|<span data-ttu-id="fd465-111">`SetSpinCount`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fd465-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="fd465-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd465-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd465-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fd465-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd465-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd465-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd465-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fd465-115">The call timed out.</span></span>|  
|<span data-ttu-id="fd465-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd465-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd465-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="fd465-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd465-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd465-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd465-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="fd465-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd465-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd465-120">E_FAIL</span></span>|<span data-ttu-id="fd465-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fd465-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd465-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fd465-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd465-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd465-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd465-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd465-124">Remarks</span></span>  
 <span data-ttu-id="fd465-125">Birden çok işlemcili sistemlerde kritik bölüm geçerli tarafından temsil edilen varsa `IHostCrst` örneği kullanılamıyorsa, çağıran iş parçacığı döner `dwSpinCount` kez çağırmadan önce [Ihostsemaphore::wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) ilişkili semafor üzerinde kritik bir bölümle.</span><span class="sxs-lookup"><span data-stu-id="fd465-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="fd465-126">Değer değiştirme işlemi sırasında kritik bölüm boş duruma gelirse, çağıran iş parçacığı bekleme işlem önler.</span><span class="sxs-lookup"><span data-stu-id="fd465-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="fd465-127">Kullanımını `dwSpinCount` Win32 aynı ada sahip parametre kullanımını aynıdır `InitializeCriticalSectionAndSpinCount` işlevi.</span><span class="sxs-lookup"><span data-stu-id="fd465-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd465-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd465-128">Requirements</span></span>  
 <span data-ttu-id="fd465-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd465-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd465-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd465-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd465-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fd465-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd465-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd465-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd465-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd465-133">See Also</span></span>  
 [<span data-ttu-id="fd465-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd465-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="fd465-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd465-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="fd465-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd465-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
