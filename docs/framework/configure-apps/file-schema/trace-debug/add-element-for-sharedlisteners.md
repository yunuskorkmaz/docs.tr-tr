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
ms.openlocfilehash: 0c7665898f8c625c2d07b67ea6c7fe25113fddd8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699485"
---
# <a name="add-element-for-sharedlisteners"></a>\< \<sharedListeners için > öğesi ekleyin >
@No__t-0 koleksiyonuna bir dinleyici ekler. `sharedListeners`, herhangi bir [\<source >](source-element.md) veya [@no__t 4trace >](trace-element.md) başvurmasına yönelik bir dinleyici koleksiyonudur.  Varsayılan olarak, `sharedListeners` koleksiyonundaki dinleyiciler bir `Listeners` koleksiyonuna yerleştirilmez. [@No__t-1source >](source-element.md) veya [\<trace >](trace-element.md)adına göre eklenmelidir. Çalışma zamanında koddaki `sharedListeners` koleksiyonundaki dinleyicileri almak mümkün değildir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**  
  
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
|`name`|Gerekli öznitelik.<br /><br /> @No__t-0 koleksiyonuna paylaşılan dinleyiciyi eklemek için kullanılan dinleyicinin adını belirtir.|  
|`type`|Gerekli öznitelik.<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br/><br/>İzleme çıktısına yazılacak verileri gösteren bir veya daha fazla <xref:System.Diagnostics.TraceOptions> numaralandırma üyesinin dize temsili. Birden çok öğe virgülle ayrılır. Varsayılan değer "none" dır.|

### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtre >](filter-element-for-add-for-sharedlisteners.md)|@No__t-0 koleksiyonundaki bir dinleyiciye bir filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir. @No__t-0 özniteliğinin değeri, bir izleme ya da izleme kaynağı için bir `Listeners` koleksiyonuna paylaşılan dinleyiciyi eklemek için kullanılır. @No__t-0 özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri `initializeData` belirtmenizi gerektirmez.  
  
> [!NOTE]
> @No__t-0 özniteliğini kullandığınızda, "ınitializedata ' özniteliği bildirilmemiş" derleyici uyarısını alabilirsiniz. " Yapılandırma ayarları, `initializeData` özniteliğini tanımayan <xref:System.Diagnostics.TraceListener> soyut taban sınıfına göre doğrulandığından bu uyarı oluşur. Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değeri açıklanmaktadır.  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|@No__t-1 oluşturucusunun `useErrorStream` değeri.  Standart hata akışına Trace ve Debug çıkışını yazmak için `initializeData` özniteliğini "`true`" olarak ayarlayın. Standart çıkış akışına yazmak için bunu "`false`" olarak ayarlayın.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|@No__t-0 ' ın yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|@No__t 0 ' ın yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|@No__t 0 ' ın yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|@No__t 0 ' ın yazdığı dosyanın adı.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Diagnostics.TextWriterTraceListener> @ no__t-2 ' i `sharedListeners` koleksiyonuna eklemek için `<add>` öğelerinin nasıl kullanılacağını gösterir.   `textListener`, `TraceSourceApp` izleme kaynağı için `Listeners` koleksiyonuna eklenir. @No__t-0 dinleyicisi, izleme çıkışını myListener. log dosyasına yazar.  
  
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
