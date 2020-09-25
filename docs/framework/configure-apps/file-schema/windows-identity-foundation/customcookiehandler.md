---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: a8ee23ac6facaea18cd7f1820616cb9b16afa336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189857"
---
# \<customCookieHandler>

Özel tanımlama bilgisi işleyici türünü ayarlar. Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "Custom" ise mevcut olabilir. Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a>Syntax  
  
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
|tür|Sınıfından türetilen özel bir tür belirtir <xref:System.IdentityModel.Services.CookieHandler> . Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> Tanımlama bilgilerini okumak ve yazmak için kullandığı öğesini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `mode`Öğesinin özniteliğini "Custom" olarak ayarlayarak özel bir tanımlama bilgisi işleyicisi belirttiğinizde `<cookieHandler>` , `<customCookieHandler>` tanımlama bilgisi işleyici türüne başvuran bir alt öğe ekleyerek özel tanımlama bilgisi işleyicisinin türünü belirtmeniz gerekir. `mode`Öznitelik "öbekli" veya "default" olarak ayarlandığında bu öğe belirtilemez. Özel tanımlama bilgisi işleyicileri <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.  
  
 `<customCookieHandler>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.CustomTypeElement> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, SAM türünde özel bir tanımlama bilgisi işleyicisi kullanmak için SAM 'ı yapılandırır `MyNamespace.MyCustomCookieHandler` .  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.CookieHandler>
