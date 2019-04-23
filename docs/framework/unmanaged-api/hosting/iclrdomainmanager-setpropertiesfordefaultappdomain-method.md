---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c42297e848844617ffdc6c85c81846b5805eb4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181361"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi
Varsayılan uygulama etki alanı başlatmak için kullanılacak özelliklerini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nProperties`  
 [in] Giriş sayısı `pwszPropertyNames` ve `pwszPropertyValues`.  
  
 `pwszPropertyNames`  
 [in] Bir dizi özellik adları ya da hiçbir özelliği yoksa null. Şu anda, bu yöntem tarafından tanınan tek özellik adı "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" ' dir.  
  
 `pwszPropertyValues`  
 [in] Bir dizi özellik değerlerini ya da hiçbir özelliği yoksa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames` Bu yöntem tarafından tanınmayan bir özellik adı içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Koşullu sahip bir derleme listesi "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" özellik değeri olan <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğiyle <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> varsayılan uygulamada görünür için kısmen güvenilmeyen çağrıcılara yapılacağı bayrak etki alanı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
