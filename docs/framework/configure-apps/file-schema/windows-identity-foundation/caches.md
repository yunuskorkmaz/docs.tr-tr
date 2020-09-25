---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 791c5be8aa48db2b17a42a216ad2bf5e7b5a4bc1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189883"
---
# \<caches>

Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.|  
|[\<tokenReplayCache>](tokenreplaycache.md)|Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Öğesi `<caches>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` . Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.  
  
 `<caches>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> . Yapılandırılan önbellekler sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCaches> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki XML, oturum güvenlik belirteçlerini () tutmak için özel bir önbelleğin yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.SessionSecurityToken> . Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
