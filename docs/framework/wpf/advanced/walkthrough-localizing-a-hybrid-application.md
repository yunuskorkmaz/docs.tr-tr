---
title: 'İzlenecek yol: Karma Uygulamayı Yerelleştirme'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111120"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>İzlenecek yol: Karma Uygulamayı Yerelleştirme

Bu gözden geçirme, Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Forms tabanlı karma bir uygulamadaki öğeleri nasıl yerelleştirdiğinizi gösterir.

Bu gözden geçirmede gösterilen görevler şunlardır:

- Windows Forms ana bilgisayar projesini oluşturma.

- Yerelleştirilebilir içerik ekleme.

- Yerelleştirmeyi etkinleştirme.

- Kaynak tanımlayıcıları atama.

- Bir uydu tertibatı üretmek için LocBaml aracını kullanma.

Bu gözden geçirme de gösterilen görevlerin tam kod listesi için, [karma uygulama örneğini yerelleştirme](https://go.microsoft.com/fwlink/?LinkID=160015)bölümüne bakın.

Bittiğinde, yerelleştirilmiş bir karma uygulama nız olacaktır.

## <a name="prerequisites"></a>Ön koşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Windows Formları Ana Bilgisayar Projesini Oluşturma

İlk adım, Windows Forms uygulama projesini oluşturmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve yerelleştireceğiniz içeriğe sahip bir öğe eklemektir.

### <a name="to-create-the-host-project"></a>Ana bilgisayar projesini oluşturmak için

1. Adında `LocalizingWpfInWf`bir **WPF Uygulaması** projesi oluşturun.  (**Dosya** > **Yeni** > **Proje** > Görsel C **#** veya Visual **Basic** > Klasik**Masaüstü** > **WPF Uygulama**).

2. Projeye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> çağrılan `SimpleControl` bir öğe ekleyin.

3. Forma <xref:System.Windows.Forms.Integration.ElementHost> bir `SimpleControl` öğe yerleştirmek için denetimi kullanın. Daha fazla bilgi için [Walkthrough: Windows Formlarında 3B WPF Bileşik Denetimi Barındırma'](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)na bakın.

## <a name="adding-localizable-content"></a>Yerelleştirilebilir İçerik Ekleme

Ardından, bir Windows Forms etiket denetimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekler ve öğenin içeriğini yerelleştirilebilir bir dizeye ayarlarsınız.

### <a name="to-add-localizable-content"></a>Yerelleştirilebilir içerik eklemek için

1. **Solution**Explorer'da, WPF Designer'da açmak için **SimpleControl.xaml'a** çift tıklayın.

2. Aşağıdaki kodu kullanarak <xref:System.Windows.Controls.Button> denetimin içeriğini ayarlayın.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. **Solution**Explorer'da, Windows Forms Designer'da açmak için **Form1'e** çift tıklayın.

4. Forma etiket denetimi eklemek için **Araç Kutusunu** açın ve **Etiket'i** çift tıklatın. <xref:System.Windows.Forms.Control.Text%2A> Özelliğinin değerini ' `"Hello"`ye ayarlayın.

5. Uygulamayı oluşturmak ve çalıştırmak için **F5** tuşuna basın.

     Hem `SimpleControl` öğe hem de etiket denetimi **"Merhaba"** metnini görüntüler.

## <a name="enabling-localization"></a>Yerelleştirmeyi Etkinleştirme

Windows Forms Designer, uydu derlemesinde yerelleştirmeyi etkinleştirmek için ayarlar sağlar.

### <a name="to-enable-localization"></a>Yerelleştirmeyi etkinleştirmek için

1. **Solution Explorer'da,** Windows Forms Designer'da açmak için **Form1.cs** çift tıklatın.

2. **Özellikler** penceresinde, formun **Yerelleştirilebilir** özelliğinin değerini `true`.

3. **Özellikler** penceresinde, **Dil** özelliğinin değerini **İspanyolca (İspanya)** olarak ayarlayın.

4. Windows Forms Designer'da etiket denetimini seçin.

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Text%2A> özelliğin değerini . `"Hola"`

     Projeye Form1.es ES.resx adlı yeni bir kaynak dosyası eklendi.

6. **Çözüm Gezgini'nde,** **Form1.cs** sağ tıklatın ve Kod Düzenleyicisi'nde açmak için **Kodu Görüntüle'yi** tıklatın.

7. Aşağıdaki kodu, `Form1` `InitializeComponent`'' için çağrıdan önce oluşturucuya kopyalayın

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. **Çözüm Gezgini'nde,** **YerelleştirmeWpfInWf'i** sağ tıklatın ve **Project'i Boşalt'ı**tıklatın.

     Proje adı etiketlenir **(kullanılamaz)**.

9. Sağ tıklayın **YerelleştirmeWpfInWf**, ve **Yerelleştirme Edit WpfInWf.csproj**.

     Proje dosyası Kod Düzenleyicisi'nde açılır.

10. Aşağıdaki satırı proje dosyasındaki ilk `PropertyGroup` satıra kopyalayın.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Proje dosyasını kaydedin ve kapatın.

12. **Çözüm Gezgini'nde,** **YerelleştirmeWpfInWf'i** sağ tıklatın ve **Project'i Yeniden Yükle'yi**tıklatın.

## <a name="assigning-resource-identifiers"></a>Kaynak Tanımlayıcıları Atama

Kaynak tanımlayıcılarını kullanarak yerelleştirilebilir içeriğinizi kaynak derlemeleri ile eşleyebilirsiniz. MsBuild.exe `updateuid` uygulaması, seçeneği belirttiğiniz zaman kaynak tanımlayıcılarını otomatik olarak atar.

### <a name="to-assign-resource-identifiers"></a>Kaynak tanımlayıcıları atamak için

1. Başlat Menüsünden Visual Studio için Geliştirici Komut Komut Ustem'ini açın.

2. Kaynak tanımlayıcılarını yerelleştirilebilir içeriğinize atamak için aşağıdaki komutu kullanın.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. **Solution**Explorer'da, Code Editor'da açmak için **SimpleControl.xaml'a** çift tıklayın. Komutun `msbuild` tüm öğelere `Uid` öznitelik ekladığını göreceksiniz. Bu, kaynak tanımlayıcılarının atanması yoluyla yerelleştirmeyi kolaylaştırır.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Çözümü oluşturmak için **F6** tuşuna basın.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>LocBaml'ı Uydu Montajı Üretmek için kullanma

Yerelleştirilmiş içeriğiniz yalnızca kaynak uydu *derlemesinde*depolanır. İçeriğiniz için yerelleştirilmiş bir derleme oluşturmak için LocBaml.exe komut satırı aracını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanın.

### <a name="to-produce-a-satellite-assembly"></a>Uydu montajı üretmek için

1. LocBaml.exe'yi projenizin obj\Debug klasörüne kopyalayın. Daha fazla bilgi için [bkz.](how-to-localize-an-application.md)

2. Komut İstemi penceresinde, kaynak dizeleri geçici bir dosyaiçine ayıklamak için aşağıdaki komutu kullanın.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Visual Studio veya başka bir metin düzenleyicisi ile temp.csv dosyasını açın. Dizeyi `"Hello"` İspanyolca çevirisi `"Hola"`ile değiştirin.

4. temp.csv dosyasını kaydedin.

5. Yerelleştirilmiş kaynak dosyasını oluşturmak için aşağıdaki komutu kullanın.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     LocalizingWpfInWf.g.es-ES.resources dosyası obj\Debug klasöründe oluşturulur.

6. Yerelleştirilmiş uydu derlemesini oluşturmak için aşağıdaki komutu kullanın.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     LocalizingWpfInWf.resources.dll dosyası obj\Debug klasöründe oluşturulur.

7. YerelleştirmeWpfInWf.resources.dll dosyasını projenin bin\Debug\es-ES klasörüne kopyalayın. Varolan dosyayı değiştirin.

8. Projenizin bin\Debug klasöründe bulunan YerelleştirmeWpfInWf.exe'yi çalıştırın. Uygulamayı yeniden yapmayın veya uydu montajı üzerine yazılacaktır.

     Uygulama, İngilizce dizeleri yerine yerelleştirilmiş dizeleri gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Bir Uygulamayı Yerelleştirme](how-to-localize-an-application.md)
- [Walkthrough: Windows Formlarını Yerelleştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
