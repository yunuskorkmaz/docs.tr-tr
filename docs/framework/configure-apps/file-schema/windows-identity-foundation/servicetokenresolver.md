---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923105"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver >
Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder. Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
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
|türü|Hizmet belirteci Çözümleyicisinin türünü belirtir. Ya tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıftan türeyen bir tür. <xref:System.IdentityModel.Selectors.SecurityTokenResolver> `type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları]. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılabilir. Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır. `type` Özniteliğini belirtmeniz gerekir. Belirtilen tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfından türetilen özel bir tür olabilir.  
  
 Bazı belirteç işleyicileri, yapılandırmada hizmet belirteci çözümleyici ayarlarını belirtmenize olanak tanır. Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.  
  
> [!NOTE]
> Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<serviceTokenResolver>` Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`  
  
## <a name="example"></a>Örnek  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
