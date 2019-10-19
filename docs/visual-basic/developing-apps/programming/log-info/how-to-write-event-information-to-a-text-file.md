---
title: 'Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 54169f1133ed4f77026c4332493a7b5f4532aec0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583280"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)

Uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz. Bu örnek, izleme bilgilerini bir günlük dosyasına kaydetmek için `My.Application.Log.WriteEntry` yönteminin nasıl kullanılacağını gösterir.

### <a name="to-add-and-configure-the-file-log-listener"></a>Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için

1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     \- veya-

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'yi tıklatın.

2. Uygulama yapılandırma dosyasında `<listeners>` bölümünü bulun.

     Üst düzey \<system altında iç içe yerleştirilmiş olan >. Diagnostics \<configuration bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı \<source > bölümünde bulunan \<listeners > bölümünü bulabilirsiniz > kısmı.

3. Bu öğeyi bu `<listeners>` bölümüne ekleyin:

    ```xml
    <add name="FileLogListener" />
    ```

4. Üst düzey `<configuration>` bölümünde iç içe `<system.diagnostics>` bölümündeki `<sharedListeners>` bölümünü bulun.

5. Bu öğeyi bu `<sharedListeners>` bölümüne ekleyin:

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     @No__t_0 özniteliğinin değerini günlük dizinine değiştirin.

    > [!NOTE]
    > Bir dinleyici özelliğinin değerini ayarlamak için, özelliğindeki aynı ada sahip bir özniteliği kullanın, ad küçük harfli tüm harfler. Örneğin, `location` ve `customlocation` öznitelikleri <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özelliklerinin değerlerini ayarlar.

### <a name="to-write-event-information-to-the-file-log"></a>Olay bilgilerini dosya günlüğüne yazmak için

Dosya günlüğüne bilgi yazmak için `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` metodunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Bir bütünleştirilmiş kod için dosya günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden yazma `My.Application.Log` tüm iletileri alır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
