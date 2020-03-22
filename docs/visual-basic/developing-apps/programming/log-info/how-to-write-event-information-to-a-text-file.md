---
title: 'Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352068"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)

Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri kullanabilirsiniz. Bu örnek, izleme `My.Application.Log.WriteEntry` bilgilerini bir günlük dosyasına günlüğe kaydetmek için yöntemin nasıl kullanılacağını gösterir.

### <a name="to-add-and-configure-the-file-log-listener"></a>Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Solution Explorer'da** app.config'e sağ tıklayın ve **Aç'ı**seçin.

     \-veya -

     App.config dosyası yoksa:

    1. **Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.

    2. Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.

    3. **Ekle**’ye tıklayın.

2. Uygulama `<listeners>` yapılandırma dosyasındaki bölümü bulun.

     \<Dinleyiciler> bölümünde \<kaynak> bölümünde, \<sistem.diagnostics> bölümü \<altında iç içe olan "DefaultSource" ad özniteliği ile> bölümü bulacaksınız.

3. Bu öğeyi `<listeners>` bu bölüme ekleyin:

    ```xml
    <add name="FileLogListener" />
    ```

4. Üst `<sharedListeners>` düzey `<configuration>` bölümün `<system.diagnostics>` altında iç içe olan bölümdeki bölümü bulun.

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

     Özniteliğin değerini `customlocation` günlük dizinine değiştirin.

    > [!NOTE]
    > Dinleyici özelliğinin değerini ayarlamak için, ad küçük harfindeki tüm harflerle birlikte özellik ile aynı ada sahip bir öznitelik kullanın. Örneğin, ve `location` `customlocation` öznitelikleri <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özellikleri değerlerini ayarlayın.

### <a name="to-write-event-information-to-the-file-log"></a>Dosya günlüğüne olay bilgilerini yazmak için

Dosya `My.Application.Log.WriteEntry` günlüğüne bilgi yazmak için veya `My.Application.Log.WriteException` yöntemi kullanın. Daha fazla bilgi için [bkz: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [Nasıl Yazılır: Özel Durumları Günlüğe Kaydedin.](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)

Bir derleme için dosya günlüğü dinleyicisini yapılandırıldıktan sonra, `My.Application.Log` bu derlemeden yazan tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
