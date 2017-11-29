---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
Güvenilen yayıncı sertifikaları yapılandırma temelli verenin adı kayıt defteri tarafından kullanılan listesini yapılandırır (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<System.IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
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
|`<add thumbprint=xs:string name=xs:string>`|Bir sertifika, güvenilen verenler koleksiyonuna ekler. Sertifika ile belirtilen `thumbprint` özniteliği. Bu özniteliği gereklidir ve sertifika parmak izi ASN.1 kodlanmış form içermelidir. `name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek için kullanılır.|  
|`<clear>`|Tüm sertifikaları Güvenilen verenler koleksiyonundan kaldırır.|  
|`<remove thumbprint=xs:string>`|Bir sertifika, güvenilen verenler koleksiyondan kaldırır. Sertifika ile belirtilen `thumbprint` özniteliği. Bu öznitelik gereklidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Yayınlayıcı adı kaydını yapılandırır. **Önemli:** `type` özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> için sınıf `<trustedIssuers>` geçerli olması için öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows Identity Foundation (WIF) sağlar, tek bir uygulama <xref:System.IdentityModel.Tokens.IssuerNameRegistry> kutusunu dışında sınıfı <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı. Yapılandırma yayınlayıcı adı kaydını yapılandırmasından yüklenen güvenilen verenlerin bir listesini tutar. Listenin her verenin adı veren tarafından üretilen belirteçleri imzasını doğrulamak için gereken X.509 sertifikası ile ilişkilendirir. Güvenilen yayıncı sertifikaları listesi altında belirtilen `<trustedIssuers>` öğesi. Her bir öğe listesi anımsatıcı verenin adı, veren tarafından üretilen belirteçleri imzasını doğrulamak için gereken X.509 sertifikası ile ilişkilendirir. Güvenilir sertifikalar ASN.1 kullanılarak kodlanmış form sertifika parmak izi belirtilir ve koleksiyon kullanılarak eklenen `<add>` öğesi. İşaretini kaldırın veya verenler (sertifika) kullanarak listeden kaldırmak `<clear>` ve `<remove>` öğeleri.  
  
 `type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> için sınıf `<trustedIssuers>` geçerli olması için öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML tabanlı yapılandırma veren belirtmek adı kayıt defteri gösterilmiştir.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
