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
ms.openlocfilehash: 79afaac4dce1c4baa9802d81af90c425f5de7a08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804916"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="ffcd1-102">IHostCrst::Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffcd1-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="ffcd1-103">Geçerli [IHostCrst](ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölüme girer.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffcd1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ffcd1-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffcd1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ffcd1-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="ffcd1-106">'ndaki [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffcd1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ffcd1-107">Return Value</span></span>  
  
|<span data-ttu-id="ffcd1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffcd1-108">HRESULT</span></span>|<span data-ttu-id="ffcd1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffcd1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffcd1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffcd1-110">S_OK</span></span>|<span data-ttu-id="ffcd1-111">`Enter`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="ffcd1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffcd1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffcd1-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffcd1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffcd1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffcd1-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-115">The call timed out.</span></span>|  
|<span data-ttu-id="ffcd1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffcd1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffcd1-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffcd1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffcd1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffcd1-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffcd1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffcd1-120">E_FAIL</span></span>|<span data-ttu-id="ffcd1-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffcd1-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffcd1-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffcd1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffcd1-124">Remarks</span></span>  
 <span data-ttu-id="ffcd1-125">`Enter`Win32 işlevini yansıtır `EnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="ffcd1-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffcd1-126">Bu yöntem, kritik bölüm girilene kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffcd1-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffcd1-127">Requirements</span></span>  
 <span data-ttu-id="ffcd1-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffcd1-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffcd1-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ffcd1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffcd1-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ffcd1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffcd1-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffcd1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffcd1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffcd1-132">See also</span></span>

- [<span data-ttu-id="ffcd1-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffcd1-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="ffcd1-134">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffcd1-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="ffcd1-135">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffcd1-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
