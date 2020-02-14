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
ms.openlocfilehash: 53cdce767d437c47aab94e883381954f8cf70653
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215916"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma
.NET Framework sürüm 2,0 ' deki yeni özelliklerden biri, gelişmiş bir izleme sistemidir. Temel şirket içi değiştirilmez: izleme iletileri, verileri ilişkili bir çıkış ortamına rapor eden, dinleyicilerine anahtarlar aracılığıyla gönderilir. Sürüm 2,0 ' in birincil bir farkı, izlemelerin <xref:System.Diagnostics.TraceSource> sınıfının örnekleri aracılığıyla başlatılabiliyordu. <xref:System.Diagnostics.TraceSource>, gelişmiş bir izleme sistemi olarak işlevine yöneliktir ve eski <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıflarının statik yöntemlerinin yerine kullanılabilir. Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıfları hala mevcuttur, ancak önerilen uygulama, izleme için <xref:System.Diagnostics.TraceSource> sınıfını kullanmaktır.  
  
 Bu konu, bir uygulama yapılandırma dosyası ile bağlanmış <xref:System.Diagnostics.TraceSource> kullanımını açıklar.  Bir yapılandırma dosyası kullanılmadan bir <xref:System.Diagnostics.TraceSource> kullanmayı izlemek mümkün olmasa da, önerilmez. Yapılandırma dosyası olmadan izleme hakkında bilgi için bkz. [nasıl yapılır: Izleme kaynakları oluşturma ve başlatma](how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>İzleme kaynağınızı oluşturmak ve başlatmak için  
  
1. İzlemeyi kullanarak bir uygulamayı izlemenin ilk adımı, izleme kaynağı oluşturmaktır. Çeşitli bileşenlere sahip büyük projelerde her bir bileşen için ayrı bir izleme kaynağı oluşturabilirsiniz. Önerilen yöntem, izleme kaynağı adı için uygulama adını kullanmaktır. Bu, farklı izlemeleri ayrı tutmaya daha kolay hale getirir. Aşağıdaki kod yeni bir izleme kaynağı oluşturur (`mySource)` ve olayları izleyen bir yöntemi (`Activity1`) çağırır.  İzleme iletileri varsayılan izleme dinleyicisi tarafından yazılır.  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>İzleme dinleyicileri ve filtreleri oluşturmak ve başlatmak için  
  
1. İlk yordamdaki kod, izleme dinleyicilerini veya filtrelerini program aracılığıyla tanımlamaz. Kod, izleme iletilerinin yalnızca varsayılan izleme dinleyicisine yazılmasıyla sonuçlanır. Belirli izleme dinleyicilerini ve bunlarla ilişkili filtreleri yapılandırmak için uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleyin. Bu dosyada, bir dinleyici ekleyebilir veya kaldırabilir, bir dinleyici için özellikleri ve filtreyi ayarlayabilir ya da dinleyicileri kaldırabilirsiniz. Aşağıdaki yapılandırma dosyası örneği, bir konsol İzleme dinleyicisinin ve önceki yordamda oluşturulan izleme kaynağı için bir metin yazıcısı İzleme dinleyicisinin nasıl başlatılacağını göstermektedir. İzleme dinleyicilerini yapılandırmanın yanı sıra, yapılandırma dosyası her iki dinleyici için de filtreler oluşturur ve izleme kaynağı için bir kaynak anahtarı oluşturur. İzleme dinleyicileri eklemek için iki teknik gösterilmektedir: dinleyiciyi doğrudan izleme kaynağına ekleme ve paylaşılan dinleyici koleksiyonuna bir dinleyici ekleme ve ardından bunu bir ad ile izleme kaynağına ekleme. İki dinleyici için tanımlanan filtreler farklı kaynak düzeyleriyle başlatılır. Bu, bazı iletilerin yalnızca biri iki dinleyiciyle yazılmasıyla sonuçlanır.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Bir dinleyicinin bir izleme iletisi yazdığı düzeyi değiştirmek için  
  
1. Yapılandırma dosyası, uygulamanın başlatıldığı sırada izleme kaynağı için ayarları başlatır. Bu ayarları değiştirmek için yapılandırma dosyasını değiştirmeniz ve uygulamayı yeniden başlatmanız veya <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemini kullanarak uygulamayı programlı olarak yenilemeniz gerekir. Uygulama, Kullanıcı tarafından belirtilen ayarları geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilir.  Örneğin, geçerli yapılandırma ayarlarından bağımsız olarak, kritik iletilerin her zaman bir metin dosyasına gönderilmesini güvence altına almak isteyebilirsiniz.  
  
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
- [İzleme Dinleyicileri](trace-listeners.md)
