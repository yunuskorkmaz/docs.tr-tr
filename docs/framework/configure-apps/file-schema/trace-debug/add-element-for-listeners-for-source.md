---
title: <add>İçin için öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153691"
---
# <a name="add-element-for-listeners-for-source"></a>\<add>İçin için öğesi \<listeners>\<source>
`Listeners`İzleme kaynağı için koleksiyona bir dinleyici ekler.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

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
|`type`|Koleksiyonda bir dinleyiciye başvurmadığınız müddetçe gerekli özniteliği, `sharedListeners` Bu durumda yalnızca ada göre buraya başvurmanız gerekir ( [örneğe](#example)bakın).<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize. <xref:System.Configuration.ConfigurationException>Sınıfın bir dize alan Oluşturucusu yoksa, oluşturulur.|  
|`name`|İsteğe bağlı öznitelik.<br /><br /> Dinleyicinin adını belirtir.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br /><br /> <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>İzleme dinleyicisi için özellik değerini belirtir.|  
|[özel öznitelikler]|İsteğe bağlı öznitelikler.<br /><br /> Bu dinleyicinin yöntemi tarafından tanımlanan dinleyiciye özgü özniteliklerin değerini belirtir <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> . <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>, sınıfına özgü olan ek bir özniteliğe örnektir <xref:System.Diagnostics.DelimitedListTraceListener> .|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|İzleme kaynağı için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .|  
  
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
  
 `name`İzleme dinleyicisinin özniteliğini belirtmezseniz, <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisinin özelliği varsayılan olarak boş bir dize ("") olur. Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz. Ancak, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için, koleksiyonda bireysel izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlayan benzersiz bir ad belirtmeniz gerekir <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> .  
  
> [!NOTE]
> Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve koleksiyona eklenmekte olan adın yalnızca bir izleme dinleyicisine neden olur `Listeners` . Ancak, koleksiyona daha fazla özdeş dinleyici ekleyebilirsiniz `Listeners` .  
  
 Özniteliğin değeri, `initializeData` oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri belirtmeniz gerekmez `initializeData` .  
  
> [!NOTE]
> `initializeData`Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz." Bu uyarı, yapılandırma ayarları özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur <xref:System.Diagnostics.TraceListener> `initializeData` . Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve özniteliklerinin değerleri açıklanmaktadır `initializeData` .  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun değeri.  `initializeData`"" Özniteliğini, `true` izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; `false` Standart çıkış akışına yazmak için "" olarak ayarlayın.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Yazdığı dosyanın adı <xref:System.Diagnostics.DelimitedListTraceListener> .|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Yazdığı dosyanın adı <xref:System.Diagnostics.EventSchemaTraceListener> .|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Yazdığı dosyanın adı <xref:System.Diagnostics.TextWriterTraceListener> .|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Yazdığı dosyanın adı <xref:System.Diagnostics.XmlWriterTraceListener> .|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `<add>` `console` `textListener` `Listeners` izleme kaynağı için dinleyicileri ve koleksiyona eklemek üzere öğelerin nasıl kullanılacağını gösterir `TraceSourceApp` . `textListener`Dinleyici, izleme çıkışını myListener. log dosyasına yazar.  
  
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
