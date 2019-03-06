---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: bb4cb5178885b90ef25ee827c2f11593ead6e73d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354563"
---
# <a name="trustedissuers"></a>\<trustedIssuers >
Yapılandırma temelli yayınlayıcı adı tarafından kullanılan Güvenilen yayıncı sertifikaları listesinde yapılandırır (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry>  
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
 Hiçbiri  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|Sertifika, güvenilen verenler koleksiyona ekler. Sertifika ile belirtilen `thumbprint` özniteliği. Bu özellik gereklidir ve sertifika parmak izini ASN.1 kodlanmış biçiminde içermelidir. `name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek için kullanılabilir.|  
|`<clear>`|Tüm sertifikaları Güvenilen verenler koleksiyonundan kaldırır.|  
|`<remove thumbprint=xs:string>`|Sertifika, güvenilen verenler koleksiyonundan kaldırır. Sertifika ile belirtilen `thumbprint` özniteliği. Bu öznitelik gereklidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Yayınlayıcı adı yapılandırır. **Önemli:**  `type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfının `<trustedIssuers>` geçerli olması için öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows Identity Foundation (WIF) tek bir uygulamasını sağlar <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı ilk günden <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı. Yapılandırma verenin ad Kayıt Defteri'ni yapılandırmasından yüklenen güvenilen verenler listesini tutar. Listenin her verenin adı veren tarafından üretilen belirteçleri imzasını için gereken X.509 sertifikası ile ilişkilendirir. Güvenilen yayıncı sertifikaları listesi altında belirtilen `<trustedIssuers>` öğesi. Listedeki her öğe bir anımsatıcı verenin adı, veren tarafından üretilen belirteçleri imzasını doğrulamak için gereken X.509 sertifikası ile ilişkilendirir. Güvenilen sertifikalar ASN.1 kullanarak kodlanmış sertifika parmak izi biçiminde belirtilir ve koleksiyonu kullanılarak eklenen `<add>` öğesi. Temizleyin veya verenler (sertifika) kullanarak listeden kaldırma `<clear>` ve `<remove>` öğeleri.  
  
 `type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfının `<trustedIssuers>` geçerli olması için öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML tabanlı yapılandırma veren belirtmek ad Kayıt Defteri'ni gösterilmektedir.  
  
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
