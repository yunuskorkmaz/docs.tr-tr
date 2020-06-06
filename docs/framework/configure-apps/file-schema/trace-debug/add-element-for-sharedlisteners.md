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
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153613"
---
# <a name="add-element-for-sharedlisteners"></a>\<sharedListeners> için \<add> Öğesi
Koleksiyona bir dinleyici ekler `sharedListeners` . `sharedListeners`, herhangi bir veya başvuruda bulunan bir dinleyici koleksiyonudur [\<source>](source-element.md) [\<trace>](trace-element.md) .  Varsayılan olarak, `sharedListeners` koleksiyondaki dinleyiciler bir koleksiyona yerleştirilmez `Listeners` . Ya da adına göre eklenmelidir [\<source>](source-element.md) [\<trace>](trace-element.md) . `sharedListeners`Çalışma zamanında koddaki koleksiyondaki dinleyicileri almak mümkün değildir.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

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
|`name`|Gerekli öznitelik.<br /><br /> Paylaşılan dinleyiciyi bir koleksiyona eklemek için kullanılan dinleyicinin adını belirtir `Listeners` .|  
|`type`|Gerekli öznitelik.<br /><br /> Dinleyicinin türünü belirtir. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dize.|  
|`traceOutputOptions`|İsteğe bağlı öznitelik.<br/><br/><xref:System.Diagnostics.TraceOptions>İzleme çıktısına yazılacak verileri gösteren bir veya daha fazla numaralandırma üyesinin dize temsili. Birden çok öğe virgülle ayrılır. Varsayılan değer "none" dır.|

### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|Koleksiyondaki bir dinleyiciye bir filtre ekler `sharedListeners` .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir. Özniteliğin değeri, `name` `Listeners` bir izleme ya da izleme kaynağı için bir koleksiyona paylaşılan dinleyiciyi eklemek için kullanılır. Özniteliğin değeri, `initializeData` oluşturduğunuz dinleyicinin türüne bağlıdır. Tüm izleme dinleyicileri belirtmeniz gerekmez `initializeData` .  
  
> [!NOTE]
> `initializeData`Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz." Bu uyarı, yapılandırma ayarları özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur <xref:System.Diagnostics.TraceListener> `initializeData` . Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve özniteliklerinin değerleri açıklanmaktadır `initializeData` .  
  
|Trace dinleyicisi sınıfı|ınitializedata öznitelik değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun değeri.  `initializeData`"" Özniteliğini, `true` izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; `false` Standart çıkış akışına yazmak için "" olarak ayarlayın.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Yazdığı dosyanın adı <xref:System.Diagnostics.DelimitedListTraceListener> .|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağının adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Yazdığı dosyanın adı <xref:System.Diagnostics.EventSchemaTraceListener> .|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Yazdığı dosyanın adı <xref:System.Diagnostics.TextWriterTraceListener> .|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Yazdığı dosyanın adı <xref:System.Diagnostics.XmlWriterTraceListener> .|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `<add>` , öğesini koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir <xref:System.Diagnostics.TextWriterTraceListener> `textListener` `sharedListeners` .   `textListener`, `Listeners` izleme kaynağı için koleksiyona adına eklenir `TraceSourceApp` . `textListener`Dinleyici, izleme çıkışını myListener. log dosyasına yazar.  
  
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
