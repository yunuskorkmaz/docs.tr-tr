---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646075"
---
# <a name="sessionsecuritytokencache"></a>\<oturumSecurityTokenCache>
Bir hizmet veya güvenlik belirteç işleyicisi koleksiyonu ile oturum belirteçleri için bir önbellek kaydeder.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<önbellekleri>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oturumSecurityTokenCache>**  
  
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
|type|<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> Sınıftan türemiş bir tür.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<önbellekleri>](caches.md)|Bir hizmet veya güvenlik belirteci işleyicisi koleksiyonu tarafından kullanılan önbellekleri kaydeder.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, oturum güvenlik belirteçlerini tutmak için özel<xref:System.IdentityModel.Tokens.SessionSecurityToken>bir önbelleğin yapılandırmasını gösterir ( ). Yapılandırma `ClaimsAwareWebFarm` örnekten alınır. Bu örnek hakkında daha fazla bilgi için [WIF Kodu Örnek Endeksi'ne](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index)bakın.  
  
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
