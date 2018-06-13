---
title: '&lt;issuerTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 646833f277c3ef4675a835ca0af3daf647e01224
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758587"
---
# <a name="ltissuertokenresolvergt"></a>&lt;issuerTokenResolver&gt;
Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan veren belirteci çözümleyiciyi kaydeder. Veren belirteç Çözümleyicisi gelen iletileri ve belirteç imzalama belirteçte çözmek için kullanılır.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerTokenResolver >  
  
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
|türü|Veren belirteç Çözümleyicisi türünü belirtir. Aşağıdakilerden biri olması gerekir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıf veya türeyen bir tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Veren belirteç Çözümleyicisi gelen iletileri ve belirteç imzalama belirteçte çözmek için kullanılır. İmza denetimi için kullanılan şifreleme malzeme almak için kullanılır. Belirtmeniz gerekir `type` özniteliği. Belirtilen tür ya da olabilir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya türetilen özel bir tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı.  
  
 Bazı belirteci işleyicileri yapılandırmasında veren belirteç Çözümleyicisi ayarları belirtmenizi sağlar. Tek tek belirteç işleyicileri ayarları güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.  
  
> [!NOTE]
>  Belirtme `<issuerTokenResolver>` öğesi bir alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak hala geriye dönük uyumluluk için desteklenir. Ayarları `<securityTokenHandlerConfiguration>` öğesi geçersiz kılar üzerinde `<identityConfiguration>` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML türetilen özel bir sınıf dayalı bir veren belirteç Çözümleyicisi için yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.IssuerTokenResolver>. Bir özel yapılandırma öğesinden başlatılmış bir sözlük İzleyici anahtar çifti belirteç Çözümleyicisi tutar (`<AddAudienceKeyPair>`) sınıfı için tanımlanmış. Sınıf geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> bu öğeyi işlemek için yöntem. Geçersiz kılma aşağıdaki örnekte gösterilir; Ancak, bunu çağıran yöntemleri okumanızdır gösterilmez. Tam bir örnek için bkz: `CustomToken` örnek.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
