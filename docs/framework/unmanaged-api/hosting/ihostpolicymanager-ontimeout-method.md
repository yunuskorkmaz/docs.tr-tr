---
title: "IHostPolicyManager::OnTimeout Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 272f78077c1d512fe574eebeaf6c92dc1939f6b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="53164-102">IHostPolicyManager::OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53164-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="53164-103">Ortak dil çalışma zamanı (CLR) için yapılan bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere olan konak bildirir [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemi yanıt olarak bir zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="53164-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53164-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53164-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53164-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53164-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="53164-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) zaman aşımına uğradı işlemi türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="53164-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="53164-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, CLR eylemini belirten sürüyor yanıt olarak zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="53164-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53164-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="53164-108">Return Value</span></span>  
  
|<span data-ttu-id="53164-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53164-109">HRESULT</span></span>|<span data-ttu-id="53164-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53164-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53164-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="53164-111">S_OK</span></span>|<span data-ttu-id="53164-112">`OnTimeout`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="53164-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="53164-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53164-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53164-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="53164-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53164-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53164-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53164-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="53164-116">The call timed out.</span></span>|  
|<span data-ttu-id="53164-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53164-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53164-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="53164-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53164-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53164-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53164-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="53164-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53164-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53164-121">E_FAIL</span></span>|<span data-ttu-id="53164-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="53164-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53164-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="53164-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53164-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="53164-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53164-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53164-125">Requirements</span></span>  
 <span data-ttu-id="53164-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53164-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53164-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53164-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53164-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="53164-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53164-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53164-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53164-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53164-130">See Also</span></span>  
 [<span data-ttu-id="53164-131">EClrOperation numaralandırması</span><span class="sxs-lookup"><span data-stu-id="53164-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="53164-132">EPolicyAction numaralandırması</span><span class="sxs-lookup"><span data-stu-id="53164-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="53164-133">Iclrpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="53164-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="53164-134">Ihostpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="53164-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
