---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251962"
---
# \<issuerNameRegistry>
Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
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
|tür|Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.IssuerNameRegistry> . Özel belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|Öznitelik, `type` yapılandırma tabanlı veren adı kayıt defterini ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı) belirttiğinde, [\<trustedIssuers>](trustedissuers.md) öğe belirtilmelidir. [\<trustedIssuers>](trustedissuers.md)Öğesi `<add>` , `<clear>` `<remove>` alt öğeleri olarak, veya öğelerini alabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm verenin belirteçleri, bir veren adı kayıt defteri kullanılarak onaylanır. Bu, sınıfından türetilen bir nesnedir <xref:System.IdentityModel.Tokens.IssuerNameRegistry> . Veren adı kayıt defteri, bir anımsatıcı adını, ilgili veren tarafından üretilen belirteçlerin imzalarını doğrulamak için gereken şifreleme malzemesiyle ilişkilendirmek için kullanılır. Veren adı kayıt defteri, bağlı olan taraf (RP) uygulaması tarafından güvenilen verenler listesini tutar. Veren adı kayıt defterinin türü, özniteliği kullanılarak belirtilir `type` . `<issuerNameRegistry>`Öğe, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğe içerebilir. Yöntemi geçersiz kılarak bu alt öğeleri işleyen mantığı sağlarsınız <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> .  
  
 WıF, sınıfından tek bir veren adı kayıt defteri türü sağlar <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> . Bu sınıf, yapılandırmada belirtilen bir güvenilen veren sertifikaları kümesi kullanır. Bu, `<trustedIssuers>` altında güvenilir veren sertifikaları koleksiyonunun yapılandırıldığı bir alt yapılandırma öğesi gerektirir. Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve `<add>` , veya öğeleri kullanılarak koleksiyona eklenir veya kaldırılır `<clear>` `<remove>` .  
  
 `<issuerNameRegistry>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> .  
  
> [!NOTE]
> Öğenin `<issuerNameRegistry>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. `<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .  
  
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
