---
title: 'Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 346fb3399993246eb8d90f7fa900ab382ae12c71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194896"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="7a651-102">Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="7a651-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="7a651-103"><xref:System.Diagnostics.TraceSource> Sınıfı uygulamalar tarafından uygulamayla ilişkilendirilebilecek izlemeler üretmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a651-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <xref:System.Diagnostics.TraceSource> <span data-ttu-id="7a651-104">kolayca izleme olayları, izleme verilerini ve sorunu bilgilendirme izlemeleri izin veren izleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a651-104">provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="7a651-105">İşlevinin İzleme çıktısı <xref:System.Diagnostics.TraceSource> oluşturulabilir ve ile veya yapılandırma dosyalarının kullanımını olmadan başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="7a651-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="7a651-106">Bu konu, her iki seçenek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a651-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="7a651-107">Ancak, çalışma zamanında iz kaynakları tarafından üretilen İzlerin yeniden yapılandırılmasını kolaylaştırmak amacıyla yapılandırma dosyalarını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="7a651-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="7a651-108">Oluşturma ve yapılandırma dosyası kullanarak bir iz kaynağını başlatmak için</span><span class="sxs-lookup"><span data-stu-id="7a651-108">To create and initialize a trace source using a configuration file</span></span>  
  
1.  <span data-ttu-id="7a651-109">Visual Studio konsol uygulama projesi oluşturun ve sağlanan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7a651-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="7a651-110">Bu kod hataları ve uyarıları günlüğe kaydeder ve bunları konsola bazıları ve bunların bazılarını konsola yapılandırma dosyasındaki girişler tarafından oluşturulan myListener dosyasına çıkarır.</span><span class="sxs-lookup"><span data-stu-id="7a651-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  <span data-ttu-id="7a651-111">Bir projeye adındaki iz kaynağını başlatmak için mevcut değilse bir uygulama yapılandırma dosyası ekleme `TraceSourceApp` , 1. adımdaki kod örneğinde.</span><span class="sxs-lookup"><span data-stu-id="7a651-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3.  <span data-ttu-id="7a651-112">Varsayılan yapılandırma dosyasının içeriği bir konsol iz dinleyicisi ve 1. adımda oluşturulan iz kaynağı için bir metin yazıcı İzleme dinleyicisi başlatmak için aşağıdaki ayarları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7a651-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="7a651-113">İz dinleyicilerini yapılandırmaya ek olarak yapılandırma dosyasının her iki dinleyici için filtreler oluşturur ve iz kaynağı için bir kaynak anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a651-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="7a651-114">İki teknik İzleyici dinleyiciler eklemek için gösterilmektedir: dinleyiciyi doğrudan izleme kaynağına ekleme ve paylaşılan dinleyici koleksiyonuna bir dinleyici ve sonra bunu adıyla izleme kaynağına ekleme.</span><span class="sxs-lookup"><span data-stu-id="7a651-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="7a651-115">İki dinleyici için belirlenen filtrelere farklı kaynak düzeyleri atanır.</span><span class="sxs-lookup"><span data-stu-id="7a651-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="7a651-116">Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="7a651-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="7a651-117">Yapılandırma dosyası izleme kaynağının ayarlarını uygulama başlatılır anda başlatır.</span><span class="sxs-lookup"><span data-stu-id="7a651-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="7a651-118">Uygulama, kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyasının belirlediği özellikleri dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a651-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="7a651-119">Örneğin, kritik iletileri her zaman geçerli yapılandırma ayarlarından bağımsız olarak bir metin dosyasına gönderilmesini sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a651-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="7a651-120">Örnek kod, kritik iletileri için izleme dinleyicilerine çıkış olmasını sağlamak için yapılandırma dosyası ayarlarının nasıl geçersiz kılınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a651-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="7a651-121">Uygulama yürütülürken yapılandırma dosyası ayarlarının değiştirilmesi başlangıç ayarlarını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="7a651-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="7a651-122">Ayarları değiştirmek için uygulamayı yeniden başlatın veya program aracılığıyla kullanarak uygulamayı yenileyin <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a651-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="7a651-123">İzleme kaynaklarına, dinleyicilere ve filtrelere bir yapılandırma dosyası olmadan başlatmak için</span><span class="sxs-lookup"><span data-stu-id="7a651-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="7a651-124">Aşağıdaki kod örneği, bir yapılandırma dosyası kullanmadan bir izleme kaynağı boyunca izlemeyi etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a651-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="7a651-125">Bu önerilen bir yöntem değildir, ancak hangi izlemeyi sağlamak için yapılandırma dosyalarına bağımlı olmak istemediğiniz durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a651-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7a651-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a651-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="7a651-127">İzleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="7a651-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
