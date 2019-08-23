---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944267"
---
# <a name="trustedissuers"></a>\<trustedIssuers >
Yapılandırma tabanlı veren adı kayıt defteri (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>) tarafından kullanılan güvenilir veren sertifikalarının listesini yapılandırır.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<ıssuernameregbakanlığı >  
\<trustedIssuers >  
  
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
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|Güvenilen verenler koleksiyonuna bir sertifika ekler. Sertifika, `thumbprint` özniteliğiyle belirtilir. Bu öznitelik gereklidir ve sertifika parmak izinin ASN. 1 kodlu biçimini içermelidir. `name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek üzere kullanılabilir.|  
|`<clear>`|Güvenilen verenler koleksiyonundan tüm sertifikaları temizler.|  
|`<remove thumbprint=xs:string>`|Güvenilen verenler koleksiyonundan bir sertifikayı kaldırır. Sertifika, `thumbprint` özniteliğiyle belirtilir. Bu öznitelik gereklidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ıssuernameregbakanlığı >](issuernameregistry.md)|Verenin adı kayıt defterini yapılandırır. **Önemli:**  Öğesinin özniteliği, öğesinin geçerli olması için <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfına başvurmalıdır. `<trustedIssuers>` `type` `<issuerNameRegistry>`|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows Identity Foundation (WIF) <xref:System.IdentityModel.Tokens.IssuerNameRegistry> <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , sınıfının kutudan, sınıfının tek bir uygulamasını sağlar. Yapılandırma verenin adı kayıt defteri, yapılandırmadan yüklenen güvenilen verenler listesini tutar. Liste, verenin adını veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla ilişkilendirir. Güvenilen veren sertifikalarının listesi `<trustedIssuers>` öğesi altında belirtilir. Listedeki her öğe, bu veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla bir anımsatıcı veren adını ilişkilendirir. Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve koleksiyon öğesi kullanılarak `<add>` eklenir. `<clear>` Ve`<remove>` öğelerini kullanarak listeden verenler (Sertifikalar) temizleyebilir veya kaldırabilirsiniz.  
  
 Öğesinin özniteliği, öğesinin geçerli olması için <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfına başvurmalıdır. `<trustedIssuers>` `type` `<issuerNameRegistry>`  
  
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
