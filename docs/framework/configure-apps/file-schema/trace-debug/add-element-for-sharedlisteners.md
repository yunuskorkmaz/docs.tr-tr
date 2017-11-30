---
title: "&lt;ekleme&gt; öğesi için &lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd8e7d18ca72cbeb558876eefcde17ebdc6c095f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a>&lt;ekleme&gt; öğesi için &lt;sharedListeners&gt;
Bir dinleyici ekler `sharedListeners` koleksiyonu. `sharedListeners`dinleyicileri herhangi bir koleksiyonudur [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) başvuruda bulunabilir.  Varsayılan olarak, dinleyicileri `sharedListeners` koleksiyonu içinde değil yerleştirilir bir `Listeners` koleksiyonu. Adına eklenmesi gerekir [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md). Dinleyicileri almak mümkün değil `sharedListeners` çalışma zamanında kodda koleksiyonu.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<sharedListeners > öğesi  
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
|`name`|Gerekli öznitelik.<br /><br /> Paylaşılan dinleyicisi eklemek için kullanılan dinleyicisinin adını belirten bir `Listeners` koleksiyonu.|  
|`type`|Gerekli öznitelik.<br /><br /> Dinleyici türünü belirtir. Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Dize için belirtilen sınıf oluşturucuya geçirilen.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Bir dinleyici için bir filtre ekler `sharedListeners` koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework ile birlikte gelen dinleyicisi sınıfları türetin <xref:System.Diagnostics.TraceListener> sınıfı. Değeri `name` özniteliği paylaşılan dinleyicisi eklemek için kullanılan bir `Listeners` koleksiyonu bir izleme ve izleme kaynağı. Değeri `initializeData` özniteliği oluşturduğunuz dinleyicisi türüne bağlıdır. Tüm izleme dinleyicileri, belirttiğiniz gerektiren `initializeData`.  
  
> [!NOTE]
>  Kullandığınızda `initializeData` özniteliği, "'initializeData' özniteliği yok bildirildi." uyarı derleyici alabilirsiniz Yapılandırma ayarları Özet temel sınıf karşı doğrulandığı için bu uyarıyı oluşur <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği. Genellikle, bir parametre alan bir oluşturucuya sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.  
  
 Aşağıdaki tabloda .NET Framework ile birlikte izleme dinleyicilerini gösterir ve değerini açıklar kendi `initializeData` öznitelikleri.  
  
|İzleme dinleyicisi sınıfı|initializeData özniteliği değeri|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.  Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıktı akışına yazmak için.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Dosyanın adını <xref:System.Diagnostics.DelimitedListTraceListener> yazar.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Var olan bir olay günlüğü kaynağı adı.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Dosya adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Dosya adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.|  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `<add>` eklemek için öğeleri <xref:System.Diagnostics.TextWriterTraceListener> `textListener` için `sharedListeners` koleksiyonu.   `textListener`adına tarafından eklenen `Listeners` izleme kaynağı toplamalarında `TraceSourceApp`. `textListener` Dinleyicisi dosya myListener.log izleme çıktısı yazar.  
  
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
 [İzleme ve hata ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [İzleme dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
