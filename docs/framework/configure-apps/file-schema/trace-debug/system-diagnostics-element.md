---
title: '&lt;System.Diagnostics&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 090c296ba84043445364b350c8b74587c35b5940
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemdiagnosticsgt-element"></a>&lt;System.Diagnostics&gt; öğesi
Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
  
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
|[\<Assert >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi; ayrıca iletileri yazmak için dosya adını belirtir.|  
|[\<performans sayaçları >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel bellek boyutunu belirtir.|  
|[\<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri içerir. Paylaşılan dinleyiciler tanımlanan dinleyicileri kaynakları veya izlemeleri adıyla eklenebilir.|  
|[\<Kaynakları >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|İzleme iletileri başlatmak izleme kaynakları belirtir.|  
|[\<anahtarları >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|İzleme anahtarları ve izleme anahtarları belirlendiği düzeyleri içerir.|  
|[\<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir izleme anahtarı ve İzleme dinleyicisi içindeki katıştırmak gösterilmiştir  **\<system.diagnostics >** öğesi. `General` İzleme anahtarı ayarlanmış <xref:System.Diagnostics.TraceLevel> düzeyi. İzleme dinleyicisi `myListener` adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar.  
  
> [!NOTE]
>  .NET Framework sürüm 2. 0'da, bir anahtar değeri belirtmek için metin kullanabilirsiniz. Örneğin, belirtebilirsiniz `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya bir numaralandırma değeri gibi temsil eden metin `Error` için bir <xref:System.Diagnostics.TraceSwitch>. Satır `<add name="myTraceSwitch" value="Error" />` eşdeğerdir `<add name="myTraceSwitch" value="1" />`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
