---
title: <ipv6> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: b8969cecf8ffb2ef23522f193bb322b1170e6111
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705070"
---
# <a name="ipv6-element-network-settings"></a>\<IPv6 > öğesi (ağ ayarları)
Internet Protokolü sürüm 6 (IPv6) sağlar eski üyeler alınan yanıtları <xref:System.Net.Dns> sınıfı.  
  
 \<Yapılandırma >  
\<system.net>  
\<Ayarlar >  
\<IPv6 >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`enabled`|Belirtir olup olmadığını üyeleri <xref:System.Net.Dns> sınıfı Internet Protokolü sürüm 6 (IPv6) adreslerini döndürür. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu ayar eski üyeler için IPv6 desteğini etkinleştirir <xref:System.Net.Dns> sınıfı: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, ve <xref:System.Net.Dns.Resolve%2A>. Diğer üyeleriyle ilgili <xref:System.Net?displayProperty=nameWithType> ad alanı, IPv6 adresleri döndürülecek IPv6 işletim sistemi içinde etkinleştirilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek için IPv6 desteğini nasıl etkinleştireceğinizi gösterir <xref:System.Net.Dns> sınıfı.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
