---
title: 'İzlenecek yol: Karma Uygulamayı Yerelleştirme'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: e1d06085b4edb5c1e102eaab766ec7636194b991
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532027"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>İzlenecek yol: Karma Uygulamayı Yerelleştirme

Bu izlenecek yol size nasıl yerelleştirileceği konusunda gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-karma tabanlı.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   Oluşturma [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konak projesi.

-   Yerelleştirilebilir İçerik ekleme.

-   Yerelleştirme etkinleştiriliyor.

-   Kaynak Tanımlayıcıları atanıyor.

-   LocBaml aracı, bir uydu derlemesi üretmek için kullanma.

Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [görevlerin yerelleştirme](https://go.microsoft.com/fwlink/?LinkID=160015).

İşlemi tamamladığınızda, yerelleştirilmiş karma uygulaması gerekir.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Windows Forms konak projesi oluşturma

İlk adım oluşturmaktır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama ekleyin ve proje bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi, yerelleştirme içeriğe sahip.

### <a name="to-create-the-host-project"></a>Konak projeyi oluşturmak için

1.  Oluşturma bir **WPF uygulaması** adlı proje `LocalizingWpfInWf`.  (**Dosya** > **yeni** > **proje** > **Visual C#** veya **Visual Basic**   >  **Klasik Masaüstü** > **WPF uygulaması**).

2.  Ekleme bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> adlı öğesi `SimpleControl` projeye.

3.  Kullanım <xref:System.Windows.Forms.Integration.ElementHost> yerleştirmek için denetimi bir `SimpleControl` formdaki öğesi. Daha fazla bilgi için [izlenecek yol: 3B WPF bileşik denetimini Windows Forms içinde barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Yerelleştirilebilir İçerik ekleme

Sonra ekleyeceksiniz bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayarlayın ve etiket denetimini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirilebilir dize öğesinin içeriği.

### <a name="to-add-localizable-content"></a>Yerelleştirilebilir İçerik eklemek için

1.  İçinde **Çözüm Gezgini**, çift **SimpleControl.XAML'e** açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2.  İçeriğini ayarlama <xref:System.Windows.Controls.Button> aşağıdaki kodu kullanarak denetimi.

     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3.  İçinde **Çözüm Gezgini**, çift **Form1** Windows Form Tasarımcısı'nda açın.

4.  Açık **araç kutusu** ve çift **etiket** forma bir etiket denetiminizi ekleyecek. Değerini kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğini `"Hello"`.

5.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

     Her iki `SimpleControl` öğesini ve etiket denetimi görüntüleme metni **"Hello"**.

## <a name="enabling-localization"></a>Yerelleştirme etkinleştiriliyor

Windows Form Tasarımcısı, bir uydu derlemeye yerelleştirme etkinleştirmek için ayarlar sağlar.

### <a name="to-enable-localization"></a>Yerelleştirme etkinleştirilemedi

1.  İçinde **Çözüm Gezgini**, çift **Form1.cs** Windows Form Tasarımcısı'nda açın.

2.  İçinde **özellikleri** penceresinde, formun ayarlayın **yerelleştirilebilir** özelliğini `true`.

3.  İçinde **özellikleri** penceresinde değerini ayarlayın **dil** özelliğini **İspanyolca (İspanya)**.

4.  Windows Form Tasarımcısı'nda, etiket denetimini seçin.

5.  İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Text%2A> özelliğini `"Hola"`.

     Form1.es ES.resx adlı yeni bir kaynak dosya projeye eklenir.

6.  İçinde **Çözüm Gezgini**, sağ **Form1.cs** tıklatıp **kodu görüntüle** Kod Düzenleyicisi'nde açın.

7.  Aşağıdaki kodu kopyalayın `Form1` Oluşturucusu çağrısının öncesine `InitializeComponent`.

     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8.  İçinde **Çözüm Gezgini**, sağ **LocalizingWpfInWf** tıklatıp **projeyi**.

     Proje adı etiketli **(kullanılamıyor)**.

9. Sağ **LocalizingWpfInWf**, tıklatıp **LocalizingWpfInWf.csproj'yi**.

     Proje dosyası Kod Düzenleyicisi'nde açılır.

10. Aşağıdaki satırı ilk kopyalamak `PropertyGroup` proje dosyasındaki.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Proje dosyasını kaydedin ve kapatın.

12. İçinde **Çözüm Gezgini**, sağ **LocalizingWpfInWf** tıklatıp **projeyi**.

## <a name="assigning-resource-identifiers"></a>Kaynak Tanımlayıcıları atama

Yerelleştirilebilir İçerik kaynak tanımlayıcılarını kullanarak, kaynak derlemelerine eşleyebilirsiniz. Belirttiğiniz zaman MsBuild.exe uygulaması kaynak tanımlayıcılarını otomatik olarak atar. `updateuid` seçeneği.

### <a name="to-assign-resource-identifiers"></a>Kaynak Tanımlayıcıları atamak için

1.  Başlat menüsünde Visual Studio komut istemi açın.

2.  Yerelleştirilebilir İçerik için kaynak tanımlayıcılarını atamak için aşağıdaki komutu kullanın.

    ```
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3.  İçinde **Çözüm Gezgini**, çift **SimpleControl.XAML'e** Kod Düzenleyicisi'nde açın. Göreceksiniz `msbuild` komut ekledi `Uid` özniteliği için tüm öğeleri. Bu kaynak tanımlayıcıları atanması yoluyla yerelleştirme kolaylaştırır.

     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4.  Tuşuna **F6** çözümü derlemek için.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>LocBaml bir uydu derlemesi üretmek için kullanma

Bir kaynak yalnızca içinde yerelleştirilmiş içeriği depolanan *uydu derleme*. Komut satırı aracı LocBaml.exe'yi için yerelleştirilmiş bir derleme oluşturmak için kullanın, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.

### <a name="to-produce-a-satellite-assembly"></a>Uydu derlemesi üretmek için

1.  LocBaml.exe projenizin obj\Debug klasörüne kopyalayın. Daha fazla bilgi için [bir uygulamayı yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).

2.  Komut İstemi penceresinde, kaynak dizeleri geçici bir dosyaya ayıklamak için aşağıdaki komutu kullanın.

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3.  Temp.csv dosyasını Visual Studio veya başka bir metin düzenleyici ile açın. Dize değiştirin `"Hello"` İspanyolca çevirisini ile `"Hola"`.

4.  Temp.csv dosyasını kaydedin.

5.  Yerelleştirilmiş kaynak dosyası oluşturmak için aşağıdaki komutu kullanın.

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     LocalizingWpfInWf.g.es ES.resources dosya obj\Debug klasöründe oluşturulur.

6.  Yerelleştirilmiş bir uydu derlemesi oluşturmak için aşağıdaki komutu kullanın.

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     LocalizingWpfInWf.resources.dll dosyasını obj\Debug klasöründe oluşturulur.

7.  LocalizingWpfInWf.resources.dll dosya projenin bin\Debug\es ES klasörüne kopyalayın. Var olan dosyayı değiştirin.

8.  Projenizin bin\Debug klasöründe bulunan LocalizingWpfInWf.exe çalıştırın. Uygulamayı yeniden değil veya uydu derlemesi üzerine yazılır.

     Uygulama yerelleştirilmiş dizeleri İngilizce dizeler yerine gösterir.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Bir Uygulamayı Yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
- [İzlenecek yol: Windows formlarının konumunu bulma](https://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
