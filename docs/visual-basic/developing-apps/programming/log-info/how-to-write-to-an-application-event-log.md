---
title: 'Nasıl yapılır: Uygulama olay günlüğüne (Visual Basic) yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: c3c7d350132ee6c891633141fc5c4b280989e77f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934361"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Nasıl yapılır: Uygulama olay günlüğüne (Visual Basic) yazma

Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda gerçekleşen olaylar hakkında bilgi yazılacak nesne. Bu örnek nasıl bir olay günlüğü dinleyicisini yapılandırmak bunu gösterir `My.Application.Log` izleme bilgileri uygulama olay günlüğüne yazar.

Güvenlik günlüğüne yazamaz. Sistem günlüğüne yazmak için LocalSystem veya yönetici hesabının bir üyesi olmanız gerekir.

Olay günlüğünü görüntülemek için kullanabileceğiniz **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi'ni**. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md).

### <a name="to-add-and-configure-the-event-log-listener"></a>Ekleme ve olay günlüğü dinleyici yapılandırma

1. App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.

    \- veya -

    Herhangi bir app.config dosyası varsa,

    1. Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.

    2. Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.

    3. **Ekle**'yi tıklatın.

2. Bulun `<listeners>` uygulama yapılandırma dosyasında bölümü.

    Size `<listeners>` konusundaki `<source>` bölümü altında iç içe "DefaultSource" ad özniteliği ile `<system.diagnostics>` üst düzey altında iç içe bölümünde `<configuration>` bölümü.

3. Bu öğe ekleyen `<listeners>` bölümü:

    ```xml
    <add name="EventLog"/>
    ```

4. Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.

5. Bu öğe ekleyen `<sharedListeners>` bölümü:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Değiştirin `APPLICATION_NAME` uygulamanızın adı.

    > [!NOTE]
    > Genellikle, uygulamanın yalnızca hataları olay günlüğüne yazar. Günlük çıktısını filtreleme hakkında daha fazla bilgi için bkz: [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

### <a name="to-write-event-information-to-the-event-log"></a>Olay bilgilerini olay günlüğüne yazmak için

- Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` bilgilerini olay günlüğüne yazmak için yöntemi. Daha fazla bilgi için [nasıl yapılır: Günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

    Bir derleme için olay günlüğü dinleyici yapılandırdıktan sonra tüm aldığı iletileri `My.Application.Log` Bu bütünleştirilmiş koddan yazar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
