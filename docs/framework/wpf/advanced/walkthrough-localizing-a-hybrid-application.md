---
title: 'İzlenecek yol: Karma Uygulamayı Yerelleştirme'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b98bf7b3f0aa4e7698a5c0ca7c8ae16051ce6300
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991765"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>İzlenecek yol: Karma Uygulamayı Yerelleştirme

Bu izlenecek yol, temel bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]karma uygulamadaki öğelerin nasıl yerelleştirileceğini gösterir.

Bu izlenecek yolda gösterilen görevler şunlardır:

- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Konak projesi oluşturuluyor.

- Yerelleştirilebilir içerik ekleme.

- Yerelleştirme etkinleştiriliyor.

- Kaynak tanımlayıcıları atanıyor.

- Bir uydu derlemesi üretmek için LocBaml aracını kullanma.

Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [karma uygulama örneğini yerelleştirme](https://go.microsoft.com/fwlink/?LinkID=160015).

İşiniz bittiğinde, yerelleştirilmiş bir karma uygulamanız olur.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Windows Forms konak projesi oluşturma

İlk adım, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama projesinin oluşturulması ve Yerelleştirilecek içeriğe sahip bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe eklemektir.

### <a name="to-create-the-host-project"></a>Konak projesini oluşturmak için

1. Adlı`LocalizingWpfInWf`bir **WPF uygulaması** projesi oluşturun.  (**Dosya** > **Yeni** **Proje görseli C#**  Visual BasicKlasikMasaüstü > **WPF uygulaması**). >  >  > 

2. Projeye adlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir`SimpleControl` öğe ekleyin. <xref:System.Windows.Controls.UserControl>

3. Form üzerinde bir `SimpleControl` öğe yerleştirmek için denetimikullanın.<xref:System.Windows.Forms.Integration.ElementHost> Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)Içinde 3-b WPF bileşik denetimi barındırma.

## <a name="adding-localizable-content"></a>Yerelleştirilebilir Içerik ekleme

Ardından, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] etiket denetimi ekleyecek ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğenin içeriğini yerelleştirilebilir bir dizeye ayarlayacaksınız.

### <a name="to-add-localizable-content"></a>Yerelleştirilebilir İçerik eklemek için

1. **Çözüm Gezgini**içinde açmak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]için **SimpleControl. xaml** ' ye çift tıklayın.

2. Aşağıdaki kodu kullanarak <xref:System.Windows.Controls.Button> denetimin içeriğini ayarlayın.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. **Çözüm Gezgini**, Windows Form Tasarımcısı açmak için **Form1** ' e çift tıklayın.

4. Forma bir etiket denetimi eklemek için **araç kutusunu** açın ve **etiket** ' e çift tıklayın. <xref:System.Windows.Forms.Control.Text%2A> Özelliğinin değerini olarak `"Hello"`ayarlayın.

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

     Hem öğe hem de etiket denetimi **"Hello"** metnini görüntüler. `SimpleControl`

## <a name="enabling-localization"></a>Yerelleştirme etkinleştiriliyor

Windows Form Tasarımcısı bir uydu derlemesinde yerelleştirmeyi etkinleştirmeye yönelik ayarları sağlar.

### <a name="to-enable-localization"></a>Yerelleştirmeyi etkinleştirmek için

1. **Çözüm Gezgini**' de, **Form1.cs** ' ye çift tıklayarak Windows Form Tasarımcısı açın.

2. **Özellikler** penceresinde, formun **yerelleştirilebilir** özelliğinin değerini olarak `true`ayarlayın.

3. **Özellikler** penceresinde, **Language** özelliğinin değerini **İspanyolca (İspanya)** olarak ayarlayın.

4. Windows Form Tasarımcısı etiket denetimini seçin.

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değerini olarak `"Hola"`ayarlayın.

     Projeye Form1.es-ES. resx adlı yeni bir kaynak dosyası eklenir.

6. **Çözüm Gezgini**' de, **Form1.cs** öğesine sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kodu düzenleyici 'de açın.

7. Çağrısından önce aşağıdaki kodu `Form1` oluşturucuya kopyalayın. `InitializeComponent`

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. **Çözüm Gezgini**, **localizingwpfinwf** öğesine sağ tıklayın ve **Projeyi Kaldır**' a tıklayın.

     Proje adı etiketlendi **(kullanılamıyor)** .

9. **Localizingwpfinwf**öğesine sağ tıklayın ve **localizingwpfinwf. csproj öğesini Düzenle**' ye tıklayın.

     Proje dosyası kod düzenleyicisinde açılır.

10. Aşağıdaki satırı proje dosyasında ilk `PropertyGroup` öğesine kopyalayın.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Proje dosyasını kaydedin ve kapatın.

12. **Çözüm Gezgini**, **localizingwpfinwf** öğesine sağ tıklayın ve **projeyi yeniden yükle**' ye tıklayın.

## <a name="assigning-resource-identifiers"></a>Kaynak tanımlayıcıları atama

Kaynak tanımlayıcılarını kullanarak, yerelleştirilebilir içeriğinizi kaynak Derlemeleriyle eşleyebilirsiniz. MSBuild. exe uygulaması, `updateuid` seçeneğini belirttiğinizde kaynak tanımlayıcılarını otomatik olarak atar.

### <a name="to-assign-resource-identifiers"></a>Kaynak tanımlayıcılarını atamak için

1. Başlat menüsünde, Visual Studio için Geliştirici Komut İstemi açın.

2. Kaynak tanımlayıcılarını yerelleştirilebilir içeriğinize atamak için aşağıdaki komutu kullanın.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. **Çözüm Gezgini**, kod düzenleyicisinde açmak Için **SimpleControl. xaml** ' ye çift tıklayın. `msbuild` Komutun `Uid` özniteliği tüm öğelerine eklediğini görürsünüz. Bu, kaynak tanımlayıcılarının atanması yoluyla yerelleştirmeyi kolaylaştırır.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Çözümü derlemek için **F6** tuşuna basın.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Bir uydu derlemesi oluşturmak için LocBaml Kullanma

Yerelleştirilmiş içeriğiniz yalnızca kaynak bir *uydu derlemesinde*depolanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriğiniz için yerelleştirilmiş bir derleme oluşturmak üzere LocBaml. exe komut satırı aracını kullanın.

### <a name="to-produce-a-satellite-assembly"></a>Uydu derlemesi oluşturmak için

1. LocBaml. exe ' yi projenizin obj\Debug klasörüne kopyalayın. Daha fazla bilgi için bkz. [uygulamayı yerelleştirin](how-to-localize-an-application.md).

2. Komut Istemi penceresinde, kaynak dizelerini geçici bir dosyaya ayıklamak için aşağıdaki komutu kullanın.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Geçici. csv dosyasını Visual Studio veya başka bir metin düzenleyici ile açın. Dizeyi `"Hello"` , İspanyolca `"Hola"`çevirisi ile değiştirin.

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
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
