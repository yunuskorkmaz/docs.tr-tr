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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352041"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)

Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylar hakkında bilgi yazmak için nesneleri ve nesneleri kullanabilirsiniz. Bu örnek, bir olay günlüğü dinleyicisinin `My.Application.Log` nasıl yapılandırılabildiğini gösterir, bu nedenle Uygulama olay günlüğüne izleme bilgileri yazar.

Güvenlik günlüğüne yazamazsınız. Sistem günlüğüne yazabilmek için Yerel Sistem veya Yönetici hesabının bir üyesi olmalısınız.

Bir olay günlüğünü görüntülemek için **Server Explorer** veya Windows **Event Viewer'ı**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework'deki ETW Olayları'na](../../../../framework/performance/etw-events.md)bakın.

## <a name="to-add-and-configure-the-event-log-listener"></a>Olay günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Solution Explorer'da** app.config'e sağ tıklayın ve **Aç'ı**seçin.

    \-veya -

    App.config dosyası yoksa,

    1. **Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.

    2. Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.

    3. **Ekle**’ye tıklayın.

2. Uygulama `<listeners>` yapılandırma dosyasındaki bölümü bulun.

    Üst düzey `<configuration>` `<listeners>` bölümün altında iç içe olan `<system.diagnostics>` bölümün altında iç içe olan "DefaultSource" ad özniteliğinin bulunduğu bölümde bulacaksınız. `<source>`

3. Bu öğeyi `<listeners>` bu bölüme ekleyin:

    ```xml
    <add name="EventLog"/>
    ```

4. `<sharedListeners>` Bölümü, `<system.diagnostics>` bölümü, üst düzey `<configuration>` bölümü bulun.

5. Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Başvurunuzun adı ile değiştirin. `APPLICATION_NAME`

    > [!NOTE]
    > Genellikle, bir uygulama yalnızca olay günlüğüne hatalar yazar. Günlük çıktısını filtreleme hakkında bilgi için [bkz.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

## <a name="to-write-event-information-to-the-event-log"></a>Olay günlüğe olay bilgilerini yazmak için

Olay `My.Application.Log.WriteEntry` günlüğüne bilgi yazmak için veya `My.Application.Log.WriteException` yöntemi kullanın. Daha fazla bilgi için [bkz: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [Nasıl Yazılır: Özel Durumları Günlüğe Kaydedin.](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)

Bir derleme için olay günlüğü dinleyicisini yapılandırıldıktan sonra, `My.Application.Log` bu derlemeden yazan tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
