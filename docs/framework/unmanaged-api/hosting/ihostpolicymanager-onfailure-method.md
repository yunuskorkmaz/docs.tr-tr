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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78d2b84598a034bf6c534745bcb99a080d039617
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993180"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="d59e8-102">IHostPolicyManager::OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d59e8-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="d59e8-103">Ortak dil çalışma zamanı (CLR) için bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere bir konağa bildirir [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yanıt olarak bir kaynak ayırma veya geri kazanma hatası yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d59e8-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d59e8-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d59e8-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="d59e8-106">[in] Aşağıdakilerden birini [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) CLR yanıt hata türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d59e8-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="d59e8-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, yanıt olarak sürüyor CLR eylemini belirten `failure`.</span><span class="sxs-lookup"><span data-stu-id="d59e8-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59e8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d59e8-108">Return Value</span></span>  
  
|<span data-ttu-id="d59e8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d59e8-109">HRESULT</span></span>|<span data-ttu-id="d59e8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d59e8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d59e8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d59e8-111">S_OK</span></span>|<span data-ttu-id="d59e8-112">`OnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d59e8-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="d59e8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d59e8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d59e8-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d59e8-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d59e8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d59e8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d59e8-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d59e8-116">The call timed out.</span></span>|  
|<span data-ttu-id="d59e8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d59e8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d59e8-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d59e8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d59e8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d59e8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d59e8-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d59e8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d59e8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d59e8-121">E_FAIL</span></span>|<span data-ttu-id="d59e8-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d59e8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d59e8-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d59e8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d59e8-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d59e8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d59e8-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d59e8-125">Requirements</span></span>  
 <span data-ttu-id="d59e8-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59e8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59e8-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d59e8-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d59e8-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d59e8-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d59e8-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59e8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59e8-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d59e8-130">See also</span></span>

- [<span data-ttu-id="d59e8-131">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d59e8-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="d59e8-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d59e8-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="d59e8-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d59e8-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d59e8-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d59e8-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
