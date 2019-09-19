---
title: 'Nasıl yapılır: Uygulama olay günlüğüne yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 385a85d956a0de727e3c061ec447a3d53ad6c159
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054143"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Nasıl yapılır: Uygulama olay günlüğüne yazma (Visual Basic)

Uygulamanızda gerçekleşen olaylar hakkında `My.Application.Log` bilgi `My.Log` yazmak için ve nesnelerini kullanabilirsiniz. Bu örnek, bir olay günlüğü dinleyicisinin izleme bilgilerini uygulama `My.Application.Log` olay günlüğü 'ne yazmalarını sağlayacak şekilde nasıl yapılandırılacağını gösterir.

Güvenlik günlüğüne yazılamıyor. Sistem günlüğüne yazmak için LocalSystem veya Administrator hesabının bir üyesi olmanız gerekir.

Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.

## <a name="to-add-and-configure-the-event-log-listener"></a>Olay günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

    \- veya -

    App. config dosyası yoksa,

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'yi tıklatın.

2. Uygulama yapılandırma dosyasında bölümünü bulun. `<listeners>`

    Bölümünün, üst düzey `<listeners>` `<system.diagnostics>` `<source>` bölüm`<configuration>` altında iç içe yerleştirilmiş olan bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz.

3. Bu öğeyi `<listeners>` bu bölüme ekleyin:

    ```xml
    <add name="EventLog"/>
    ```

4. Bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bölümünde bulunan bölümünübulun.`<sharedListeners>`

5. Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Uygulamanızın `APPLICATION_NAME` adıyla değiştirin.

    > [!NOTE]
    > Genellikle, bir uygulama olay günlüğüne yalnızca hataları yazar. Günlük çıktısını filtreleme hakkında daha fazla bilgi için [bkz. İzlenecek yol: My. Application. log çıktımı](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)filtreleniyor.

## <a name="to-write-event-information-to-the-event-log"></a>Olay günlüğüne olay bilgilerini yazmak için

Olay günlüğüne bilgi `My.Application.Log.WriteException` yazmak için veyayönteminikullanın.`My.Application.Log.WriteEntry` Daha fazla bilgi için [nasıl yapılır: Yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)durumları.

Bir derleme için olay günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden `My.Application.Log` yazan tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [İzlenecek yol: My. Application. log bilgisinin nereden yazabileceğini belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
