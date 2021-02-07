---
description: ': IHostPolicyManager:: OnFailure yöntemi hakkında daha fazla bilgi edinin'
title: IHostPolicyManager::OnFailure Yöntemi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 9fb359d4ba1b1b89e029a0772a0f67a49b2b380b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671847"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="13a29-103">IHostPolicyManager::OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13a29-103">IHostPolicyManager::OnFailure Method</span></span>

<span data-ttu-id="13a29-104">Ortak dil çalışma zamanının (CLR), bir kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) metoduna yapılan bir çağrı ile belirtilen eylemi gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="13a29-104">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a29-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13a29-105">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a29-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13a29-106">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="13a29-107">'ndaki CLR yanıt verdiğini belirten hata türünü gösteren [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="13a29-107">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="13a29-108">'ndaki CLR 'nin yanıt olarak aldığı eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri `failure` .</span><span class="sxs-lookup"><span data-stu-id="13a29-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13a29-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13a29-109">Return Value</span></span>  
  
|<span data-ttu-id="13a29-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13a29-110">HRESULT</span></span>|<span data-ttu-id="13a29-111">Description</span><span class="sxs-lookup"><span data-stu-id="13a29-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13a29-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="13a29-112">S_OK</span></span>|<span data-ttu-id="13a29-113">`OnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13a29-113">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="13a29-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13a29-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13a29-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="13a29-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13a29-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13a29-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13a29-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="13a29-117">The call timed out.</span></span>|  
|<span data-ttu-id="13a29-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13a29-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13a29-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="13a29-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13a29-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13a29-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13a29-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="13a29-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13a29-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13a29-122">E_FAIL</span></span>|<span data-ttu-id="13a29-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="13a29-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13a29-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="13a29-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13a29-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="13a29-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13a29-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13a29-126">Requirements</span></span>  

 <span data-ttu-id="13a29-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a29-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a29-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13a29-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13a29-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="13a29-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13a29-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a29-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a29-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13a29-131">See also</span></span>

- [<span data-ttu-id="13a29-132">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="13a29-132">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="13a29-133">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="13a29-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="13a29-134">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13a29-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="13a29-135">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13a29-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
