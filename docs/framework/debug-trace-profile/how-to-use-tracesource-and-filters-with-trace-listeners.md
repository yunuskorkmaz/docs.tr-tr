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
ms.openlocfilehash: d51092aebad340a7549acef248d009518314505d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157475"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma
.NET Framework 2.0 sürümünde yeni özelliklerden biri, Gelişmiş bir izleme sistemidir. Temel değiştirilmez: izleme iletileri rapor verilerini bir ilişkili çıkış Orta dinleyici için anahtarlar aracılığıyla gönderilir. Sürüm 2.0 için birincil bir fark var izlemeleri örneklerini başlatılabilir mı <xref:System.Diagnostics.TraceSource> sınıfı. <xref:System.Diagnostics.TraceSource> bir Gelişmiş izleme sistemi olarak çalışmaya yöneliktir ve eski yerine statik yöntemleri kullanılabilir <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıfları. Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıfları yine de mevcut, ancak kullanmak için önerilen yöntemdir <xref:System.Diagnostics.TraceSource> izleme sınıfı.  
  
 Bu konuda kullanımını açıklayan bir <xref:System.Diagnostics.TraceSource> uygulama yapılandırma dosyası ile birlikte.  İzleme kullanarak önerilmez olsa da, mümkündür bir <xref:System.Diagnostics.TraceSource> kullanmadan bir yapılandırma dosyası. Bir yapılandırma dosyası olmadan izleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: İzleme kaynakları oluşturma ve başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Oluşturup, iz kaynağını başlatmak için  
  
1.  İzleme ile uygulamada ölçümlü izleme yapma ilk adımı, bir izleme kaynağı oluşturmaktır. Çeşitli bileşenleri ile büyük projelerinde, her bileşen için ayrı bir iz oluşturabilirsiniz. Önerilen uygulama izleme kaynağı adı için uygulama adı kullanmaktır. Bu farklı izlemeleri ayrı tutmak kolaylaştırır. Aşağıdaki kod yeni bir izleme kaynağı oluşturur (`mySource)` ve bir yöntemi çağıran (`Activity1`) bu olayları izler.  İzleme iletileri tarafından varsayılan İzleme dinleyicisi yazılır.  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Oluşturma ve izleme dinleyicilerine ve filtreleri Başlat  
  
1.  İlk yordam kodunda programlı olarak herhangi bir izleme dinleyicilerine veya filtreleri tanımlamaz. İzleme iletileri için varsayılan İzleme dinleyicisi yazılmakta olan tek başına kod sonuçlanır. Belirli izleme dinleyicilerine ve bunların ilişkili filtrelerini yapılandırmak için uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleyin. Bu dosyada ekleyebilir veya bir dinleyiciyi kaldırmak, özellikleri ve filtresi için bir dinleyici ayarlayın veya dinleyicileri kaldırabilirsiniz. Aşağıdaki yapılandırma dosyası örneği nasıl bir konsol iz dinleyicisi ve bir metin yazıcı İzleme dinleyicisi önceki yordamda oluşturduğunuz izleme kaynağının başlatılacağını gösterir. İz dinleyicilerini yapılandırmaya ek olarak yapılandırma dosyasının her iki dinleyici için filtreler oluşturur ve iz kaynağı için bir kaynak anahtarı oluşturur. İki teknik İzleyici dinleyiciler eklemek için gösterilmektedir: dinleyiciyi doğrudan izleme kaynağına ekleme ve paylaşılan dinleyici koleksiyonuna bir dinleyici ve sonra bunu adıyla izleme kaynağına ekleme. İki dinleyici için belirlenen filtrelere farklı kaynak düzeyleri atanır. Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Başlangıçtan bir dinleyici izleme iletisi Yazar düzeyi değiştirme  
  
1.  Yapılandırma dosyası izleme kaynağının ayarlarını uygulama başlatılır anda başlatır. Bu ayarları değiştirmek için yapılandırma dosyasını değiştirin ve uygulamayı yeniden başlatın veya gerekir kullanarak uygulamayı programlama yoluyla Yenile <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi. Uygulama, kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyasının belirlediği özellikleri dinamik olarak değiştirebilirsiniz.  Örneğin, güvence altına almak kritik iletileri bir metin dosyası, geçerli yapılandırma ayarlarından bağımsız olarak her zaman gönderilen isteyebilirsiniz.  
  
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
- [Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [İz Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
