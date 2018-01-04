---
title: "&lt;Yuva&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fefb8e119d428d86501e1c8cdd5eec5ef0809cbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;Yuva&gt; öğesi (ağ ayarları)
Yuva işlemleri tamamlama bağlantı noktalarını kullanacak olup olmadığını belirtir.  
  
 \<Yapılandırma >  
\<System.NET >  
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
  
|**Özniteliği**|**Açıklama**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Yuva her zaman tamamlama bağlantı noktalarını kabul yöntemi çağrıları için kullanılması gerekip gerekmediğini gösterir. Varsayılan değer `false` şeklindedir.|  
|`alwaysUseCompletionPortsForConnect`|Yuva her zaman tamamlama bağlantı noktalarını Bağlan yöntem çağrıları için kullanılması gerekip gerekmediğini gösterir. Varsayılan değer `false` şeklindedir.|  
|`ipProtectionLevel`|Varsayılan belirtir <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> yuva için kullanılacak. Varsayılan değer Windows sürümüne bağlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `alwaysUseCompletionPortsForAccept` Ve `alwaysUseCompletionPortsForConnect` öznitelikleri tamamlama bağlantı noktaları kullanımına ilişkin varsayılan davranışı belirtmek için tarafından kullanılan sınıfları <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Tamamlama bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.  
  
 İçin varsayılan değer `alwaysUseCompletionPortsForAccept` ve `alwaysUseCompletionPortsForConnect` öznitelikleri **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForAccept` geçerli yapılandırma dosyalarını özniteliği. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForConnect` geçerli yapılandırma dosyalarını özniteliği.  
  
 `ipProtectionLevel` Özniteliği belirtir. varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> yuva için kullanılacak. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, belirtilen kapsam için bir IPv6 yuva için bir kısıtlama yapılandırması gibi aynı adresleriyle site yerel öneki veya yerel bağlantı sağlar. Bu seçenek, erişim kısıtlamaları IPv6 yuvalarda yerleştirmek uygulamaları etkinleştirir. Tür kısıtlamaları sadece ve yerine kendi dış saldırılara karşı sağlamlaştırmak özel bir LAN üzerinde çalışan bir uygulama etkinleştirin. Bu seçenek widens veya dinleme yuva, ortak ve özel kullanıcılar uygun olduğunda veya yalnızca aynı sitede gerektiği için erişimi kısıtlamak etkinleştirme Kısıtlanmamış erişim kapsamını daraltır.  
  
 Bu `ipProtectionLevel` özniteliği ayar, yalnızca ilk gelen trafiğe etkiler:  
  
-   Bir yuvada gelen bağlantılar için dinleme TCP sunucu.  
  
-   Paket bir yuvada alma UDP uygulama.  
  
 Bu yapılandırma ayarının (her iki yönde trafik Kısıtlanmamış) zaten oluşturulmuş TCP bağlantılarını etkilemez ve UDP paketlerini gönderen uygulama etkilemez.  
  
 Olası değerler için `ipProtectionLevel` özniteliğinin ayarına karşılık gelen belirtilen tanımlanan koruma düzeyleri ile <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> şekilde numaralandırma:  
  
|**Öznitelik değeri**|**Açıklama**|  
|-|-|  
|EdgeRestricted|IP koruma düzeyi kenar sınırlı olur. Bu değer Internet üzerinden çalışmak için tasarlanmış uygulamalar tarafından kullanılır. Bu ayar Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) geçişine izin vermiyor. Açılan bağlantı noktasına yönelik Internet saldırılarına karşı uygulamalar sıkı gerekir böylece bu uygulamaları IPv4 güvenlik duvarları, atlayabilir. Windows Server 2003 ve Windows XP üzerinde bir yuvada IP koruma düzeyi için varsayılan değer kısıtlanmış kenar ' dir.|  
|Sınırlı|IP koruma düzeyi sınırlıdır. Bu değer Internet senaryoları kullanılmaz intranet uygulamalar tarafından kullanılır. Bu uygulamalar genellikle değil test veya Internet stili saldırılarına karşı sıkı. Bu ayar yalnızca bağlantı yerel alınan trafiğini sınırlar.|  
|Sınırsız|IP koruma düzeyi kısıtlanır. Bu değer yerleşik IPv6 NAT geçişi özelliklerini yararlanarak uygulamalar dahil olmak üzere, Internet üzerinden çalışmak için tasarlanmış uygulamalar tarafından kullanılması halinde Windows (örneğin, Teredo). Açılan bağlantı noktasına yönelik Internet saldırılarına karşı uygulamalar sıkı gerekir böylece bu uygulamaları IPv4 güvenlik duvarları, atlayabilir. Windows Server 2008 R2 ve Windows Vista üzerinde bir yuvada IP koruma düzeyi için varsayılan değer kısıtlanır.|  
|Belirtilmemiş|IP koruma düzeyi belirtilmedi. Windows 7 ve Windows Server 2008 R2 üzerinde bir yuvada IP koruma düzeyi için varsayılan değer belirtilmedi.|  
  
 İçin varsayılan değer `ipProtectionLevel` özniteliği **belirtilmemiş**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, geçerli değerini almak için kullanılabilir `ipProtectionLevel` geçerli yapılandırma dosyalarını özniteliği.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tamamlama bağlantı noktalarının kullanılacağını belirtin ve sonra gösterir varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> Kısıtlanmamış olmalıdır.  
  
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
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
