---
description: ': IHostCrst:: TryEnter yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 59c632b7c9edd422e2ceee1e0526a7bb077759a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708742"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="d9ae1-103">IHostCrst::TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9ae1-103">IHostCrst::TryEnter Method</span></span>

<span data-ttu-id="d9ae1-104">Geçerli [IHostCrst](ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölümü girmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-104">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ae1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9ae1-105">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9ae1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9ae1-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="d9ae1-107">'ndaki [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="d9ae1-108">[out] `true` kritik bölüm girilirse, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="d9ae1-108">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9ae1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9ae1-109">Return Value</span></span>  
  
|<span data-ttu-id="d9ae1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9ae1-110">HRESULT</span></span>|<span data-ttu-id="d9ae1-111">Description</span><span class="sxs-lookup"><span data-stu-id="d9ae1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9ae1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9ae1-112">S_OK</span></span>|<span data-ttu-id="d9ae1-113">`TryEnter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-113">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="d9ae1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9ae1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9ae1-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9ae1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9ae1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9ae1-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-117">The call timed out.</span></span>|  
|<span data-ttu-id="d9ae1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9ae1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9ae1-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9ae1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9ae1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9ae1-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9ae1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9ae1-122">E_FAIL</span></span>|<span data-ttu-id="d9ae1-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9ae1-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9ae1-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9ae1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9ae1-126">Remarks</span></span>  

 <span data-ttu-id="d9ae1-127">`TryEnter` hemen döndürür ve çağıran iş parçacığının kritik bölüme girilip girilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-127">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="d9ae1-128">Bu yöntem Wind32 işlevini yansıtır `TryEnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="d9ae1-128">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ae1-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9ae1-129">Requirements</span></span>  

 <span data-ttu-id="d9ae1-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9ae1-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ae1-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d9ae1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9ae1-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d9ae1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9ae1-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9ae1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ae1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9ae1-134">See also</span></span>

- [<span data-ttu-id="d9ae1-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9ae1-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d9ae1-136">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9ae1-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="d9ae1-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9ae1-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
