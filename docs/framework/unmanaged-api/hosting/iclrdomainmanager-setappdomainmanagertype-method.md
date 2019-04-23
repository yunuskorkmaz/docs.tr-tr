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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183254"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType Yöntemi
Türetilmiş tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılacak uygulama etki alanı yöneticisi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszAppDomainManagerAssembly`  
 [in] Uygulama etki alanı yöneticisi türünü içeren derlemenin görünen adını; Örneğin: "AdMgrExample, sürüm 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3 =".  
  
 `wszAppDomainManagerType`  
 [in] Ad alanı dahil olmak üzere uygulama etki alanı yöneticisi türü adı.  
  
 `dwInitializeDomainFlags`  
 [in] Bir birleşimi [Eınitializenewdomainflags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) numaralandırma değerlerinin, uygulama etki alanı yöneticisi hakkında bilgi sağlar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda yalnızca tanımlı bir değer için `dwInitializeDomainFlags` olduğu `eInitializeNewDomainFlags_NoSecurityChanges`, uygulama etki alanı yöneticisi yürütülmesi sırasında güvenlik ayarlarını değiştirmez ortak dil çalışma zamanı (CLR) söyleyen <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi. Koşul olan derlemeler yüklenmesi iyileştirmek CLR böylece <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA). Bu derlemeler kümesini geçişli kapatılmasını büyükse, bu önemli bir iyileştirme başlangıç zamanında neden olabilir.  
  
> [!IMPORTANT]
>  Konak belirtiyorsa `eInitializeNewDomainFlags_NoSecurityChanges` uygulama etki alanı yöneticisi için bir <xref:System.InvalidOperationException> her türlü girişim uygulama etki alanının güvenliğini değiştirmek için yapılması durumunda oluşturulur.  
  
 Çağırma [Iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)yöntemini çağırmaya eşdeğerdir `ICLRDomainManager::SetAppDomainManagerType` ile `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
