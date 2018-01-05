---
title: "ICLRHostProtectionManager::SetProtectedCategories Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetProtectedCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0971e93f02420966d6561c5b7d4dce8b75e222fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="a15c4-102">ICLRHostProtectionManager::SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a15c4-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="a15c4-103">Yönetilen türler ve üyeleri kategorilerini kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a15c4-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a15c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a15c4-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a15c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a15c4-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="a15c4-106">[in] Bir birleşimini [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) Kategorilerini yönetilen tür ve üye kısmen güvenilen kodu çalıştırma engellenmesi gerektiğini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="a15c4-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a15c4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a15c4-107">Return Value</span></span>  
  
|<span data-ttu-id="a15c4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a15c4-108">HRESULT</span></span>|<span data-ttu-id="a15c4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a15c4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a15c4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a15c4-110">S_OK</span></span>|<span data-ttu-id="a15c4-111">`SetProtectedCategories`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a15c4-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="a15c4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a15c4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a15c4-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a15c4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a15c4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a15c4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a15c4-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a15c4-115">The call timed out.</span></span>|  
|<span data-ttu-id="a15c4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a15c4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a15c4-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="a15c4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a15c4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a15c4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a15c4-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="a15c4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a15c4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a15c4-120">E_FAIL</span></span>|<span data-ttu-id="a15c4-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a15c4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a15c4-122">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a15c4-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a15c4-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a15c4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a15c4-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a15c4-124">Remarks</span></span>  
 <span data-ttu-id="a15c4-125">Her `EApiCategories` değeri, yönetilen türler ve üyeleri listesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a15c4-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="a15c4-126">`EApiCategories` Numaralandırma ve `SetProtectedCategories` yöntemi doğrudan ilgili yönetilen için <xref:System.Security.Permissions.HostProtectionAttribute> yönetilen türler ve özellikleri tarafından açıklanan kategoriye karşılık gelen açığa üyeleri işaretlemek için kullanılan sınıf `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="a15c4-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="a15c4-127">Daha fazla bilgi için bkz: <xref:System.Security.Permissions.HostProtectionAttribute> ve <xref:System.Security.Permissions.HostProtectionResource> doğrudan karşılık gelen numaralandırma `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="a15c4-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a15c4-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a15c4-128">Requirements</span></span>  
 <span data-ttu-id="a15c4-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a15c4-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a15c4-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a15c4-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a15c4-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a15c4-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a15c4-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a15c4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a15c4-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a15c4-133">See Also</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [<span data-ttu-id="a15c4-134">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a15c4-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="a15c4-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a15c4-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a15c4-136">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a15c4-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
