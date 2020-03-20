---
title: <sistemi.tanılama> Elemanı
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153213"
---
# <a name="systemdiagnostics-element"></a>\<system.diagnostics> Element
İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<>iddia](assert-element.md)|Yöntemi aradiğinizde ileti kutusunun görüntülenip <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> görüntülenip görüntülenmeyeceğini belirtir; ayrıca ileti yazacak dosyanın adını belirtir.|  
|[\<performansSayaçları>](performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.|  
|[\<paylaşılanDinleyiciler>](sharedlisteners-element.md)|Herhangi bir kaynak veya izleme öğesinin başvuruedebileceği dinleyicileri içerir. Paylaşılan dinleyici olarak tanımlanan dinleyiciler kaynaklara veya izadile eklenebilir.|  
|[\<kaynaklar>](sources-element.md)|İletileri izlemeyi başlatan izleme kaynaklarını belirtir.|  
|[\<anahtarları>](switches-element.md)|İzleme anahtarları ve izleme anahtarlarının ayarlandığı düzeyleri içerir.|  
|[\<izleme>](trace-element.md)|İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ** \<sistemin** içine izleme anahtarı ve izleme dinleyicisi nasıl yerleştirilir gösterilmektedir.tanılama>öğesi. `General` İzleme anahtarı düzeye <xref:System.Diagnostics.TraceLevel> ayarlanır. İzleme dinleyicisi `myListener` adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar.  
  
> [!NOTE]
> .NET Framework sürüm 2.0'da, bir anahtarın değerini belirtmek için metni kullanabilirsiniz. Örneğin, `true` bir <xref:System.Diagnostics.BooleanSwitch> için belirtebilir veya bir `Error` <xref:System.Diagnostics.TraceSwitch>. gibi numaralandırma değerini temsil eden metni kullanabilirsiniz. Satır `<add name="myTraceSwitch" value="Error" />` ' a `<add name="myTraceSwitch" value="1" />`eşdeğerdir.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
