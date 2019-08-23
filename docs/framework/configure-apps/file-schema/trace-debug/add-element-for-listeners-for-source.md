---
title: <add>İçin için <listeners> öğesi<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 96bfde3ec425f6f77d1d655808d155eb0e6fcd0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927210"
---
# <a name="add-element-for-listeners-for-source"></a>\<Kaynak > için \<dinleyiciler \<> için > öğesi ekleyin
İzleme kaynağı için `Listeners` koleksiyona bir dinleyici ekler.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<Kaynaklar >  
\<Kaynak >  
\<dinleyiciler >  
\<> Ekle  
  
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
|`type`|`sharedListeners` Koleksiyonda bir dinleyiciye başvurmadığınız müddetçe gerekli özniteliği, bu durumda yalnızca ada göre buraya başvurmanız gerekir ( [örneğe](#example)bakın).<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize. Sınıfın bir dize alan Oluşturucusu yoksa ,oluşturulur.<xref:System.Configuration.ConfigurationException>|  
|`name`|İsteğe bağlı öznitelik.<br /><br /> Dinleyicinin adını belirtir.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br /><br /> İzleme dinleyicisi için özellik değerini belirtir. <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>|  
|[özel öznitelikler]|İsteğe bağlı öznitelikler.<br /><br /> Bu dinleyicinin <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> yöntemi tarafından tanımlanan dinleyiciye özgü özniteliklerin değerini belirtir. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>, <xref:System.Diagnostics.DelimitedListTraceListener> sınıfına özgü olan ek bir özniteliğe örnektir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](filter-element-for-add-for-listeners-for-source.md)|İzleme kaynağı için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
|`source`|İzleme iletilerini Başlatan bir izleme kaynağını belirtir.|  
|`listeners`|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.  
  
 İzleme dinleyicisinin `name` özniteliğini belirtmezseniz <xref:System.Diagnostics.TraceListener.Name%2A> , İzleme dinleyicisinin özelliği varsayılan olarak boş bir dize ("") olur. Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz. Ancak, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için, <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyonda bireysel izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlayan benzersiz bir ad belirtmeniz gerekir.  
  
> [!NOTE]
> Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve `Listeners` koleksiyona eklenmekte olan adın yalnızca bir izleme dinleyicisine neden olur. Ancak, `Listeners` koleksiyona daha fazla özdeş dinleyici ekleyebilirsiniz.  
  
 `initializeData` Özniteliğin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri belirtmeniz `initializeData`gerekmez.  
  
> [!NOTE]
> `initializeData` Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz." Bu uyarı, yapılandırma ayarları <xref:System.Diagnostics.TraceListener> `initializeData` özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur. Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değerleri açıklanmaktadır.  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun `useErrorStream` değeri.  " `initializeData` `false`" Özniteliğini, izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; standart çıkış akışına yazmak için "" olarak ayarlayın.`true`|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, izleme kaynağı `<add>` `textListener` `Listeners` `console` içindinleyicilerivekoleksiyonaeklemeküzereöğelerinnasılkullanılacağınıgösterir`TraceSourceApp`. Dinleyici `textListener` , izleme çıkışını MyListener. log dosyasına yazar.  
  
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
