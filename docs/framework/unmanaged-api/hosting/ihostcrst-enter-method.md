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
ms.openlocfilehash: 3a54135a0daff3f207d1365d2c27335440f7f1fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763781"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="58223-102">IHostCrst::Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58223-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="58223-103">Geçerli tarafından temsil edilen kritik bölüm girer [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="58223-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58223-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58223-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58223-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58223-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="58223-106">[in] Biri [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) konak sürebilir, hangi eylemini belirten değerleri, işlem engeller.</span><span class="sxs-lookup"><span data-stu-id="58223-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58223-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58223-107">Return Value</span></span>  
  
|<span data-ttu-id="58223-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58223-108">HRESULT</span></span>|<span data-ttu-id="58223-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58223-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58223-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="58223-110">S_OK</span></span>|<span data-ttu-id="58223-111">`Enter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="58223-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="58223-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58223-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58223-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="58223-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58223-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58223-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58223-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="58223-115">The call timed out.</span></span>|  
|<span data-ttu-id="58223-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58223-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58223-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="58223-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58223-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58223-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58223-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="58223-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58223-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58223-120">E_FAIL</span></span>|<span data-ttu-id="58223-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="58223-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58223-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="58223-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58223-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="58223-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58223-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58223-124">Remarks</span></span>  
 <span data-ttu-id="58223-125">`Enter` Win32 yansıtır `EnterCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="58223-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58223-126">Bu yöntem, kritik bölüm girilene kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="58223-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58223-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58223-127">Requirements</span></span>  
 <span data-ttu-id="58223-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58223-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58223-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58223-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58223-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="58223-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58223-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58223-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58223-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58223-132">See also</span></span>

- [<span data-ttu-id="58223-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58223-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="58223-134">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58223-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="58223-135">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58223-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
