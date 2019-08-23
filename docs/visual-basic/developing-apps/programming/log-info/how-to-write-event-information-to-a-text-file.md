---
title: 'Nasıl yapılır: Olay bilgilerini metin dosyasına yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 4a34b57eb0a22dcf206456775cdd5817431292e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956830"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Nasıl yapılır: Olay bilgilerini metin dosyasına yazma (Visual Basic)
Uygulamanızda gerçekleşen olaylar hakkındaki `My.Application.Log` bilgileri `My.Log` günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz. Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini bir günlük dosyasına kaydetmek için yönteminin nasıl kullanılacağını gösterir.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için  
  
1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.  
  
     \- veya -  
  
     App. config dosyası yoksa:  
  
    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.  
  
    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.  
  
    3. **Ekle**'yi tıklatın.  
  
2. Uygulama yapılandırma dosyasında bölümünü bulun. `<listeners>`  
  
     Üst düzey \< \< \<altında içiçeyerleştirilmişolanSystem.Diagnostics>bölümündeiçiçeyerleştirilmişolan"DefaultSource"adözniteliğiyle,kaynak>bölümündebulunanListeners>bölümünübulabilirsiniz.\<yapılandırma > bölümü.  
  
3. Bu öğeyi `<listeners>` bu bölüme ekleyin:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Bölümünün üst `<system.diagnostics>` düzey`<configuration>` bölüm altında iç içe olan bölümünü bulun. `<sharedListeners>`  
  
5. Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     `customlocation` Özniteliğin değerini günlük dizinine değiştirin.  
  
    > [!NOTE]
    > Bir dinleyici özelliğinin değerini ayarlamak için, özelliğindeki aynı ada sahip bir özniteliği kullanın, ad küçük harfli tüm harfler. Örneğin, `location` ve `customlocation` öznitelikleri, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özelliklerinin değerlerini ayarlar.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Olay bilgilerini dosya günlüğüne yazmak için  
  
- Dosya günlüğüne bilgi `My.Application.Log.WriteException` yazmak için veyayönteminikullanın.`My.Application.Log.WriteEntry` Daha fazla bilgi için [nasıl yapılır: Yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)durumları.  
  
     Bir derlemenin dosya günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden `My.Application.Log` yazan tüm iletileri alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
