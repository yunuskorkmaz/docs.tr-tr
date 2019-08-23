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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdc597e741023af1c7cc1f48e378083157dd4a5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937748"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="2d161-102">IHostCrst::Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d161-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="2d161-103">Geçerli [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölüme girer.</span><span class="sxs-lookup"><span data-stu-id="2d161-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d161-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d161-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d161-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d161-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="2d161-106">'ndaki [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d161-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d161-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d161-107">Return Value</span></span>  
  
|<span data-ttu-id="2d161-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d161-108">HRESULT</span></span>|<span data-ttu-id="2d161-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d161-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d161-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d161-110">S_OK</span></span>|<span data-ttu-id="2d161-111">`Enter`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2d161-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="2d161-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d161-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d161-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2d161-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d161-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d161-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d161-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2d161-115">The call timed out.</span></span>|  
|<span data-ttu-id="2d161-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d161-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d161-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2d161-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d161-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d161-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d161-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2d161-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d161-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d161-120">E_FAIL</span></span>|<span data-ttu-id="2d161-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2d161-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d161-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2d161-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d161-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d161-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d161-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d161-124">Remarks</span></span>  
 <span data-ttu-id="2d161-125">`Enter`Win32 `EnterCriticalSection` işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="2d161-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d161-126">Bu yöntem, kritik bölüm girilene kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="2d161-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d161-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d161-127">Requirements</span></span>  
 <span data-ttu-id="2d161-128">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d161-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d161-129">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d161-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d161-130">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2d161-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d161-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d161-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d161-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d161-132">See also</span></span>

- [<span data-ttu-id="2d161-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d161-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="2d161-134">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d161-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="2d161-135">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d161-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
