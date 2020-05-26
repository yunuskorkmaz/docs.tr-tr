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
ms.openlocfilehash: 8ad4943aa9bf1b66b34bcd83a5422a977b16518d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804227"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="6f649-102">IHostPolicyManager::OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f649-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="6f649-103">Ortak dil çalışma zamanının (CLR), bir kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) metoduna yapılan bir çağrı ile belirtilen eylemi gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f649-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f649-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6f649-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f649-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f649-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="6f649-106">'ndaki CLR yanıt verdiğini belirten hata türünü gösteren [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="6f649-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="6f649-107">'ndaki CLR 'nin yanıt olarak aldığı eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri `failure` .</span><span class="sxs-lookup"><span data-stu-id="6f649-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f649-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6f649-108">Return Value</span></span>  
  
|<span data-ttu-id="6f649-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f649-109">HRESULT</span></span>|<span data-ttu-id="6f649-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f649-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f649-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f649-111">S_OK</span></span>|<span data-ttu-id="6f649-112">`OnFailure`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6f649-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="6f649-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f649-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f649-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6f649-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f649-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f649-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f649-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6f649-116">The call timed out.</span></span>|  
|<span data-ttu-id="6f649-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f649-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f649-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6f649-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f649-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f649-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f649-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6f649-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f649-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f649-121">E_FAIL</span></span>|<span data-ttu-id="6f649-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6f649-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f649-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f649-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f649-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f649-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f649-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f649-125">Requirements</span></span>  
 <span data-ttu-id="6f649-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f649-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f649-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f649-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f649-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6f649-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f649-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f649-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f649-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f649-130">See also</span></span>

- [<span data-ttu-id="6f649-131">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6f649-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="6f649-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6f649-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="6f649-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f649-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="6f649-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f649-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
