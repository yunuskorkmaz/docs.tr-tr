---
title: '&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e27187c05b49b7f73ef19243a3286e8c1de71579
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;
Bir dinleyici ekler **dinleyicileri** koleksiyonu.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<İzleme >  
\<dinleyicileri >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**Türü**|Gerekli öznitelik.<br /><br /> Dinleyici türünü belirtir. Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|İsteğe bağlı öznitelik.<br /><br /> Dize için belirtilen sınıf oluşturucuya geçirilen.|  
|**Adı**|İsteğe bağlı öznitelik.<br /><br /> Dinleyici adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Bir dinleyici için bir filtre ekler `Listeners` koleksiyonu için bir izleme.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`listeners`|Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir. Dinleyicileri uygun hedef İzleme çıkışı yönlendirir.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için kök öğesi belirtir.|  
|`trace`|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Diagnostics.Debug> Ve <xref:System.Diagnostics.Trace> sınıfları paylaşmak aynı **dinleyicileri** koleksiyonu. Bu sınıfların birinde koleksiyonuna bir dinleyici nesnesi eklerseniz, başka bir sınıf aynı dinleyicisi kullanır. Dinleyici sınıf türetin <xref:System.Diagnostics.TraceListener>.  
  
 Belirtmezseniz, `name` İzleme dinleyicisi özniteliği <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisi varsayılanları için boş bir dize (""). Yalnızca tek bir dinleyici uygulamanız varsa, bir ad belirtmeden ekleyin ve boş bir dize adı belirterek kaldırın. Ancak, birden çok dinleyici uygulamanız varsa, tanımlamanıza ve tek tek izleme dinleyicileri içinde yönetmenize olanak tanıyan her İzleme dinleyicisi için benzersiz adlar belirtmeniz gerekir <xref:System.Diagnostics.Debug.Listeners%2A> ve <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonları.  
  
> [!NOTE]
>  Birden fazla İzleme dinleyicisi aynı türde ve aynı ekleme yalnızca bir izleme dinleyicisi sonuçlarında türü ve eklenmesini adlandırın `Listeners` koleksiyonu. Ancak, program aracılığıyla birden çok özdeş dinleyici ekleyebilirsiniz `Listeners` koleksiyonu.  
  
 Değeri **initializeData** özniteliği oluşturduğunuz dinleyicisi türüne bağlıdır. Tüm izleme dinleyicileri, belirttiğiniz gerektiren **initializeData**.  
  
> [!NOTE]
>  Kullandığınızda `initializeData` özniteliği, "'initializeData' özniteliği yok bildirildi." uyarı derleyici alabilirsiniz Yapılandırma ayarları Özet temel sınıf karşı doğrulandığı için bu uyarıyı oluşur <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği. Genellikle, bir parametre alan bir oluşturucuya sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda .NET Framework ile birlikte izleme dinleyicilerini gösterir ve değerini açıklar kendi **initializeData** öznitelikleri.  
  
|İzleme dinleyicisi sınıfı|initializeData özniteliği değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.  Ayarlama `initializeData` özniteliğini "`true`" izleme ve hata ayıklama yazmak için çıktı için <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" yazmak için <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Dosyanın adını <xref:System.Diagnostics.DelimitedListTraceListener> yazar.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağı adı adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<Ekle >** dinleyicileri eklemek için öğeleri `MyListener` ve `MyEventListener` için **dinleyicileri** koleksiyonu. `MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar. `MyEventListener` olay günlüğünde bir giriş oluşturur.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
