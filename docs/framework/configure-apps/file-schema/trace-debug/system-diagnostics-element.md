---
title: <System. Diagnostics> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153213"
---
# <a name="systemdiagnostics-element"></a>\<system.diagnostics> Öğesi
İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.  
  
[**\<configuration>**](../configuration-element.md)  
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
|[\<assert>](assert-element.md)|Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.|  
|[\<performanceCounters>](performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir. Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.|  
|[\<sources>](sources-element.md)|İzleme iletilerini Başlatan izleme kaynaklarını belirtir.|  
|[\<switches>](switches-element.md)|İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyleri içerir.|  
|[\<trace>](trace-element.md)|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir izleme anahtarı ve bir İzleme dinleyicisinin öğenin içine nasıl ekleneceğini gösterir **\<system.diagnostics>** . `General`İzleme anahtarı düzeyi olarak ayarlanır <xref:System.Diagnostics.TraceLevel> . İzleme dinleyicisi `myListener` adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' de, bir anahtarın değerini belirtmek için metin kullanabilirsiniz. Örneğin, `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya gibi bir numaralandırma değerini temsil eden metni kullanabilirsiniz `Error` <xref:System.Diagnostics.TraceSwitch> . Satır `<add name="myTraceSwitch" value="Error" />` ile eşdeğerdir `<add name="myTraceSwitch" value="1" />` .  
  
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
