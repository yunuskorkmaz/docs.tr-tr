---
title: IHostPolicyManager::OnTimeout Yöntemi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75e6ff3b2b7c8f4b8611630092203aace0ce3136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781024"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="96a0e-102">IHostPolicyManager::OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a0e-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="96a0e-103">Ortak dil çalışma zamanı (CLR) için bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere bir konağa bildirir [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemi yanıt olarak bir zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="96a0e-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96a0e-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96a0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96a0e-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="96a0e-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) zaman aşımına uğradı işlem türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="96a0e-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="96a0e-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, CLR eylemini belirten sürüyor yanıt olarak zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="96a0e-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96a0e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="96a0e-108">Return Value</span></span>  
  
|<span data-ttu-id="96a0e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96a0e-109">HRESULT</span></span>|<span data-ttu-id="96a0e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96a0e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96a0e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="96a0e-111">S_OK</span></span>|<span data-ttu-id="96a0e-112">`OnTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="96a0e-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="96a0e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="96a0e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="96a0e-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="96a0e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="96a0e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="96a0e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="96a0e-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="96a0e-116">The call timed out.</span></span>|  
|<span data-ttu-id="96a0e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="96a0e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="96a0e-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="96a0e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="96a0e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="96a0e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="96a0e-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="96a0e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="96a0e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="96a0e-121">E_FAIL</span></span>|<span data-ttu-id="96a0e-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="96a0e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="96a0e-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="96a0e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="96a0e-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="96a0e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96a0e-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96a0e-125">Requirements</span></span>  
 <span data-ttu-id="96a0e-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96a0e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96a0e-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96a0e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96a0e-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="96a0e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96a0e-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96a0e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a0e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96a0e-130">See also</span></span>

- [<span data-ttu-id="96a0e-131">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="96a0e-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="96a0e-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="96a0e-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="96a0e-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96a0e-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="96a0e-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96a0e-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
