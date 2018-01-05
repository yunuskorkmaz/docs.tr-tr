---
title: "IHostCrst::TryEnter Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.TryEnter
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1ddec99069e3cd7777e45031e7f0e8d3eabeccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="3bf91-102">IHostCrst::TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bf91-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="3bf91-103">Geçerli tarafından temsil edilen kritik bölüm girin girişiminde [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="3bf91-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bf91-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bf91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bf91-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="3bf91-106">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri, ana bilgisayar varsa almalıdır hangi eylemini belirten işlemi engeller.</span><span class="sxs-lookup"><span data-stu-id="3bf91-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="3bf91-107">[out] `true` kritik bölüm olabilir, girilen Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="3bf91-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bf91-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3bf91-108">Return Value</span></span>  
  
|<span data-ttu-id="3bf91-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3bf91-109">HRESULT</span></span>|<span data-ttu-id="3bf91-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bf91-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bf91-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bf91-111">S_OK</span></span>|<span data-ttu-id="3bf91-112">`TryEnter`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3bf91-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="3bf91-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3bf91-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3bf91-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3bf91-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3bf91-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3bf91-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3bf91-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3bf91-116">The call timed out.</span></span>|  
|<span data-ttu-id="3bf91-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3bf91-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3bf91-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="3bf91-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3bf91-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3bf91-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3bf91-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="3bf91-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3bf91-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3bf91-121">E_FAIL</span></span>|<span data-ttu-id="3bf91-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3bf91-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3bf91-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3bf91-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3bf91-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3bf91-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bf91-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bf91-125">Remarks</span></span>  
 <span data-ttu-id="3bf91-126">`TryEnter`hemen döndürür ve çağıran iş parçacığı kritik bölüm girilen olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bf91-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="3bf91-127">Bu yöntem Wind32 yansıtan `TryEnterCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="3bf91-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bf91-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bf91-128">Requirements</span></span>  
 <span data-ttu-id="3bf91-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bf91-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bf91-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bf91-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bf91-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3bf91-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bf91-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf91-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf91-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf91-133">See Also</span></span>  
 [<span data-ttu-id="3bf91-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bf91-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="3bf91-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bf91-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="3bf91-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bf91-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
