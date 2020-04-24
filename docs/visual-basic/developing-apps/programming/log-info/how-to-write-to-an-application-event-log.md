---
title: 'Nasıl yapılır: Uygulama Olay Günlüğüne Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352041"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)

Uygulamanızda gerçekleşen olaylar hakkında `My.Application.Log` bilgi `My.Log` yazmak için ve nesnelerini kullanabilirsiniz. Bu örnek, bir olay günlüğü dinleyicisinin izleme bilgilerini uygulama `My.Application.Log` olay günlüğü 'ne yazmalarını sağlayacak şekilde nasıl yapılandırılacağını gösterir.

Güvenlik günlüğüne yazılamıyor. Sistem günlüğüne yazmak için LocalSystem veya Administrator hesabının bir üyesi olmanız gerekir.

Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.

## <a name="to-add-and-configure-the-event-log-listener"></a>Olay günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

    \-veya

    App. config dosyası yoksa,

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. Uygulama yapılandırma `<listeners>` dosyasında bölümünü bulun.

    Bölümünün, üst düzey `<listeners>` `<configuration>` bölüm altında iç `<source>` içe yerleştirilmiş olan `<system.diagnostics>` bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz.

3. Bu öğeyi bu `<listeners>` bölüme ekleyin:

    ```xml
    <add name="EventLog"/>
    ```

4. Bölümünde, `<sharedListeners>` üst düzey `<configuration>` bölümünde bölümünde `<system.diagnostics>` bulunan bölümünü bulun.

5. Bu öğeyi bu `<sharedListeners>` bölüme ekleyin:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Uygulamanızın `APPLICATION_NAME` adıyla değiştirin.

    > [!NOTE]
    > Genellikle, bir uygulama olay günlüğüne yalnızca hataları yazar. Günlük çıkışını filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: filtreleme My. Application. log output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Olay günlüğüne olay bilgilerini yazmak için

Olay günlüğüne `My.Application.Log.WriteEntry` bilgi `My.Application.Log.WriteException` yazmak için veya yöntemini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Bir derleme için olay günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden `My.Application.Log` yazan tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
