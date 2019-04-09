---
title: ICLRDomainManager::SetAppDomainManagerType Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cfef7d929d40996716a02a4db51630827011a68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183254"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="4d3fd-102">ICLRDomainManager::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d3fd-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="4d3fd-103">Türetilmiş tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılacak uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d3fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d3fd-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d3fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d3fd-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="4d3fd-106">[in] Uygulama etki alanı yöneticisi türünü içeren derlemenin görünen adını; Örneğin: "AdMgrExample, sürüm 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3 =".</span><span class="sxs-lookup"><span data-stu-id="4d3fd-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="4d3fd-107">[in] Ad alanı dahil olmak üzere uygulama etki alanı yöneticisi türü adı.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="4d3fd-108">[in] Bir birleşimi [Eınitializenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) numaralandırma değerlerinin, uygulama etki alanı yöneticisi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d3fd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d3fd-109">Return Value</span></span>  
 <span data-ttu-id="4d3fd-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4d3fd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d3fd-111">HRESULT</span></span>|<span data-ttu-id="4d3fd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d3fd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d3fd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d3fd-113">S_OK</span></span>|<span data-ttu-id="4d3fd-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="4d3fd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4d3fd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4d3fd-116">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d3fd-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d3fd-117">Remarks</span></span>  
 <span data-ttu-id="4d3fd-118">Şu anda yalnızca tanımlı bir değer için `dwInitializeDomainFlags` olduğu `eInitializeNewDomainFlags_NoSecurityChanges`, uygulama etki alanı yöneticisi yürütülmesi sırasında güvenlik ayarlarını değiştirmez ortak dil çalışma zamanı (CLR) söyleyen <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4d3fd-119">Koşul olan derlemeler yüklenmesi iyileştirmek CLR böylece <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA).</span><span class="sxs-lookup"><span data-stu-id="4d3fd-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="4d3fd-120">Bu derlemeler kümesini geçişli kapatılmasını büyükse, bu önemli bir iyileştirme başlangıç zamanında neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d3fd-121">Konak belirtiyorsa `eInitializeNewDomainFlags_NoSecurityChanges` uygulama etki alanı yöneticisi için bir <xref:System.InvalidOperationException> her türlü girişim uygulama etki alanının güvenliğini değiştirmek için yapılması durumunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="4d3fd-122">Çağırma [Iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)yöntemini çağırmaya eşdeğerdir `ICLRDomainManager::SetAppDomainManagerType` ile `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d3fd-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d3fd-123">Requirements</span></span>  
 <span data-ttu-id="4d3fd-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d3fd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d3fd-125">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4d3fd-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4d3fd-126">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4d3fd-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4d3fd-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4d3fd-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4d3fd-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d3fd-128">See also</span></span>

- [<span data-ttu-id="4d3fd-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="4d3fd-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="4d3fd-130">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d3fd-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="4d3fd-131">EInitializeNewDomainFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4d3fd-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
