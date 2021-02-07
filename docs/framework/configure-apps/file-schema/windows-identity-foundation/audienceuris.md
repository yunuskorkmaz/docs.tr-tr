---
description: 'Hakkında daha fazla bilgi edinin: <audienceUris>'
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 98b411e73d4b9941e65daaf5d1d63285cdc90fd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681857"
---
# \<audienceUris>

Bağlı olan tarafın (RP) kabul edilebilir tanımlayıcıları olan URI kümesini belirtir. Belirteçleri, izin verilen hedef kitle URI 'lerinden biri kapsamında olmadıkları müddetçe kabul edilmez.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a>Syntax  
  
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
|mod|<xref:System.IdentityModel.Selectors.AudienceUriMode>Hedef kitle kısıtlamasının bir gelen belirtece uygulanıp uygulanmayacağını belirten bir değer. Olası değerler şunlardır "Always", "hiçbir" ve "Yataerkeyonly". Varsayılan değer "Always" dır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<add value=xs:string>`|Öznitelik tarafından belirtilen URI `value` 'Yi AudienceUri koleksiyonuna ekler. `value`Özniteliği gereklidir. URI, büyük/küçük harfe duyarlıdır.|  
|`<clear>`|AudienceUris koleksiyonunu temizler. Tüm tanımlayıcılar koleksiyondan kaldırılır.|  
|`<remove value=xs:string>`|`value`AudienceUri koleksiyonundan özniteliği tarafından BELIRTILEN URI 'yi kaldırır. `value`Özniteliği gereklidir. URI, büyük/küçük harfe duyarlıdır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak, koleksiyon boştur; `<add>` `<clear>` `<remove>` koleksiyonu değiştirmek için, ve öğelerini kullanın. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nesneler, nesnelerinde izin verilen tüm hedef KITLE URI kısıtlamalarını yapılandırmak için hedef KITLE URI koleksiyonundaki değerleri kullanır <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .  
  
 `<audienceUris>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> . Koleksiyona eklenen tek bir URI sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElement> .  
  
> [!NOTE]
> Öğenin `<audienceUris>` bir alt öğesi olarak kullanılması [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. `<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki XML, bir uygulama için kabul edilebilir hedef kitle URI 'Lerinin nasıl yapılandırılacağını gösterir. Bu örnek, tek bir URI 'yi yapılandırır. Bu URI için kapsamlı belirteçler kabul edilecek, diğerleri reddedilir.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
