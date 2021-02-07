---
description: ': ICLRDomainManager:: SetPropertiesForDefaultAppDomain Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 08e6c885d5d089fa22c30a4e3cef69480b840031
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689449"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="a5f8f-103">ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5f8f-103">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>

<span data-ttu-id="a5f8f-104">Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-104">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f8f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5f8f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5f8f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5f8f-106">Parameters</span></span>  

 `nProperties`  
 <span data-ttu-id="a5f8f-107">'ndaki Ve içindeki giriş sayısı `pwszPropertyNames` `pwszPropertyValues` .</span><span class="sxs-lookup"><span data-stu-id="a5f8f-107">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="a5f8f-108">'ndaki Özellik adları dizisi veya özellik yoksa null.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-108">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="a5f8f-109">Şu anda, bu yöntemin tanıdığı tek özellik adı "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="a5f8f-109">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="a5f8f-110">'ndaki Özellik değerleri dizisi veya özellik yoksa null.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-110">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5f8f-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a5f8f-111">Return Value</span></span>  

 <span data-ttu-id="a5f8f-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5f8f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5f8f-113">HRESULT</span></span>|<span data-ttu-id="a5f8f-114">Description</span><span class="sxs-lookup"><span data-stu-id="a5f8f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5f8f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5f8f-115">S_OK</span></span>|<span data-ttu-id="a5f8f-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a5f8f-117">HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="a5f8f-117">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="a5f8f-118">`pwszPropertyNames` Bu yöntem tarafından tanınmayan bir özellik adı içerir.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-118">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5f8f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5f8f-119">Remarks</span></span>  

 <span data-ttu-id="a5f8f-120">"PARTIAL_TRUST_VISIBLE_ASSEMBLIES" için özellik değeri, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> Varsayılan uygulama etki alanında kısmen güvenilen çağıranlara görünür hale getirilme bayrağıyla koşullu (aptca) özniteliği olan derlemelerin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-120">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5f8f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5f8f-121">Requirements</span></span>  

 <span data-ttu-id="a5f8f-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5f8f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5f8f-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a5f8f-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a5f8f-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a5f8f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5f8f-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5f8f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f8f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f8f-126">See also</span></span>

- [<span data-ttu-id="a5f8f-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="a5f8f-127">Hosting</span></span>](index.md)
- [<span data-ttu-id="a5f8f-128">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5f8f-128">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
