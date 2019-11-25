---
title: <source> için <listeners> <add> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: c32205310f9fc451a5a55a943f925ee52f65c8a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088995"
---
# <a name="add-element-for-listeners-for-source"></a>\<kaynak için \<dinleyicileri > için > öğesi \<ekleyin >
İzleme kaynağı için `Listeners` koleksiyonuna bir dinleyici ekler.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynakları >** ](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynak >** ](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**dinleyicileri >** ](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ekleme >**

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
|`type`|`sharedListeners` koleksiyonundaki bir dinleyiciye başvurmadığınız müddetçe gerekli özniteliği, bu durumda yalnızca ada göre başvurmak zorunda değilsiniz ( [örneğe](#example)bakın).<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize. Sınıfın bir dize alan Oluşturucusu yoksa bir <xref:System.Configuration.ConfigurationException> oluşturulur.|  
|`name`|İsteğe bağlı öznitelik.<br /><br /> Dinleyicinin adını belirtir.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br /><br /> İzleme dinleyicisi için <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> özellik değerini belirtir.|  
|[özel öznitelikler]|İsteğe bağlı öznitelikler.<br /><br /> Bu dinleyicinin <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> yöntemi tarafından tanımlanan dinleyiciye özgü özniteliklerin değerini belirtir. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>, <xref:System.Diagnostics.DelimitedListTraceListener> sınıfına özgü olan fazladan bir özniteliğe örnektir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Filtre > \<](filter-element-for-add-for-listeners-for-source.md)|İzleme kaynağı için `Listeners` koleksiyonundaki bir dinleyiciye bir filtre ekler.|  
  
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
  
 İzleme dinleyicisinin `name` özniteliğini belirtmezseniz, İzleme dinleyicisinin <xref:System.Diagnostics.TraceListener.Name%2A> özelliği varsayılan olarak boş bir dize ("") olur. Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz. Ancak, uygulamanız birden fazla dinleyici içeriyorsa, her izleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir. Bu, <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyonundaki bireysel izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlar.  
  
> [!NOTE]
> Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve adın yalnızca bir izleme dinleyicisine `Listeners` koleksiyonuna eklendiğine neden olur. Ancak, `Listeners` koleksiyonuna program aracılığıyla birden çok özdeş dinleyici ekleyebilirsiniz.  
  
 `initializeData` özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri `initializeData`belirtmenizi gerektirmez.  
  
> [!NOTE]
> `initializeData` özniteliğini kullandığınızda, "ınitializedata ' özniteliği bildirilmemiş" derleyici uyarısını alabilirsiniz. " Yapılandırma ayarları, `initializeData` özniteliğini tanımayan <xref:System.Diagnostics.TraceListener>soyut taban sınıfına göre doğrulandığından bu uyarı oluşur. Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework dahil edilen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değerleri açıklanmaktadır.  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> oluşturucusunun `useErrorStream` değeri.  Standart hata akışına Trace ve Debug çıkışını yazmak için `initializeData` özniteliğini "`true`" olarak ayarlayın. Standart çıkış akışına yazmak için bunu "`false`" olarak ayarlayın.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> yazdığı dosyanın adı.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.XmlWriterTraceListener> yazdığı dosyanın adı.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `<add>` öğelerinin `console` ve `textListener` izleme kaynağı `TraceSourceApp`için `Listeners` koleksiyonuna nasıl ekleneceğini gösterir. `textListener` dinleyicisi izleme çıkışını myListener. log dosyasına yazar.  
  
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
