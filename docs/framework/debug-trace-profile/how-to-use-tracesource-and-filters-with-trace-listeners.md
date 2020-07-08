---
title: 'Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma'
description: .NET ' te iz dinleyicileri ile TraceSource sınıfını ve filtrelerini kullanın. TraceSource eski Izleme ve hata ayıklama sınıflarının statik yöntemlerinin yerini alır.
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
ms.openlocfilehash: 432c866f7c3ca1fd59f8f3d36acd61740b6584c0
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051265"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="3323a-104">Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma</span><span class="sxs-lookup"><span data-stu-id="3323a-104">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="3323a-105">.NET Framework sürüm 2,0 ' deki yeni özelliklerden biri, gelişmiş bir izleme sistemidir.</span><span class="sxs-lookup"><span data-stu-id="3323a-105">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="3323a-106">Temel şirket içi değiştirilmez: izleme iletileri, verileri ilişkili bir çıkış ortamına rapor eden, dinleyicilerine anahtarlar aracılığıyla gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3323a-106">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="3323a-107">Sürüm 2,0 ' in birincil bir farkı, izlemelerin sınıf örnekleri aracılığıyla başlatılabiliyordu <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="3323a-107">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="3323a-108"><xref:System.Diagnostics.TraceSource>, gelişmiş bir izleme sistemi olarak işlevine yöneliktir ve eski <xref:System.Diagnostics.Trace> ve izleme sınıflarının statik yöntemlerinin yerine kullanılabilir <xref:System.Diagnostics.Debug> .</span><span class="sxs-lookup"><span data-stu-id="3323a-108"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="3323a-109">Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıfları hala mevcuttur, ancak önerilen uygulama, <xref:System.Diagnostics.TraceSource> izleme için sınıfını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3323a-109">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="3323a-110">Bu konuda, bir <xref:System.Diagnostics.TraceSource> uygulama yapılandırma dosyası ile bağlanmış bir kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3323a-110">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="3323a-111">Bir yapılandırma dosyası kullanılmadan ' ı kullanarak izlemek mümkün olmasa da, kullanılması önerilmez <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="3323a-111">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="3323a-112">Yapılandırma dosyası olmadan izleme hakkında bilgi için bkz. [nasıl yapılır: Izleme kaynakları oluşturma ve başlatma](how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="3323a-112">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="3323a-113">İzleme kaynağınızı oluşturmak ve başlatmak için</span><span class="sxs-lookup"><span data-stu-id="3323a-113">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="3323a-114">İzlemeyi kullanarak bir uygulamayı izlemenin ilk adımı, izleme kaynağı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="3323a-114">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="3323a-115">Çeşitli bileşenlere sahip büyük projelerde her bir bileşen için ayrı bir izleme kaynağı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3323a-115">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="3323a-116">Önerilen yöntem, izleme kaynağı adı için uygulama adını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3323a-116">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="3323a-117">Bu, farklı izlemeleri ayrı tutmaya daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3323a-117">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="3323a-118">Aşağıdaki kod yeni bir izleme kaynağı oluşturur ( `mySource)` ve olayları izleyen bir yöntemi ( `Activity1` ) çağırır.</span><span class="sxs-lookup"><span data-stu-id="3323a-118">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="3323a-119">İzleme iletileri varsayılan izleme dinleyicisi tarafından yazılır.</span><span class="sxs-lookup"><span data-stu-id="3323a-119">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="3323a-120">İzleme dinleyicileri ve filtreleri oluşturmak ve başlatmak için</span><span class="sxs-lookup"><span data-stu-id="3323a-120">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="3323a-121">İlk yordamdaki kod, izleme dinleyicilerini veya filtrelerini program aracılığıyla tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="3323a-121">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="3323a-122">Kod, izleme iletilerinin yalnızca varsayılan izleme dinleyicisine yazılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3323a-122">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="3323a-123">Belirli izleme dinleyicilerini ve bunlarla ilişkili filtreleri yapılandırmak için uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="3323a-123">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="3323a-124">Bu dosyada, bir dinleyici ekleyebilir veya kaldırabilir, bir dinleyici için özellikleri ve filtreyi ayarlayabilir ya da dinleyicileri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3323a-124">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="3323a-125">Aşağıdaki yapılandırma dosyası örneği, bir konsol İzleme dinleyicisinin ve önceki yordamda oluşturulan izleme kaynağı için bir metin yazıcısı İzleme dinleyicisinin nasıl başlatılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3323a-125">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="3323a-126">İzleme dinleyicilerini yapılandırmanın yanı sıra, yapılandırma dosyası her iki dinleyici için de filtreler oluşturur ve izleme kaynağı için bir kaynak anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3323a-126">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="3323a-127">İzleme dinleyicileri eklemek için iki teknik gösterilmektedir: dinleyiciyi doğrudan izleme kaynağına ekleme ve paylaşılan dinleyici koleksiyonuna bir dinleyici ekleme ve ardından bunu bir ad ile izleme kaynağına ekleme.</span><span class="sxs-lookup"><span data-stu-id="3323a-127">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="3323a-128">İki dinleyici için tanımlanan filtreler farklı kaynak düzeyleriyle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="3323a-128">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="3323a-129">Bu, bazı iletilerin yalnızca biri iki dinleyiciyle yazılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3323a-129">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="3323a-130">Bir dinleyicinin bir izleme iletisi yazdığı düzeyi değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="3323a-130">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="3323a-131">Yapılandırma dosyası, uygulamanın başlatıldığı sırada izleme kaynağı için ayarları başlatır.</span><span class="sxs-lookup"><span data-stu-id="3323a-131">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="3323a-132">Bu ayarları değiştirmek için yapılandırma dosyasını değiştirmeniz ve uygulamayı yeniden başlatmanız ya da yöntemi kullanarak uygulamayı programlı olarak yenilemeniz gerekir <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3323a-132">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3323a-133">Uygulama, Kullanıcı tarafından belirtilen ayarları geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3323a-133">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="3323a-134">Örneğin, geçerli yapılandırma ayarlarından bağımsız olarak, kritik iletilerin her zaman bir metin dosyasına gönderilmesini güvence altına almak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3323a-134">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3323a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3323a-135">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="3323a-136">Nasıl yapılır: İzleme Kaynakları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="3323a-136">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="3323a-137">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="3323a-137">Trace Listeners</span></span>](trace-listeners.md)
