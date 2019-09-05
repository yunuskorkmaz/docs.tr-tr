---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251962"
---
# <a name="issuernameregistry"></a>\<ıssuernameregbakanlığı >
Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ıssuernameregbakanlığı >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
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
|türü|<xref:System.IdentityModel.Tokens.IssuerNameRegistry> Sınıfından türeten bir tür. Özel `type`belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<trustedIssuers >](trustedissuers.md)|Öznitelik, yapılandırma tabanlı veren adı kayıt defterini <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (sınıfı) belirttiğinde, [ \<trustedissuers >](trustedissuers.md) öğesinin belirtilmesi gerekir. `type` `<add>` `<clear>` `<remove>` [ Trustedissuers>öğesi\<](trustedissuers.md) alt öğe olarak, veya öğelerini alabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm verenin belirteçleri, bir veren adı kayıt defteri kullanılarak onaylanır. Bu, <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfından türetilen bir nesnedir. Veren adı kayıt defteri, bir anımsatıcı adını, ilgili veren tarafından üretilen belirteçlerin imzalarını doğrulamak için gereken şifreleme malzemesiyle ilişkilendirmek için kullanılır. Veren adı kayıt defteri, bağlı olan taraf (RP) uygulaması tarafından güvenilen verenler listesini tutar. Veren adı kayıt defterinin türü, `type` özniteliği kullanılarak belirtilir. `<issuerNameRegistry>` Öğe, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğe içerebilir. <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> Yöntemi geçersiz kılarak bu alt öğeleri işleyen mantığı sağlarsınız.  
  
 WIF, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfından tek bir veren adı kayıt defteri türü sağlar. Bu sınıf, yapılandırmada belirtilen bir güvenilen veren sertifikaları kümesi kullanır. Bu, altında güvenilir veren sertifikaları koleksiyonunun `<trustedIssuers>`yapılandırıldığı bir alt yapılandırma öğesi gerektirir. Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve, `<add>` `<clear>`veya `<remove>` öğeleri kullanılarak koleksiyona eklenir veya kaldırılır.  
  
 `<issuerNameRegistry>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> tarafından temsil edilir.  
  
> [!NOTE]
> Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<issuerNameRegistry>` Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
