---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942793"
---
# <a name="customcookiehandler"></a>\<Custombir ıehandler >
Özel tanımlama bilgisi işleyici türünü ayarlar. Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "Custom" ise mevcut olabilir. Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.  
  
 \<System. IdentityModel. Services >  
\<federationConfiguration >  
\<Tanımlama, ıehandler >  
\<Custombir ıehandler >  
  
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
|türü|<xref:System.IdentityModel.Services.CookieHandler> Sınıfından türetilen özel bir tür belirtir. `type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tanımlama, ıehandler >](cookiehandler.md)|Tanımlama bilgilerini okumak ve yazmak için kullandığıöğesiniyapılandırır.<xref:System.IdentityModel.Services.SessionAuthenticationModule> <xref:System.IdentityModel.Services.CookieHandler>|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesinin özniteliğini "Custom" olarak ayarlayarak `<customCookieHandler>` özel bir tanımlama bilgisi işleyicisi belirttiğinizde, tanımlama bilgisi işleyici türüne başvuran bir alt öğe ekleyerek özel tanımlama bilgisi işleyicisinin türünü belirtmeniz gerekir. `mode` `<cookieHandler>` `mode` Öznitelik "öbekli" veya "default" olarak ayarlandığında bu öğe belirtilemez. Özel tanımlama bilgisi işleyicileri <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.  
  
 `<customCookieHandler>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.CustomTypeElement> tarafından temsil edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, SAM türünde `MyNamespace.MyCustomCookieHandler`özel bir tanımlama bilgisi işleyicisi kullanmak için Sam 'ı yapılandırır.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.CookieHandler>
