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
ms.openlocfilehash: 943621b953fbe158b3be6ae0695ba7692b7c517f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389206"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma
<xref:System.Diagnostics.Debug?displayProperty=nameWithType> Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları almak ve bu iletileri işleyen dinleyicileri olarak adlandırılan nesnelere ileti gönderme. Bu tür bir dinleyici <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, otomatik olarak oluşturulur ve izleme veya hata ayıklama etkinleştirildiğinde başlatıldı. İsterseniz <xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.Debug> herhangi bir ek kaynağına yönlendirilmesi için çıktı, oluşturmalı ve ek izleme dinleyicileri başlatılamıyor.  
  
 Oluşturduğunuz dinleyicileri uygulamanızın gereksinimlerine yansıtmalıdır. Örneğin, metin kaydı tüm izleme çıktısını istiyorsanız, oluşturun bir <xref:System.Diagnostics.TextWriterTraceListener> dinleyici etkinleştirildiğinde, tüm çıktı yeni bir metin dosyasına yazar. Diğer taraftan, yalnızca uygulama yürütmesi sırasında çıktı görüntülemek istiyorsanız, oluşturma bir <xref:System.Diagnostics.ConsoleTraceListener> tüm çıkış konsol penceresine yönlendirir dinleyicisi. <xref:System.Diagnostics.EventLogTraceListener> İzleme çıktısı için bir olay günlüğüne yönlendirebilirsiniz. Daha fazla bilgi için bkz: [izleme dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 İzleme dinleyicileri oluşturabileceğiniz bir [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) ya da kodunuzdaki. Eklemek, değiştirmek veya iz dinleyicileri kodunuzu değiştirmek zorunda kalmadan kaldırmanıza izin vermek için uygulama yapılandırma dosyaları, kullanılmasını öneririz.  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Oluşturma ve yapılandırma dosyası kullanarak bir izleme dinleyicisi kullanma  
  
1.  Uygulama yapılandırma dosyanızda, İzleme dinleyicisi bildirin. Oluşturmakta olduğunuz dinleyicisi diğer nesneleri gerektiriyorsa, bunları da bildirin. Aşağıdaki örnek olarak adlandırılan bir dinleyici oluşturulacağını gösterir `myListener` metin dosyasına yazar `TextWriterOutput.log`.  
  
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
  
2.  Kullanım <xref:System.Diagnostics.Trace> kodunuzda izleme dinleyicileri bir ileti yazmak için sınıf.  
  
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
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a>Oluşturma ve İzleme dinleyicisi kod içinde kullanma  
  
-   İzleme dinleyicisi eklemek <xref:System.Diagnostics.Trace.Listeners%2A> izleme dinleyicileri için bilgi toplama ve Gönder.  
  
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
  
-   İzleme çıktısını almak için dinleyici istemiyorsanız, kendisine eklemeyin <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu. Bağımsız bir dinleyici aracılığıyla çıktı yayma <xref:System.Diagnostics.Trace.Listeners%2A> dinleyicisi 's kendi çağırarak koleksiyon yöntemleri çıktı. Aşağıdaki örnek, kullanımda olmayan bir dinleyici için bir satır yazmak gösterilmiştir <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
