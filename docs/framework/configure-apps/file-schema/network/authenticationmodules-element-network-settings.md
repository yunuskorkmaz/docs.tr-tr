---
title: <authenticationModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154978"
---
# <a name="authenticationmodules-element-network-settings"></a>\<kimlik doğrulamaModülleri> Elemanı (Ağ Ayarları)
Ağ isteklerini doğrulamak için kullanılan modülleri belirtir.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<kimlik doğrulamaModülleri>**

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
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ekle](add-element-for-authenticationmodules-network-settings.md)|Uygulamaya bir kimlik doğrulama modülü ekler.|  
|[Temizleyin](clear-element-for-authenticationmodules-network-settings.md)|Tüm kimlik doğrulama modüllerini uygulamadan temizler.|  
|[Kaldırmak](remove-element-for-authenticationmodules-network-settings.md)|Uygulamadan bir kimlik doğrulama modüllerini kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework'ün ağa nasıl bağladığını belirten ayarlar içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `authenticationModule` kimlik doğrulama işlemini bir sunucuyla yürüten kimlik doğrulama modüllerini belirtir. Kimlik doğrulama modülü <xref:System.Net.IAuthenticationModule> arabirimi uygulamalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir kimlik doğrulama modülü sağlar. Sürüm ve PublicKeyToken değerlerini belirtilen modül için doğru değerlerle değiştirmelisiniz.  
  
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
- [Ağ Ayarları Şeması](index.md)
