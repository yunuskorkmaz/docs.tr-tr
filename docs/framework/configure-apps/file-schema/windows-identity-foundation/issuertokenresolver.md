---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942636"
---
# <a name="issuertokenresolver"></a>\<IssuerTokenResolver >
Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder. Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<IssuerTokenResolver >  
  
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
|türü|Verenin belirteç Çözümleyicisinin türünü belirtir. Sınıf ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıftan türetilmiş bir tür olmalıdır. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır. İmzayı denetlemek için kullanılan şifreleme malzemesini almak için kullanılır. `type` Özniteliğini belirtmeniz gerekir. Belirtilen tür ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen özel bir tür olabilir.  
  
 Bazı belirteç işleyicileri yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır. Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.  
  
> [!NOTE]
> Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<issuerTokenResolver>` Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, ' den <xref:System.IdentityModel.Tokens.IssuerTokenResolver>türetilen özel bir sınıfa dayalı bir veren belirteç Çözümleyicisi için yapılandırmayı gösterir. Belirteç çözümleyici, sınıf için tanımlanan özel bir yapılandırma öğesinden (`<AddAudienceKeyPair>`) başlatılan bir hedef kitle anahtar çiftleri sözlüğü içerir. Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> bu öğeyi işlemek için yöntemini geçersiz kılar. Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak çağrı yaptığı Yöntemler breçekimi için gösterilmez. Tüm örnek için `CustomToken` örneğe bakın.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Örnek  
  
```  
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
