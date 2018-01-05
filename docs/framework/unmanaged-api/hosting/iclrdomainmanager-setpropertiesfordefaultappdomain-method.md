---
title: "ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de72568f5908dc89c9a4105c927cfba6c7366b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="e7f0e-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7f0e-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="e7f0e-103">Varsayılan uygulama etki alanı başlatmak için kullanılan özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7f0e-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7f0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7f0e-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="e7f0e-106">[in] Giriş sayısı `pwszPropertyNames` ve `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="e7f0e-107">[in] Bir dizi özellik adları ya da hiçbir özelliği yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="e7f0e-108">Şu anda, bu yöntem tarafından tanınan tek özellik adı "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" ' dir.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="e7f0e-109">[in] Bir dizi özellik değerlerini ya da hiçbir özelliği yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7f0e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e7f0e-110">Return Value</span></span>  
 <span data-ttu-id="e7f0e-111">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e7f0e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7f0e-112">HRESULT</span></span>|<span data-ttu-id="e7f0e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7f0e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7f0e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7f0e-114">S_OK</span></span>|<span data-ttu-id="e7f0e-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="e7f0e-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="e7f0e-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="e7f0e-117">`pwszPropertyNames`Bu yöntem tarafından tanınmayan bir özellik adı içerir.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7f0e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7f0e-118">Remarks</span></span>  
 <span data-ttu-id="e7f0e-119">Koşullu sahip bir derleme listesi "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" için özellik değeri olan <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğiyle <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> varsayılan uygulamada kısmen güvenilen arayanlara görünür yapılacağı bayrağı etki alanı.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f0e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7f0e-120">Requirements</span></span>  
 <span data-ttu-id="e7f0e-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7f0e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f0e-122">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e7f0e-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e7f0e-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e7f0e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7f0e-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7f0e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f0e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7f0e-125">See Also</span></span>  
 [<span data-ttu-id="e7f0e-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e7f0e-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="e7f0e-127">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7f0e-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
