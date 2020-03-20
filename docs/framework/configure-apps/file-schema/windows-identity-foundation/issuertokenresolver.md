---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152677"
---
# <a name="issuertokenresolver"></a>\<verenTokenResolver>
Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder. Veren belirteç çözümleyici, gelen belirteçler ve iletiler üzerinde imza belirteci çözmek için kullanılır.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<verenTokenResolver>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
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
|type|Veren belirteç çözücünün türünü belirtir. <xref:System.IdentityModel.Tokens.IssuerTokenResolver> Sınıf veya <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıftan türemiş bir tür olmalıdır. Gereklidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<güvenlikTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Güvenlik belirteç işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Veren belirteç çözümleyici, gelen belirteçler ve iletiler üzerinde imza belirteci çözmek için kullanılır. İmzayı denetlemek için kullanılan şifreleme materyalini almak için kullanılır. Özniteliği belirtmeniz `type` gerekir. Belirtilen tür, <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıftan türeyen özel bir tür olabilir.  
  
 Bazı belirteç işleyicileri, yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır. Tek tek belirteç işleyicileri ayarları, güvenlik belirteci işleyicisi koleksiyonunda belirtilenleri geçersiz kılar.  
  
> [!NOTE]
> Kimlik Yapılandırma `<issuerTokenResolver>` [ \<>](identityconfiguration.md) öğesinin alt öğesi olarak öğebelirtilmesi küçümsenmiştir, ancak yine de geriye dönük uyumluluk için desteklenir. Öğedeki `<securityTokenHandlerConfiguration>` `<identityConfiguration>` ayarlar, öğedekiayarları geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, 'den <xref:System.IdentityModel.Tokens.IssuerTokenResolver>türeyen özel bir sınıfa dayanan bir veren belirteç çözümleyicisi için yapılandırmayı gösterir. Belirteç çözümleyicisi, sınıf için tanımlanan özel bir yapılandırma öğesinden`<AddAudienceKeyPair>`( ) başharfe basılan hedef kitle anahtarı çiftlerinden oluşan bir sözlük tutar. Sınıf, bu <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> öğeyi işlemek için yöntemi geçersiz kılar. Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak, adlandırdığı yöntemler kısalık için gösterilmez. Tam örnek için, `CustomToken` örneğe bakın.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Örnek
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
