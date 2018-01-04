---
title: "&lt;authenticationModules&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: e7fcaee557884d0c24b7bb15f2424a9e0a413439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a>&lt;authenticationModules&gt; öğesi (ağ ayarları)
Ağ isteklerine kimlik doğrulaması için kullanılan modülleri belirtir.  
  
 \<Yapılandırma >  
\<System.NET >  
\<authenticationModules >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|Bir kimlik doğrulama modülü uygulamaya ekler.|  
|[Temizle](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|Uygulamadaki tüm kimlik doğrulama modülleri temizler.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|Bir kimlik doğrulama modülü uygulamadan kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `authenticationModule` Öğesi ile bir sunucu kimlik doğrulama işlemi gerçekleştir kimlik doğrulama modülleri belirtir. Bir kimlik doğrulama modülü uygulamalıdır <xref:System.Net.IAuthenticationModule> arabirimi.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir kimlik doğrulama modülü sağlar. Belirtilen modül için doğru değerlerle sürüm ve PublicKeyToken için değerleri değiştirmelisiniz.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
