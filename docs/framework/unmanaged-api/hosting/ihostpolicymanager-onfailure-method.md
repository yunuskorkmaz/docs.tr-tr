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
ms.openlocfilehash: 87b4d4a9606723e5cf55fac19469809e1014b7c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439693"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="32602-102">IHostPolicyManager::OnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32602-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="32602-103">Ortak dil çalışma zamanı (CLR) için yapılan bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere olan konak bildirir [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yöntemi yanıt olarak kaynak ayırma veya geri kazanma hatası.</span><span class="sxs-lookup"><span data-stu-id="32602-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32602-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32602-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32602-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32602-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="32602-106">[in] Aşağıdakilerden birini [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hatası CLR yanıt türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="32602-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="32602-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, CLR eylemini belirten sürüyor yanıt olarak `failure`.</span><span class="sxs-lookup"><span data-stu-id="32602-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32602-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32602-108">Return Value</span></span>  
  
|<span data-ttu-id="32602-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32602-109">HRESULT</span></span>|<span data-ttu-id="32602-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32602-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32602-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="32602-111">S_OK</span></span>|<span data-ttu-id="32602-112">`OnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="32602-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="32602-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32602-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32602-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="32602-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="32602-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32602-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32602-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="32602-116">The call timed out.</span></span>|  
|<span data-ttu-id="32602-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32602-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32602-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="32602-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32602-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32602-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32602-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="32602-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32602-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32602-121">E_FAIL</span></span>|<span data-ttu-id="32602-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="32602-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32602-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="32602-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32602-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="32602-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32602-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32602-125">Requirements</span></span>  
 <span data-ttu-id="32602-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32602-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32602-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32602-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32602-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="32602-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32602-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32602-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32602-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32602-130">See Also</span></span>  
 [<span data-ttu-id="32602-131">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="32602-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="32602-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="32602-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="32602-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32602-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="32602-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32602-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
