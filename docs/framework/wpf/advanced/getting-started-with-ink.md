---
title: Visual Studio 'da WPF uygulamasında bir InkCanvas oluşturma
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920245"
---
# <a name="get-started-with-ink-in-wpf"></a>WPF 'de mürekkeple çalışmaya başlama

Windows Presentation Foundation (WPF), uygulamanıza dijital mürekkep eklemenizi kolaylaştıran bir mürekkep özelliğine sahiptir.

## <a name="prerequisites"></a>Prerequisites

Aşağıdaki örnekleri kullanmak için, önce [Visual Studio 'yu](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)yüklemeniz gerekir. Ayrıca, temel WPF uygulamalarının nasıl yazılacağını öğrenmenize de yardımcı olur. WPF kullanmaya başlarken yardım için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.

## <a name="quick-start"></a>hızlı başlangıç

Bu bölüm, mürekkep toplayan basit bir WPF uygulaması yazmanıza yardımcı olur.

### <a name="got-ink"></a>Mürekkep mi var?

Mürekkebi destekleyen bir WPF uygulaması oluşturmak için:

1. Visual Studio'yu açın.

2. Yeni bir **WPF uygulaması**oluşturun.

   **Yeni proje** iletişim kutusunda, **yüklü** > **Visual C#**  veya **Visual Basic** > **Windows Masaüstü** kategorisini genişletin. Ardından, **WPF uygulaması (.NET Framework)** uygulama şablonunu seçin. Bir ad girin ve **Tamam**' ı seçin.

   Visual Studio projeyi oluşturur ve *MainWindow. xaml* tasarımcıda açılır.

3. `<Grid>` etiketleri arasına `<InkCanvas/>` yazın.

   ![InkCanvas etiketiyle XAML Tasarımcısı](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. Uygulamanızı hata ayıklayıcıda başlatmak için **F5** tuşuna basın.

5. Ekran kalemi veya fare kullanarak pencerede **Merhaba Dünya** yazın.

Bir "Hello World" uygulamasının mürekkep eşdeğerini yalnızca 12 tuş vuruşu ile yazmış oldunuz!

### <a name="spice-up-your-app"></a>Uygulamanızı artırma

WPF 'nin bazı özelliklerinden faydalanalım. Açma ve kapatma \<pencere > etiketleri arasındaki her şeyi aşağıdaki biçimlendirme ile değiştirin:

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

Bu XAML, mürekkep yüzeyiniz üzerinde bir gradyan fırçası arka planı oluşturur.

![WPF uygulamasında mürekkep yüzeyinde gradyan renkler](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>XAML 'nin arkasında kod ekleme

XAML Kullanıcı arabirimini tasarlamayı çok kolay hale getirir, ancak herhangi bir gerçek dünya uygulamasının olayları işlemek için kod eklemesi gerekir. Bir farede sağ tıklaa yanıt olarak mürekkebe yakınlaşarak bir basit örnek aşağıda verilmiştir.

1. XAML 'de `MouseRightButtonUp` işleyicisini ayarlayın:

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. **Çözüm Gezgini**, MainWindow. xaml ' i genişletin ve arka plan kod dosyasını (MainWindow.xaml.cs veya MainWindow. xaml. vb) açın. Aşağıdaki olay işleyici kodunu ekleyin:

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Uygulamayı çalıştırın. Biraz mürekkep ekleyin ve fareyle sağ tıklayın veya ekran kalemiyle bir basma ve bekletme eşdeğeri gerçekleştirin.

   Ekran, sağ fare düğmesine her tıkladığınızda yakınlaştırılır.

### <a name="use-procedural-code-instead-of-xaml"></a>XAML yerine yordamsal kodu kullanın

Yordamsal koddan tüm WPF özelliklerine erişebilirsiniz. Her türlü XAML kullanmayan WPF için "Merhaba mürekkep dünyası" uygulaması oluşturmak için bu adımları izleyin.

1. Visual Studio 'da yeni bir konsol uygulama projesi oluşturun.

   **Yeni proje** iletişim kutusunda, **yüklü** > **Visual C#**  veya **Visual Basic** > **Windows Masaüstü** kategorisini genişletin. Ardından **konsol uygulaması (.NET Framework)** uygulama şablonunu seçin. Bir ad girin ve **Tamam**' ı seçin.

1. Aşağıdaki kodu Program.cs veya program. vb dosyasına yapıştırın:

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. **Çözüm Gezgini** **Başvurular** ' a sağ tıklayıp **Başvuru Ekle**' yi seçerek PresentationCore, PresentationFramework ve WindowsBase derlemelerine başvurular ekleyin.

   ![PresentationCore ve PresentationFramework gösteren başvuru Yöneticisi](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. **F5**tuşuna basarak uygulamayı oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Dijital Mürekkep](digital-ink.md)
- [Mürekkep Toplama](collecting-ink.md)
- [El Yazısı Tanıma](handwriting-recognition.md)
- [Mürekkep Depolama](storing-ink.md)
