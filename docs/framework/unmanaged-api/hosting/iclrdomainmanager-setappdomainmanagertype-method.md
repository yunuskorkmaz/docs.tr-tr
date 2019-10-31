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
ms.openlocfilehash: 5c61e2e1208cec0bda1492964a8d02bd71f5a1c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129325"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="9a8d9-102">ICLRDomainManager::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a8d9-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="9a8d9-103">Varsayılan uygulama etki alanını başlatmak için kullanılacak olan uygulama etki alanı yöneticisinin <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfından türetilen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a8d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a8d9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a8d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a8d9-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="9a8d9-106">'ndaki Uygulama etki alanı yöneticisi türünü içeren derlemenin görünen adı; Örneğin: "Admgrexexample, sürüm = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="9a8d9-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="9a8d9-107">'ndaki Ad alanı dahil olmak üzere uygulama etki alanı yöneticisinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="9a8d9-108">'ndaki Uygulama etki alanı Yöneticisi hakkında bilgi sağlayan [Eınitialenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) numaralandırma değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a8d9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a8d9-109">Return Value</span></span>  
 <span data-ttu-id="9a8d9-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9a8d9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a8d9-111">HRESULT</span></span>|<span data-ttu-id="9a8d9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a8d9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a8d9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a8d9-113">S_OK</span></span>|<span data-ttu-id="9a8d9-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="9a8d9-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a8d9-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a8d9-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a8d9-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a8d9-117">Remarks</span></span>  
 <span data-ttu-id="9a8d9-118">Şu anda `dwInitializeDomainFlags` için tek tanımlı değer `eInitializeNewDomainFlags_NoSecurityChanges`ve bu, ortak dil çalışma zamanına (CLR) <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yönteminin yürütülmesi sırasında uygulama etki alanı yöneticisinin güvenlik ayarlarını değiştirmeyeceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9a8d9-119">Bu, CLR 'nin koşullu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğine sahip derlemelerin yüklenmesini iyileştirmek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="9a8d9-120">Bu derleme kümesinin geçişli kapanışı büyükse, bu, Başlangıç zamanında önemli bir gelişme yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9a8d9-121">Konak, uygulama etki alanı Yöneticisi için `eInitializeNewDomainFlags_NoSecurityChanges` belirtiyorsa, uygulama etki alanının güvenliğini değiştirmek için herhangi bir girişimde bulunulduğunda bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="9a8d9-122">[ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metodunu çağırmak, `eInitializeNewDomainFlags_None``ICLRDomainManager::SetAppDomainManagerType` çağırma ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a8d9-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a8d9-123">Requirements</span></span>  
 <span data-ttu-id="9a8d9-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a8d9-125">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9a8d9-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9a8d9-126">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9a8d9-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a8d9-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a8d9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a8d9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-128">See also</span></span>

- [<span data-ttu-id="9a8d9-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="9a8d9-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="9a8d9-130">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a8d9-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="9a8d9-131">EInitializeNewDomainFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9a8d9-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
