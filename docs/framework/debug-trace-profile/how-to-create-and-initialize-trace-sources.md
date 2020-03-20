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
ms.openlocfilehash: eeccad44bd2719a3cb2a721ba4e32a7bf477636f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174738"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="39829-102">Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="39829-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="39829-103">Sınıf, <xref:System.Diagnostics.TraceSource> uygulamayla ilişkilendirilebilen izlemeleri oluşturmak için uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39829-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="39829-104"><xref:System.Diagnostics.TraceSource>olayları kolayca izlemenize, verileri izlemenize ve bilgilendirici izlemeler vermenize olanak tanıyan izleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="39829-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="39829-105">Yapılandırma dosyaları <xref:System.Diagnostics.TraceSource> nın kullanımı yla veya kullanmadan oluşturulabilir ve başolarak başolarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="39829-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="39829-106">Bu konu her iki seçenek için de yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="39829-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="39829-107">Ancak, izleme kaynakları tarafından üretilen izleme lerin çalışma zamanında yeniden yapılandırılmasını kolaylaştırmak için yapılandırma dosyalarını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="39829-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="39829-108">Yapılandırma dosyası kullanarak izleme kaynağı oluşturmak ve başlatma</span><span class="sxs-lookup"><span data-stu-id="39829-108">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="39829-109">Visual Studio konsol uygulama projesi (.NET Framework) oluşturun ve verilen kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="39829-109">Create a Visual Studio console application project (.NET Framework) and replace the supplied code with the following code.</span></span> <span data-ttu-id="39829-110">Bu kod hataları ve uyarıları günlüğe kaydeder ve bazıları konsola, bazıları da yapılandırma dosyasındaki girişler tarafından oluşturulan myListener dosyasına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="39829-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="39829-111">Adım 1'deki kod örneğinde adı geçen `TraceSourceApp` izleme kaynağını başlatmayı sağlamak için projeye bir uygulama yapılandırma dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="39829-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="39829-112">Varsayılan yapılandırma dosyası içeriğini, adım 1'de oluşturulan izleme kaynağı için bir konsol izleme dinleyicisi ve metin yazarı izleme dinleyicisini başlatmayı aşağıdaki ayarlarla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="39829-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="39829-113">İzleme dinleyicilerini yapılandırmanın yanı sıra, yapılandırma dosyası her iki dinleyici için de filtreler oluşturur ve izleme kaynağı için bir kaynak anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39829-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="39829-114">İz dinleyici eklemek için iki teknik gösterilir: dinleyiciyi doğrudan izleme kaynağına eklemek ve paylaşılan dinleyici koleksiyonuna bir dinleyici eklemek ve ardından izleme kaynağına adıyla eklemek.</span><span class="sxs-lookup"><span data-stu-id="39829-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="39829-115">İki dinleyici için tanımlanan filtreler farklı kaynak düzeyleri ile başharfe alınır.</span><span class="sxs-lookup"><span data-stu-id="39829-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="39829-116">Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="39829-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="39829-117">Yapılandırma dosyası, uygulamanın başlatılması sırasında izleme kaynağının ayarlarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="39829-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="39829-118">Uygulama, kullanıcı tarafından belirtilen ayarları geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="39829-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="39829-119">Örneğin, geçerli yapılandırma ayarlarından bağımsız olarak, kritik iletilerin her zaman bir metin dosyasına gönderilmesini sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39829-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="39829-120">Örnek kod, kritik iletilerin izleme dinleyicilerine çıktı olduğundan emin olmak için yapılandırma dosya ayarlarını nasıl geçersiz kılındığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="39829-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="39829-121">Uygulama yürütülerken yapılandırma dosyası ayarlarını değiştirme, ilk ayarları değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="39829-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="39829-122">Ayarları değiştirmek için uygulamayı yeniden başlatmanız veya <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi kullanarak uygulamayı programlı olarak yenilemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="39829-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="39829-123">Yapılandırma dosyası olmadan izleme kaynaklarını, dinleyicileri ve filtreleri başlatma</span><span class="sxs-lookup"><span data-stu-id="39829-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
- <span data-ttu-id="39829-124">Yapılandırma dosyası kullanmadan izleme kaynağı üzerinden izlemeyi etkinleştirmek için aşağıdaki örnek kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="39829-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="39829-125">Bu önerilen bir uygulama değildir, ancak izleme sağlamak için yapılandırma dosyalarına bağımlı olmak istemediğiniz durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="39829-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="39829-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39829-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="39829-127">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="39829-127">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
