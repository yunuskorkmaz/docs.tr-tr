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
ms.openlocfilehash: e8a14dd6a6d196cea9caa6be669b2b75a167eca8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141122"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="b588b-102">IHostPolicyManager::OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b588b-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="b588b-103">Ortak dil çalışma zamanının (CLR) bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemine yapılan bir çağrı ile belirtilen eylemi gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b588b-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b588b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b588b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b588b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b588b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="b588b-106">'ndaki [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerlerinden biri, zaman aşımına uğrayan işlem türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b588b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="b588b-107">'ndaki Yanıt zaman aşımına uğramasıyla CLR 'nin aldığı eylemi belirten [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="b588b-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b588b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b588b-108">Return Value</span></span>  
  
|<span data-ttu-id="b588b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b588b-109">HRESULT</span></span>|<span data-ttu-id="b588b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b588b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b588b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b588b-111">S_OK</span></span>|<span data-ttu-id="b588b-112">`OnTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b588b-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="b588b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b588b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b588b-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b588b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b588b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b588b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b588b-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b588b-116">The call timed out.</span></span>|  
|<span data-ttu-id="b588b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b588b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b588b-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b588b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b588b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b588b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b588b-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b588b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b588b-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="b588b-121">E_FAIL</span></span>|<span data-ttu-id="b588b-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b588b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b588b-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b588b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b588b-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b588b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b588b-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b588b-125">Requirements</span></span>  
 <span data-ttu-id="b588b-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b588b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b588b-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b588b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b588b-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b588b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b588b-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b588b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b588b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b588b-130">See also</span></span>

- [<span data-ttu-id="b588b-131">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b588b-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="b588b-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b588b-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="b588b-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b588b-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="b588b-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b588b-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
