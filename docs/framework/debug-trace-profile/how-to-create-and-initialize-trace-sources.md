---
title: "Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a790ca50522adcffd5d8cd8433f1291102672430
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="45eb8-102">Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="45eb8-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="45eb8-103"><xref:System.Diagnostics.TraceSource> Sınıfı, uygulama ile ilişkili olabilir izlemeleri üretmek için uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45eb8-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="45eb8-104"><xref:System.Diagnostics.TraceSource>kolayca izleme olayları, izleme verileri ve sorunu bilgilendirme izlemeleri için ver izleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="45eb8-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="45eb8-105">İzleme çıktısı <xref:System.Diagnostics.TraceSource> oluşturuldu ve ile veya yapılandırma dosyalarının kullanılması olmadan başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="45eb8-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="45eb8-106">Bu konu, her iki seçenek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="45eb8-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="45eb8-107">Ancak, çalışma zamanında izleme kaynaklar tarafından üretilen izlemeleri yapılandırılmasına kolaylaştırmak amacıyla yapılandırma dosyalarını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="45eb8-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="45eb8-108">Oluşturma ve yapılandırma dosyası kullanarak bir izleme kaynağı başlatmak için</span><span class="sxs-lookup"><span data-stu-id="45eb8-108">To create and initialize a trace source using a configuration file</span></span>  
  
1.  <span data-ttu-id="45eb8-109">Visual Studio konsol uygulama projesi oluşturun ve sağlanan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="45eb8-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="45eb8-110">Bu kod hataları ve uyarıları günlüğe kaydeder ve bunları konsola bazıları ve bazı yapılandırma dosyasındaki girişleri tarafından oluşturulan myListener dosyasına çıkarır.</span><span class="sxs-lookup"><span data-stu-id="45eb8-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  <span data-ttu-id="45eb8-111">Bir projeye adlı izleme kaynağı başlatılamadı, yoksa bir uygulama yapılandırma dosyası ekleme `TraceSourceApp` 1. adımda kod örneğindeki.</span><span class="sxs-lookup"><span data-stu-id="45eb8-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3.  <span data-ttu-id="45eb8-112">Varsayılan yapılandırma dosyası içeriği konsol İzleme dinleyicisi ve 1. adımda oluşturulan izleme kaynağı için metin yazıcı İzleme dinleyicisi başlatmak için aşağıdaki ayarları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="45eb8-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
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
  
     <span data-ttu-id="45eb8-113">İzleme dinleyicileri yapılandırmaya, ek yapılandırma dosyası filtreleri hem dinleyicileri için ve izleme kaynağı için kaynak anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45eb8-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="45eb8-114">İzleme dinleyicileri eklemek için iki teknikleri gösterilir: dinleyicisi doğrudan izleme kaynağı ekleme ve bir dinleyici paylaşılan dinleyiciler koleksiyona ekleme ve bunu ada göre izleme kaynağını ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="45eb8-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="45eb8-115">İki dinleyicileri için tanımlanan filtreler farklı kaynak düzeyleriyle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="45eb8-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="45eb8-116">Bu, iki dinleyicileri yalnızca biri tarafından yazılan bazı iletiler sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="45eb8-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="45eb8-117">Yapılandırma dosyası uygulama başlatılmadan zamanında izleme kaynağı ayarlarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="45eb8-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="45eb8-118">Uygulamanın kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45eb8-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="45eb8-119">Örneğin, kritik iletileri bir metin dosyasına, geçerli yapılandırma ayarlarına bakılmaksızın her zaman gönderildiğinden emin olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45eb8-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="45eb8-120">Örnek kod kritik iletileri izleme dinleyicilerini çıktısına olduğundan emin olmak için yapılandırma dosyası ayarlarının geçersiz kılınıp kılınmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45eb8-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="45eb8-121">Uygulama yürütülürken yapılandırma dosyası ayarları değiştirme ve ilk ayarları değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="45eb8-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="45eb8-122">Ayarları değiştirmek için uygulamayı yeniden başlatın veya program aracılığıyla kullanarak uygulamayı yenileyin <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45eb8-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="45eb8-123">İzleme kaynakları, dinleyicileri ve filtreleri bir yapılandırma dosyası olmadan başlatmak için</span><span class="sxs-lookup"><span data-stu-id="45eb8-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="45eb8-124">Aşağıdaki kod örneği, bir yapılandırma dosyası kullanmadan izleme kaynağına izleme etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="45eb8-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="45eb8-125">Bu önerilen bir uygulama değildir, ancak yapılandırma dosyalarını izleme emin olmak için bağımlı istediğiniz değil koşullar olabilir.</span><span class="sxs-lookup"><span data-stu-id="45eb8-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="45eb8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45eb8-126">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="45eb8-127">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="45eb8-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
