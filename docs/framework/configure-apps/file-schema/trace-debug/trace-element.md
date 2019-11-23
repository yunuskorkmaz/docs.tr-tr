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
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699178"
---
# <a name="trace-element"></a>\<Trace > öğesi
İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
[ **System. diagnostics\<** &nbsp;&nbsp;>](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<izleme >**  
  
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
|`autoflush`|İsteğe bağlı öznitelik.<br /><br /> İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleğini otomatik olarak temizlemesini belirtir.|  
|`indentsize`|İsteğe bağlı öznitelik.<br /><br /> Girintilendirmek için boşluk sayısını belirtir.|  
|`useGlobalLock`|İsteğe bağlı öznitelik.<br /><br /> Genel kilidin kullanılıp kullanılmayacağını belirtir.|  
  
## <a name="autoflush-attribute"></a>Oto Temizleme özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|, Çıkış arabelleğini otomatik olarak temizlemez. Bu varsayılandır.|  
|`true`|Çıktı arabelleğini otomatik olarak temizler.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Dinleyicisi iş parçacığı güvenli ise, genel kilidi kullanmaz; Aksi takdirde, genel kilidi kullanır.|  
|`true`|Dinleyicinin iş parçacığı güvenli olup olmamasına bakılmaksızın genel kilidi kullanır. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dinleyicileri >](listeners-element-for-trace.md)|İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Listeners` koleksiyonuna dinleyici `MyListener` eklemek için `<trace>` öğesinin nasıl kullanılacağını gösterir. `MyListener`, `MyListener.log` adlı bir dosya oluşturur ve çıktıyı dosyaya yazar. `useGlobalLock` özniteliği, izleme dinleyicisi iş parçacığı güvenli ise, genel kilidin kullanılmasına neden olan `false`olarak ayarlanır. `autoflush` özniteliği `true`olarak ayarlanır, bu da İzleme dinleyicisinin <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> yönteminin çağrılmasının ne olursa olsun dosyaya yazmasına neden olur. `indentsize` özniteliği 0 (sıfır) olarak ayarlanır ve bu, <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> yöntemi çağrıldığında dinleyicinin sıfır boşluk girintilemesini sağlar.  
  
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
