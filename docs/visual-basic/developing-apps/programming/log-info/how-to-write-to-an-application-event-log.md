---
title: 'Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352041"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)

Uygulamanızda gerçekleşen olaylar hakkında bilgi yazmak için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz. Bu örnek bir olay günlüğü dinleyicisinin nasıl yapılandırılacağını gösterir. bu nedenle, `My.Application.Log` izleme bilgilerini uygulama olay günlüğüne yazar.

Güvenlik günlüğüne yazılamıyor. Sistem günlüğüne yazmak için LocalSystem veya Administrator hesabının bir üyesi olmanız gerekir.

Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.

## <a name="to-add-and-configure-the-event-log-listener"></a>Olay günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

    \- veya-

    App. config dosyası yoksa,

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'yi tıklatın.

2. Uygulama yapılandırma dosyasında `<listeners>` bölümünü bulun.

    En üst düzey `<configuration>` bölümünün altında yer aldığı `<system.diagnostics>` bölümünde iç içe yerleştirilmiş olan "DefaultSource" ad özniteliğiyle birlikte `<source>` bölümünde `<listeners>` bölümünü bulabilirsiniz.

3. Bu öğeyi bu `<listeners>` bölümüne ekleyin:

    ```xml
    <add name="EventLog"/>
    ```

4. Üst düzey `<configuration>` bölümündeki `<system.diagnostics>` bölümünde `<sharedListeners>` bölümünü bulun.

5. Bu öğeyi bu `<sharedListeners>` bölümüne ekleyin:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    `APPLICATION_NAME` değerini uygulamanızın adıyla değiştirin.

    > [!NOTE]
    > Genellikle, bir uygulama olay günlüğüne yalnızca hataları yazar. Günlük çıkışını filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: filtreleme My. Application. log output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Olay günlüğüne olay bilgilerini yazmak için

Olay günlüğüne bilgi yazmak için `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` metodunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Bir derleme için olay günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden yazma `My.Application.Log` tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
