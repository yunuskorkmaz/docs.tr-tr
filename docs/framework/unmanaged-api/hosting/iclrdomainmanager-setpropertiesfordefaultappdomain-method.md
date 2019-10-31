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
ms.openlocfilehash: 37919be2d0ebd7d243615bc5845b0781ac13e574
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129311"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="6aef3-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6aef3-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="6aef3-103">Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6aef3-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aef3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6aef3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aef3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6aef3-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="6aef3-106">'ndaki `pwszPropertyNames` ve `pwszPropertyValues`giriş sayısı.</span><span class="sxs-lookup"><span data-stu-id="6aef3-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="6aef3-107">'ndaki Özellik adları dizisi veya özellik yoksa null.</span><span class="sxs-lookup"><span data-stu-id="6aef3-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="6aef3-108">Şu anda, bu yöntemin tanıdığı tek özellik adı "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="6aef3-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="6aef3-109">'ndaki Özellik değerleri dizisi veya özellik yoksa null.</span><span class="sxs-lookup"><span data-stu-id="6aef3-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6aef3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6aef3-110">Return Value</span></span>  
 <span data-ttu-id="6aef3-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="6aef3-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6aef3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6aef3-112">HRESULT</span></span>|<span data-ttu-id="6aef3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6aef3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6aef3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6aef3-114">S_OK</span></span>|<span data-ttu-id="6aef3-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6aef3-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="6aef3-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="6aef3-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="6aef3-117">`pwszPropertyNames`, bu yöntem tarafından tanınmayan bir özellik adı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6aef3-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6aef3-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6aef3-118">Remarks</span></span>  
 <span data-ttu-id="6aef3-119">"PARTIAL_TRUST_VISIBLE_ASSEMBLIES" için özellik değeri, varsayılan uygulama etki alanında kısmen güvenilen çağıranlara görünür hale getirilme <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> bayrağıyla koşullu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğine sahip derlemelerin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="6aef3-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aef3-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6aef3-120">Requirements</span></span>  
 <span data-ttu-id="6aef3-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aef3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aef3-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6aef3-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6aef3-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6aef3-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6aef3-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aef3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aef3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aef3-125">See also</span></span>

- [<span data-ttu-id="6aef3-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="6aef3-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="6aef3-127">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6aef3-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
