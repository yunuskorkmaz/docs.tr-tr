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
ms.openlocfilehash: 02f36068f12bf0a40e5f0ac477803abfb84c72a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729544"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="bde78-102">IHostCrst::TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bde78-102">IHostCrst::TryEnter Method</span></span>

<span data-ttu-id="bde78-103">Geçerli [IHostCrst](ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölümü girmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="bde78-103">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde78-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bde78-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bde78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bde78-105">Parameters</span></span>  

 `option`  
 <span data-ttu-id="bde78-106">'ndaki [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bde78-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="bde78-107">[out] `true` kritik bölüm girilirse, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="bde78-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bde78-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bde78-108">Return Value</span></span>  
  
|<span data-ttu-id="bde78-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bde78-109">HRESULT</span></span>|<span data-ttu-id="bde78-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bde78-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bde78-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bde78-111">S_OK</span></span>|<span data-ttu-id="bde78-112">`TryEnter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bde78-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="bde78-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bde78-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bde78-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bde78-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bde78-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bde78-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bde78-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bde78-116">The call timed out.</span></span>|  
|<span data-ttu-id="bde78-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bde78-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bde78-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bde78-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bde78-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bde78-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bde78-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bde78-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bde78-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bde78-121">E_FAIL</span></span>|<span data-ttu-id="bde78-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bde78-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bde78-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bde78-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bde78-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bde78-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bde78-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bde78-125">Remarks</span></span>  

 <span data-ttu-id="bde78-126">`TryEnter` hemen döndürür ve çağıran iş parçacığının kritik bölüme girilip girilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bde78-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="bde78-127">Bu yöntem Wind32 işlevini yansıtır `TryEnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="bde78-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde78-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bde78-128">Requirements</span></span>  

 <span data-ttu-id="bde78-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bde78-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde78-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bde78-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bde78-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bde78-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bde78-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bde78-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde78-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bde78-133">See also</span></span>

- [<span data-ttu-id="bde78-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bde78-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="bde78-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bde78-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="bde78-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bde78-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
