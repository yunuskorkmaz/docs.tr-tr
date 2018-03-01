---
title: "ICLRRuntimeHost::ExecuteInAppDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8c540c9618655e6df30ad253e0c4cccdf6624e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="3ea6c-102">ICLRRuntimeHost::ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ea6c-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="3ea6c-103">Belirtir <xref:System.AppDomain> belirtilen yönetilen kod yürütmek üzere.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ea6c-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ea6c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ea6c-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="3ea6c-106">[in] Sayısal kimliği <xref:System.AppDomain> belirtilen yöntem yürütmek üzere.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="3ea6c-107">[in] Belirtilen içinde yürütülecek işlevi için bir işaretçi <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="3ea6c-108">[in] Donuk arayana ayrılan bellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="3ea6c-109">Bu parametre ortak dil çalışma zamanı tarafından (CLR) için etki alanı geri iletilir.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="3ea6c-110">Çalışma zamanı tarafından yönetilen yığın bellek olmadığı; ayırma ve bu bellek ömrü çağıran tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ea6c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3ea6c-111">Return Value</span></span>  
  
|<span data-ttu-id="3ea6c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ea6c-112">HRESULT</span></span>|<span data-ttu-id="3ea6c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ea6c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ea6c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ea6c-114">S_OK</span></span>|<span data-ttu-id="3ea6c-115">`ExecuteInAppDomain`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="3ea6c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ea6c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ea6c-117">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ea6c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ea6c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ea6c-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-119">The call timed out.</span></span>|  
|<span data-ttu-id="3ea6c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ea6c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ea6c-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ea6c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ea6c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ea6c-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ea6c-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ea6c-124">E_FAIL</span></span>|<span data-ttu-id="3ea6c-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ea6c-126">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ea6c-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ea6c-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ea6c-128">Remarks</span></span>  
 <span data-ttu-id="3ea6c-129">`ExecuteInAppDomain`Denetim ana bilgisayar tanır yönetilen üzerinden <xref:System.AppDomain> belirtilen Yönetilen yöntemi içinde yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="3ea6c-130">Değerine karşılık gelen bir uygulama etki alanının tanımlayıcının değerini alabilir <xref:System.AppDomain.Id%2A> çağırarak özelliği, [Getcurrentappdomainıd yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="3ea6c-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea6c-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ea6c-131">Requirements</span></span>  
 <span data-ttu-id="3ea6c-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea6c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea6c-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ea6c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ea6c-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3ea6c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ea6c-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea6c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea6c-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ea6c-136">See Also</span></span>  
 [<span data-ttu-id="3ea6c-137">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ea6c-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
