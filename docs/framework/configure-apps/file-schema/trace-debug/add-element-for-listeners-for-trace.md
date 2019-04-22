---
title: <add> Öğe için <listeners> için <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ba0ffc4f95b9af7fcd319068501ce0bb9714c2ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089588"
---
# <a name="add-element-for-listeners-for-trace"></a>\<Ekle > öğesi için \<dinleyicileri > için \<İzleme >
Bir ekler **dinleyicileri** koleksiyonu.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<İzleme >  
\<dinleyicileri >  
\<Ekle >  
  
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
|**type**|Gerekli öznitelik.<br /><br /> Dinleyici türünü belirtir. Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dizesi.|  
|**Adı**|İsteğe bağlı öznitelik.<br /><br /> Dinleyicisinin adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`listeners`|Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir. Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.|  
|`trace`|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Diagnostics.Debug> Ve <xref:System.Diagnostics.Trace> sınıfları paylaşma aynı **dinleyicileri** koleksiyonu. Bu sınıflardan birine koleksiyonuna bir dinleyici nesne eklerseniz, başka bir sınıfın aynı dinleyicisi kullanır. Dinleyici sınıfların türetilmesi <xref:System.Diagnostics.TraceListener>.  
  
 Siz belirtmezseniz `name` İzleme dinleyicisi özniteliği <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisi Varsayılanları boş bir dize (""). Uygulamanızın yalnızca bir dinleyicisi varsa, bir adı belirtmeden ekleme ve boş bir dize adı belirterek kaldırın. Ancak, uygulamanızın birden fazla dinleyici varsa tanımlamanıza ve içinde tek tek izleme dinleyicilerine yönetmenize olanak tanıyan her İzleme dinleyicisi için benzersiz adlar belirtmeniz gerekir <xref:System.Diagnostics.Debug.Listeners%2A> ve <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonları.  
  
> [!NOTE]
>  Birden fazla İzleme dinleyicisi aynı türde ve aynı adı yalnızca bir izleme dinleyicisi sonuçlarında türü ekleyip eklenmesini ad `Listeners` koleksiyonu. Ancak, program aracılığıyla birden fazla özdeş dinleyicilere ekleyebilirsiniz `Listeners` koleksiyonu.  
  
 Değeri **initializeData** özniteliği oluşturduğunuz dinleyici türüne bağlıdır. Tüm izleme dinleyicilerine belirtmenizi gerektiren **initializeData**.  
  
> [!NOTE]
>  Kullanırken `initializeData` özniteliği, "'initializeData' özniteliği. bildirilmedi" uyarı derleyici alabilirsiniz Bu uyarı oluşur yapılandırma ayarlarını soyut temel sınıf doğrulanır <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği. Genellikle, bir parametre alan bir oluşturucu sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tablo .NET Framework ile birlikte izleme dinleyicilerine gösterir ve değerinin açıklanmıştır kendi **initializeData** öznitelikleri.  
  
|İzleme dinleyicisi sınıfı|initializeData özniteliği değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.  Ayarlama `initializeData` özniteliğini "`true`" izleme ve hata ayıklama yazılacak çıkış <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" yazılacak <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Dosya adı <xref:System.Diagnostics.DelimitedListTraceListener> yazar.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Mevcut bir olay günlüğü kaynağı adı adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<Ekle >** dinleyiciler eklemek için öğeleri `MyListener` ve `MyEventListener` için **dinleyicileri** koleksiyonu. `MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar. `MyEventListener` olay günlüğünde bir giriş oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
