---
title: "IHostPolicyManager::OnTimeout Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b8c29bc281b64368e8b310e2b13f3fcb1bdc6ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="6b764-102">IHostPolicyManager::OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b764-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="6b764-103">Ortak dil çalışma zamanı (CLR) için yapılan bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere olan konak bildirir [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemi yanıt olarak bir zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="6b764-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b764-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b764-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b764-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b764-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="6b764-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) zaman aşımına uğradı işlemi türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6b764-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="6b764-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, CLR eylemini belirten sürüyor yanıt olarak zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="6b764-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b764-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b764-108">Return Value</span></span>  
  
|<span data-ttu-id="6b764-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b764-109">HRESULT</span></span>|<span data-ttu-id="6b764-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b764-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b764-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b764-111">S_OK</span></span>|<span data-ttu-id="6b764-112">`OnTimeout`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6b764-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="6b764-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b764-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b764-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6b764-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b764-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b764-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b764-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6b764-116">The call timed out.</span></span>|  
|<span data-ttu-id="6b764-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b764-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b764-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="6b764-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b764-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b764-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b764-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="6b764-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b764-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b764-121">E_FAIL</span></span>|<span data-ttu-id="6b764-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6b764-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b764-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6b764-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b764-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b764-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b764-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b764-125">Requirements</span></span>  
 <span data-ttu-id="6b764-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b764-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b764-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b764-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b764-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6b764-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b764-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b764-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b764-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b764-130">See Also</span></span>  
 [<span data-ttu-id="6b764-131">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6b764-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="6b764-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6b764-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="6b764-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b764-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="6b764-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b764-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
