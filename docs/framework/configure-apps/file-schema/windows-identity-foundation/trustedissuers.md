---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251755"
---
# \<trustedIssuers>
Yapılandırma tabanlı veren adı kayıt defteri () tarafından kullanılan güvenilir veren sertifikalarının listesini yapılandırır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
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
|`<add thumbprint=xs:string name=xs:string>`|Güvenilen verenler koleksiyonuna bir sertifika ekler. Sertifika, `thumbprint` özniteliğiyle belirtilir. Bu öznitelik gereklidir ve sertifika parmak izinin ASN. 1 kodlu biçimini içermelidir. `name`Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek üzere kullanılabilir.|  
|`<clear>`|Güvenilen verenler koleksiyonundan tüm sertifikaları temizler.|  
|`<remove thumbprint=xs:string>`|Güvenilen verenler koleksiyonundan bir sertifikayı kaldırır. Sertifika, `thumbprint` özniteliğiyle belirtilir. Bu öznitelik gereklidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Verenin adı kayıt defterini yapılandırır. **Önemli:**  `type`Öğesinin özniteliği, `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` öğesinin geçerli olması için sınıfına başvurmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows Identity Foundation (WıF) <xref:System.IdentityModel.Tokens.IssuerNameRegistry> , sınıfının kutudan, sınıfının tek bir uygulamasını sağlar <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> . Yapılandırma verenin adı kayıt defteri, yapılandırmadan yüklenen güvenilen verenler listesini tutar. Liste, verenin adını veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla ilişkilendirir. Güvenilen veren sertifikalarının listesi öğesi altında belirtilir `<trustedIssuers>` . Listedeki her öğe, bu veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla bir anımsatıcı veren adını ilişkilendirir. Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve koleksiyon öğesi kullanılarak eklenir `<add>` . Ve öğelerini kullanarak listeden verenler (Sertifikalar) temizleyebilir veya kaldırabilirsiniz `<clear>` `<remove>` .  
  
 `type`Öğesinin özniteliği, `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` öğesinin geçerli olması için sınıfına başvurmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
