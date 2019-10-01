---
title: <socket> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: ec2c8388411e24940041dc9dcb7f6a6755e89805
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697582"
---
# <a name="socket-element-network-settings"></a>\<socket > öğesi (ağ ayarları)
Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<socket >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Yuvanın Yöntem çağrılarını kabul etmek için her zaman tamamlama bağlantı noktalarını kullanıp kullanmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`alwaysUseCompletionPortsForConnect`|Yuvanın, bağlantı yöntemi çağrıları için her zaman tamamlama bağlantı noktaları kullanması gerekip gerekmediğini belirtir. Varsayılan değer `false` şeklindedir.|  
|`ipProtectionLevel`|Yuva için kullanılacak varsayılan @no__t (0) belirtir. Varsayılan değer, Windows sürümüne bağlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](settings-element-network-settings.md)|@No__t-0 ad alanı için temel ağ seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 ve `alwaysUseCompletionPortsForConnect` öznitelikleri, @no__t -2. Namespace içindeki sınıflar tarafından tamamlama bağlantı noktalarının kullanımıyla ilgili varsayılan davranışı belirtmek için kullanılır. Tamamlanma bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.  
  
 @No__t-0 ve `alwaysUseCompletionPortsForConnect` öznitelikleri için varsayılan değer **false**'dur.  
  
 @No__t-0, uygun yapılandırma dosyalarından `alwaysUseCompletionPortsForAccept` özniteliğinin geçerli değerini almak için kullanılabilir. @No__t-0, uygun yapılandırma dosyalarından `alwaysUseCompletionPortsForConnect` özniteliğinin geçerli değerini almak için kullanılabilir.  
  
 @No__t-0 özniteliği, bir yuva için kullanılacak varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ' i belirtir. @No__t-0 özelliği, aynı bağlantı yerel veya site yerel ön ekine sahip adresler gibi, IPv6 soketi için belirtilen kapsama yönelik bir kısıtlama yapılandırılmasını sağlar. Bu seçenek, uygulamaların IPv6 yuvaları üzerinde erişim kısıtlamaları yerleştirmesini sağlar. Bu tür kısıtlamalar, özel bir LAN üzerinde çalışan bir uygulamanın kendisini dış saldırılara karşı tek ve robustly bir şekilde kendi kendine ister. Bu seçenek, bir dinleme yuvasının kapsamını widens veya daraltır, uygun olduğunda genel ve özel kullanıcılardan Kısıtlanmamış erişimi etkinleştirir ya da gerektiğinde erişimi yalnızca aynı siteye kısıtlamadır.  
  
 Bu `ipProtectionLevel` öznitelik ayarı yalnızca ilk gelen trafiği etkiler:  
  
- Bir yuvada gelen bağlantıları dinleyen bir TCP sunucusu.  
  
- Bir yuvada paket alan UDP uygulaması.  
  
 Bu yapılandırma ayarı, zaten kurulu olan TCP bağlantılarını etkilemez (trafik her iki yönde kısıtlanır) ve UDP paketleri gönderen bir uygulamayı etkilemez.  
  
 @No__t-0 öznitelik ayarı için olası değerler, aşağıdaki gibi <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> numaralandırmasında belirtilen tanımlı koruma düzeylerine karşılık gelir:  
  
|**Öznitelik değeri**|**Açıklama**|  
|-|-|  
|EdgeRestricted|IP koruma düzeyi kenar kısıtlanıyor. Bu değer, Internet 'te çalışacak şekilde tasarlanan uygulamalar tarafından kullanılır. Bu ayar, Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) çapraz geçişine izin vermez. Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir. Windows Server 2003 ve Windows XP 'de, bir yuvada IP koruma düzeyi için varsayılan değer kenar kısıtlıdır.|  
|Dığından|IP koruması düzeyi kısıtlıdır. Bu değer, Internet senaryoları uygulamayan intranet uygulamaları tarafından kullanılır. Bu uygulamalar genellikle Internet stili saldırılara karşı sınanmamıştır veya sağlamlamazlar. Bu ayar, alınan trafiği yalnızca bağlantı yerel ile sınırlandırır.|  
|Edin|IP koruması düzeyi Kısıtlanmamış. Bu değer, Windows 'da yerleşik olarak bulunan IPv6 NAT çapraz geçiş özelliğinden faydalanan uygulamalar da dahil olmak üzere tasarlanan uygulamalar tarafından kullanılır (örneğin, Teredo). Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir. Windows Server 2008 R2 ve Windows Vista 'da, bir yuvada IP koruma düzeyi için varsayılan değer Kısıtlamasız olur.|  
|Memesi|IP koruması düzeyi belirtilmemiş. Windows 7 ve Windows Server 2008 R2 'de, bir yuvada IP koruma düzeyi için varsayılan değer belirtilmemiş olur.|  
  
 @No__t-0 özniteliği için varsayılan değer **belirtilmemiş**.  
  
 @No__t-0 özelliği uygulanabilir yapılandırma dosyalarından `ipProtectionLevel` özniteliğinin geçerli değerini almak için kullanılabilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bu tamamlama bağlantı noktalarının kullanılması gerektiğini ve varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ' ın Kısıtlanmamış olması gerektiğini gösterir.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
