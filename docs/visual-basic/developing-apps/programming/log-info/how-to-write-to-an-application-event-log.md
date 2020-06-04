---
title: 'Nasıl yapılır: Uygulama Olay Günlüğüne Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 298d6d85f8b21176b72db8e676617577eb03fada
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410042"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)

`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkında bilgi yazmak için ve nesnelerini kullanabilirsiniz. Bu örnek, bir olay günlüğü dinleyicisinin `My.Application.Log` izleme bilgilerini uygulama olay günlüğü 'ne yazmalarını sağlayacak şekilde nasıl yapılandırılacağını gösterir.

Güvenlik günlüğüne yazılamıyor. Sistem günlüğüne yazmak için LocalSystem veya Administrator hesabının bir üyesi olmanız gerekir.

Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.

## <a name="to-add-and-configure-the-event-log-listener"></a>Olay günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

    \-veya

    App. config dosyası yoksa,

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. `<listeners>`Uygulama yapılandırma dosyasında bölümünü bulun.

    Bölümünün, `<listeners>` `<source>` `<system.diagnostics>` üst düzey bölüm altında iç içe yerleştirilmiş olan bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz `<configuration>` .

3. Bu öğeyi bu bölüme ekleyin `<listeners>` :

    ```xml
    <add name="EventLog"/>
    ```

4. Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .

5. Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    `APPLICATION_NAME`Uygulamanızın adıyla değiştirin.

    > [!NOTE]
    > Genellikle, bir uygulama olay günlüğüne yalnızca hataları yazar. Günlük çıkışını filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: filtreleme My. Application. log output](walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Olay günlüğüne olay bilgilerini yazmak için

`My.Application.Log.WriteEntry` `My.Application.Log.WriteException` Olay günlüğüne bilgi yazmak için veya yöntemini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](how-to-log-exceptions.md).

Bir derleme için olay günlüğü dinleyicisini yapılandırdıktan sonra, `My.Application.Log` Bu derlemeden yazan tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](how-to-log-exceptions.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](walkthrough-determining-where-my-application-log-writes-information.md)
