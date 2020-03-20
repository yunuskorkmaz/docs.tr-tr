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
ms.openlocfilehash: d5b5fa5198ae2c0bba30ae0f8d6d3834f2891672
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178012"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="1af2a-102">IHostPolicyManager::OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1af2a-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="1af2a-103">Ortak dil çalışma zamanının (CLR) [iCLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemiile bir zaman anına yanıt olarak bir çağrı tarafından belirtilen eylemi yapmak üzere olduğunu ana bilgisayara ilettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1af2a-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1af2a-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1af2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1af2a-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="1af2a-106">[içinde] Zaman lanmış operasyonun türünü gösteren [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1af2a-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="1af2a-107">[içinde] CLR'nin zaman anına yanıt olarak aldığı eylemi gösteren [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1af2a-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1af2a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1af2a-108">Return Value</span></span>  
  
|<span data-ttu-id="1af2a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1af2a-109">HRESULT</span></span>|<span data-ttu-id="1af2a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1af2a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1af2a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1af2a-111">S_OK</span></span>|<span data-ttu-id="1af2a-112">`OnTimeout`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1af2a-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="1af2a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1af2a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1af2a-114">CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="1af2a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1af2a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1af2a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1af2a-116">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="1af2a-116">The call timed out.</span></span>|  
|<span data-ttu-id="1af2a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1af2a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1af2a-118">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="1af2a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1af2a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1af2a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1af2a-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1af2a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1af2a-121">E_faıl</span><span class="sxs-lookup"><span data-stu-id="1af2a-121">E_FAIL</span></span>|<span data-ttu-id="1af2a-122">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="1af2a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1af2a-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1af2a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1af2a-124">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="1af2a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1af2a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1af2a-125">Requirements</span></span>  
 <span data-ttu-id="1af2a-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1af2a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1af2a-127">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1af2a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1af2a-128">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="1af2a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1af2a-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1af2a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af2a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1af2a-130">See also</span></span>

- [<span data-ttu-id="1af2a-131">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1af2a-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="1af2a-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1af2a-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="1af2a-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1af2a-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="1af2a-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1af2a-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
