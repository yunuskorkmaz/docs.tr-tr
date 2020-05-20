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
ms.openlocfilehash: 89b3f9f248a445cc0568236d6a1df14269de4187
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615702"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType Yöntemi
<xref:System.AppDomainManager?displayProperty=nameWithType>Varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisinin sınıfından türetilen türü belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Uygulama etki alanı Yöneticisi hakkında bilgi sağlayan [Eınitialenewdomainflags](einitializenewdomainflags-enumeration.md) numaralandırma değerlerinin birleşimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda, için tek tanımlı değer `dwInitializeDomainFlags` , `eInitializeNewDomainFlags_NoSecurityChanges` uygulama etki alanı yöneticisi 'nin yöntemin yürütülmesi sırasında güvenlik ayarlarını değiştirmeyeceğini belirten, ortak dil çalışma zamanına (CLR) bildirir <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> . Bu, CLR 'nin koşullu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (aptca) özniteliğine sahip derlemelerin yüklenmesini iyileştirmek için izin verir. Bu derleme kümesinin geçişli kapanışı büyükse, bu, Başlangıç zamanında önemli bir gelişme yol açabilir.  
  
> [!IMPORTANT]
> Ana bilgisayar `eInitializeNewDomainFlags_NoSecurityChanges` uygulama etki alanı Yöneticisi için belirtiyorsa, <xref:System.InvalidOperationException> uygulama etki alanının güvenliğini değiştirmek için herhangi bir girişimde bulunulduğunda bir oluşturulur.  
  
 [ICLRControl:: SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)metodunu çağırmak `ICLRDomainManager::SetAppDomainManagerType` ile çağırma ile eşdeğerdir `eInitializeNewDomainFlags_None` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma](index.md)
- [ICLRDomainManager Arabirimi](iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags Numaralandırması](einitializenewdomainflags-enumeration.md)
