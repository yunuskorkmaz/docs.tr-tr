---
title: 'Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 6e83f8450ca7be8a2dcd5ff43eab3dd2ec0d2f1b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410068"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)

`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz. Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini bir günlük dosyasına kaydetmek için yönteminin nasıl kullanılacağını gösterir.

### <a name="to-add-and-configure-the-file-log-listener"></a>Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     \-veya

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. `<listeners>`Uygulama yapılandırma dosyasında bölümünü bulun.

     Bölümünün, \<listeners> \<source> \<system.diagnostics> üst düzey bölüm altında iç içe yerleştirilmiş olan bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz \<configuration> .

3. Bu öğeyi bu bölüme ekleyin `<listeners>` :

    ```xml
    <add name="FileLogListener" />
    ```

4. Bölümünün `<sharedListeners>` `<system.diagnostics>` üst düzey bölüm altında iç içe olan bölümünü bulun `<configuration>` .

5. Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     `customlocation`Özniteliğin değerini günlük dizinine değiştirin.

    > [!NOTE]
    > Bir dinleyici özelliğinin değerini ayarlamak için, özelliğindeki aynı ada sahip bir özniteliği kullanın, ad küçük harfli tüm harfler. Örneğin, `location` ve öznitelikleri, `customlocation` <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve özelliklerinin değerlerini ayarlar <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> .

### <a name="to-write-event-information-to-the-file-log"></a>Olay bilgilerini dosya günlüğüne yazmak için

`My.Application.Log.WriteEntry` `My.Application.Log.WriteException` Dosya günlüğüne bilgi yazmak için veya yöntemini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](how-to-log-exceptions.md).

Bir derlemenin dosya günlüğü dinleyicisini yapılandırdıktan sonra, `My.Application.Log` Bu derlemeden yazan tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](how-to-log-exceptions.md)
