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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45167a2b358b9a7a39390c07f552aa3f3dabce4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108660"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="7f1e3-102">IHostPolicyManager::OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f1e3-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="7f1e3-103">Ortak dil çalışma zamanı (CLR) için bir çağrı tarafından ayarlanmış varsayılan eylem gerçekleştirmek üzere bir konağa bildirir [Iclrpolicymanager::setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) yanıt olarak bir iş parçacığı durdurma yöntemi veya <xref:System.AppDomain> kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f1e3-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f1e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f1e3-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="7f1e3-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) CLR yanıt olay türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="7f1e3-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) CLR olaya yanıt olarak alma eylemini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f1e3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f1e3-108">Return Value</span></span>  
  
|<span data-ttu-id="7f1e3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f1e3-109">HRESULT</span></span>|<span data-ttu-id="7f1e3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f1e3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f1e3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f1e3-111">S_OK</span></span>|`OnDefaultAction` <span data-ttu-id="7f1e3-112">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-112">returned successfully.</span></span>|  
|<span data-ttu-id="7f1e3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f1e3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f1e3-114">CLR'yi bir işleme yüklü değil veya CLR içinde bunu yapamazsınız yönetilen kodu çalıştırmak veya çağrısı işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="7f1e3-115">başarıyla</span><span class="sxs-lookup"><span data-stu-id="7f1e3-115">successfully</span></span>|  
|<span data-ttu-id="7f1e3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f1e3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f1e3-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-117">The call timed out.</span></span>|  
|<span data-ttu-id="7f1e3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f1e3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f1e3-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f1e3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f1e3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f1e3-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f1e3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f1e3-122">E_FAIL</span></span>|<span data-ttu-id="7f1e3-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f1e3-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f1e3-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f1e3-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f1e3-126">Requirements</span></span>  
 <span data-ttu-id="7f1e3-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f1e3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1e3-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f1e3-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f1e3-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7f1e3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7f1e3-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7f1e3-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f1e3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f1e3-131">See also</span></span>

- [<span data-ttu-id="7f1e3-132">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7f1e3-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="7f1e3-133">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7f1e3-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="7f1e3-134">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f1e3-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="7f1e3-135">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f1e3-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
