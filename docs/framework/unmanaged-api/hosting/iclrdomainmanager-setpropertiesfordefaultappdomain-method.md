---
description: ': ICLRDomainManager:: SetPropertiesForDefaultAppDomain Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 08e6c885d5d089fa22c30a4e3cef69480b840031
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689449"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain Yöntemi

Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `nProperties`  
 'ndaki Ve içindeki giriş sayısı `pwszPropertyNames` `pwszPropertyValues` .  
  
 `pwszPropertyNames`  
 'ndaki Özellik adları dizisi veya özellik yoksa null. Şu anda, bu yöntemin tanıdığı tek özellik adı "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".  
  
 `pwszPropertyValues`  
 'ndaki Özellik değerleri dizisi veya özellik yoksa null.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames` Bu yöntem tarafından tanınmayan bir özellik adı içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" için özellik değeri, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> Varsayılan uygulama etki alanında kısmen güvenilen çağıranlara görünür hale getirilme bayrağıyla koşullu (aptca) özniteliği olan derlemelerin bir listesidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hosting](index.md)
- [ICLRDomainManager Arabirimi](iclrdomainmanager-interface.md)
