---
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
ms.openlocfilehash: efa7b9d49ea9807af2164bb6ee54422dd72b14e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730428"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="3db2d-102">IHostPolicyManager::OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3db2d-102">IHostPolicyManager::OnFailure Method</span></span>

<span data-ttu-id="3db2d-103">Ortak dil çalışma zamanının (CLR), bir kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) metoduna yapılan bir çağrı ile belirtilen eylemi gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3db2d-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db2d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3db2d-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3db2d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3db2d-105">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="3db2d-106">'ndaki CLR yanıt verdiğini belirten hata türünü gösteren [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="3db2d-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="3db2d-107">'ndaki CLR 'nin yanıt olarak aldığı eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri `failure` .</span><span class="sxs-lookup"><span data-stu-id="3db2d-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3db2d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3db2d-108">Return Value</span></span>  
  
|<span data-ttu-id="3db2d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3db2d-109">HRESULT</span></span>|<span data-ttu-id="3db2d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3db2d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3db2d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3db2d-111">S_OK</span></span>|<span data-ttu-id="3db2d-112">`OnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3db2d-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="3db2d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3db2d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3db2d-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3db2d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3db2d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3db2d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3db2d-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3db2d-116">The call timed out.</span></span>|  
|<span data-ttu-id="3db2d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3db2d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3db2d-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3db2d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3db2d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3db2d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3db2d-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3db2d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3db2d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3db2d-121">E_FAIL</span></span>|<span data-ttu-id="3db2d-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3db2d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3db2d-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3db2d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3db2d-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3db2d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3db2d-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3db2d-125">Requirements</span></span>  

 <span data-ttu-id="3db2d-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db2d-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db2d-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3db2d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3db2d-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3db2d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3db2d-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db2d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db2d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3db2d-130">See also</span></span>

- [<span data-ttu-id="3db2d-131">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3db2d-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="3db2d-132">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3db2d-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="3db2d-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3db2d-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="3db2d-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3db2d-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
