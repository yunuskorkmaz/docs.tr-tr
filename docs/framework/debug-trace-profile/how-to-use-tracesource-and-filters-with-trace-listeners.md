---
title: 'Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7a912386d93e727a1f4cd2253ad06be76ae3385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma
.NET Framework sürüm 2.0'deki yeni özelliklerin bir Gelişmiş izleme sistemi biridir. Değişmeden dayanır: izleme iletileri veriler bir ilişkili çıktı Orta rapor dinleyicileri için anahtarlar aracılığıyla gönderilir. Bir birincil sürüm 2.0 için izlemeleri örneklerini başlatılabilir farktır <xref:System.Diagnostics.TraceSource> sınıfı. <xref:System.Diagnostics.TraceSource> bir Gelişmiş izleme sistemi olarak çalışmaya yöneliktir ve eski yerine statik yöntemleri kullanılabilir <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıfları. Bilinen <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıflar hala mevcut, ancak kullanmak için önerilen yöntemdir <xref:System.Diagnostics.TraceSource> izleme için sınıf.  
  
 Bu konuda kullanımını açıklar bir <xref:System.Diagnostics.TraceSource> uygulama yapılandırma dosyası ile birlikte.  Bu, izleme kullanmaya Önerilmemesine rağmen mümkün olduğunda, bir <xref:System.Diagnostics.TraceSource> olmadan bir yapılandırma dosyası kullanın. Bir yapılandırma dosyası olmadan izleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: oluşturma ve izleme kaynaklarını başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Oluşturma ve izleme kaynağınız başlatmak için  
  
1.  Uygulama izleme ile düzenleme ilk adımı, bir izleme kaynağını oluşturmaktır. Çeşitli bileşenleri ile büyük projeler her bileşen için ayrı izleme kaynağı oluşturabilirsiniz. Önerilen uygulama izleme kaynağı adı için uygulama adı kullanmaktır. Bu, farklı izlemeleri ayrı tutmak daha kolay hale getirir. Aşağıdaki kod yeni bir izleme kaynağı oluşturur (`mySource)` ve bir yöntemi çağırır (`Activity1`) olayları izler.  İzleme iletileri varsayılan İzleme dinleyicisi tarafından yazılır.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Oluşturma ve izleme dinleyicileri ve filtreleri başlatmak için  
  
1.  İlk yordam kodda, herhangi bir izleme dinleyicileri veya filtreleri programlı olarak tanımlamıyor. Tek başına kodu için varsayılan İzleme dinleyicisi yazılmakta izleme iletilerini sonuçlanır. Belirli izleme dinleyicileri ve bunların ilişkili filtrelerini yapılandırmak için uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleyin. Bu dosyada, eklemek veya bir dinleyici kaldırın, özellikleri ve filtre için bir dinleyici ayarlayın veya dinleyicileri kaldırın. Aşağıdaki yapılandırma dosyası örneği, bir konsol İzleme dinleyicisi ve önceki yordamda oluşturduğunuz izleme kaynağı için metin yazıcı İzleme dinleyicisi başlatılamadı gösterilmiştir. İzleme dinleyicileri yapılandırmaya, ek yapılandırma dosyası filtreleri hem de dinleyicileri ve izleme kaynağı için kaynak anahtarı oluşturur. İzleme dinleyicileri eklemek için iki teknikleri gösterilir: dinleyicisi doğrudan izleme kaynağı ekleme ve bir dinleyici paylaşılan dinleyiciler koleksiyona ekleme ve bunu ada göre izleme kaynağını ekleyerek. İki dinleyicileri için tanımlanan filtreler farklı kaynak düzeyleriyle başlatılır. Bu, iki dinleyicileri yalnızca biri tarafından yazılan bazı iletiler sonuçlanır.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Hangi dinleyici izleme iletisi Yazar düzeyini değiştirmek için  
  
1.  Yapılandırma dosyası uygulama başlatılmadan zamanında izleme kaynağı ayarlarını başlatır. Bu ayarları değiştirmek için yapılandırma dosyasını değiştirme ve uygulamayı yeniden başlatın veya program aracılığıyla kullanarak uygulamayı yenileyin <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi. Uygulamanın kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilirsiniz.  Örneğin, size güvence altına almak kritik iletileri her zaman geçerli yapılandırma ayarlarına bakılmaksızın bir metin dosyasına gönderilen isteyebilirsiniz.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified   
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =   
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures   
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners   
                // for all event types. This statement will override   
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,   
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,   
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [Nasıl yapılır: İzleme Kaynakları Oluşturma ve Başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [İzleme Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
