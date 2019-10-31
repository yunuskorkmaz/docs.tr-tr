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
ms.openlocfilehash: 757fb996b268892818a54a3f80a54edfd89c7630
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124436"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="cb529-102">IHostCrst::Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb529-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="cb529-103">Geçerli [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölüme girer.</span><span class="sxs-lookup"><span data-stu-id="cb529-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb529-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb529-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb529-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb529-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="cb529-106">'ndaki [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb529-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb529-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb529-107">Return Value</span></span>  
  
|<span data-ttu-id="cb529-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb529-108">HRESULT</span></span>|<span data-ttu-id="cb529-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb529-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb529-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb529-110">S_OK</span></span>|<span data-ttu-id="cb529-111">`Enter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cb529-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="cb529-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb529-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb529-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cb529-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb529-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb529-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb529-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb529-115">The call timed out.</span></span>|  
|<span data-ttu-id="cb529-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb529-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb529-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cb529-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb529-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb529-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb529-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cb529-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb529-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="cb529-120">E_FAIL</span></span>|<span data-ttu-id="cb529-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cb529-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb529-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cb529-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb529-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb529-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb529-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb529-124">Remarks</span></span>  
 <span data-ttu-id="cb529-125">`Enter` Win32 `EnterCriticalSection` işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="cb529-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb529-126">Bu yöntem, kritik bölüm girilene kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="cb529-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb529-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb529-127">Requirements</span></span>  
 <span data-ttu-id="cb529-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb529-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb529-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cb529-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb529-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cb529-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb529-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb529-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb529-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb529-132">See also</span></span>

- [<span data-ttu-id="cb529-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb529-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="cb529-134">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb529-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="cb529-135">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb529-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
