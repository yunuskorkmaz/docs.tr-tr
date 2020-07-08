---
title: 'Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma'
description: .NET içinde System. Diagnostics. DefaultTraceListener gibi sınıfları kullanarak izleme dinleyicileri oluşturmayı ve başlatmayı öğrenin.
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
ms.openlocfilehash: 752306124e41a7fb7458daccc8c2891631eb9616
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051213"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma

<xref:System.Diagnostics.Debug?displayProperty=nameWithType>Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları, bu iletileri alıp işleyen dinleyiciler adlı nesnelere iletiler gönderir. Bu tür bir dinleyici, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType> izleme veya hata ayıklama etkinleştirildiğinde otomatik olarak oluşturulur ve başlatılır. <xref:System.Diagnostics.Trace>Ya da <xref:System.Diagnostics.Debug> çıktının herhangi bir ek kaynağa yönlendirilmesini istiyorsanız, ek izleme dinleyicileri oluşturmanız ve bunları başlatmalısınız.

Oluşturduğunuz dinleyiciler uygulamanızın ihtiyaçlarını yansıtmalıdır. Örneğin, tüm izleme çıktılarına ait bir metin kaydı istiyorsanız, <xref:System.Diagnostics.TextWriterTraceListener> etkin olduğunda tüm çıktıyı yeni bir metin dosyasına yazan bir dinleyici oluşturun. Öte yandan, çıktıyı yalnızca uygulama yürütmesi sırasında görüntülemek istiyorsanız, <xref:System.Diagnostics.ConsoleTraceListener> tüm çıktıyı bir konsol penceresine yönlendiren bir dinleyici oluşturun. , <xref:System.Diagnostics.EventLogTraceListener> İzleme çıkışını bir olay günlüğüne yönlendirebilir. Daha fazla bilgi için bkz. [Trace dinleyicileri](trace-listeners.md).

Bir [uygulama yapılandırma dosyasında](../configure-apps/index.md) veya kodunuzda izleme dinleyicileri oluşturabilirsiniz. Kodunuzu değiştirmeye gerek kalmadan izleme dinleyicileri eklemenize, değiştirmenize veya kaldırmanıza izin verdiklerinden, uygulama yapılandırma dosyalarının kullanılmasını öneririz.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Bir yapılandırma dosyası kullanarak izleme dinleyicisi oluşturma ve kullanma

1. İzleme dinleyicinizi uygulama yapılandırma dosyanızda bildirin. Oluşturmakta olduğunuz dinleyici başka nesneler gerektiriyorsa, bunları da bildirin. Aşağıdaki örnek, metin dosyasına yazan adlı bir dinleyicinin nasıl oluşturulacağını gösterir `myListener` `TextWriterOutput.log` .

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

2. <xref:System.Diagnostics.Trace>Trace dinleyicilerine bir ileti yazmak için kodunuzda sınıfını kullanın.

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a>Kodda bir izleme dinleyicisi oluşturmak ve kullanmak için

- İzleme dinleyicisini <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyona ekleyin ve dinleyicilerine izleme bilgileri gönderin.

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

    \-veya

- Dinleyicinizin izleme çıkışını almasını istemiyorsanız, <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyona eklemeyin. Dinleyicinin kendi çıkış yöntemlerini çağırarak, bir dinleyicinin içinden bir dinleyici aracılığıyla çıkış yapabilirsiniz <xref:System.Diagnostics.Trace.Listeners%2A> . Aşağıdaki örnek, koleksiyonda olmayan bir dinleyicinin bir satırın nasıl yazılacağını gösterir <xref:System.Diagnostics.Trace.Listeners%2A> .

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

- [İz Dinleyicileri](trace-listeners.md)
- [İzleme Anahtarları](trace-switches.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
