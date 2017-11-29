---
title: "ICLRDomainManager::SetAppDomainManagerType Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17c99d21155d8f985ea455e171067855edcafedc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="fb0f6-102">ICLRDomainManager::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb0f6-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="fb0f6-103">Öğesinden türetilen tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılan uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb0f6-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb0f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb0f6-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="fb0f6-106">[in] Uygulama etki alanı yöneticisi türünü içeren bütünleştirilmiş kodun görünen adını; Örneğin: "AdMgrExample, sürüm 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3 =".</span><span class="sxs-lookup"><span data-stu-id="fb0f6-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="fb0f6-107">[in] Ad alanı dahil olmak üzere uygulama etki alanı yöneticisi türü adı.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="fb0f6-108">[in] Bir birleşimini [Eınitializenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) uygulama etki alanı yöneticisi hakkında bilgi sağlayan numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb0f6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb0f6-109">Return Value</span></span>  
 <span data-ttu-id="fb0f6-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fb0f6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb0f6-111">HRESULT</span></span>|<span data-ttu-id="fb0f6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb0f6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb0f6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb0f6-113">S_OK</span></span>|<span data-ttu-id="fb0f6-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="fb0f6-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb0f6-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb0f6-116">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb0f6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb0f6-117">Remarks</span></span>  
 <span data-ttu-id="fb0f6-118">Şu anda yalnızca tanımlı bir değer için `dwInitializeDomainFlags` olan `eInitializeNewDomainFlags_NoSecurityChanges`, uygulama etki alanı yöneticisi yürütülmesi sırasında güvenlik ayarlarını değiştirmez ortak dil çalışma zamanı (CLR) söyleyen <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fb0f6-119">Bu koşul olan derlemeler yüklenmesini iyileştirmek CLR sağlar <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="fb0f6-120">Bu derlemeler kümesini geçişli kapatması büyükse, başlangıç zamanında önemli bir iyileştirme sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb0f6-121">Ana bilgisayar belirtiyorsa `eInitializeNewDomainFlags_NoSecurityChanges` uygulama etki alanı yöneticisi için bir <xref:System.InvalidOperationException> uygulama etki alanı güvenlik değiştirmek için her türlü girişim yaptıysanız atılır.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="fb0f6-122">Çağırma [Iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)yöntemi çağırmak için eşdeğer `ICLRDomainManager::SetAppDomainManagerType` ile `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb0f6-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb0f6-123">Requirements</span></span>  
 <span data-ttu-id="fb0f6-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb0f6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb0f6-125">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fb0f6-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fb0f6-126">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fb0f6-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb0f6-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb0f6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb0f6-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb0f6-128">See Also</span></span>  
 [<span data-ttu-id="fb0f6-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="fb0f6-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="fb0f6-130">Iclrdomainmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb0f6-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="fb0f6-131">Eınitializenewdomainflags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fb0f6-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
