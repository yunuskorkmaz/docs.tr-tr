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
ms.openlocfilehash: ea10f9b7d23d8ca6a94d05cac6e586b434c000d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType Yöntemi
Öğesinden türetilen tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılan uygulama etki alanı yöneticisi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszAppDomainManagerAssembly`  
 [in] Uygulama etki alanı yöneticisi türünü içeren bütünleştirilmiş kodun görünen adını; Örneğin: "AdMgrExample, sürüm 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3 =".  
  
 `wszAppDomainManagerType`  
 [in] Ad alanı dahil olmak üzere uygulama etki alanı yöneticisi türü adı.  
  
 `dwInitializeDomainFlags`  
 [in] Bir birleşimini [Eınitializenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) uygulama etki alanı yöneticisi hakkında bilgi sağlayan numaralandırma değerleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda yalnızca tanımlı bir değer için `dwInitializeDomainFlags` olan `eInitializeNewDomainFlags_NoSecurityChanges`, uygulama etki alanı yöneticisi yürütülmesi sırasında güvenlik ayarlarını değiştirmez ortak dil çalışma zamanı (CLR) söyleyen <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi. Bu koşul olan derlemeler yüklenmesini iyileştirmek CLR sağlar <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliği. Bu derlemeler kümesini geçişli kapatması büyükse, başlangıç zamanında önemli bir iyileştirme sonuçlanabilir.  
  
> [!IMPORTANT]
>  Ana bilgisayar belirtiyorsa `eInitializeNewDomainFlags_NoSecurityChanges` uygulama etki alanı yöneticisi için bir <xref:System.InvalidOperationException> uygulama etki alanı güvenlik değiştirmek için her türlü girişim yaptıysanız atılır.  
  
 Çağırma [Iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)yöntemi çağırmak için eşdeğer `ICLRDomainManager::SetAppDomainManagerType` ile `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRDomainManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [EInitializeNewDomainFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
