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
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType Yöntemi
Varsayılan uygulama etki alanını başlatmak için kullanılacak <xref:System.AppDomainManager?displayProperty=nameWithType> uygulama etki alanı yöneticisinin sınıfından türetilen türü belirtir.  
  
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
 'ndaki Uygulama etki alanı yöneticisi türünü içeren derlemenin görünen adı; Örneğin: "Admgrexörnek, sürüm = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
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
 Şu anda, için `dwInitializeDomainFlags` `eInitializeNewDomainFlags_NoSecurityChanges`tek tanımlı değer, uygulama etki alanı yöneticisi 'nin <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemin yürütülmesi sırasında güvenlik ayarlarını değiştirmeyeceğini belirten, ortak dil çalışma zamanına (CLR) bildirir. Bu, clr 'nin koşullu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (aptca) özniteliğine sahip derlemelerin yüklenmesini iyileştirmek için izin verir. Bu derleme kümesinin geçişli kapanışı büyükse, bu, Başlangıç zamanında önemli bir gelişme yol açabilir.  
  
> [!IMPORTANT]
> Ana bilgisayar uygulama etki `eInitializeNewDomainFlags_NoSecurityChanges` alanı Yöneticisi için belirtiyorsa, uygulama etki <xref:System.InvalidOperationException> alanının güvenliğini değiştirmek için herhangi bir girişimde bulunulduğunda bir oluşturulur.  
  
 [ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metodunu çağırmak ile çağırma `ICLRDomainManager::SetAppDomainManagerType` ile `eInitializeNewDomainFlags_None`eşdeğerdir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MetaHost. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
