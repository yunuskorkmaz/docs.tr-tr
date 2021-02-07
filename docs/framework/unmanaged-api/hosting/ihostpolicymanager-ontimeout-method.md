---
description: 'Şu konuda daha fazla bilgi edinin: IHostPolicyManager:: OnTimeout yöntemi'
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
ms.openlocfilehash: 3a4b1dcf632a0a67c541cacf7c872b3f994e8a07
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671834"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="34f3c-103">IHostPolicyManager::OnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34f3c-103">IHostPolicyManager::OnTimeout Method</span></span>

<span data-ttu-id="34f3c-104">Ortak dil çalışma zamanının (CLR) bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) yöntemine yapılan bir çağrı ile belirtilen eylemi gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="34f3c-104">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f3c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34f3c-105">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34f3c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34f3c-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="34f3c-107">'ndaki [EClrOperation](eclroperation-enumeration.md) değerlerinden biri, zaman aşımına uğrayan işlem türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="34f3c-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="34f3c-108">'ndaki Yanıt zaman aşımına uğramasıyla CLR 'nin aldığı eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="34f3c-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34f3c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34f3c-109">Return Value</span></span>  
  
|<span data-ttu-id="34f3c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34f3c-110">HRESULT</span></span>|<span data-ttu-id="34f3c-111">Description</span><span class="sxs-lookup"><span data-stu-id="34f3c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34f3c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="34f3c-112">S_OK</span></span>|<span data-ttu-id="34f3c-113">`OnTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="34f3c-113">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="34f3c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34f3c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34f3c-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="34f3c-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34f3c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34f3c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34f3c-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="34f3c-117">The call timed out.</span></span>|  
|<span data-ttu-id="34f3c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34f3c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34f3c-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="34f3c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34f3c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34f3c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34f3c-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="34f3c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34f3c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34f3c-122">E_FAIL</span></span>|<span data-ttu-id="34f3c-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="34f3c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34f3c-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="34f3c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34f3c-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="34f3c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34f3c-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34f3c-126">Requirements</span></span>  

 <span data-ttu-id="34f3c-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34f3c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f3c-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34f3c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34f3c-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="34f3c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34f3c-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34f3c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f3c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34f3c-131">See also</span></span>

- [<span data-ttu-id="34f3c-132">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="34f3c-132">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="34f3c-133">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="34f3c-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="34f3c-134">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34f3c-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="34f3c-135">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34f3c-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
