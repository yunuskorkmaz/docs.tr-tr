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
ms.openlocfilehash: 805e1cc7d1def74a2a3e7b28afd052be1c4836c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596832"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma
<xref:System.Diagnostics.TraceSource> Sınıfı uygulamalar tarafından uygulamayla ilişkilendirilebilecek izlemeler üretmek için kullanılır. <xref:System.Diagnostics.TraceSource> kolayca izleme olayları, izleme verilerini ve sorunu bilgilendirme izlemeleri izin veren izleme yöntemleri sağlar. İşlevinin İzleme çıktısı <xref:System.Diagnostics.TraceSource> oluşturulabilir ve ile veya yapılandırma dosyalarının kullanımını olmadan başlatıldı. Bu konu, her iki seçenek için yönergeler sağlar. Ancak, çalışma zamanında iz kaynakları tarafından üretilen İzlerin yeniden yapılandırılmasını kolaylaştırmak amacıyla yapılandırma dosyalarını kullanmanızı öneririz.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Oluşturma ve yapılandırma dosyası kullanarak bir iz kaynağını başlatmak için  
  
1. Visual Studio konsol uygulama projesi oluşturun ve sağlanan kodu aşağıdaki kodla değiştirin. Bu kod hataları ve uyarıları günlüğe kaydeder ve bunları konsola bazıları ve bunların bazılarını konsola yapılandırma dosyasındaki girişler tarafından oluşturulan myListener dosyasına çıkarır.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Bir projeye adındaki iz kaynağını başlatmak için mevcut değilse bir uygulama yapılandırma dosyası ekleme `TraceSourceApp` , 1. adımdaki kod örneğinde.  
  
3. Varsayılan yapılandırma dosyasının içeriği bir konsol iz dinleyicisi ve 1. adımda oluşturulan iz kaynağı için bir metin yazıcı İzleme dinleyicisi başlatmak için aşağıdaki ayarları değiştirin.  
  
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
  
     İz dinleyicilerini yapılandırmaya ek olarak yapılandırma dosyasının her iki dinleyici için filtreler oluşturur ve iz kaynağı için bir kaynak anahtarı oluşturur. İki teknik İzleyici dinleyiciler eklemek için gösterilmektedir: dinleyiciyi doğrudan izleme kaynağına ekleme ve paylaşılan dinleyici koleksiyonuna bir dinleyici ve sonra bunu adıyla izleme kaynağına ekleme. İki dinleyici için belirlenen filtrelere farklı kaynak düzeyleri atanır. Bu, bazı iletilerin iki dinleyiciden yalnızca biri tarafından yazılmasıyla sonuçlanır.  
  
     Yapılandırma dosyası izleme kaynağının ayarlarını uygulama başlatılır anda başlatır. Uygulama, kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyasının belirlediği özellikleri dinamik olarak değiştirebilirsiniz. Örneğin, kritik iletileri her zaman geçerli yapılandırma ayarlarından bağımsız olarak bir metin dosyasına gönderilmesini sağlamak isteyebilirsiniz. Örnek kod, kritik iletileri için izleme dinleyicilerine çıkış olmasını sağlamak için yapılandırma dosyası ayarlarının nasıl geçersiz kılınacağını gösterir.  
  
     Uygulama yürütülürken yapılandırma dosyası ayarlarının değiştirilmesi başlangıç ayarlarını değiştirmez. Ayarları değiştirmek için uygulamayı yeniden başlatın veya program aracılığıyla kullanarak uygulamayı yenileyin <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>İzleme kaynaklarına, dinleyicilere ve filtrelere bir yapılandırma dosyası olmadan başlatmak için  
  
- Aşağıdaki kod örneği, bir yapılandırma dosyası kullanmadan bir izleme kaynağı boyunca izlemeyi etkinleştirmek için kullanın. Bu önerilen bir yöntem değildir, ancak hangi izlemeyi sağlamak için yapılandırma dosyalarına bağımlı olmak istemediğiniz durumlar olabilir.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
