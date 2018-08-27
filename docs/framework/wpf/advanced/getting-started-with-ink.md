---
title: Bir InkCanvas Visual Studio'da WPF uygulaması oluşturma
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 600d8528125606c6e1af5b031e2fc31aabb79206
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925050"
---
# <a name="get-started-with-ink-in-wpf"></a>WPF mürekkep ile çalışmaya başlama

Windows Presentation Foundation (WPF), dijital mürekkep uygulamanıza eklemenizi kolaylaştırır bir mürekkep özelliği vardır.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki örneklerde, ilk olarak kullanmaya [Microsoft Visual Studio yükleme](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Ayrıca temel WPF uygulamaları yazmak nasıl yardımcı olur. WPF ile çalışmaya başlama konusunda yardım için bkz. [izlenecek yol: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Hızlı Başlangıç

Bu bölümde Mürekkep toplayan Basit WPF uygulaması yazmanıza yardımcı olur.

### <a name="got-ink"></a>Mürekkep var mı?

Mürekkep destekleyen bir WPF uygulaması oluşturmak için:

1. Visual Studio'yu açın.

2. Yeni bir **WPF uygulaması**.

   İçinde **yeni proje** iletişim kutusunda Genişlet **yüklü** > **Visual C#** veya **Visual Basic**  >   **Windows Masaüstü** kategorisi. Ardından, **WPF uygulaması (.NET Framework)** uygulaması şablonu. Bir ad girin ve ardından **Tamam**.

   Visual Studio projesi oluşturur ve *MainWindow.xaml* Tasarımcısı'nda açılır.

3. Tür `<InkCanvas/>` arasında `<Grid>` etiketler.

   ![InkCanvas etiketi ile XAML Tasarımcısı](media/getting-started-with-ink/inkcanvas-xaml.png)

4. Tuşuna **F5** uygulamanızda hata ayıklayıcıyı başlatmak için.

5. Ekran kalemi veya fare kullanarak yazma **Merhaba Dünya** penceresinde.

Bir "hello world" uygulaması yalnızca 12 tuş mürekkep denk yazdığınız!

### <a name="spice-up-your-app"></a>Uygulamanızı renklendirin

Bazı WPF özelliklerinden ele alalım. Her şey açılış ve kapanış arasında Değiştir \<penceresi > aşağıdaki işaretlemeyle etiketler:

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

Bu XAML arka plan gradyan fırçası Mürekkep yüzeyiniz oluşturur.

![WPF uygulaması yüzeyini mürekkep üzerinde Gradyan renklerini](media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>XAML arkasındaki kod ekleyin

XAML kullanıcı arabirimi tasarlamak çok kolay hale karşın, olayları işlemek üzere kod eklemek herhangi bir gerçek yaşam uygulaması gerekir. Yanıtta bir sağ tıklama fare tarafından mürekkep yakınlaştırır basit bir örnek aşağıda verilmiştir.

1. Ayarlama `MouseRightButtonUp` , XAML işleyicisinde:

   [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. İçinde **Çözüm Gezgini**MainWindow.XAML'yi genişletin ve (MainWindow.xaml.cs veya MainWindow.xaml.vb) arka plan kod dosyasını açın. Aşağıdaki olay işleyicisini ekleyin:

   [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Uygulamayı çalıştırın. Bazı mürekkep ekleyebilir ve ardından fareyle sağ tıklayın ya da tuşuna basın ve basılı eşdeğer bir ekran kalemi ile gerçekleştirin.

   Farenin sağ düğmesiyle tıklatın her zaman görünümü yakınlaştırır.

### <a name="use-procedural-code-instead-of-xaml"></a>XAML yerine yordam kodu kullanın

Yordam kodundan tüm WPF özelliklerine erişebilirsiniz. Tüm XAML kullanmayan WPF için bir "Hello mürekkep World" uygulaması oluşturmak için aşağıdaki adımları izleyin.

1. Visual Studio'da yeni bir konsol uygulama projesi oluşturun.

   İçinde **yeni proje** iletişim kutusunda Genişlet **yüklü** > **Visual C#** veya **Visual Basic**  >   **Windows Masaüstü** kategorisi. Ardından, **konsol uygulaması (.NET Framework)** uygulaması şablonu. Bir ad girin ve ardından **Tamam**.

1. Program.cs veya Program.vb dosyaya aşağıdaki kodu yapıştırın:

   [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Sağ tıklayarak PresentationCore PresentationFramework ve WindowsBase derlemelere başvurular ekleyin **başvuruları** içinde **Çözüm Gezgini** seçip **BaşvuruEkle**.

   ![Başvuru Yöneticisi PresentationCore ve PresentationFramework gösteriliyor](media/getting-started-with-ink/references.png)

1. Tuşlarına basarak uygulamayı derleyin **F5**.

## <a name="see-also"></a>Ayrıca Bkz.

- [Dijital Mürekkep](../../../../docs/framework/wpf/advanced/digital-ink.md)
- [Mürekkep Toplama](../../../../docs/framework/wpf/advanced/collecting-ink.md)
- [El Yazısı Tanıma](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)
- [Mürekkep Depolama](../../../../docs/framework/wpf/advanced/storing-ink.md)
