---
title: <add>İçin için <listeners> öğesi<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d4ff919991ab1505b2845a225706d32cc1e57d0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920566"
---
# <a name="add-element-for-listeners-for-trace"></a>\<Trace için \< \<> > öğesi ekleme >
**Dinleyiciler** koleksiyonuna bir dinleyici ekler.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<İzleme >  
\<dinleyiciler >  
\<> Ekle  
  
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
|**type**|Gerekli öznitelik.<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|**initializeData**|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize.|  
|**name**|İsteğe bağlı öznitelik.<br /><br /> Dinleyicinin adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](filter-element-for-add-for-listeners-for-trace.md)|İzleme için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`listeners`|İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir. Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümünün kök öğesini belirtir.|  
|`trace`|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ve sınıfları aynı dinleyicileri toplamayı paylaşır. <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır. Dinleyici sınıfları öğesinden <xref:System.Diagnostics.TraceListener>türetilir.  
  
 İzleme dinleyicisinin `name` özniteliğini belirtmezseniz <xref:System.Diagnostics.TraceListener.Name%2A> , İzleme dinleyicisinin varsayılan değeri boş bir dize ("") olur. Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz. Bununla birlikte, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için benzersiz adlar belirtmelisiniz. Bu, <xref:System.Diagnostics.Debug.Listeners%2A> ve <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonları içindeki tek tek izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlar.  
  
> [!NOTE]
> Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve `Listeners` koleksiyona eklenmekte olan adın yalnızca bir izleme dinleyicisine neden olur. Ancak, `Listeners` koleksiyona daha fazla özdeş dinleyici ekleyebilirsiniz.  
  
 **Initializedata** özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri **ınitializedata**belirtmenizi gerektirmez.  
  
> [!NOTE]
> `initializeData` Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz." Bu uyarı, yapılandırma ayarları <xref:System.Diagnostics.TraceListener> `initializeData` özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur. Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve **ınitializedata** özniteliklerinin değeri açıklanmaktadır.  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun `useErrorStream` değeri.  Trace ve Debug çıkışını yazmak`true`için `initializeData` özniteliği "" olarak ayarlayın <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false` "<xref:System.Console.Out%2A?displayProperty=nameWithType>yazmak için.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Mevcut bir olay günlüğü kaynağı adının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek,  **\<Add >** öğelerinin `MyListener` nasıl kullanılacağını ve dinleyicileri ve `MyEventListener` **dinleyici** koleksiyonuna nasıl ekleneceğini gösterir. `MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar. `MyEventListener`olay günlüğünde bir giriş oluşturur.  
  
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
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [İzleme Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
