---
title: <add><listeners> Için element<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153678"
---
# <a name="add-element-for-listeners-for-trace"></a>\<izleme> \<için> \<dinleyiciler için> Öğesi ekleyin
**Dinleyici** koleksiyonuna bir dinleyici ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**

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
|**Türü**|Gerekli öznitelik.<br /><br /> Dinleyicinin türünü belirtir. [Tam Nitelikli Tür Adları Belirtme'de](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|**initializeData**|İsteğe bağlı öznitelik.<br /><br /> Dize, belirtilen sınıfın oluşturucuya geçti.|  
|**Adı**|İsteğe bağlı öznitelik.<br /><br /> Dinleyicinin adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtre>](filter-element-for-add-for-listeners-for-trace.md)|`Listeners` İzleme için koleksiyondaki bir dinleyiciye filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`listeners`|İletileri toplayan, depolayan ve gönderen bir dinleyici belirtir. Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümünün kök öğesini belirtir.|  
|`trace`|İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ve <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> sınıflar aynı **Dinleyici** koleksiyonunu paylaşır. Bu sınıflardan birinde koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır. Dinleyici sınıfları. <xref:System.Diagnostics.TraceListener>  
  
 İzleme dinleyicisinin özniteliğini `name` belirtmezseniz, izleme <xref:System.Diagnostics.TraceListener.Name%2A> dinleyicisinin varsayılan olarak boş bir dize ("") olduğunu belirtirsiniz. Uygulamanızda yalnızca bir dinleyici varsa, bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz. Ancak, uygulamanızda birden fazla dinleyici varsa, her izleme dinleyicisi için benzersiz adlar belirtmeniz gerekir, <xref:System.Diagnostics.Debug.Listeners%2A> bu <xref:System.Diagnostics.Trace.Listeners%2A> da izleme dinleyicilerini ve koleksiyonlarını tek tek belirlemenize ve yönetmenize olanak tanır.  
  
> [!NOTE]
> Aynı türden ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, koleksiyona bu tür `Listeners` ve addan yalnızca bir izleme dinleyicisi eklenmesiyle sonuçlanır. Ancak, `Listeners` koleksiyona programlı olarak birden çok aynı dinleyici ekleyebilirsiniz.  
  
 **InitializeData** özniteliğinin değeri, oluşturduğunuz dinleyici türüne bağlıdır. Tüm izleme **dinleyicileri, initializeData**belirtmenizi gerektirmez.  
  
> [!NOTE]
> Özniteliği kullandığınızda, `initializeData` derleyici uyarı alabilirsiniz "'InitializeData' özniteliği ilan edilmez." Yapılandırma ayarları özniteliği tanımayan <xref:System.Diagnostics.TraceListener> `initializeData` soyut taban sınıfa karşı doğrulandığı için bu uyarı oluşur. Genellikle, bir parametre alan bir oluşturucu ya da izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda .NET Framework'e dahil olan izleme dinleyicileri gösterilmektedir ve **initializeData** özniteliklerinin değerini açıklar.  
  
|İzleme dinleyici sınıfı|initializeData öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Oluşturucunun `useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> değeri.  İz `initializeData` ve hata`true`ayıklama çıktısı yazmak için <xref:System.Console.Error%2A?displayProperty=nameWithType>özniteliği " " olarak ayarlayın; "`false`" " <xref:System.Console.Out%2A?displayProperty=nameWithType>yazmak için .|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Varolan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dinleyicileri `MyListener` ve `MyEventListener` **Dinleyiciler** koleksiyonuna eklemek için ** \<>** öğelerini nasıl kullanacağımı gösterir. `MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar. `MyEventListener`olay günlüğünde bir giriş oluşturur.  
  
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
- [İz Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
