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
ms.openlocfilehash: 851a63b41dfb5d3b4058e1373148f48d47d9d6ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664076"
---
# <a name="module-element-network-settings"></a>\<Module > öğesi (ağ ayarları)
Uygulamaya yeni bir proxy modülü ekler.  
  
 \<Yapılandırma >  
\<system.net>  
\<defaultProxy >  
\<Modül >  
  
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
|`type`|Proxy 'yi uygulayan tam tür adı ( <xref:System.Type.FullName%2A> özelliği ile gösterilir) ve derleme adı ( <xref:System.Reflection.Assembly.FullName%2A> özelliği ile gösterilir).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesi, <xref:System.Net.IWebProxy> arabirimini uygulayan proxy sınıflarını kaydeder. `module` Proxy sınıfına kaydolduktan sonra, `module` desteklenen proxy aracılığıyla bilgi istemek için kullanılabilir.  
  
 `type` Özniteliğin değeri, modülün sınıf adı ve karşılık gelen dinamik bağlantı kitaplığının (dll) adı olmalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir özel proxy sınıfı kaydeder.  
  
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
