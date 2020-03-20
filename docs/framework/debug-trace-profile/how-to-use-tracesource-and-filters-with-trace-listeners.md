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
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="6b837-102">Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma</span><span class="sxs-lookup"><span data-stu-id="6b837-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="6b837-103">.NET Framework sürüm 2.0'ın yeni özelliklerinden biri gelişmiş bir izleme sistemidir.</span><span class="sxs-lookup"><span data-stu-id="6b837-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="6b837-104">Temel öncül değişmemiştir: izleme iletileri, verileri ilişkili bir çıktı ortamına bildiren dinleyicilere anahtarlarla gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6b837-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="6b837-105">Sürüm 2.0 için birincil fark, izlemelerin <xref:System.Diagnostics.TraceSource> sınıfın örnekleri aracılığıyla başlatılabilen olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6b837-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="6b837-106"><xref:System.Diagnostics.TraceSource>gelişmiş bir izleme sistemi olarak işlev görmek için tasarlanmıştır ve eski <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıflarının statik yöntemleri yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b837-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="6b837-107">Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıflar hala var, ancak önerilen <xref:System.Diagnostics.TraceSource> uygulama izleme için sınıf kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6b837-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="6b837-108">Bu konu, bir <xref:System.Diagnostics.TraceSource> uygulama yapılandırma dosyası ile birleştiğinde kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b837-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="6b837-109">Önerilmese de, yapılandırma dosyası <xref:System.Diagnostics.TraceSource> kullanmadan izleme yapmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6b837-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="6b837-110">Yapılandırma dosyası olmadan izleme hakkında bilgi için [bkz.](how-to-create-and-initialize-trace-sources.md)</span><span class="sxs-lookup"><span data-stu-id="6b837-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="6b837-111">İzleme kaynağınızı oluşturmak ve başlatma</span><span class="sxs-lookup"><span data-stu-id="6b837-111">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="6b837-112">İzleme ile bir uygulama enstrümanting için ilk adım bir izleme kaynağı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6b837-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="6b837-113">Çeşitli bileşenlere sahip büyük projelerde, her bileşen için ayrı bir izleme kaynağı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b837-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="6b837-114">Önerilen uygulama, izleme kaynağı adı için uygulama adını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6b837-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="6b837-115">Bu, farklı izleri ayrı tutmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6b837-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="6b837-116">Aşağıdaki kod yeni bir izleme`mySource)` kaynağı oluşturur (ve olayları izleyen bir yöntem ( )`Activity1`çağırır.</span><span class="sxs-lookup"><span data-stu-id="6b837-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="6b837-117">İzleme iletileri varsayılan izleme dinleyicisi tarafından yazılır.</span><span class="sxs-lookup"><span data-stu-id="6b837-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="6b837-118">İzleme dinleyicileri ve filtreleroluşturmak ve başlatma</span><span class="sxs-lookup"><span data-stu-id="6b837-118">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="6b837-119">İlk yordamdaki kod, izleme dinleyicilerini veya filtreleri programlı olarak tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="6b837-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="6b837-120">Kod tek başına, izleme iletilerinin varsayılan izleme dinleyicisine yazılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6b837-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="6b837-121">Belirli izleme dinleyicilerini ve ilişkili filtrelerini yapılandırmak için, uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleme.</span><span class="sxs-lookup"><span data-stu-id="6b837-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="6b837-122">Bu dosyada, dinleyici ekleyebilir veya kaldırabilir, bir dinleyiciiçin özellikleri ve filtreyi ayarlayabilir veya dinleyicileri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b837-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="6b837-123">Aşağıdaki yapılandırma dosyası örneği, önceki yordamda oluşturulan izleme kaynağı için bir konsol izleme dinleyicisi ve metin yazarı izleme dinleyicisinin nasıl başharflere uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b837-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="6b837-124">İzleme dinleyicilerini yapılandırmanın yanı sıra, yapılandırma dosyası her iki dinleyici için de filtreler oluşturur ve izleme kaynağı için bir kaynak anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b837-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="6b837-125">İz dinleyici eklemek için iki teknik gösterilir: dinleyiciyi doğrudan izleme kaynağına eklemek ve paylaşılan dinleyici koleksiyonuna bir dinleyici eklemek ve ardından izleme kaynağına adıyla eklemek.</span><span class="sxs-lookup"><span data-stu-id="6b837-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="6b837-126">İki dinleyici için tanımlanan filtreler farklı kaynak düzeyleri ile başharfe alınır.</span><span class="sxs-lookup"><span data-stu-id="6b837-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="6b837-127">Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6b837-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="6b837-128">Dinleyicinin izleme iletisi yazma düzeyini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="6b837-128">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="6b837-129">Yapılandırma dosyası, uygulamanın başlatılması sırasında izleme kaynağının ayarlarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="6b837-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="6b837-130">Bu ayarları değiştirmek için yapılandırma dosyasını değiştirmeniz ve uygulamayı yeniden başlatmanız <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> veya yöntemi kullanarak uygulamayı programlı olarak yenilemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b837-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6b837-131">Uygulama, kullanıcı tarafından belirtilen ayarları geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6b837-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="6b837-132">Örneğin, geçerli yapılandırma ayarlarından bağımsız olarak, kritik iletilerin her zaman bir metin dosyasına gönderildiğinden emin olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b837-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b837-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b837-133">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="6b837-134">Nasıl yapılır: İzleme Kaynakları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="6b837-134">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="6b837-135">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="6b837-135">Trace Listeners</span></span>](trace-listeners.md)
