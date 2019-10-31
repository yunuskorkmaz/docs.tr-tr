---
title: IHostPolicyManager::OnDefaultAction Yöntemi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: cdf0a720ac440d156b5b8bdc8dc2c78d3bb5ba86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128557"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="8b550-102">IHostPolicyManager::OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b550-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="8b550-103">Ortak dil çalışma zamanının (CLR), bir iş parçacığı iptali veya <xref:System.AppDomain> bellekten yanıt olarak [ICLRPolicyManager:: SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) yöntemine yapılan bir çağrı tarafından ayarlanan varsayılan eylemi almak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8b550-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b550-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b550-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b550-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b550-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="8b550-106">'ndaki CLR 'nin yanıt verdiğini belirten olay türünü gösteren [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="8b550-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="8b550-107">'ndaki CLR 'nin olaya yanıt olarak ele aldığı eylemi belirten [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="8b550-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b550-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b550-108">Return Value</span></span>  
  
|<span data-ttu-id="8b550-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b550-109">HRESULT</span></span>|<span data-ttu-id="8b550-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b550-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b550-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b550-111">S_OK</span></span>|<span data-ttu-id="8b550-112">`OnDefaultAction` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8b550-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="8b550-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b550-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b550-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8b550-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="8b550-115">yararlanan</span><span class="sxs-lookup"><span data-stu-id="8b550-115">successfully</span></span>|  
|<span data-ttu-id="8b550-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b550-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b550-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8b550-117">The call timed out.</span></span>|  
|<span data-ttu-id="8b550-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b550-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b550-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b550-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b550-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b550-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b550-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8b550-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b550-122">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="8b550-122">E_FAIL</span></span>|<span data-ttu-id="8b550-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8b550-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b550-124">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b550-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b550-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b550-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b550-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b550-126">Requirements</span></span>  
 <span data-ttu-id="8b550-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b550-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b550-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b550-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b550-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8b550-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b550-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b550-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b550-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b550-131">See also</span></span>

- [<span data-ttu-id="8b550-132">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8b550-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="8b550-133">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8b550-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="8b550-134">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b550-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="8b550-135">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b550-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
