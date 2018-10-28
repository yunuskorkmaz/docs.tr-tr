---
title: '&lt;Yuva&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: ff06fd6518e67020b4d67d4e081307b8e54bae85
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194702"
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;Yuva&gt; öğesi (ağ ayarları)
Yuva işlemleri tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.  
  
 \<Yapılandırma >  
\<system.net>  
\<Ayarlar >  
\<Yuva >  
  
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
|`alwaysUseCompletionPortsForAccept`|Yuva tamamlama bağlantı noktaları her zaman için Accept yöntemi çağrıları kullanıp kullanmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`alwaysUseCompletionPortsForConnect`|Yuva tamamlama bağlantı noktaları her zaman Connect yöntem çağrıları için kullanıp kullanmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`ipProtectionLevel`|Varsayılan belirtir <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> bir yuva için kullanılacak. Varsayılan değer Windows sürümüne bağlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `alwaysUseCompletionPortsForAccept` Ve `alwaysUseCompletionPortsForConnect` öznitelikleri tamamlama bağlantı noktaları kullanımına ilişkin varsayılan davranışını belirtmek için kullanılan sınıfları tarafından <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Tamamlama bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.  
  
 İçin varsayılan değer `alwaysUseCompletionPortsForAccept` ve `alwaysUseCompletionPortsForConnect` öznitelikleri **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForAccept` ilgili yapılandırma dosyaları özniteliği. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForConnect` ilgili yapılandırma dosyaları özniteliği.  
  
 `ipProtectionLevel` Özniteliği belirtir Varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> bir yuva için kullanılacak. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, belirtilen bir kapsam için bir IPv6 yuva için bir kısıtlama yapılandırması gibi adresleri aynı sitede yerel bir önek veya yerel bağlantı sağlar. Bu seçenek, IPv6 yuvalarda erişim kısıtlaması için uygulamaları etkinleştirir. Bu kısıtlamaların yeterlidir ve yerine kendisini dış saldırılarına karşı zorlaştırmak özel bir LAN üzerinde çalışan bir uygulama. Bu seçenek widens veya dinleme yuva, genel ve özel kullanıcılar uygun olduğunda veya gerektiği gibi aynı site için yalnızca erişimini etkinleştirme sınırsız erişim kapsamını daraltır.  
  
 Bu `ipProtectionLevel` özniteliğini yalnızca ilk gelen trafiği etkiler:  
  
-   Bir TCP yuva gelen bağlantıları için dinlemek sunucu.  
  
-   Bir paketin bir yuvada alma bir UDP uygulamasıdır.  
  
 Bu yapılandırma ayarının (her iki yönde trafik Kısıtlanmamış) önceden kurulmuş TCP bağlantıları etkilemez ve UDP paketlerini gönderen uygulama etkilemez.  
  
 Olası değerler için `ipProtectionLevel` özniteliğini karşılık gelen belirtilen tanımlı koruma düzeyleri ile <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> sabit listesi aşağıdaki gibi:  
  
|**Öznitelik değeri**|**Açıklama**|  
|-|-|  
|EdgeRestricted|IP koruma düzeyi kısıtlı edge ' dir. Bu değer Internet üzerinden çalışmak üzere tasarlanmış uygulamalar tarafından kullanılabilir. Bu ayar Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) geçişine izin vermez. Bu uygulamalar, uygulamalar, açık bağlantı noktalarından yönlendirilmiş Internet saldırılarına karşı sıkı gerekir böylece IPv4 güvenlik duvarları, atlayabilir. Windows Server 2003 ve Windows XP'de bir yuvada IP koruma düzeyi için varsayılan değer edge kısıtlı ' dir.|  
|kısıtlı|IP koruma düzeyi sınırlıdır. Bu değer olarak Internet senaryoları uygulamayan intranet uygulamalar tarafından kullanılır. Bu uygulamalar genel olmayan test veya Internet stili saldırılarına karşı sıkı. Bu ayar yalnızca bağlantı yerel alınan trafik sınırlar.|  
|Sınırsız|IP koruma düzeyi kısıtlanır. Bu değer yerleşik IPv6 NAT geçişi özelliklerini yararlanarak uygulamaları dahil olmak üzere Internet üzerinden çalışmak üzere tasarlanmış uygulamalar tarafından kullanılması halinde Windows (örneğin, Teredo). Bu uygulamalar, uygulamalar, açık bağlantı noktalarından yönlendirilmiş Internet saldırılarına karşı sıkı gerekir böylece IPv4 güvenlik duvarları, atlayabilir. Bir yuva IP koruma düzeyi için varsayılan değer, Windows Server 2008 R2 ve Windows Vista, kısıtlanır.|  
|Belirtilmemiş|IP koruma düzeyi belirtilmemiş. Windows 7 ve Windows Server 2008 R2 üzerinde bir yuvada IP koruma düzeyi için varsayılan değer belirtilmemiş.|  
  
 İçin varsayılan değer `ipProtectionLevel` özniteliği **belirtilmemiş**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, geçerli değerini almak için kullanılabilir `ipProtectionLevel` geçerli yapılandırma dosyalarından özniteliği.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl tamamlama bağlantı noktalarının kullanılması gerektiğini belirtin ve bu gösterir. varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> sınırsız olmalıdır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
- <xref:System.Net?displayProperty=nameWithType>  
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
- <xref:System.Net.Sockets?displayProperty=nameWithType>  
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
