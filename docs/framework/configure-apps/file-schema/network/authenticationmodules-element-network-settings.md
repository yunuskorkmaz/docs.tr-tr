---
description: 'Daha fazla bilgi edinin: <authenticationModules> öğesi (ağ ayarları)'
title: <authenticationModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 2c2dc3c6a3d8fc064bb24c3d86a4441c269e43f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698628"
---
# <a name="authenticationmodules-element-network-settings"></a>\<authenticationModules> Öğesi (Ağ Ayarları)

Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a>Syntax  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[add](add-element-for-authenticationmodules-network-settings.md)|Uygulamaya bir kimlik doğrulama modülü ekler.|  
|[lediğiniz](clear-element-for-authenticationmodules-network-settings.md)|Tüm kimlik doğrulama modüllerini uygulamadan temizler.|  
|[temizlenmesine](remove-element-for-authenticationmodules-network-settings.md)|Bir kimlik doğrulama modülünü uygulamadan kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `authenticationModule`Öğesi, bir sunucusuyla kimlik doğrulama işlemini gerçekleştiren kimlik doğrulama modüllerini belirtir. Bir kimlik doğrulama modülünün arabirimini uygulaması gerekir <xref:System.Net.IAuthenticationModule> .  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek bir kimlik doğrulama modülünü mümkün bir şekilde sunar. Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Ağ ayarları şeması](index.md)
