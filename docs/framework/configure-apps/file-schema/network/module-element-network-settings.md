---
title: <module> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154835"
---
# <a name="module-element-network-settings"></a>\<modül> Elemanı (Ağ Ayarları)
Uygulamaya yeni bir proxy modülü ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<modül>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`type`|Tam nitelikli tür adı <xref:System.Type.FullName%2A> (özellik tarafından gösterilir) ve derleme <xref:System.Reflection.Assembly.FullName%2A> adı (özellik tarafından gösterilir), bir virgül ile ayrılmış, proxy uygular.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `module` arabirimi uygulayan proxy <xref:System.Net.IWebProxy> sınıflarını kaydeder. Proxy sınıfını kaydettikten `module` sonra, desteklenen proxy aracılığıyla bilgi istemek için kullanılabilir.  
  
 Öznitelik değeri `type` modülün sınıf adı ve ilgili Dinamik Bağlantı Kitaplığı (DLL) adı olmalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneközel bir proxy sınıf kaydeder.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
