---
description: ': ICLRDomainManager:: SetAppDomainManagerType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 479e6596982d21c4e9ae445a7d4453235dbef729
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799765"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType Yöntemi

<xref:System.AppDomainManager?displayProperty=nameWithType>Varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisinin sınıfından türetilen türü belirtir.  
  
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
 'ndaki Uygulama etki alanı Yöneticisi hakkında bilgi sağlayan [Eınitialenewdomainflags](einitializenewdomainflags-enumeration.md) numaralandırma değerlerinin birleşimi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
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
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hosting](index.md)
- [ICLRDomainManager Arabirimi](iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags Numaralandırması](einitializenewdomainflags-enumeration.md)
