---
title: "ICLRDomainManager::SetAppDomainManagerType Yöntemi"
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
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 37c94da8295a0ebb96d45e3a8f122d96bc2126c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="abc81-102">ICLRDomainManager::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abc81-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="abc81-103">Öğesinden türetilen tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılan uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="abc81-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abc81-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abc81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abc81-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="abc81-106">[in] Uygulama etki alanı yöneticisi türünü içeren bütünleştirilmiş kodun görünen adını; Örneğin: "AdMgrExample, sürüm 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3 =".</span><span class="sxs-lookup"><span data-stu-id="abc81-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="abc81-107">[in] Ad alanı dahil olmak üzere uygulama etki alanı yöneticisi türü adı.</span><span class="sxs-lookup"><span data-stu-id="abc81-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="abc81-108">[in] Bir birleşimini [Eınitializenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) uygulama etki alanı yöneticisi hakkında bilgi sağlayan numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="abc81-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abc81-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="abc81-109">Return Value</span></span>  
 <span data-ttu-id="abc81-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="abc81-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="abc81-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abc81-111">HRESULT</span></span>|<span data-ttu-id="abc81-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abc81-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abc81-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="abc81-113">S_OK</span></span>|<span data-ttu-id="abc81-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="abc81-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="abc81-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="abc81-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="abc81-116">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="abc81-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abc81-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abc81-117">Remarks</span></span>  
 <span data-ttu-id="abc81-118">Şu anda yalnızca tanımlı bir değer için `dwInitializeDomainFlags` olan `eInitializeNewDomainFlags_NoSecurityChanges`, uygulama etki alanı yöneticisi yürütülmesi sırasında güvenlik ayarlarını değiştirmez ortak dil çalışma zamanı (CLR) söyleyen <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="abc81-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="abc81-119">Bu koşul olan derlemeler yüklenmesini iyileştirmek CLR sağlar <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="abc81-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="abc81-120">Bu derlemeler kümesini geçişli kapatması büyükse, başlangıç zamanında önemli bir iyileştirme sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="abc81-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="abc81-121">Ana bilgisayar belirtiyorsa `eInitializeNewDomainFlags_NoSecurityChanges` uygulama etki alanı yöneticisi için bir <xref:System.InvalidOperationException> uygulama etki alanı güvenlik değiştirmek için her türlü girişim yaptıysanız atılır.</span><span class="sxs-lookup"><span data-stu-id="abc81-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="abc81-122">Çağırma [Iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)yöntemi çağırmak için eşdeğer `ICLRDomainManager::SetAppDomainManagerType` ile `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="abc81-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc81-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abc81-123">Requirements</span></span>  
 <span data-ttu-id="abc81-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abc81-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abc81-125">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="abc81-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="abc81-126">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="abc81-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abc81-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abc81-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc81-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abc81-128">See Also</span></span>  
 [<span data-ttu-id="abc81-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="abc81-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="abc81-130">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abc81-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="abc81-131">EInitializeNewDomainFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="abc81-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
