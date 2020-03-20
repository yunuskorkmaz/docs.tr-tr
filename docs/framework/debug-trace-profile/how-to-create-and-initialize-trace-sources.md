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
# <a name="how-to-create-and-initialize-trace-sources"></a>Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma
Sınıf, <xref:System.Diagnostics.TraceSource> uygulamayla ilişkilendirilebilen izlemeleri oluşturmak için uygulamalar tarafından kullanılır. <xref:System.Diagnostics.TraceSource>olayları kolayca izlemenize, verileri izlemenize ve bilgilendirici izlemeler vermenize olanak tanıyan izleme yöntemleri sağlar. Yapılandırma dosyaları <xref:System.Diagnostics.TraceSource> nın kullanımı yla veya kullanmadan oluşturulabilir ve başolarak başolarak oluşturulabilir. Bu konu her iki seçenek için de yönergeler sağlar. Ancak, izleme kaynakları tarafından üretilen izleme lerin çalışma zamanında yeniden yapılandırılmasını kolaylaştırmak için yapılandırma dosyalarını kullanmanızı öneririz.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Yapılandırma dosyası kullanarak izleme kaynağı oluşturmak ve başlatma  
  
1. Visual Studio konsol uygulama projesi (.NET Framework) oluşturun ve verilen kodu aşağıdaki kodla değiştirin. Bu kod hataları ve uyarıları günlüğe kaydeder ve bazıları konsola, bazıları da yapılandırma dosyasındaki girişler tarafından oluşturulan myListener dosyasına kaydeder.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Adım 1'deki kod örneğinde adı geçen `TraceSourceApp` izleme kaynağını başlatmayı sağlamak için projeye bir uygulama yapılandırma dosyası ekleyin.  
  
3. Varsayılan yapılandırma dosyası içeriğini, adım 1'de oluşturulan izleme kaynağı için bir konsol izleme dinleyicisi ve metin yazarı izleme dinleyicisini başlatmayı aşağıdaki ayarlarla değiştirin.  
  
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
  
     İzleme dinleyicilerini yapılandırmanın yanı sıra, yapılandırma dosyası her iki dinleyici için de filtreler oluşturur ve izleme kaynağı için bir kaynak anahtarı oluşturur. İz dinleyici eklemek için iki teknik gösterilir: dinleyiciyi doğrudan izleme kaynağına eklemek ve paylaşılan dinleyici koleksiyonuna bir dinleyici eklemek ve ardından izleme kaynağına adıyla eklemek. İki dinleyici için tanımlanan filtreler farklı kaynak düzeyleri ile başharfe alınır. Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.  
  
     Yapılandırma dosyası, uygulamanın başlatılması sırasında izleme kaynağının ayarlarını başlatır. Uygulama, kullanıcı tarafından belirtilen ayarları geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilir. Örneğin, geçerli yapılandırma ayarlarından bağımsız olarak, kritik iletilerin her zaman bir metin dosyasına gönderilmesini sağlamak isteyebilirsiniz. Örnek kod, kritik iletilerin izleme dinleyicilerine çıktı olduğundan emin olmak için yapılandırma dosya ayarlarını nasıl geçersiz kılındığını gösterir.  
  
     Uygulama yürütülerken yapılandırma dosyası ayarlarını değiştirme, ilk ayarları değiştirmez. Ayarları değiştirmek için uygulamayı yeniden başlatmanız veya <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi kullanarak uygulamayı programlı olarak yenilemeniz gerekir.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Yapılandırma dosyası olmadan izleme kaynaklarını, dinleyicileri ve filtreleri başlatma  
  
- Yapılandırma dosyası kullanmadan izleme kaynağı üzerinden izlemeyi etkinleştirmek için aşağıdaki örnek kodu kullanın. Bu önerilen bir uygulama değildir, ancak izleme sağlamak için yapılandırma dosyalarına bağımlı olmak istemediğiniz durumlar olabilir.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
