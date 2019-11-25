---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 451750a1facd9a886b53427a8d54580d1a939fa5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968508"
---
# <a name="issuertokenresolver"></a>\<IssuerTokenResolver >
Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder. Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuerTokenResolver >**  
  
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
|türü|Verenin belirteç Çözümleyicisinin türünü belirtir. <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen bir tür olmalıdır. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır. İmzayı denetlemek için kullanılan şifreleme malzemesini almak için kullanılır. `type` özniteliğini belirtmeniz gerekir. Belirtilen tür ya <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen özel bir tür olabilir.  
  
 Bazı belirteç işleyicileri yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır. Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.  
  
> [!NOTE]
> `<issuerTokenResolver>` öğesini [\<IdentityConfiguration >](identityconfiguration.md) öğesinin bir alt öğesi olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenmektedir. `<securityTokenHandlerConfiguration>` öğesindeki ayarlar `<identityConfiguration>` öğesinde olanları geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, <xref:System.IdentityModel.Tokens.IssuerTokenResolver>türetilen özel bir sınıfa dayalı bir veren belirteç Çözümleyicisi için yapılandırmayı gösterir. Belirteç çözümleyici, sınıf için tanımlanan özel bir yapılandırma öğesinden (`<AddAudienceKeyPair>`) başlatılan bir hedef kitle anahtar çiftleri sözlüğü içerir. Sınıfı, bu öğeyi işlemek için <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> yöntemini geçersiz kılar. Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak çağrı yaptığı Yöntemler breçekimi için gösterilmez. Tüm örnek için `CustomToken` örneğe bakın.  
  
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
