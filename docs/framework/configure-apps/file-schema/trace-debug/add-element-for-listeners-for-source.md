---
title: '&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ba8ff652003a9167ec370643797ac9300b83889a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745662"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;
Bir dinleyici ekler `Listeners` koleksiyonu için bir izleme kaynağı.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<Kaynakları >  
\<Kaynak >  
\<dinleyicileri >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`type`|Öznitelik, bir dinleyici başvuran sürece gerekli `sharedListeners` koleksiyon, bu durumda yalnızca ada göre başvurduğu gerek (bkz [örnek](#example)).<br /><br /> Dinleyici türünü belirtir. Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Dize için belirtilen sınıf oluşturucuya geçirilen. A <xref:System.Configuration.ConfigurationException> sınıfı bir dize alır bir oluşturucuya sahip değilse oluşturulur.|  
|`name`|İsteğe bağlı öznitelik.<br /><br /> Dinleyici adını belirtir.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br /><br /> Belirtir <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> İzleme dinleyicisi için özellik değeri.|  
|[özel öznitelikler]|İsteğe bağlı öznitelik.<br /><br /> Tarafından tanımlanan dinleyici özel öznitelikleri için değer belirtir <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> bu dinleyici için yöntem. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> ek bir öznitelik için benzersiz örneğidir <xref:System.Diagnostics.DelimitedListTraceListener> sınıfı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Bir dinleyici için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletileri başlatmak izleme kaynaklarını içerir.|  
|`source`|İzleme iletileri başlatan bir izleme kaynağını belirtir.|  
|`listeners`|Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyicisi sınıfları türetin <xref:System.Diagnostics.TraceListener> sınıfı.  
  
 Belirtmezseniz, `name` İzleme dinleyicisi özniteliği <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisi özelliği varsayılan olarak boş bir dize (""). Yalnızca tek bir dinleyici uygulamanız varsa, bir adı belirtmeden ekleyebilir ve boş bir dize adı belirterek kaldırabilirsiniz. Ancak, birden çok dinleyici uygulamanız varsa, tanımlamanıza ve tek tek izleme dinleyicileri yönetmenize olanak tanıyan her İzleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyonu.  
  
> [!NOTE]
>  Birden fazla İzleme dinleyicisi aynı türde ve aynı ekleme yalnızca bir izleme dinleyicisi sonuçlarında türü ve eklenmesini adlandırın `Listeners` koleksiyonu. Ancak, program aracılığıyla birden çok özdeş dinleyici ekleyebilirsiniz `Listeners` koleksiyonu.  
  
 Değeri `initializeData` özniteliği oluşturduğunuz dinleyicisi türüne bağlıdır. Tüm izleme dinleyicileri, belirttiğiniz gerektiren `initializeData`.  
  
> [!NOTE]
>  Kullandığınızda `initializeData` özniteliği, "'initializeData' özniteliği yok bildirildi." uyarı derleyici alabilirsiniz Yapılandırma ayarları Özet temel sınıf karşı doğrulandığı için bu uyarıyı oluşur <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği. Genellikle, bir parametre alan bir oluşturucuya sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda .NET Framework ile birlikte izleme dinleyicilerini gösterir ve değerini açıklar kendi `initializeData` öznitelikleri.  
  
|İzleme dinleyicisi sınıfı|initializeData özniteliği değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.  Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıktı akışına yazmak için.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Dosyanın adını <xref:System.Diagnostics.DelimitedListTraceListener> yazar.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağı adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `<add>` dinleyicileri eklemek için öğeleri `console` ve `textListener` için `Listeners` izleme kaynağı toplamalarında `TraceSourceApp`. `textListener` Dinleyicisi dosya myListener.log izleme çıktısı yazar.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
