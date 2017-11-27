---
title: "Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b557a9f9f462df2d1afe6d6b61871e0e9f40174
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="acce0-102">Nasıl yapılır: İz Dinleyicileri ile TraceSource ve Filtreler Kullanma</span><span class="sxs-lookup"><span data-stu-id="acce0-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="acce0-103">.NET Framework sürüm 2.0'deki yeni özelliklerin bir Gelişmiş izleme sistemi biridir.</span><span class="sxs-lookup"><span data-stu-id="acce0-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="acce0-104">Değişmeden dayanır: izleme iletileri veriler bir ilişkili çıktı Orta rapor dinleyicileri için anahtarlar aracılığıyla gönderilir.</span><span class="sxs-lookup"><span data-stu-id="acce0-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="acce0-105">Bir birincil sürüm 2.0 için izlemeleri örneklerini başlatılabilir farktır <xref:System.Diagnostics.TraceSource> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="acce0-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="acce0-106"><xref:System.Diagnostics.TraceSource>bir Gelişmiş izleme sistemi olarak çalışmaya yöneliktir ve eski yerine statik yöntemleri kullanılabilir <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıfları.</span><span class="sxs-lookup"><span data-stu-id="acce0-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="acce0-107">Bilinen <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıflar hala mevcut, ancak kullanmak için önerilen yöntemdir <xref:System.Diagnostics.TraceSource> izleme için sınıf.</span><span class="sxs-lookup"><span data-stu-id="acce0-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="acce0-108">Bu konuda kullanımını açıklar bir <xref:System.Diagnostics.TraceSource> uygulama yapılandırma dosyası ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="acce0-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="acce0-109">Bu, izleme kullanmaya Önerilmemesine rağmen mümkün olduğunda, bir <xref:System.Diagnostics.TraceSource> olmadan bir yapılandırma dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="acce0-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="acce0-110">Bir yapılandırma dosyası olmadan izleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: oluşturma ve izleme kaynaklarını başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="acce0-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="acce0-111">Oluşturma ve izleme kaynağınız başlatmak için</span><span class="sxs-lookup"><span data-stu-id="acce0-111">To create and initialize your trace source</span></span>  
  
1.  <span data-ttu-id="acce0-112">Uygulama izleme ile düzenleme ilk adımı, bir izleme kaynağını oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="acce0-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="acce0-113">Çeşitli bileşenleri ile büyük projeler her bileşen için ayrı izleme kaynağı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acce0-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="acce0-114">Önerilen uygulama izleme kaynağı adı için uygulama adı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="acce0-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="acce0-115">Bu, farklı izlemeleri ayrı tutmak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="acce0-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="acce0-116">Aşağıdaki kod yeni bir izleme kaynağı oluşturur (`mySource)` ve bir yöntemi çağırır (`Activity1`) olayları izler.</span><span class="sxs-lookup"><span data-stu-id="acce0-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="acce0-117">İzleme iletileri varsayılan İzleme dinleyicisi tarafından yazılır.</span><span class="sxs-lookup"><span data-stu-id="acce0-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="acce0-118">Oluşturma ve izleme dinleyicileri ve filtreleri başlatmak için</span><span class="sxs-lookup"><span data-stu-id="acce0-118">To create and initialize trace listeners and filters</span></span>  
  
1.  <span data-ttu-id="acce0-119">İlk yordam kodda, herhangi bir izleme dinleyicileri veya filtreleri programlı olarak tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="acce0-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="acce0-120">Tek başına kodu için varsayılan İzleme dinleyicisi yazılmakta izleme iletilerini sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="acce0-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="acce0-121">Belirli izleme dinleyicileri ve bunların ilişkili filtrelerini yapılandırmak için uygulamanızın adına karşılık gelen yapılandırma dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="acce0-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="acce0-122">Bu dosyada, eklemek veya bir dinleyici kaldırın, özellikleri ve filtre için bir dinleyici ayarlayın veya dinleyicileri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="acce0-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="acce0-123">Aşağıdaki yapılandırma dosyası örneği, bir konsol İzleme dinleyicisi ve önceki yordamda oluşturduğunuz izleme kaynağı için metin yazıcı İzleme dinleyicisi başlatılamadı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="acce0-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="acce0-124">İzleme dinleyicileri yapılandırmaya, ek yapılandırma dosyası filtreleri hem de dinleyicileri ve izleme kaynağı için kaynak anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="acce0-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="acce0-125">İzleme dinleyicileri eklemek için iki teknikleri gösterilir: dinleyicisi doğrudan izleme kaynağı ekleme ve bir dinleyici paylaşılan dinleyiciler koleksiyona ekleme ve bunu ada göre izleme kaynağını ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="acce0-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="acce0-126">İki dinleyicileri için tanımlanan filtreler farklı kaynak düzeyleriyle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="acce0-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="acce0-127">Bu, iki dinleyicileri yalnızca biri tarafından yazılan bazı iletiler sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="acce0-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="acce0-128">Hangi dinleyici izleme iletisi Yazar düzeyini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="acce0-128">To change the level at which a listener writes a trace message</span></span>  
  
1.  <span data-ttu-id="acce0-129">Yapılandırma dosyası uygulama başlatılmadan zamanında izleme kaynağı ayarlarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="acce0-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="acce0-130">Bu ayarları değiştirmek için yapılandırma dosyasını değiştirme ve uygulamayı yeniden başlatın veya program aracılığıyla kullanarak uygulamayı yenileyin <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="acce0-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="acce0-131">Uygulamanın kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acce0-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="acce0-132">Örneğin, size güvence altına almak kritik iletileri her zaman geçerli yapılandırma ayarlarına bakılmaksızın bir metin dosyasına gönderilen isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acce0-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acce0-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="acce0-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="acce0-134">Nasıl yapılır: oluşturma ve başlatma izleme kaynakları</span><span class="sxs-lookup"><span data-stu-id="acce0-134">How to: Create and Initialize Trace Sources</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [<span data-ttu-id="acce0-135">İzleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="acce0-135">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
