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
ms.openlocfilehash: f4b40a595bbdea4dd390a42af6a0d4b1a5efa2f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130503"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="8c7a7-102">IHostCrst::TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c7a7-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="8c7a7-103">Geçerli [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölümü girmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c7a7-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c7a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c7a7-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="8c7a7-106">'ndaki [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="8c7a7-107">[out] kritik bölüm girilebileceği `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c7a7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8c7a7-108">Return Value</span></span>  
  
|<span data-ttu-id="8c7a7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c7a7-109">HRESULT</span></span>|<span data-ttu-id="8c7a7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c7a7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c7a7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c7a7-111">S_OK</span></span>|<span data-ttu-id="8c7a7-112">`TryEnter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="8c7a7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c7a7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c7a7-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c7a7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c7a7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c7a7-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-116">The call timed out.</span></span>|  
|<span data-ttu-id="8c7a7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c7a7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c7a7-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c7a7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c7a7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c7a7-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c7a7-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="8c7a7-121">E_FAIL</span></span>|<span data-ttu-id="8c7a7-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c7a7-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c7a7-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c7a7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c7a7-125">Remarks</span></span>  
 <span data-ttu-id="8c7a7-126">`TryEnter` hemen döndürür ve çağıran iş parçacığının kritik bölüme girilip girilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="8c7a7-127">Bu yöntem, Wind32 `TryEnterCriticalSection` işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c7a7-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c7a7-128">Requirements</span></span>  
 <span data-ttu-id="8c7a7-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c7a7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c7a7-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c7a7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c7a7-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8c7a7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c7a7-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c7a7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c7a7-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-133">See also</span></span>

- [<span data-ttu-id="8c7a7-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c7a7-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8c7a7-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c7a7-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="8c7a7-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c7a7-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
