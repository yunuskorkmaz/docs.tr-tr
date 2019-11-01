---
title: 'İzlenecek yol: Karma Uygulamayı Yerelleştirme'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: bef296d5de4735780c839af312b5d4fe7eeeb960
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197858"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>İzlenecek yol: Karma Uygulamayı Yerelleştirme

Bu izlenecek yol, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]tabanlı karma uygulamadaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerinin nasıl yerelleştirileceğini gösterir.

Bu izlenecek yolda gösterilen görevler şunlardır:

- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konak projesi oluşturuluyor.

- Yerelleştirilebilir içerik ekleme.

- Yerelleştirme etkinleştiriliyor.

- Kaynak tanımlayıcıları atanıyor.

- Bir uydu derlemesi üretmek için LocBaml aracını kullanma.

Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [karma uygulama örneğini yerelleştirme](https://go.microsoft.com/fwlink/?LinkID=160015).

İşiniz bittiğinde, yerelleştirilmiş bir karma uygulamanız olur.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Windows Forms konak projesi oluşturma

İlk adım [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama projesinin oluşturulması ve Yerelleştirilecek içeriğe sahip bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi eklemektir.

### <a name="to-create-the-host-project"></a>Konak projesini oluşturmak için

1. `LocalizingWpfInWf`adlı bir **WPF uygulaması** projesi oluşturun.  (**Dosya** > **Yeni** > **projesi** > **görsel C#**  veya **Visual Basic** > **Klasik Masaüstü** > **WPF uygulaması**).

2. Projeye `SimpleControl` adlı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> öğesi ekleyin.

3. Forma bir `SimpleControl` öğesi yerleştirmek için <xref:System.Windows.Forms.Integration.ElementHost> denetimini kullanın. Daha fazla bilgi için bkz. [Izlenecek yol: 3-b WPF bileşik denetimini barındırma Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Yerelleştirilebilir Içerik ekleme

Sonra, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Label denetimi ekleyeceksiniz ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinin içeriğini yerelleştirilebilir bir dizeye ayarlayacaksınız.

### <a name="to-add-localizable-content"></a>Yerelleştirilebilir İçerik eklemek için

1. **Çözüm Gezgini**, [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]açmak Için **SimpleControl. xaml** ' ye çift tıklayın.

2. Aşağıdaki kodu kullanarak <xref:System.Windows.Controls.Button> denetiminin içeriğini ayarlayın.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. **Çözüm Gezgini**, Windows Form Tasarımcısı açmak için **Form1** ' e çift tıklayın.

4. Forma bir etiket denetimi eklemek için **araç kutusunu** açın ve **etiket** ' e çift tıklayın. <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değerini `"Hello"`olarak ayarlayın.

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

     Hem `SimpleControl` öğesi hem de Label denetimi **"Hello"** metnini görüntüler.

## <a name="enabling-localization"></a>Yerelleştirme etkinleştiriliyor

Windows Form Tasarımcısı bir uydu derlemesinde yerelleştirmeyi etkinleştirmeye yönelik ayarları sağlar.

### <a name="to-enable-localization"></a>Yerelleştirmeyi etkinleştirmek için

1. **Çözüm Gezgini**' de, **Form1.cs** ' ye çift tıklayarak Windows Form Tasarımcısı açın.

2. **Özellikler** penceresinde, formun **yerelleştirilebilir** özelliğinin değerini `true`olarak ayarlayın.

3. **Özellikler** penceresinde, **Language** özelliğinin değerini **İspanyolca (İspanya)** olarak ayarlayın.

4. Windows Form Tasarımcısı etiket denetimini seçin.

5. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değerini `"Hola"`olarak ayarlayın.

     Projeye Form1.es-ES. resx adlı yeni bir kaynak dosyası eklenir.

6. **Çözüm Gezgini**' de, **Form1.cs** öğesine sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kodu düzenleyici 'de açın.

7. Aşağıdaki kodu, `InitializeComponent`çağrısından önce `Form1` oluşturucusuna kopyalayın.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. **Çözüm Gezgini**, **localizingwpfinwf** öğesine sağ tıklayın ve **Projeyi Kaldır**' a tıklayın.

     Proje adı etiketlendi **(kullanılamıyor)** .

9. **Localizingwpfinwf**öğesine sağ tıklayın ve **localizingwpfinwf. csproj öğesini Düzenle**' ye tıklayın.

     Proje dosyası kod düzenleyicisinde açılır.

10. Aşağıdaki satırı proje dosyasındaki ilk `PropertyGroup` kopyalayın.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Proje dosyasını kaydedin ve kapatın.

12. **Çözüm Gezgini**, **localizingwpfinwf** öğesine sağ tıklayın ve **projeyi yeniden yükle**' ye tıklayın.

## <a name="assigning-resource-identifiers"></a>Kaynak tanımlayıcıları atama

Kaynak tanımlayıcılarını kullanarak, yerelleştirilebilir içeriğinizi kaynak Derlemeleriyle eşleyebilirsiniz. MsBuild. exe uygulaması, `updateuid` seçeneğini belirttiğinizde kaynak tanımlayıcılarını otomatik olarak atar.

### <a name="to-assign-resource-identifiers"></a>Kaynak tanımlayıcılarını atamak için

1. Başlat menüsünde, Visual Studio için Geliştirici Komut İstemi açın.

2. Kaynak tanımlayıcılarını yerelleştirilebilir içeriğinize atamak için aşağıdaki komutu kullanın.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. **Çözüm Gezgini**, kod düzenleyicisinde açmak Için **SimpleControl. xaml** ' ye çift tıklayın. `msbuild` komutun tüm öğelere `Uid` özniteliğini eklediğini göreceksiniz. Bu, kaynak tanımlayıcılarının atanması yoluyla yerelleştirmeyi kolaylaştırır.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Çözümü derlemek için **F6** tuşuna basın.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Bir uydu derlemesi oluşturmak için LocBaml Kullanma

Yerelleştirilmiş içeriğiniz yalnızca kaynak bir *uydu derlemesinde*depolanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğiniz için yerelleştirilmiş bir derleme oluşturmak üzere LocBaml. exe komut satırı aracını kullanın.

### <a name="to-produce-a-satellite-assembly"></a>Uydu derlemesi oluşturmak için

1. LocBaml. exe ' yi projenizin obj\Debug klasörüne kopyalayın. Daha fazla bilgi için bkz. [uygulamayı yerelleştirin](how-to-localize-an-application.md).

2. Komut Istemi penceresinde, kaynak dizelerini geçici bir dosyaya ayıklamak için aşağıdaki komutu kullanın.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Geçici. csv dosyasını Visual Studio veya başka bir metin düzenleyici ile açın. Dize `"Hello"`, Ispanyolca çevirisi, `"Hola"`ile değiştirin.

4. Temp. csv dosyasını kaydedin.

5. Yerelleştirilmiş kaynak dosyasını oluşturmak için aşağıdaki komutu kullanın.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     LocalizingWpfInWf.g.es-ES. resources dosyası obj\Debug klasöründe oluşturulur.

6. Yerelleştirilmiş uydu derlemesini derlemek için aşağıdaki komutu kullanın.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     LocalizingWpfInWf. resources. dll dosyası obj\Debug klasöründe oluşturulur.

7. LocalizingWpfInWf. resources. dll dosyasını projenin bin\Debug\es-ES klasörüne kopyalayın. Varolan dosyayı değiştirin.

8. Projenizin bin\Debug klasöründe bulunan LocalizingWpfInWf. exe ' yi çalıştırın. Uygulamayı yeniden oluşturma veya uydu derlemesinin üzerine yazılacak.

     Uygulama, Ingilizce dizeler yerine yerelleştirilmiş dizeleri gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Bir Uygulamayı Yerelleştirme](how-to-localize-an-application.md)
- [İzlenecek yol: Windows Forms yerelleştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
