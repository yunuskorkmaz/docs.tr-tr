---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152586"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver>
Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder. Hizmet belirteci çözümleyicisi, gelen belirteçler ve iletiler üzerindeki şifreleme belirteci çözümlemek için kullanılır.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
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
|type|Hizmet belirteci çözümleyicisinin türünü belirtir. <xref:System.IdentityModel.Selectors.SecurityTokenResolver> Sınıftan <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tür veya tür. Öznitelik nasıl belirtilir `type` hakkında daha fazla bilgi için bkz: [Özel Tür Başvuruları]. Gereklidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<güvenlikTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Güvenlik belirteç işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmet belirteci çözümleyicisi, gelen belirteçler ve iletiler üzerindeki şifreleme belirteci çözümlemek için kullanılabilir. Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır. Özniteliği belirtmeniz `type` gerekir. Belirtilen tür, <xref:System.IdentityModel.Selectors.SecurityTokenResolver> <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıftan türeyen özel bir tür olabilir.  
  
 Bazı belirteç işleyicileri yapılandırmada hizmet belirteç çözümleyicisi ayarlarını belirtmenize olanak tanır. Tek tek belirteç işleyicileri ayarları, güvenlik belirteci işleyicisi koleksiyonunda belirtilenleri geçersiz kılar.  
  
> [!NOTE]
> Kimlik Yapılandırma `<serviceTokenResolver>` [ \<>](identityconfiguration.md) öğesinin alt öğesi olarak öğebelirtilmesi küçümsenmiştir, ancak yine de geriye dönük uyumluluk için desteklenir. Öğedeki `<securityTokenHandlerConfiguration>` `<identityConfiguration>` ayarlar, öğedekiayarları geçersiz kılar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
