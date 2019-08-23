---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942453"
---
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration >
Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
  
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
|Savebootstrapbağlamı|Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir. Ayrıca, `saveBootstrapContext` [ \<IdentityConfiguration >](identityconfiguration.md) öğesinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda değer de ayarlanabilir. Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|  
|maximumClockSkew|İzin <xref:System.TimeSpan> verilen maksimum saat eğriliğini belirten bir. Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler. Varsayılan değer 5 dakikadır, "00:05:00". Değerlerin nasıl belirtilmesi <xref:System.TimeSpan> hakkında daha fazla bilgi için bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md). Ayrıca, `maximumClockSkew` [ \<IdentityConfiguration >](identityconfiguration.md) öğesinde özniteliği ayarlanarak hizmet düzeyinde maksimum saat eğriltme de ayarlanabilir. Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<audienceUris >](audienceuris.md)|Bu bağlı olan tarafın kabul edilebilir tanımlayıcıları olan URI kümesini belirtir. İsteğe bağlı.|  
|[\<önbellekler >](caches.md)|Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<certificateValidation >](certificatevalidation.md)|Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır. İsteğe bağlı.|  
|[\<ıssuernameregbakanlığı >](issuernameregistry.md)|Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır. İsteğe bağlı.|  
|[\<IssuerTokenResolver >](issuertokenresolver.md)|Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder. Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır. İsteğe bağlı.|  
|[\<serviceTokenResolver >](servicetokenresolver.md)|Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder. Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır. İsteğe bağlı.|  
|[\<tokenReplayDetection >](tokenreplaydetection.md)|Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](securitytokenhandlers.md)|Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölüm bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne için özellik değerleri sağlar. Bu bölümde yapılandırılan ayarlar, hizmette yapılandırılan ayarları geçersiz kılar. Bu ayarlardan bazıları, güvenlik belirteci işleyici koleksiyonuna bir işleyici eklendiğinde belirtilen ayarlar tarafından geçersiz kılınabilir.  
  
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
