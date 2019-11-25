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
ms.openlocfilehash: 116a9633d16b8dd36c82f07a8e727f6f9f98f0ee
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088974"
---
# <a name="add-element-for-sharedlisteners"></a>\<sharedListeners için > öğesi \<ekleyin >
`sharedListeners` koleksiyonuna bir dinleyici ekler. `sharedListeners`, [\<kaynak >](source-element.md) veya [\<izleme >](trace-element.md) başvurmasına yönelik bir dinleyici koleksiyonudur.  Varsayılan olarak, `sharedListeners` koleksiyonundaki dinleyiciler bir `Listeners` koleksiyonuna yerleştirilmez. [\<kaynak >](source-element.md) veya [\<Trace >](trace-element.md)adına göre eklenmelidir. Çalışma zamanında koddaki `sharedListeners` koleksiyonundaki dinleyicileri almak mümkün değildir.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;\<[**sharedListeners**](sharedlisteners-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**

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
|`name`|Gerekli öznitelik.<br /><br /> Paylaşılan dinleyiciyi bir `Listeners` koleksiyonuna eklemek için kullanılan dinleyicinin adını belirtir.|  
|`type`|Gerekli öznitelik.<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br/><br/>İzleme çıktısına yazılacak verileri gösteren bir veya daha fazla <xref:System.Diagnostics.TraceOptions> numaralandırma üyesinin dize temsili. Birden çok öğe virgülle ayrılır. Varsayılan değer "none" dır.|

### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Filtre > \<](filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` koleksiyonundaki bir dinleyiciye bir filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir. `name` özniteliğinin değeri, bir izleme veya izleme kaynağı için bir `Listeners` koleksiyonuna paylaşılan dinleyiciyi eklemek için kullanılır. `initializeData` özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri `initializeData`belirtmenizi gerektirmez.  
  
> [!NOTE]
> `initializeData` özniteliğini kullandığınızda, "ınitializedata ' özniteliği bildirilmemiş" derleyici uyarısını alabilirsiniz. " Yapılandırma ayarları, `initializeData` özniteliğini tanımayan <xref:System.Diagnostics.TraceListener>soyut taban sınıfına göre doğrulandığından bu uyarı oluşur. Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework dahil edilen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değerleri açıklanmaktadır.  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> oluşturucusunun `useErrorStream` değeri.  Standart hata akışına Trace ve Debug çıkışını yazmak için `initializeData` özniteliğini "`true`" olarak ayarlayın. Standart çıkış akışına yazmak için bunu "`false`" olarak ayarlayın.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<xref:System.Diagnostics.DelimitedListTraceListener> yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<xref:System.Diagnostics.XmlWriterTraceListener> yazdığı dosyanın adı.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `sharedListeners` koleksiyonuna <xref:System.Diagnostics.TextWriterTraceListener>`textListener` eklemek için `<add>` öğelerinin nasıl kullanılacağını gösterir.   `textListener`, izleme kaynağı `TraceSourceApp`için `Listeners` koleksiyonuna eklenir. `textListener` dinleyicisi izleme çıkışını myListener. log dosyasına yazar.  
  
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
