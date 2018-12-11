---
title: 'Nasıl Yapılır: İzleme dinleyicileri ile TraceSource ve filtreler kullanma'
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
ms.openlocfilehash: bc81e1e13f942f5db4fec5cc607264d499b63629
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146085"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="48aeb-102">Nasıl Yapılır: İzleme dinleyicileri ile TraceSource ve filtreler kullanma</span><span class="sxs-lookup"><span data-stu-id="48aeb-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="48aeb-103">.NET Framework 2.0 sürümünde yeni özelliklerden biri, Gelişmiş bir izleme sistemidir.</span><span class="sxs-lookup"><span data-stu-id="48aeb-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="48aeb-104">Temel değiştirilmez: izleme iletileri rapor verilerini bir ilişkili çıkış Orta dinleyici için anahtarlar aracılığıyla gönderilir.</span><span class="sxs-lookup"><span data-stu-id="48aeb-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="48aeb-105">Sürüm 2.0 için birincil bir fark var izlemeleri örneklerini başlatılabilir mı <xref:System.Diagnostics.TraceSource> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="48aeb-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="48aeb-106"><xref:System.Diagnostics.TraceSource> bir Gelişmiş izleme sistemi olarak çalışmaya yöneliktir ve eski yerine statik yöntemleri kullanılabilir <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıfları.</span><span class="sxs-lookup"><span data-stu-id="48aeb-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="48aeb-107">Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıfları yine de mevcut, ancak kullanmak için önerilen yöntemdir <xref:System.Diagnostics.TraceSource> izleme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="48aeb-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="48aeb-108">Bu konuda kullanımını açıklayan bir <xref:System.Diagnostics.TraceSource> uygulama yapılandırma dosyası ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="48aeb-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="48aeb-109">İzleme kullanarak önerilmez olsa da, mümkündür bir <xref:System.Diagnostics.TraceSource> kullanmadan bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="48aeb-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="48aeb-110">Bir yapılandırma dosyası olmadan izleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: İzleme kaynakları oluşturma ve başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="48aeb-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="48aeb-111">Oluşturup, iz kaynağını başlatmak için</span><span class="sxs-lookup"><span data-stu-id="48aeb-111">To create and initialize your trace source</span></span>  
  
1.  <span data-ttu-id="48aeb-112">İzleme ile uygulamada ölçümlü izleme yapma ilk adımı, bir izleme kaynağı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="48aeb-113">Çeşitli bileşenleri ile büyük projelerinde, her bileşen için ayrı bir iz oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48aeb-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="48aeb-114">Önerilen uygulama izleme kaynağı adı için uygulama adı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="48aeb-115">Bu farklı izlemeleri ayrı tutmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="48aeb-116">Aşağıdaki kod yeni bir izleme kaynağı oluşturur (`mySource)` ve bir yöntemi çağıran (`Activity1`) bu olayları izler.</span><span class="sxs-lookup"><span data-stu-id="48aeb-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="48aeb-117">İzleme iletileri tarafından varsayılan İzleme dinleyicisi yazılır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="48aeb-118">Oluşturma ve izleme dinleyicilerine ve filtreleri Başlat</span><span class="sxs-lookup"><span data-stu-id="48aeb-118">To create and initialize trace listeners and filters</span></span>  
  
1.  <span data-ttu-id="48aeb-119">İlk yordam kodunda programlı olarak herhangi bir izleme dinleyicilerine veya filtreleri tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="48aeb-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="48aeb-120">İzleme iletileri için varsayılan İzleme dinleyicisi yazılmakta olan tek başına kod sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="48aeb-121">Belirli izleme dinleyicilerine ve bunların ilişkili filtrelerini yapılandırmak için uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="48aeb-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="48aeb-122">Bu dosyada ekleyebilir veya bir dinleyiciyi kaldırmak, özellikleri ve filtresi için bir dinleyici ayarlayın veya dinleyicileri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48aeb-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="48aeb-123">Aşağıdaki yapılandırma dosyası örneği nasıl bir konsol iz dinleyicisi ve bir metin yazıcı İzleme dinleyicisi önceki yordamda oluşturduğunuz izleme kaynağının başlatılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="48aeb-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="48aeb-124">İz dinleyicilerini yapılandırmaya ek olarak yapılandırma dosyasının her iki dinleyici için filtreler oluşturur ve iz kaynağı için bir kaynak anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48aeb-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="48aeb-125">İki teknik İzleyici dinleyiciler eklemek için gösterilmektedir: dinleyiciyi doğrudan izleme kaynağına ekleme ve paylaşılan dinleyici koleksiyonuna bir dinleyici ve sonra bunu adıyla izleme kaynağına ekleme.</span><span class="sxs-lookup"><span data-stu-id="48aeb-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="48aeb-126">İki dinleyici için belirlenen filtrelere farklı kaynak düzeyleri atanır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="48aeb-127">Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="48aeb-128">Başlangıçtan bir dinleyici izleme iletisi Yazar düzeyi değiştirme</span><span class="sxs-lookup"><span data-stu-id="48aeb-128">To change the level at which a listener writes a trace message</span></span>  
  
1.  <span data-ttu-id="48aeb-129">Yapılandırma dosyası izleme kaynağının ayarlarını uygulama başlatılır anda başlatır.</span><span class="sxs-lookup"><span data-stu-id="48aeb-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="48aeb-130">Bu ayarları değiştirmek için yapılandırma dosyasını değiştirin ve uygulamayı yeniden başlatın veya gerekir kullanarak uygulamayı programlama yoluyla Yenile <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48aeb-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="48aeb-131">Uygulama, kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyasının belirlediği özellikleri dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48aeb-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="48aeb-132">Örneğin, güvence altına almak kritik iletileri bir metin dosyası, geçerli yapılandırma ayarlarından bağımsız olarak her zaman gönderilen isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48aeb-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48aeb-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48aeb-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="48aeb-134">Nasıl Yapılır: Oluşturma ve izleme kaynaklarını başlatma</span><span class="sxs-lookup"><span data-stu-id="48aeb-134">How to: Create and Initialize Trace Sources</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [<span data-ttu-id="48aeb-135">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="48aeb-135">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
