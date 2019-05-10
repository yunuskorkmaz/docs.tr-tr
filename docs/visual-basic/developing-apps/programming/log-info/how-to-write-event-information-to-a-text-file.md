---
title: 'Nasıl yapılır: Olay bilgilerini metin dosyasına (Visual Basic) yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: f9abf99a06437f08c65eca69e54760e44a217023
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665762"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Nasıl yapılır: Olay bilgilerini metin dosyasına (Visual Basic) yazma
Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri. Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` bir günlük dosyasına izleme bilgileri günlüğe kaydetmek için yöntemi.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Ekleme ve dosya günlüğünü dinleyici yapılandırma  
  
1. App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     \- veya -  
  
     App.config dosyası yoksa:  
  
    1. Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2. Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.  
  
    3. **Ekle**'yi tıklatın.  
  
2. Bulun `<listeners>` uygulama yapılandırma dosyasında bölümü.  
  
     Size \<dinleyicileri > konusundaki \<kaynak > bölümü altında iç içe "DefaultSource" ad özniteliği ile \<system.diagnostics > üst düzey altındaiçiçebölümünde\<yapılandırma > bölümü.  
  
3. Bu öğe ekleyen `<listeners>` bölümü:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Bulun `<sharedListeners>` konusundaki `<system.diagnostics>` bölümünde, üst düzey altında iç içe geçmiş `<configuration>` bölümü.  
  
5. Bu öğe ekleyen `<sharedListeners>` bölümü:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Değiştirin `customlocation` günlük dizini için özniteliği.  
  
    > [!NOTE]
    >  Dinleyici özelliğin değerini ayarlamak için tüm adı küçük harfle ile özelliğiyle aynı ada sahip bir öznitelik kullanın. Örneğin, `location` ve `customlocation` özniteliklerini ayarlayın değerlerini <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özellikleri.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Olay bilgilerini dosya günlüğüne yazmak için  
  
- Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` bilgi dosyası günlüğüne yazmak için yöntemi. Daha fazla bilgi için [nasıl yapılır: Günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Bir derleme için dosya günlük dinleyici yapılandırdıktan sonra tüm aldığı iletileri `My.Application.Log` Bu bütünleştirilmiş koddan yazar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
