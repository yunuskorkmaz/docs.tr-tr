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
# <a name="how-to-create-and-initialize-trace-sources"></a>Nasıl yapılır: İz Kaynakları Oluşturma ve Başlatma
<xref:System.Diagnostics.TraceSource> Sınıfı, uygulama ile ilişkili olabilir izlemeleri üretmek için uygulamalar tarafından kullanılır. <xref:System.Diagnostics.TraceSource>kolayca izleme olayları, izleme verileri ve sorunu bilgilendirme izlemeleri için ver izleme yöntemleri sağlar. İzleme çıktısı <xref:System.Diagnostics.TraceSource> oluşturuldu ve ile veya yapılandırma dosyalarının kullanılması olmadan başlatıldı. Bu konu, her iki seçenek için yönergeler sağlar. Ancak, çalışma zamanında izleme kaynaklar tarafından üretilen izlemeleri yapılandırılmasına kolaylaştırmak amacıyla yapılandırma dosyalarını kullanmanızı öneririz.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Oluşturma ve yapılandırma dosyası kullanarak bir izleme kaynağı başlatmak için  
  
1.  Visual Studio konsol uygulama projesi oluşturun ve sağlanan kodu aşağıdaki kodla değiştirin. Bu kod hataları ve uyarıları günlüğe kaydeder ve bunları konsola bazıları ve bazı yapılandırma dosyasındaki girişleri tarafından oluşturulan myListener dosyasına çıkarır.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  Bir projeye adlı izleme kaynağı başlatılamadı, yoksa bir uygulama yapılandırma dosyası ekleme `TraceSourceApp` 1. adımda kod örneğindeki.  
  
3.  Varsayılan yapılandırma dosyası içeriği konsol İzleme dinleyicisi ve 1. adımda oluşturulan izleme kaynağı için metin yazıcı İzleme dinleyicisi başlatmak için aşağıdaki ayarları değiştirir.  
  
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
  
     İzleme dinleyicileri yapılandırmaya, ek yapılandırma dosyası filtreleri hem dinleyicileri için ve izleme kaynağı için kaynak anahtarı oluşturur. İzleme dinleyicileri eklemek için iki teknikleri gösterilir: dinleyicisi doğrudan izleme kaynağı ekleme ve bir dinleyici paylaşılan dinleyiciler koleksiyona ekleme ve bunu ada göre izleme kaynağını ekleyerek. İki dinleyicileri için tanımlanan filtreler farklı kaynak düzeyleriyle başlatılır. Bu, iki dinleyicileri yalnızca biri tarafından yazılan bazı iletiler sonuçlanır.  
  
     Yapılandırma dosyası uygulama başlatılmadan zamanında izleme kaynağı ayarlarını başlatır. Uygulamanın kullanıcı tarafından belirtilen herhangi bir ayarı geçersiz kılmak için yapılandırma dosyası tarafından ayarlanan özellikleri dinamik olarak değiştirebilirsiniz. Örneğin, kritik iletileri bir metin dosyasına, geçerli yapılandırma ayarlarına bakılmaksızın her zaman gönderildiğinden emin olmak isteyebilirsiniz. Örnek kod kritik iletileri izleme dinleyicilerini çıktısına olduğundan emin olmak için yapılandırma dosyası ayarlarının geçersiz kılınıp kılınmayacağını gösterir.  
  
     Uygulama yürütülürken yapılandırma dosyası ayarları değiştirme ve ilk ayarları değiştirmez. Ayarları değiştirmek için uygulamayı yeniden başlatın veya program aracılığıyla kullanarak uygulamayı yenileyin <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> yöntemi.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>İzleme kaynakları, dinleyicileri ve filtreleri bir yapılandırma dosyası olmadan başlatmak için  
  
-   Aşağıdaki kod örneği, bir yapılandırma dosyası kullanmadan izleme kaynağına izleme etkinleştirmek için kullanın. Bu önerilen bir uygulama değildir, ancak yapılandırma dosyalarını izleme emin olmak için bağımlı istediğiniz değil koşullar olabilir.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
