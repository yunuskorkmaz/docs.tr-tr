---
title: <trace> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153172"
---
# <a name="trace-element"></a>\<izleme> Öğesi
İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<izleme>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`autoflush`|İsteğe bağlı öznitelik.<br /><br /> İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleği otomatik olarak sifonu çekip çıkarmadığını belirtir.|  
|`indentsize`|İsteğe bağlı öznitelik.<br /><br /> Girinecek alanların sayısını belirtir.|  
|`useGlobalLock`|İsteğe bağlı öznitelik.<br /><br /> Genel kilidin kullanılıp kullanılmayacağını gösterir.|  
  
## <a name="autoflush-attribute"></a>autoflush Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çıktı arabelleği otomatik olarak sifonu çekmez. Bu varsayılandır.|  
|`true`|Çıkış arabelleği otomatik olarak temize çıkar.|  
  
## <a name="usegloballock-attribute"></a>globallock özniteliğini kullanma  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Dinleyici iş parçacığı güvenliyse genel kilidi kullanmaz; aksi takdirde, genel kilidi kullanır.|  
|`true`|Dinleyicinin iş parçacığı nın güvenli olup olmadığına bakılmaksızın genel kilidi kullanır. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dinleyici ler>](listeners-element-for-trace.md)|İletileri toplayan, depolayan ve gönderen bir dinleyici belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dinleyiciyi `<trace>` `MyListener` koleksiyona eklemek için öğenin nasıl kullanılacağını `Listeners` gösterir. `MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar. Öznitelik, `useGlobalLock` izleme `false`dinleyicisi iş parçacığı güvenliyse, genel kilidin kullanılmaması için gereken enitelik olarak ayarlanır. `true`Öznitelik, <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> `autoflush` izleme dinleyicisinin yöntemin çağrılıp çağrılmadığına bakılmaksızın dosyaya yazmasına neden olan olarak ayarlanır. Öznitelik `indentsize` 0 (sıfır) olarak ayarlanır ve bu da dinleyicinin <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> yöntem çağrıldığında girinal sıfır boşluklarına neden olur.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
