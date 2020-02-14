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
ms.openlocfilehash: ae5e98a1ebf3753b24127f96ed563eba27eea2fb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217434"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma
<xref:System.Diagnostics.TraceSource> sınıfı, uygulamalar tarafından uygulamayla ilişkilendirilebilen izlemeler üretmek için kullanılır. <xref:System.Diagnostics.TraceSource>, olayları kolayca izlemenize, verileri izlemenize ve bilgilendirici izlemeler yapmanıza imkan tanıyan izleme yöntemleri sağlar. <xref:System.Diagnostics.TraceSource> izleme çıktısı, yapılandırma dosyaları kullanılmadan oluşturulabilir ve kullanılabilir. Bu konuda her iki seçenek için de yönergeler sağlanmaktadır. Ancak, çalışma zamanında izleme kaynakları tarafından üretilen izlemelerin yeniden yapılandırılmasını kolaylaştırmak için yapılandırma dosyalarını kullanmanızı öneririz.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Yapılandırma dosyası kullanarak izleme kaynağı oluşturma ve başlatma  
  
1. Bir Visual Studio konsol uygulaması projesi oluşturun ve sağlanan kodu aşağıdaki kodla değiştirin. Bu kod, hataları ve uyarıları günlüğe kaydeder ve bunların bazılarını konsola ve bunlardan bazılarını yapılandırma dosyasındaki girişler tarafından oluşturulan myListener dosyasına verir.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. 1\. adımdaki kod örneğinde `TraceSourceApp` adlı izleme kaynağını başlatmak için projeye, yoksa bir uygulama yapılandırma dosyası ekleyin.  
  
3. Varsayılan yapılandırma dosyası içeriğini aşağıdaki ayarlarla değiştirin ve adım 1 ' de oluşturulan izleme kaynağı için bir metin yazıcısı izleme dinleyicisi başlatın.  
  
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
  
     Yapılandırma dosyası, izleme dinleyicilerini yapılandırmanın yanı sıra her iki dinleyici için de filtreler oluşturur ve izleme kaynağı için bir kaynak anahtarı oluşturur. İzleme dinleyicileri eklemek için iki teknik gösterilmektedir: dinleyiciyi doğrudan izleme kaynağına ekleme ve paylaşılan dinleyici koleksiyonuna bir dinleyici ekleme ve ardından bunu bir ad ile izleme kaynağına ekleme. İki dinleyici için tanımlanan filtreler farklı kaynak düzeyleriyle başlatılır. Bu, bazı iletilerin yalnızca biri iki dinleyiciyle yazılmasıyla sonuçlanır.  
  
     Yapılandırma dosyası, uygulamanın başlatıldığı sırada izleme kaynağı için ayarları başlatır. Uygulama, Kullanıcı tarafından belirtilen ayarları geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilir. Örneğin, geçerli yapılandırma ayarlarından bağımsız olarak, kritik iletilerin her zaman bir metin dosyasına gönderilmesini sağlamak isteyebilirsiniz. Örnek kod, kritik iletilerin izleme dinleyicilerine çıkış olduğundan emin olmak için yapılandırma dosya ayarlarının nasıl geçersiz kılınacağını göstermektedir.  
  
     Uygulama yürütülürken yapılandırma dosyası ayarlarının değiştirilmesi, başlangıç ayarlarını değiştirmez. Ayarları değiştirmek için uygulamayı yeniden başlatmanız veya <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemini kullanarak uygulamayı programlı olarak yenilemeniz gerekir.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Yapılandırma dosyası olmadan izleme kaynaklarını, dinleyicileri ve filtreleri başlatmak için  
  
- Bir yapılandırma dosyası kullanmadan izleme kaynağı aracılığıyla izlemeyi etkinleştirmek için aşağıdaki örnek kodu kullanın. Bu önerilen bir uygulama değildir, ancak izlemeyi sağlamak için yapılandırma dosyalarına bağlı olmasını istemediğiniz durumlar olabilir.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
