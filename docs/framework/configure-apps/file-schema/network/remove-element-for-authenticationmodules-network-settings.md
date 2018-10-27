---
title: '&lt;kaldırma&gt; authenticationModules (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: 65b5b7f717912ecaee73a5b24e65d22b902a4e44
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180711"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a>&lt;kaldırma&gt; authenticationModules (ağ ayarları) için
Bir kimlik doğrulama modülü uygulamadan kaldırır.  
  
 \<Yapılandırma >  
\<system.net>  
\<authenticationModules >  
\<kaldırma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|**Türü**|Kimlik doğrulama modülünü kaldırmak için adı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `remove` , Daha önce yapılandırma dosyası veya yapılandırma hiyerarşideki daha yüksek bir düzeyde tanımlanan kimlik doğrulama modülü öğeyi kaldırır.  
  
 Değeri `type` özniteliği geçerli bir sınıf adı olmalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir kimlik doğrulama modülü kaldırır.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- <xref:System.Net.IAuthenticationModule>  
- <xref:System.Net.AuthenticationManager>  
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
