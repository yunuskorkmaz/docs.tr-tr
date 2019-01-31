---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267283"
---
# <a name="audienceuris"></a>\<audienceUris>
Bağlı olan taraf (RP) kabul edilebilir tanımlayıcılardır bir URI'leri kümesini belirtir. Bunlar bir URI'leri izin verilen kitle için kapsamlı sürece belirteçleri kabul edilmedi.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<audienceUris>  
  
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
|mod|Bir <xref:System.IdentityModel.Selectors.AudienceUriMode> İzleyici kısıtlama için gelen bir belirteci uygulanmış olup olmadığını belirten bir değer. Olası değerler şunlardır: "Her zaman", "Hiçbir zaman" ve "BearerKeyOnly". Varsayılan değer "Her zaman" dir. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<add value=xs:string>`|Tarafından belirtilen URI ekler `value` özniteliği için AudienceUri koleksiyonu. `value` Özniteliği gereklidir. URI, büyük/küçük harf duyarlıdır.|  
|`<clear>`|AudienceUri koleksiyonu temizler. Tüm tanımlayıcılar koleksiyondan kaldırılır.|  
|`<remove value=xs:string>`|Tarafından belirtilen URI kaldırır `value` AudienceUri koleksiyondan özniteliği. `value` Özniteliği gereklidir. URI, büyük/küçük harf duyarlıdır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, boş bir koleksiyon oluşturulur; kullanma `<add>`, `<clear>`, ve `<remove>` öğeleri koleksiyonu değiştirmek için. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> yapılandırmak için hedef kitleyi URI toplama değerleri hedef kitle URİ'si kısıtlamaları kullanılabilir nesneleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesneleri.  
  
 `<audienceUris>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> sınıfı. Koleksiyona eklenmesini tek bir URI tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı.  
  
> [!NOTE]
>  Kullanımını `<audienceUris>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir. Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, bir uygulama için kabul edilebilir İzleyici URI'ler yapılandırma işlemi gösterilmektedir. Bu örnek, tek bir URI yapılandırır. Bu URI için kapsamlı belirteçleri kabul edilir, diğer tüm reddedilir.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
