---
title: "&lt;kaldırma&gt; öğesi authenticationModules (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 077a6f3cb7020d501978fa112a0c318efee27e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a>&lt;kaldırma&gt; öğesi authenticationModules (ağ ayarları) için
Bir kimlik doğrulama modülü uygulamadan kaldırır.  
  
 \<Yapılandırma >  
\<System.NET >  
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
  
|**Özniteliği**|**Açıklama**|  
|-------------------|---------------------|  
|**türü**|Kaldırmak için kimlik doğrulama modülü adı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Ağ isteklerine kimlik doğrulaması için kullanılan modülleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `remove` Öğeyi yapılandırma dosyası veya yapılandırma hiyerarşisindeki daha yüksek düzeyde daha önce tanımlanan kimlik doğrulama modülleri kaldırır.  
  
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
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
