---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941954"
---
# <a name="audienceuris"></a>\<audienceUris >
Bağlı olan tarafın (RP) kabul edilebilir tanımlayıcıları olan URI kümesini belirtir. Belirteçleri, izin verilen hedef kitle URI 'lerinden biri kapsamında olmadıkları müddetçe kabul edilmez.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<audienceUris >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
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
|mod|Hedef <xref:System.IdentityModel.Selectors.AudienceUriMode> kitle kısıtlamasının bir gelen belirtece uygulanıp uygulanmayacağını belirten bir değer. Olası değerler şunlardır "Always", "hiçbir" ve "Yataerkeyonly". Varsayılan değer "Always" dır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<add value=xs:string>`|`value` Öznitelik tarafından belirtilen URI 'yi AudienceUri koleksiyonuna ekler. `value` Özniteliği gereklidir. URI, büyük/küçük harfe duyarlıdır.|  
|`<clear>`|AudienceUris koleksiyonunu temizler. Tüm tanımlayıcılar koleksiyondan kaldırılır.|  
|`<remove value=xs:string>`|AudienceUri koleksiyonundan `value` özniteliği tarafından belirtilen URI 'yi kaldırır. `value` Özniteliği gereklidir. URI, büyük/küçük harfe duyarlıdır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, koleksiyon boştur; koleksiyonu `<add>`değiştirmek `<clear>`için, `<remove>` ve öğelerini kullanın. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nesneler, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesnelerinde izin verilen tüm hedef kitle URI kısıtlamalarını yapılandırmak için hedef kitle URI koleksiyonundaki değerleri kullanır.  
  
 `<audienceUris>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.AudienceUriElementCollection> tarafından temsil edilir. Koleksiyona eklenen tek bir URI <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı tarafından temsil edilir.  
  
> [!NOTE]
> `<audienceUris>` [Öğesinin \<IdentityConfiguration >](identityconfiguration.md) öğesinin bir alt öğesi olarak kullanılması kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, bir uygulama için kabul edilebilir hedef kitle URI 'Lerinin nasıl yapılandırılacağını gösterir. Bu örnek, tek bir URI 'yi yapılandırır. Bu URI için kapsamlı belirteçler kabul edilecek, diğerleri reddedilir.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
