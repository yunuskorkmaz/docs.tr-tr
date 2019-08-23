---
title: <sharedListeners> için <add> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927204"
---
# <a name="add-element-for-sharedlisteners"></a>\<sharedListeners için \<> öğesi ekleyin >
`sharedListeners` Koleksiyona bir dinleyici ekler. `sharedListeners`, herhangi [ \<bir kaynak >](source-element.md) veya [ \<izleme >](trace-element.md) başvurmasına yönelik bir dinleyici koleksiyonudur.  Varsayılan olarak, `sharedListeners` koleksiyondaki dinleyiciler bir `Listeners` koleksiyona yerleştirilmez. Bunlar, [ \<kaynak >](source-element.md) veya [ \<izleme >](trace-element.md)adına göre eklenmelidir. Çalışma zamanında koddaki `sharedListeners` koleksiyondaki dinleyicileri almak mümkün değildir.  
  
 \<Yapılandırma >  
&nbsp;&nbsp;\<System. Diagnostics >  
&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > öğesi  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<> Ekle  
  
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
|`name`|Gerekli öznitelik.<br /><br /> Paylaşılan dinleyiciyi bir `Listeners` koleksiyona eklemek için kullanılan dinleyicinin adını belirtir.|  
|`type`|Gerekli öznitelik.<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br/><br/>İzleme çıktısına yazılacak verileri gösteren bir veya <xref:System.Diagnostics.TraceOptions> daha fazla numaralandırma üyesinin dize temsili. Birden çok öğe virgülle ayrılır. Varsayılan değer "none" dır.|

### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` Koleksiyondaki bir dinleyiciye bir filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir. `name` Özniteliğin değeri, bir izleme ya da izleme kaynağı için bir `Listeners` koleksiyona paylaşılan dinleyiciyi eklemek için kullanılır. `initializeData` Özniteliğin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri belirtmeniz `initializeData`gerekmez.  
  
> [!NOTE]
> `initializeData` Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz." Bu uyarı, yapılandırma ayarları <xref:System.Diagnostics.TraceListener> `initializeData` özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur. Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değerleri açıklanmaktadır.  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun `useErrorStream` değeri.  " `initializeData` `false`" Özniteliğini, izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; standart çıkış akışına yazmak için "" olarak ayarlayın.`true`|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `<add>` örnek, <xref:System.Diagnostics.TextWriterTraceListener> `textListener` öğesini koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir. `sharedListeners`   `textListener`, izleme kaynağı `Listeners` `TraceSourceApp`için koleksiyona adına eklenir. Dinleyici `textListener` , izleme çıkışını MyListener. log dosyasına yazar.  
  
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
- [İzleme Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
