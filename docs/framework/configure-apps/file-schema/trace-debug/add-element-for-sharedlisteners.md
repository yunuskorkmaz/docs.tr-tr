---
title: <add> için <sharedListeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: cbce115c6a485c5642a60528614480324e3e5665
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274054"
---
# <a name="add-element-for-sharedlisteners"></a>\<Ekle > öğesi için \<sharedListeners >
Bir ekler `sharedListeners` koleksiyonu. `sharedListeners` dinleyicileri herhangi bir koleksiyonudur [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) başvurabilirsiniz.  Varsayılan olarak, dinleyicileri `sharedListeners` koleksiyon yerleştirildiğinde değil bir `Listeners` koleksiyonu. Ada göre eklenmelidir [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md). Dinleyiciler almak mümkün değildir `sharedListeners` çalışma zamanında kod koleksiyonu.  
  
 \<Yapılandırma >  
&nbsp;&nbsp;\<System.Diagnostics >  
&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > öğesi  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add>  
  
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
|`name`|Gerekli öznitelik.<br /><br /> Paylaşılan dinleyici için eklemek için kullanılan dinleyicisinin adını belirten bir `Listeners` koleksiyonu.|  
|`type`|Gerekli öznitelik.<br /><br /> Dinleyici türünü belirtir. Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dizesi.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br/><br/>Bir veya daha fazla dize gösterimi <xref:System.Diagnostics.TraceOptions> izleme çıktısına yazılmasına verileri gösteren numaralandırma üyeleri. Birden çok öğe virgülle ayrılır. Varsayılan değer "None" dir.|

### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Bir dinleyicisi için bir filtre ekler `sharedListeners` koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya trace ögesi başvurabilirsiniz dinleyicileri koleksiyonudur.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyici sınıfların türetilmesi <xref:System.Diagnostics.TraceListener> sınıfı. Değeri `name` özniteliği için paylaşılan dinleyici eklemek için kullanılan bir `Listeners` koleksiyonu için bir izleme ya da bir izleme kaynağı. Değeri `initializeData` özniteliği oluşturduğunuz dinleyici türüne bağlıdır. Tüm izleme dinleyicilerine belirtmenizi gerektiren `initializeData`.  
  
> [!NOTE]
>  Kullanırken `initializeData` özniteliği, "'initializeData' özniteliği. bildirilmedi" uyarı derleyici alabilirsiniz Bu uyarı oluşur yapılandırma ayarlarını soyut temel sınıf doğrulanır <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği. Genellikle, bir parametre alan bir oluşturucu sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tablo .NET Framework ile birlikte izleme dinleyicilerine gösterir ve değerinin açıklanmıştır kendi `initializeData` öznitelikleri.  
  
|İzleme dinleyicisi sınıfı|initializeData özniteliği değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.  Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıkış akışına yazmak için.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Dosya adı <xref:System.Diagnostics.DelimitedListTraceListener> yazar.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Mevcut bir olay günlüğü kaynağı adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Dosyanın adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Dosyanın adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<add>` eklemek için öğeleri <xref:System.Diagnostics.TextWriterTraceListener> `textListener` için `sharedListeners` koleksiyonu.   `textListener` adına tarafından eklenen `Listeners` iz kaynağı için koleksiyon `TraceSourceApp`. `textListener` Dinleyici için dosya myListener.log izleme çıktısına yazar.  
  
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
