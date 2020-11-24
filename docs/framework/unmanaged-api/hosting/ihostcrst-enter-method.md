---
title: IHostCrst::Enter Yöntemi
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: a5c2646d7c9dbf8a7aea4a7fb9bd0a6b8c1d5d66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680560"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="39851-102">IHostCrst::Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39851-102">IHostCrst::Enter Method</span></span>

<span data-ttu-id="39851-103">Geçerli [IHostCrst](ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölüme girer.</span><span class="sxs-lookup"><span data-stu-id="39851-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39851-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="39851-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39851-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39851-105">Parameters</span></span>  

 `option`  
 <span data-ttu-id="39851-106">'ndaki [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="39851-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39851-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="39851-107">Return Value</span></span>  
  
|<span data-ttu-id="39851-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39851-108">HRESULT</span></span>|<span data-ttu-id="39851-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39851-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39851-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="39851-110">S_OK</span></span>|<span data-ttu-id="39851-111">`Enter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="39851-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="39851-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="39851-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="39851-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="39851-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="39851-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="39851-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="39851-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="39851-115">The call timed out.</span></span>|  
|<span data-ttu-id="39851-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="39851-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="39851-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="39851-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="39851-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="39851-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="39851-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="39851-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="39851-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="39851-120">E_FAIL</span></span>|<span data-ttu-id="39851-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="39851-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="39851-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="39851-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="39851-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="39851-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39851-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39851-124">Remarks</span></span>  

 <span data-ttu-id="39851-125">`Enter` Win32 işlevini yansıtır `EnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="39851-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39851-126">Bu yöntem, kritik bölüm girilene kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="39851-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39851-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39851-127">Requirements</span></span>  

 <span data-ttu-id="39851-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39851-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39851-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="39851-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39851-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="39851-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39851-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39851-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39851-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39851-132">See also</span></span>

- [<span data-ttu-id="39851-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39851-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="39851-134">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39851-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="39851-135">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39851-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
