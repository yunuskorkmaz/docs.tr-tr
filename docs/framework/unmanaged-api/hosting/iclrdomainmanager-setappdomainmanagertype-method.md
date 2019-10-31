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
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType Yöntemi
Varsayılan uygulama etki alanını başlatmak için kullanılacak olan uygulama etki alanı yöneticisinin <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfından türetilen türü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszAppDomainManagerAssembly`  
 'ndaki Uygulama etki alanı yöneticisi türünü içeren derlemenin görünen adı; Örneğin: "Admgrexexample, sürüm = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 'ndaki Ad alanı dahil olmak üzere uygulama etki alanı yöneticisinin tür adı.  
  
 `dwInitializeDomainFlags`  
 'ndaki Uygulama etki alanı Yöneticisi hakkında bilgi sağlayan [Eınitialenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) numaralandırma değerlerinin birleşimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda `dwInitializeDomainFlags` için tek tanımlı değer `eInitializeNewDomainFlags_NoSecurityChanges`ve bu, ortak dil çalışma zamanına (CLR) <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yönteminin yürütülmesi sırasında uygulama etki alanı yöneticisinin güvenlik ayarlarını değiştirmeyeceğini söyler. Bu, CLR 'nin koşullu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğine sahip derlemelerin yüklenmesini iyileştirmek için izin verir. Bu derleme kümesinin geçişli kapanışı büyükse, bu, Başlangıç zamanında önemli bir gelişme yol açabilir.  
  
> [!IMPORTANT]
> Konak, uygulama etki alanı Yöneticisi için `eInitializeNewDomainFlags_NoSecurityChanges` belirtiyorsa, uygulama etki alanının güvenliğini değiştirmek için herhangi bir girişimde bulunulduğunda bir <xref:System.InvalidOperationException> oluşturulur.  
  
 [ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metodunu çağırmak, `eInitializeNewDomainFlags_None``ICLRDomainManager::SetAppDomainManagerType` çağırma ile eşdeğerdir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
