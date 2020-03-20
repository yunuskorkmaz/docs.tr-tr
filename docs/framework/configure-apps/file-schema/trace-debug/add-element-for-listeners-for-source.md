---
title: <add><listeners> Için element<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153691"
---
# <a name="add-element-for-listeners-for-source"></a>\<kaynak> \<için> \<dinleyiciler için> Öğesi ekleyin
İzleme kaynağı için `Listeners` koleksiyona dinleyici ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**

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
|`type`|`sharedListeners` Koleksiyonda bir dinleyiciye başvurmadığınız sürece gerekli öznitelik, bu durumda yalnızca ada göre başvurmanız gerekir [(Bkz. Örnek).](#example)<br /><br /> Dinleyicinin türünü belirtir. [Tam Nitelikli Tür Adları Belirtme'de](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Dize, belirtilen sınıfın oluşturucuya geçti. Sınıfın <xref:System.Configuration.ConfigurationException> dize alan bir oluşturucusu yoksa a atılır.|  
|`name`|İsteğe bağlı öznitelik.<br /><br /> Dinleyicinin adını belirtir.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br /><br /> İzleme dinleyicisinin <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> özellik değerini belirtir.|  
|[özel öznitelikler]|İsteğe bağlı öznitelikler.<br /><br /> Dinleyiciye özgü özniteliklerin <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> değerini belirtir. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A><xref:System.Diagnostics.DelimitedListTraceListener> sınıfa özgü ek bir öznitelik örneğidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtre>](filter-element-for-add-for-listeners-for-source.md)|İzleme kaynağı için `Listeners` koleksiyondaki dinleyiciye filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
|`sources`|İletileri izlemeyi başlatan izleme kaynakları içerir.|  
|`source`|İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.|  
|`listeners`|İletileri toplayan, depolayan ve yönlendiren dinleyicileri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile gönderilen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıftan türetilmiştir.  
  
 İzleme dinleyicisinin özniteliğini `name` belirtmezseniz, izleme <xref:System.Diagnostics.TraceListener.Name%2A> dinleyicisinin özelliği varsayılan olarak boş bir dize ("") olur. Uygulamanızda yalnızca bir dinleyici varsa, bir ad belirtmeden ekleyebilirsiniz ve ad için boş bir dize belirterek kaldırabilirsiniz. Ancak, uygulamanızda birden fazla dinleyici varsa, <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyondaki tek tek izleme dinleyicilerini tanımlamanızı ve yönetmeniz için her izleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir.  
  
> [!NOTE]
> Aynı türden ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, koleksiyona bu tür `Listeners` ve addan yalnızca bir izleme dinleyicisi eklenmesiyle sonuçlanır. Ancak, `Listeners` koleksiyona programlı olarak birden çok aynı dinleyici ekleyebilirsiniz.  
  
 Öznitelik değeri `initializeData` oluşturduğunuz dinleyici türüne bağlıdır. Tüm izleme dinleyicileri belirtmenizi `initializeData`gerektirmez.  
  
> [!NOTE]
> Özniteliği kullandığınızda, `initializeData` derleyici uyarı alabilirsiniz "'InitializeData' özniteliği ilan edilmez." Yapılandırma ayarları özniteliği tanımayan <xref:System.Diagnostics.TraceListener> `initializeData` soyut taban sınıfa karşı doğrulandığı için bu uyarı oluşur. Genellikle, bir parametre alan bir oluşturucu ya da izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda .NET Framework'e dahil olan izleme dinleyicileri `initializeData` gösterilmektedir ve özniteliklerinin değerini açıklar.  
  
|İzleme dinleyici sınıfı|initializeData öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Oluşturucunun `useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> değeri.  İzleme `initializeData` ve hata`true`ayıklama çıktısını standart hata akışına yazmak için " " özniteliğini ayarlayın; standart çıktı`false`akışına yazmak için " " olarak ayarlayın.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Varolan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dinleyicileri `<add>` `console` ve `textListener` izleme kaynağı `Listeners` `TraceSourceApp`için koleksiyona öğeleri nasıl kullanacağımı gösterir. `textListener` Dinleyici myListener.log dosyasına izleme çıktısı yazar.  
  
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
