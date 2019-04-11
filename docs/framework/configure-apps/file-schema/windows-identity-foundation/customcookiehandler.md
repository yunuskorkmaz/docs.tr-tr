---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 0129c63fe17b63889a77ea1a56c0d7e657def859
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224057"
---
# <a name="customcookiehandler"></a>\<customCookieHandler >
Özel bir tanımlama bilgisi işleyici türünü ayarlar. Bu öğe yalnızca mevcut olması durumunda `mode` özniteliği `<cookieHandler>` "Özel" bir öğedir. Özel tür nesnesinden türetilmesi <xref:System.IdentityModel.Services.CookieHandler> sınıfı.  
  
 \<System.IdentityModel.Services >  
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
| türü|Öğesinden türetilen özel bir türü belirtiyor <xref:System.IdentityModel.Services.CookieHandler> sınıfı. Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgileri kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarlayarak özel bir tanımlama bilgisi işleyici belirttiğinizde `mode` özniteliği `<cookieHandler>` öğesi "Özel" dahil ederek özel tanımlama bilgisi işleyicisinin türü belirtmelisiniz bir `<customCookieHandler>` tanımlama bilgisi işleyici türe başvuran alt öğesi. Bu öğe olamaz belirtilen `mode` "Öbekli" veya "Varsayılan" özniteliğini ayarlayın. Özel bir tanımlama bilgisi işleyicileri türetilmesi gereken <xref:System.IdentityModel.Services.CookieHandler> sınıfı.  
  
 `<customCookieHandler>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.CustomTypeElement> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir özel tanımlama bilgisi işleyicisi türü kullanacak şekilde SAM yapılandırır `MyNamespace.MyCustomCookieHandler`.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.CookieHandler>
