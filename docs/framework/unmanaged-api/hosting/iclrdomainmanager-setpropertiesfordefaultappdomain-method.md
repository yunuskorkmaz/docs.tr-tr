---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c42297e848844617ffdc6c85c81846b5805eb4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181361"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="e9c68-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9c68-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="e9c68-103">Varsayılan uygulama etki alanı başlatmak için kullanılacak özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e9c68-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9c68-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9c68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9c68-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="e9c68-106">[in] Giriş sayısı `pwszPropertyNames` ve `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="e9c68-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="e9c68-107">[in] Bir dizi özellik adları ya da hiçbir özelliği yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e9c68-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="e9c68-108">Şu anda, bu yöntem tarafından tanınan tek özellik adı "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" ' dir.</span><span class="sxs-lookup"><span data-stu-id="e9c68-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="e9c68-109">[in] Bir dizi özellik değerlerini ya da hiçbir özelliği yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e9c68-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9c68-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9c68-110">Return Value</span></span>  
 <span data-ttu-id="e9c68-111">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e9c68-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e9c68-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9c68-112">HRESULT</span></span>|<span data-ttu-id="e9c68-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9c68-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9c68-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9c68-114">S_OK</span></span>|<span data-ttu-id="e9c68-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e9c68-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="e9c68-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="e9c68-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|`pwszPropertyNames` <span data-ttu-id="e9c68-117">Bu yöntem tarafından tanınmayan bir özellik adı içerir.</span><span class="sxs-lookup"><span data-stu-id="e9c68-117">includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9c68-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9c68-118">Remarks</span></span>  
 <span data-ttu-id="e9c68-119">Koşullu sahip bir derleme listesi "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" özellik değeri olan <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğiyle <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> varsayılan uygulamada görünür için kısmen güvenilmeyen çağrıcılara yapılacağı bayrak etki alanı.</span><span class="sxs-lookup"><span data-stu-id="e9c68-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9c68-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9c68-120">Requirements</span></span>  
 <span data-ttu-id="e9c68-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9c68-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9c68-122">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e9c68-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e9c68-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9c68-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e9c68-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e9c68-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e9c68-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9c68-125">See also</span></span>

- [<span data-ttu-id="e9c68-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e9c68-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="e9c68-127">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9c68-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
