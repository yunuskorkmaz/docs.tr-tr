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
ms.openlocfilehash: 7d2b9da72ae0b2a5c60eb90da0b56b45634e6e05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181823"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma
.NET Framework sürüm 2.0'ın yeni özelliklerinden biri gelişmiş bir izleme sistemidir. Temel öncül değişmemiştir: izleme iletileri, verileri ilişkili bir çıktı ortamına bildiren dinleyicilere anahtarlarla gönderilir. Sürüm 2.0 için birincil fark, izlemelerin <xref:System.Diagnostics.TraceSource> sınıfın örnekleri aracılığıyla başlatılabilen olmasıdır. <xref:System.Diagnostics.TraceSource>gelişmiş bir izleme sistemi olarak işlev görmek için tasarlanmıştır ve eski <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıflarının statik yöntemleri yerine kullanılabilir. Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıflar hala var, ancak önerilen <xref:System.Diagnostics.TraceSource> uygulama izleme için sınıf kullanmaktır.  
  
 Bu konu, bir <xref:System.Diagnostics.TraceSource> uygulama yapılandırma dosyası ile birleştiğinde kullanımını açıklar.  Önerilmese de, yapılandırma dosyası <xref:System.Diagnostics.TraceSource> kullanmadan izleme yapmak mümkündür. Yapılandırma dosyası olmadan izleme hakkında bilgi için [bkz.](how-to-create-and-initialize-trace-sources.md)  
  
### <a name="to-create-and-initialize-your-trace-source"></a>İzleme kaynağınızı oluşturmak ve başlatma  
  
1. İzleme ile bir uygulama enstrümanting için ilk adım bir izleme kaynağı oluşturmaktır. Çeşitli bileşenlere sahip büyük projelerde, her bileşen için ayrı bir izleme kaynağı oluşturabilirsiniz. Önerilen uygulama, izleme kaynağı adı için uygulama adını kullanmaktır. Bu, farklı izleri ayrı tutmayı kolaylaştırır. Aşağıdaki kod yeni bir izleme`mySource)` kaynağı oluşturur (ve olayları izleyen bir yöntem ( )`Activity1`çağırır.  İzleme iletileri varsayılan izleme dinleyicisi tarafından yazılır.  
  
    ```csharp
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>İzleme dinleyicileri ve filtreleroluşturmak ve başlatma  
  
1. İlk yordamdaki kod, izleme dinleyicilerini veya filtreleri programlı olarak tanımlamaz. Kod tek başına, izleme iletilerinin varsayılan izleme dinleyicisine yazılmasıyla sonuçlanır. Belirli izleme dinleyicilerini ve ilişkili filtrelerini yapılandırmak için, uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleme. Bu dosyada, dinleyici ekleyebilir veya kaldırabilir, bir dinleyiciiçin özellikleri ve filtreyi ayarlayabilir veya dinleyicileri kaldırabilirsiniz. Aşağıdaki yapılandırma dosyası örneği, önceki yordamda oluşturulan izleme kaynağı için bir konsol izleme dinleyicisi ve metin yazarı izleme dinleyicisinin nasıl başharflere uygulandığını gösterir. İzleme dinleyicilerini yapılandırmanın yanı sıra, yapılandırma dosyası her iki dinleyici için de filtreler oluşturur ve izleme kaynağı için bir kaynak anahtarı oluşturur. İz dinleyici eklemek için iki teknik gösterilir: dinleyiciyi doğrudan izleme kaynağına eklemek ve paylaşılan dinleyici koleksiyonuna bir dinleyici eklemek ve ardından izleme kaynağına adıyla eklemek. İki dinleyici için tanımlanan filtreler farklı kaynak düzeyleri ile başharfe alınır. Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Dinleyicinin izleme iletisi yazma düzeyini değiştirmek için  
  
1. Yapılandırma dosyası, uygulamanın başlatılması sırasında izleme kaynağının ayarlarını başlatır. Bu ayarları değiştirmek için yapılandırma dosyasını değiştirmeniz ve uygulamayı yeniden başlatmanız <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> veya yöntemi kullanarak uygulamayı programlı olarak yenilemeniz gerekir. Uygulama, kullanıcı tarafından belirtilen ayarları geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilir.  Örneğin, geçerli yapılandırma ayarlarından bağımsız olarak, kritik iletilerin her zaman bir metin dosyasına gönderildiğinden emin olmak isteyebilirsiniz.  
  
    ```csharp
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Nasıl yapılır: İzleme Kaynakları Oluşturma ve Başlatma](how-to-create-and-initialize-trace-sources.md)
- [İz Dinleyicileri](trace-listeners.md)
