---
title: "ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fabf42c16dc41e29ca3d14e00e76797fa8f2a9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi
Varsayılan uygulama etki alanı başlatmak için kullanılan özelliklerini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `nProperties`  
 [in] Giriş sayısı `pwszPropertyNames` ve `pwszPropertyValues`.  
  
 `pwszPropertyNames`  
 [in] Bir dizi özellik adları ya da hiçbir özelliği yoksa null. Şu anda, bu yöntem tarafından tanınan tek özellik adı "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" ' dir.  
  
 `pwszPropertyValues`  
 [in] Bir dizi özellik değerlerini ya da hiçbir özelliği yoksa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames`Bu yöntem tarafından tanınmayan bir özellik adı içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Koşullu sahip bir derleme listesi "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" için özellik değeri olan <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğiyle <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> varsayılan uygulamada kısmen güvenilen arayanlara görünür yapılacağı bayrağı etki alanı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [Iclrdomainmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
