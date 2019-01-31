---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 697c20d1f526cb376c2430f0006349f7d8f9b2f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257948"
---
# <a name="sessionsecuritytokencache"></a>\<sessionSecurityTokenCache>
Bir hizmet ya da bir güvenlik belirteci işleyicisi koleksiyon oturumu belirteçleri için bir önbelleği kaydeder.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<önbelleğe alan >  
\<sessionSecurityTokenCache>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Türetilen bir tür <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<önbelleğe alan >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML oturumu güvenlik belirteçleri tutmak için özel bir önbellek yapılandırmasını gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>). Yapılandırma alınır `ClaimsAwareWebFarm` örnek. Bu örnek hakkında daha fazla bilgi için bkz: [WIF kod örneği dizini](../../../../../docs/framework/security/wif-code-sample-index.md).  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
