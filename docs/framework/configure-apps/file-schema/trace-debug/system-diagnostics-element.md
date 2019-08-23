---
title: < System. Diagnostics > öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: f3b4238a8d7028d47122a420526b38ee4f327332
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926939"
---
# <a name="systemdiagnostics-element"></a>\<System. Diagnostics > öğesi
İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
  
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
|[\<onaylama >](assert-element.md)|<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.|  
|[\<performanceCounters >](performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.|  
|[\<sharedListeners >](sharedlisteners-element.md)|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir. Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.|  
|[\<Kaynaklar >](sources-element.md)|İzleme iletilerini Başlatan izleme kaynaklarını belirtir.|  
|[\<Anahtarlar >](switches-element.md)|İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyleri içerir.|  
|[\<İzleme >](trace-element.md)|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir izleme anahtarı ve bir İzleme dinleyicisinin  **\<System. Diagnostics >** öğesinin içine nasıl ekleneceğini gösterir. İzleme anahtarı <xref:System.Diagnostics.TraceLevel> düzeyi olarak ayarlanır. `General` İzleme dinleyicisi `myListener` adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' de, bir anahtarın değerini belirtmek için metin kullanabilirsiniz. Örneğin, `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya gibi `Error` bir numaralandırma <xref:System.Diagnostics.TraceSwitch>değerini temsil eden metni kullanabilirsiniz. Satır `<add name="myTraceSwitch" value="Error" />` ile`<add name="myTraceSwitch" value="1" />`eşdeğerdir.  
  
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
