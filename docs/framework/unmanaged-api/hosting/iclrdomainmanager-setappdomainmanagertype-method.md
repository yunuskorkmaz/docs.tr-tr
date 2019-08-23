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
ms.openlocfilehash: 9b142f1a05036eddf44c69d8b7da95091dc8f445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963090"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="c1c3e-102">ICLRDomainManager::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1c3e-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="c1c3e-103">Varsayılan uygulama etki alanını başlatmak için kullanılacak <xref:System.AppDomainManager?displayProperty=nameWithType> uygulama etki alanı yöneticisinin sınıfından türetilen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1c3e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1c3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1c3e-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="c1c3e-106">'ndaki Uygulama etki alanı yöneticisi türünü içeren derlemenin görünen adı; Örneğin: "Admgrexörnek, sürüm = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="c1c3e-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="c1c3e-107">'ndaki Ad alanı dahil olmak üzere uygulama etki alanı yöneticisinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="c1c3e-108">'ndaki Uygulama etki alanı Yöneticisi hakkında bilgi sağlayan [Eınitialenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) numaralandırma değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1c3e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1c3e-109">Return Value</span></span>  
 <span data-ttu-id="c1c3e-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c1c3e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1c3e-111">HRESULT</span></span>|<span data-ttu-id="c1c3e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1c3e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1c3e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1c3e-113">S_OK</span></span>|<span data-ttu-id="c1c3e-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="c1c3e-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1c3e-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1c3e-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1c3e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1c3e-117">Remarks</span></span>  
 <span data-ttu-id="c1c3e-118">Şu anda, için `dwInitializeDomainFlags` `eInitializeNewDomainFlags_NoSecurityChanges`tek tanımlı değer, uygulama etki alanı yöneticisi 'nin <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemin yürütülmesi sırasında güvenlik ayarlarını değiştirmeyeceğini belirten, ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c1c3e-119">Bu, clr 'nin koşullu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (aptca) özniteliğine sahip derlemelerin yüklenmesini iyileştirmek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="c1c3e-120">Bu derleme kümesinin geçişli kapanışı büyükse, bu, Başlangıç zamanında önemli bir gelişme yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c1c3e-121">Ana bilgisayar uygulama etki `eInitializeNewDomainFlags_NoSecurityChanges` alanı Yöneticisi için belirtiyorsa, uygulama etki <xref:System.InvalidOperationException> alanının güvenliğini değiştirmek için herhangi bir girişimde bulunulduğunda bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="c1c3e-122">[ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metodunu çağırmak ile çağırma `ICLRDomainManager::SetAppDomainManagerType` ile `eInitializeNewDomainFlags_None`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1c3e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1c3e-123">Requirements</span></span>  
 <span data-ttu-id="c1c3e-124">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1c3e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1c3e-125">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c1c3e-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c1c3e-126">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c1c3e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1c3e-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1c3e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c3e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1c3e-128">See also</span></span>

- [<span data-ttu-id="c1c3e-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="c1c3e-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="c1c3e-130">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1c3e-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="c1c3e-131">EInitializeNewDomainFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c1c3e-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
