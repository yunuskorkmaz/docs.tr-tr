---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b974767aa86801bff234e200e1fce021bfc422c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomcookiehandlergt"></a>&lt;customCookieHandler&gt;
Özel tanımlama bilgisi işleyici türünü ayarlar. Bu öğe yalnızca mevcut olabilir, `mode` özniteliği `<cookieHandler>` "Özel" bir öğedir. Özel tür öğesinden türetilmelidir <xref:System.IdentityModel.Services.CookieHandler> sınıfı.  
  
 \<system.identityModel.services >  
\<Federationconfiguration'a >  
\<cookieHandler >  
\<customCookieHandler >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Türetilen bir özel tür belirtir <xref:System.IdentityModel.Services.CookieHandler> sınıfı. Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgilerini kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarlayarak özel tanımlama bilgisi işleyici belirttiğinizde `mode` özniteliği `<cookieHandler>` öğesi "Özel" ekleyerek özel tanımlama bilgisi işleyicisinin türü belirtmelisiniz bir `<customCookieHandler>` tanımlama bilgisi işleyici türüne başvuran alt öğesi. Bu öğe olamaz belirtilen `mode` özniteliği "Chunked" veya "Varsayılan" olarak ayarlanmış. Özel tanımlama bilgisi işleyicileri öğesinden türetilmelidir <xref:System.IdentityModel.Services.CookieHandler> sınıfı.  
  
 `<customCookieHandler>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.CustomTypeElement> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek türünde bir özel tanımlama bilgisi işleyicisi kullanmak için SAM yapılandırır `MyNamespace.MyCustomCookieHandler`.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Services.CookieHandler>
