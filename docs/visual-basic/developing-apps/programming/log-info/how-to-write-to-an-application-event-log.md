---
title: 'Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: a62e1e8f6112a96935ce165e42d34c57b223cd95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)
Kullanabileceğiniz `My.Application.Log` ve `My.Log` , uygulamanızda gerçekleşen olaylar hakkında bilgi yazılacak nesne. Bu örnekte bir olay günlüğü dinleyicisi yapılandırmak bunu gösterilmiştir `My.Application.Log` izleme bilgilerini uygulama olay günlüğüne yazar.  
  
 Güvenlik günlüğüne yazamaz. Sistem günlüğüne yazmak için LocalSystem veya yönetici hesabının bir üyesi olması gerekir.  
  
 Olay günlüğünü görüntülemek için kullanabileceğiniz **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi'ni**. Daha fazla bilgi için bkz: [.NET Framework'te ETW olayları](../../../../framework/performance/etw-events.md).  
  
> [!NOTE]
>  Olay günlükleri, Windows 95, Windows 98 veya Windows Millennium Edition desteklenmez.  
  
### <a name="to-add-and-configure-the-event-log-listener"></a>Eklemek ve olay günlüğü dinleyicisi yapılandırmak için  
  
1.  App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     \- veya -  
  
     App.config dosyası yoksa,  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2.  Bulun `<listeners>` uygulama yapılandırma dosyasında bölüm.  
  
     Size `<listeners>` bölümüne `<source>` bölümü altında yer alan "DefaultSource" ad özniteliği olan `<system.diagnostics>` altında en üst düzey iç içe bölüm `<configuration>` bölümü.  
  
3.  Bu öğe için eklemek `<listeners>` bölümü:  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
5.  Bu öğe için eklemek `<sharedListeners>` bölümü:  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     Değiştir `APPLICATION_NAME` , uygulamanızın adı.  
  
    > [!NOTE]
    >  Genellikle, uygulamanın yalnızca hataları olay günlüğüne yazar. Günlük çıktısını filtreleme hakkında daha fazla bilgi için bkz: [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
### <a name="to-write-event-information-to-the-event-log"></a>Olay günlüğüne olay bilgilerini yazma  
  
-   Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` yöntemi bilgileri olay günlüğüne yazma. Daha fazla bilgi için bkz: [nasıl yapılır: günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Derleme için olay günlüğüne dinleyici yapılandırdıktan sonra tüm aldığı iletileri `My.Applcation.Log` bütünleştirilmiş koddan yazar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
