---
title: 'Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 3adb594ee42b7b1fad77a54af04bb9f37f30c19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)
Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri. Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` yöntemi izleme bilgilerini bir günlük dosyasına kaydedin.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Ekleme ve dosya günlüğünü dinleyicisi yapılandırmak için  
  
1.  App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     \- veya -  
  
     Herhangi bir app.config dosyası ise:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2.  Bulun `<listeners>` uygulama yapılandırma dosyasında bölüm.  
  
     Size \<dinleyicileri > bölümüne \<kaynak > bölümü altında yer alan "DefaultSource" ad özniteliği olan \<system.diagnostics > altında en üst düzey içiçebölüm\<yapılandırma > bölümü.  
  
3.  Bu öğe için eklemek `<listeners>` bölümü:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  Bulun `<sharedListeners>` bölümüne `<system.diagnostics>` altında en üst düzey iç içe geçmiş bölüm `<configuration>` bölümü.  
  
5.  Bu öğe için eklemek `<sharedListeners>` bölümü:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Değerini değiştirme `customlocation` özniteliği günlük dizini.  
  
    > [!NOTE]
    >  Dinleyici özelliğinin değeri ayarlamak için tüm adı küçük harflerle sahip özellik aynı ada sahip bir öznitelik kullanın. Örneğin, `location` ve `customlocation` özniteliklerini ayarla değerlerini <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özellikleri.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Olay bilgilerini dosya günlüğüne yazmak için  
  
-   Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` yöntemi dosya günlük bilgilerini yazar. Daha fazla bilgi için bkz: [nasıl yapılır: günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Bir derlemenin dosya günlük dinleyicisi yapılandırdıktan sonra tüm aldığı iletileri `My.Application.Log` bütünleştirilmiş koddan yazar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
