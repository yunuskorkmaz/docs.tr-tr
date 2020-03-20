---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152573"
---
# <a name="securitytokenhandlerconfiguration"></a>\<güvenlikTokenHandlerConfiguration>
Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<güvenlikTokenHandlerConfiguration>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|saveBootstrapContext|Bootstrap belirteçlerinin oturum belirtecine dahil edilip edilmemesi gerektiğini belirtir. Değer, [ \<identityConfiguration>](identityconfiguration.md) öğesindeki özniteliği ayarlayarak `saveBootstrapContext` bir belirteç işleyicisi koleksiyonunda da ayarlanabilir. Belirteç işleyicisi koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|  
|maksimumClockSkew|İzin <xref:System.TimeSpan> verilen maksimum saat eğriliğini belirten bir saat. Oturum açma oturumunun son kullanma süresini doğrulamak gibi zamana duyarlı işlemleri gerçekleştirirken izin verilen maksimum saat eğriliğini denetler. Varsayılan değer 5 dakika, "00:05:00". Değerleri nasıl belirtirim <xref:System.TimeSpan> hakkında daha fazla bilgi için [Timespan Değerleri'ne](../windows-workflow-foundation/index.md)bakın. Maksimum saat eğriliği, `maximumClockSkew` [ \<identityConfiguration>](identityconfiguration.md) öğesiözebiyi ayarlayarak hizmet düzeyinde de ayarlanabilir. Belirteç işleyicisi koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<izleyiciUris>](audienceuris.md)|Bu güvenen tarafın kabul edilebilir tanımlayıcıları olan URI kümesini belirtir. İsteğe bağlı.|  
|[\<önbellekleri>](caches.md)|Oturum belirteçleri ve belirteç yeniden algılamaiçin kullanılan önbellekleri kaydeder. Hizmet düzeyinde veya güvenlik belirteç leri koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<sertifikaDoğrulama>](certificatevalidation.md)|Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler. Hizmet düzeyinde veya güvenlik belirteç leri koleksiyonunda belirtilebilir. Belirli bir işleyici kendi doğrulayıcısı ile yapılandırılırsa, bu ayarlar geçersiz kılınur. İsteğe bağlı.|  
|[\<verenNameRegistry>](issuernameregistry.md)|Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan veren ad kayıt defterini yapılandırır. İsteğe bağlı.|  
|[\<verenTokenResolver>](issuertokenresolver.md)|Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder. Veren belirteç çözümleyici, gelen belirteçler ve iletiler üzerinde imza belirteci çözmek için kullanılır. İsteğe bağlı.|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder. Hizmet belirteci çözümleyicisi, gelen belirteçler ve iletiler üzerindeki şifreleme belirteci çözümlemek için kullanılır. İsteğe bağlı.|  
|[\<tokenReplayAlgılama>](tokenreplaydetection.md)|Belirteç yeniden oynatma algılamasını sağlar ve belirteçlerin son kullanma süresini belirtir. Hizmet düzeyinde veya güvenlik belirteç leri koleksiyonunda belirtilebilir. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<güvenlikTokenHandlers>](securitytokenhandlers.md)|Bitiş noktasına kayıtlı bir güvenlik belirteç işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölümde bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne için özellik değerleri sağlar. Bu bölümde yapılandırılan ayarlar, hizmette yapılandırılanları geçersiz kılar. Bu ayarlardan bazıları, sırayla, güvenlik belirteci işleyicisi koleksiyonuna bir işleyici eklendiğinde belirtilen ayarlar tarafından geçersiz kılınabilir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
