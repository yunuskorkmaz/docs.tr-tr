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
ms.openlocfilehash: 0d108f2350d82666e3dc24f0f6854fe64ea4755f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674498"
---
# <a name="module-element-network-settings"></a>\<Modül > öğesi (ağ ayarları)
Yeni proxy modülü uygulamayı ekler.  
  
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
|`type`|Tam nitelikli tür adı (belirttiği <xref:System.Type.FullName%2A> özelliği) ve derleme adı (belirttiği <xref:System.Reflection.Assembly.FullName%2A> özelliği) proxy uygulayan bir virgülle ayrılmış.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `module` Öğesi kaydeder uygulayan proxy sınıflar <xref:System.Net.IWebProxy> arabirimi. Proxy sınıfı kaydettikten sonra `module` desteklenen proxy üzerinden bilgi istemek için kullanılabilir.  
  
 Değeri `type` modülünün sınıfı adı ve ' % s'adı, karşılık gelen dinamik bağlantı kitaplığı (DLL), öznitelik olmalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
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
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
