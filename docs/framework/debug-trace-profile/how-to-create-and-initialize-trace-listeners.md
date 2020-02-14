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
ms.openlocfilehash: ce0df0af32d6798c89c8db6761d18febc1c398bb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217436"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma

<xref:System.Diagnostics.Debug?displayProperty=nameWithType> ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları, bu iletileri alıp işleyen dinleyiciler adlı nesnelere iletiler gönderir. <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>bir dinleyici, izleme veya hata ayıklama etkinleştirildiğinde otomatik olarak oluşturulur ve başlatılır. <xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.Debug> çıkışının herhangi bir ek kaynağa yönlendirilmesini istiyorsanız, ek izleme dinleyicileri oluşturmanız ve başlatmalısınız.

Oluşturduğunuz dinleyiciler uygulamanızın ihtiyaçlarını yansıtmalıdır. Örneğin, tüm izleme çıktılarına ait bir metin kaydı istiyorsanız, etkin olduğunda tüm çıktıyı yeni bir metin dosyasına yazan <xref:System.Diagnostics.TextWriterTraceListener> dinleyicisi oluşturun. Öte yandan, çıktıyı yalnızca uygulama yürütmesi sırasında görüntülemek istiyorsanız, tüm çıktıyı bir konsol penceresine yönlendiren bir <xref:System.Diagnostics.ConsoleTraceListener> dinleyicisi oluşturun. <xref:System.Diagnostics.EventLogTraceListener>, izleme çıkışını bir olay günlüğüne yönlendirebilir. Daha fazla bilgi için bkz. [Trace dinleyicileri](trace-listeners.md).

Bir [uygulama yapılandırma dosyasında](../configure-apps/index.md) veya kodunuzda izleme dinleyicileri oluşturabilirsiniz. Kodunuzu değiştirmeye gerek kalmadan izleme dinleyicileri eklemenize, değiştirmenize veya kaldırmanıza izin verdiklerinden, uygulama yapılandırma dosyalarının kullanılmasını öneririz.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Bir yapılandırma dosyası kullanarak izleme dinleyicisi oluşturma ve kullanma

1. İzleme dinleyicinizi uygulama yapılandırma dosyanızda bildirin. Oluşturmakta olduğunuz dinleyici başka nesneler gerektiriyorsa, bunları da bildirin. Aşağıdaki örnek, `TextWriterOutput.log`metin dosyasına yazan `myListener` adlı bir dinleyicinin nasıl oluşturulacağını gösterir.

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

2. İzleme dinleyicilerine bir ileti yazmak için kodunuzda <xref:System.Diagnostics.Trace> sınıfını kullanın.

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

- İzleme dinleyicisini <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonuna ekleyin ve dinleyicilerine izleme bilgileri gönderin.

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

    \- veya-

- Dinleyicinizin izleme çıkışını almasını istemiyorsanız, <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonuna eklemeyin. Dinleyicinin kendi çıkış yöntemlerini çağırarak <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonundan bağımsız bir dinleyici aracılığıyla çıktı oluşturabilirsiniz. Aşağıdaki örnek, <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonunda olmayan bir dinleyiciye bir çizgi yazmayı gösterir.

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

- [İzleme Dinleyicileri](trace-listeners.md)
- [İzleme Anahtarları](trace-switches.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
