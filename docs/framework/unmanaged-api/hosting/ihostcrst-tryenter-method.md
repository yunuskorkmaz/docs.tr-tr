---
title: IHostCrst::TryEnter Yöntemi
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0b4074d9dab8ad46468930373ad44b0c72bd690
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763746"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="12dff-102">IHostCrst::TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12dff-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="12dff-103">Geçerli tarafından temsil edilen kritik bölümünde girmenizi çalışır [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="12dff-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12dff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12dff-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12dff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12dff-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="12dff-106">[in] Biri [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) konak sürebilir, hangi eylemini belirten değerleri, işlem engeller.</span><span class="sxs-lookup"><span data-stu-id="12dff-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="12dff-107">[out] `true` kritik bölüm olabiliyorsa, girilen; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="12dff-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12dff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="12dff-108">Return Value</span></span>  
  
|<span data-ttu-id="12dff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12dff-109">HRESULT</span></span>|<span data-ttu-id="12dff-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12dff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12dff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="12dff-111">S_OK</span></span>|<span data-ttu-id="12dff-112">`TryEnter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="12dff-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="12dff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12dff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12dff-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="12dff-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="12dff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="12dff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="12dff-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="12dff-116">The call timed out.</span></span>|  
|<span data-ttu-id="12dff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="12dff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="12dff-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="12dff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="12dff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="12dff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="12dff-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="12dff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="12dff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12dff-121">E_FAIL</span></span>|<span data-ttu-id="12dff-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="12dff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="12dff-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="12dff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="12dff-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="12dff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12dff-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12dff-125">Remarks</span></span>  
 <span data-ttu-id="12dff-126">`TryEnter` hemen döndüren ve çağıran iş parçacığı, kritik bölüm girilen olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12dff-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="12dff-127">Bu yöntem Wind32 yansıtır `TryEnterCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="12dff-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12dff-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12dff-128">Requirements</span></span>  
 <span data-ttu-id="12dff-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12dff-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12dff-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="12dff-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12dff-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="12dff-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12dff-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12dff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dff-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12dff-133">See also</span></span>

- [<span data-ttu-id="12dff-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12dff-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="12dff-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12dff-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="12dff-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12dff-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
