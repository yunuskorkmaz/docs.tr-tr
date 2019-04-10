---
title: 'Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58edf1c6f2dca5c2b269370139533f1f8da17813
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222724"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma
<xref:System.Diagnostics.Debug?displayProperty=nameWithType> Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları almak ve bu iletileri işleyen dinleyicileri adlı nesnelere iletiler gönderir. Tür bir dinleyici <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, otomatik olarak oluşturulur ve izleme ya da hata ayıklama etkin olduğunda başlatılır. İsterseniz <xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.Debug> herhangi bir ek kaynaklar için yönlendirilmesine çıktısını oluşturmalı ve ek izleme dinleyicileri başlatır.  
  
 Oluşturduğunuz dinleyicileri, uygulamanızın ihtiyaçlarına yansıtmalıdır. Örneğin, bir metin kayıt tüm izleme çıkışı istiyorsanız, oluşturun bir <xref:System.Diagnostics.TextWriterTraceListener> dinleyicisi etkinleştirildiğinde, tüm çıktı yeni bir metin dosyasına yazar. Öte yandan, yalnızca uygulama yürütme sırasında çıkış görüntülemek istiyorsanız, oluşturun bir <xref:System.Diagnostics.ConsoleTraceListener> dinleyici, tüm çıkış için bir konsol penceresi yönlendirir. <xref:System.Diagnostics.EventLogTraceListener> Bir olay günlüğüne izleme çıkış yönlendirebilir. Daha fazla bilgi için [izleme dinleyicilerine](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 İzleme dinleyicilerine içinde oluşturduğunuz bir [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) ya da kodunuzda. Ekleme, değiştirme veya kodunuzu değiştirmek zorunda kalmadan izleme dinleyicilerine kaldırmanıza olanak tanıdığı uygulama yapılandırma dosyaları, kullanılmasını öneririz.  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Oluşturma ve yapılandırma dosyası kullanarak izleme dinleyicisi  
  
1.  Uygulama yapılandırma dosyasında, İzleme dinleyicisi bildirin. Oluşturmakta olduğunuz dinleyici diğer nesneler gerektiriyorsa, bunları da bildirin. Aşağıdaki örnekte adlı bir dinleyici oluşturma işlemi gösterilmektedir `myListener` metin dosyasına yazar `TextWriterOutput.log`.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <trace autoflush="false" indentsize="4">  
          <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />  
            <remove name="Default" />  
          </listeners>  
        </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
2.  Kullanım <xref:System.Diagnostics.Trace> izleme dinleyicilerine ileti yazmak için kodunuzda sınıfı.  
  
    ```vb  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a>Oluşturma ve İzleme dinleyicisi kodda kullanma  
  
-   İzleme dinleyicisi için ekleme <xref:System.Diagnostics.Trace.Listeners%2A> izleme dinleyicilerine bilgi toplama ve Gönder.  
  
    ```vb  
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
     - veya -  
  
-   Dinleyicinize izleme çıkışını almak istemiyorsanız, kendisine eklemeyin <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu. Bağımsız bir dinleyici çıkışını yayar <xref:System.Diagnostics.Trace.Listeners%2A> dinleyicinin kendi çağırarak koleksiyon çıkış yöntemleri. Aşağıdaki örnek, bir çizgi olmayan bir dinleyici için yazma işlemi gösterilmektedir <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu.  
  
    ```vb  
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")  
    myListener.WriteLine("Test message.")  
    ' You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush()  
    ```  
  
    ```csharp  
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");  
    myListener.WriteLine("Test message.");  
    // You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İz Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [İzleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
