---
title: <add> için <listeners> için <source> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: ae5231f43e7c157b5250376f7ab97deccea595e5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277127"
---
# <a name="add-element-for-listeners-for-source"></a>\<Ekle > öğesi için \<dinleyicileri > için \<kaynak >
Bir ekler `Listeners` koleksiyonu için bir izleme kaynağı.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<Kaynakları >  
\<Kaynak >  
\<dinleyicileri >  
\<Ekle >  
  
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
|`type`|Gerekli öznitelik, bir dinleyicisi başvuran sürece `sharedListeners` koleksiyon, yalnızca ada göre başvurduğu gerek case (bkz [örnek](#example)).<br /><br /> Dinleyici türünü belirtir. Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dizesi. A <xref:System.Configuration.ConfigurationException> sınıfı bir dize alan bir oluşturucu yoksa, oluşturulur.|  
|`name`|İsteğe bağlı öznitelik.<br /><br /> Dinleyicisinin adını belirtir.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br /><br /> Belirtir <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> İzleme dinleyicisi için özellik değeri.|  
|[özel öznitelikler]|İsteğe bağlı öznitelikleri.<br /><br /> Tarafından tanımlanan dinleyicisi özel öznitelikler için bir değer belirtir <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> bu dinleyici için yöntemi. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> ek bir öznitelik için benzersiz örneğidir <xref:System.Diagnostics.DelimitedListTraceListener> sınıfı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletileri başlatmak iz kaynakları içerir.|  
|`source`|İzleme iletileri başlatan bir izleme kaynağı belirtir.|  
|`listeners`|Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyici sınıfların türetilmesi <xref:System.Diagnostics.TraceListener> sınıfı.  
  
 Siz belirtmezseniz `name` İzleme dinleyicisi özniteliği <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisi özelliği varsayılan olarak boş bir dize olarak (""). Uygulamanızın yalnızca bir dinleyicisi varsa, bir adı belirtmeden ekleyebilir ve boş bir dize adı belirterek kaldırabilirsiniz. Ancak, uygulamanızın birden fazla dinleyici varsa, tanımlamak ve yönetmek, tek tek izleme dinleyicilerine olanak tanıyan her İzleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyonu.  
  
> [!NOTE]
>  Birden fazla İzleme dinleyicisi aynı türde ve aynı adı yalnızca bir izleme dinleyicisi sonuçlarında türü ekleyip eklenmesini ad `Listeners` koleksiyonu. Ancak, program aracılığıyla birden fazla özdeş dinleyicilere ekleyebilirsiniz `Listeners` koleksiyonu.  
  
 Değeri `initializeData` özniteliği oluşturduğunuz dinleyici türüne bağlıdır. Tüm izleme dinleyicilerine belirtmenizi gerektiren `initializeData`.  
  
> [!NOTE]
>  Kullanırken `initializeData` özniteliği, "'initializeData' özniteliği. bildirilmedi" uyarı derleyici alabilirsiniz Bu uyarı oluşur yapılandırma ayarlarını soyut temel sınıf doğrulanır <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği. Genellikle, bir parametre alan bir oluşturucu sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tablo .NET Framework ile birlikte izleme dinleyicilerine gösterir ve değerinin açıklanmıştır kendi `initializeData` öznitelikleri.  
  
|İzleme dinleyicisi sınıfı|initializeData özniteliği değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.  Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıkış akışına yazmak için.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Dosya adı <xref:System.Diagnostics.DelimitedListTraceListener> yazar.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Mevcut bir olay günlüğü kaynağı adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<add>` dinleyiciler eklemek için öğeleri `console` ve `textListener` için `Listeners` iz kaynağı için koleksiyon `TraceSourceApp`. `textListener` Dinleyici için dosya myListener.log izleme çıktısına yazar.  
  
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
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
