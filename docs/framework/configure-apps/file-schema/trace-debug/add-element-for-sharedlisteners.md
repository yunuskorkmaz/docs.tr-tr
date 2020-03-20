---
title: <sharedListeners> için <add> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153613"
---
# <a name="add-element-for-sharedlisteners"></a>\<paylaşılan Dinleyiciler \<için> Öğesi>
`sharedListeners` Koleksiyona bir dinleyici ekler. `sharedListeners`herhangi [ \<](source-element.md) bir kaynağın>veya [ \<izleme>](trace-element.md) başvurulabileceği bir dinleyici topluluğudur.  Varsayılan olarak, `sharedListeners` koleksiyondaki dinleyiciler koleksiyona `Listeners` yerleştirilmez. Kaynak [ \<>](source-element.md) veya [ \<izleme>](trace-element.md)adile eklenmelidir. Dinleyicileri çalışma zamanında kod halinde `sharedListeners` toplama almak mümkün değildir.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<paylaşılanDinleyiciler>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli öznitelik.<br /><br /> Paylaşılan dinleyiciyi koleksiyona `Listeners` eklemek için kullanılan dinleyicinin adını belirtir.|  
|`type`|Gerekli öznitelik.<br /><br /> Dinleyicinin türünü belirtir. [Tam Nitelikli Tür Adları Belirtme'de](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Dize, belirtilen sınıfın oluşturucuya geçti.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br/><br/>İzleme çıktısına yazılacak <xref:System.Diagnostics.TraceOptions> verileri gösteren bir veya daha fazla numaralandırma üyesinin dize gösterimi. Birden çok öğe virgülle ayrılır. Varsayılan değer "Yok"dur.|

### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtre>](filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` Koleksiyondaki bir dinleyiciye filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya izleme öğesinin başvuruda bulunabileceği dinleyici koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile gönderilen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıftan türetilmiştir. Öznitelik değeri, `name` paylaşılan dinleyiciyi bir izleme veya `Listeners` izleme kaynağı için bir koleksiyona eklemek için kullanılır. Öznitelik değeri `initializeData` oluşturduğunuz dinleyici türüne bağlıdır. Tüm izleme dinleyicileri belirtmenizi `initializeData`gerektirmez.  
  
> [!NOTE]
> Özniteliği kullandığınızda, `initializeData` derleyici uyarı alabilirsiniz "'InitializeData' özniteliği ilan edilmez." Yapılandırma ayarları özniteliği tanımayan <xref:System.Diagnostics.TraceListener> `initializeData` soyut taban sınıfa karşı doğrulandığı için bu uyarı oluşur. Genellikle, bir parametre alan bir oluşturucu ya da izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda .NET Framework'e dahil olan izleme dinleyicileri `initializeData` gösterilmektedir ve özniteliklerinin değerini açıklar.  
  
|İzleme dinleyici sınıfı|initializeData öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|Oluşturucunun `useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> değeri.  İzleme `initializeData` ve hata`true`ayıklama çıktısını standart hata akışına yazmak için " " özniteliğini ayarlayın; standart çıktı`false`akışına yazmak için " " olarak ayarlayın.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Varolan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, koleksiyona `<add>` eklemek için <xref:System.Diagnostics.TextWriterTraceListener> `textListener` öğelerin nasıl kullanılacağını `sharedListeners` gösterir.   `textListener`izleme kaynağı `TraceSourceApp`için `Listeners` koleksiyona ad ile eklenir. `textListener` Dinleyici myListener.log dosyasına izleme çıktısı yazar.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [İz Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
