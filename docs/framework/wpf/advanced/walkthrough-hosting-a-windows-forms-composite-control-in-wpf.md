---
title: "İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: e30b1bb45cc2dae2783cddf54dda400b742cdf73
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920323"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodda önemli bir yatırımınız olduğunda, sıfırdan yazmak yerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanızda bu kodların en az bir kısmını yeniden kullanmak daha etkili olabilir. En yaygın senaryo, Windows Forms denetimlerinizi var. Bazı durumlarda, bu denetimlerin kaynak koduna bile erişiminiz olmayabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu denetimleri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasında barındırmak için kolay bir yordam sağlar. Örneğin, özelleştirilmiş <xref:System.Windows.Forms.DataGridView> denetimlerinizi barındırırken birçok programlama için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanabilirsiniz.  
  
 Bu izlenecek yol, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasında veri girişi gerçekleştirmek üzere Windows Forms Bileşik bir denetim barındıran bir uygulamada size kılavuzluk ediyor. Bileşik denetim bir DLL içinde paketlenmiştir. Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu izlenecek yol, görünüm ve işlevlerle neredeyse özdeş olacak şekilde tasarlanmıştır [: WINDOWS Forms WPF bileşik denetimini barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Birincil fark, barındırma senaryosunun tersine çevrilme olur.  
  
 İzlenecek yol iki bölüme ayrılmıştır. İlk bölüm Windows Forms Bileşik denetimin uygulamasını kısaca açıklar. İkinci bölüm, bileşik denetimin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamada nasıl barındırılacağını, denetimden olayları nasıl alacağını ve denetimin bazı özelliklerine nasıl erişebileceğini açıklamaktadır.  
  
 Bu izlenecek yolda gösterilen görevler şunlardır:  
  
- Windows Forms Bileşik denetimi uygulama.  
  
- WPF konak uygulamasını uygulama.  
  
 Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms Bileşik denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Prerequisites  

Bu yönergeyi tamamlamak için Visual Studio gerekir.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Windows Forms Bileşik denetimi uygulama  
 Bu örnekte kullanılan Windows Forms Bileşik denetim basit bir veri girişi biçimidir. Bu form kullanıcının adını ve adresini alır ve bu bilgileri konağa döndürmek için özel bir olay kullanır. Aşağıdaki çizimde işlenmiş denetim gösterilmektedir.  

 Aşağıdaki görüntüde Windows Forms Bileşik bir denetim gösterilmektedir:  

 ![Basit bir Windows Forms denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Visual Studio 'yu başlatın ve **Yeni proje** iletişim kutusunu açın.  
  
2. Pencere kategorisinde **Windows Forms denetim kitaplığı** şablonunu seçin.  
  
3. Yeni proje `MyControls`adlandırın.  
  
4. Konum için `WpfHostingWindowsFormsControl`gibi kolay adlandırılmış bir üst düzey klasör belirtin. Daha sonra, ana bilgisayar uygulamasını bu klasöre yerleştirebilirsiniz.  
  
5. Projeyi oluşturmak için **Tamam** ' ı tıklatın. Varsayılan proje, `UserControl1`adlı tek bir denetim içerir.  
  
6. Çözüm Gezgini `UserControl1` `MyControl1`olarak yeniden adlandırın.  
  
 Projenizin aşağıdaki sistem dll 'Lerine başvuruları olmalıdır. Bu dll 'Lerden herhangi biri varsayılan olarak dahil edilmez, bunları projeye ekleyin.  
  
- Sistem  
  
- System.Data  
  
- System. Drawing  
  
- System. Windows. Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Forma denetim ekleme  
 Forma denetim eklemek için:  
  
- Tasarımcıda `MyControl1` açın.  
  
 Form üzerinde, önceki çizimde oldukları gibi boyutlandırılmış ve düzenlenmiş beş <xref:System.Windows.Forms.Label> denetimi ve bunlara karşılık gelen <xref:System.Windows.Forms.TextBox> denetimlerini ekleyin. Örnekte <xref:System.Windows.Forms.TextBox> denetimleri şu şekilde adlandırılır:  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 **Tamam** ve **iptal**etiketli iki <xref:System.Windows.Forms.Button> denetimi ekleyin. Örnekte, düğme adları sırasıyla `btnOK` ve `btnCancel`.  
  
### <a name="implementing-the-supporting-code"></a>Destekleyici kodu uygulama  
 Formu kod görünümünde açın. Denetim, toplanan verileri özel `OnButtonClick` olayını yükselterek ana bilgisayarına döndürür. Veriler, olay bağımsız değişkeni nesnesinde yer alır. Aşağıdaki kod, olay ve temsilci bildirimini gösterir.  
  
 Aşağıdaki kodu `MyControl1` sınıfına ekleyin.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs` sınıfı, konağa döndürülecek bilgileri içerir.

 Aşağıdaki sınıfı forma ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında, <xref:System.Windows.Forms.Control.Click> olay işleyicileri verileri içeren ve `OnButtonClick` olayını başlatan bir `MyControlEventArgs` nesnesi oluşturur. İki işleyici arasındaki tek fark, olay bağımsız değişkeninin `IsOK` özelliğidir. Bu özellik, ana bilgisayarın hangi düğmeye tıklandığını belirlemesine olanak sağlar. **Tamam** düğmesi için `true` olarak ayarlanır ve **iptal** düğmesi için `false`. Aşağıdaki kod iki düğme işleyicisini gösterir.

 Aşağıdaki kodu `MyControl1` sınıfına ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Derlemeye tanımlayıcı bir ad verme ve derlemeyi oluşturma
 Bu derlemeye bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması tarafından başvurulması için, bir tanımlayıcı adı olması gerekir. Güçlü bir ad oluşturmak için sn. exe ile bir anahtar dosyası oluşturun ve bunu projenize ekleyin.

1. Bir Visual Studio komut istemi açın. Bunu yapmak için **Başlat** menüsüne tıklayın ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**' ni seçin. Bu, özelleştirilmiş ortam değişkenleriyle bir konsol penceresi başlatır.

2. Komut isteminde, proje klasörünüze gitmek için `cd` komutunu kullanın.

3. Aşağıdaki komutu çalıştırarak MyControls. snk adlı bir anahtar dosya oluşturun.

    ```console
    Sn.exe -k MyControls.snk
    ```

4. Projenize anahtar dosyasını dahil etmek için Çözüm Gezgini ' de proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın. Proje tasarımcısında **imzalama** sekmesine tıklayın, **derlemeyi imzala** onay kutusunu seçin ve ardından anahtar dosyanıza göz atın.

5. Çözümü oluşturun. Derleme MyControls. dll adlı bir DLL üretecektir.

## <a name="implementing-the-wpf-host-application"></a>WPF ana bilgisayar uygulamasını uygulama
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana bilgisayar uygulaması `MyControl1`barındırmak için <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimini kullanır. Uygulama, denetimdeki verileri almak için `OnButtonClick` olayını işler. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamadan bazı denetim özelliklerini değiştirmenizi sağlayan bir seçenek düğmeleri koleksiyonuna sahiptir. Aşağıdaki çizimde tamamlanmış uygulama gösterilmektedir.

Aşağıdaki görüntüde WPF uygulamasına katıştırılmış denetim dahil olmak üzere tüm uygulama gösterilmektedir:

 ![WPF sayfasında gömülü bir denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Projeyi Oluşturma
 Projeyi başlatmak için:

1. Visual Studio 'yu açın ve **Yeni proje**' yi seçin.

2. Pencere kategorisinde, **WPF uygulama** şablonunu seçin.

3. Yeni proje `WpfHost`adlandırın.

4. Konum için, MyControls projesini içeren en üst düzey klasörü belirtin.

5. Projeyi oluşturmak için **Tamam** ' ı tıklatın.

 Ayrıca, `MyControl1` ve diğer derlemeleri içeren DLL 'ye başvurular eklemeniz gerekir.

1. Çözüm Gezgini ' de proje adına sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. **Araştır** sekmesine tıklayın ve MyControls. dll dosyasını içeren klasöre gidin. Bu izlenecek yol için, bu klasör Mycontrols\bin\debugklasörüdür.

3. MyControls. dll ' yi seçin ve ardından **Tamam**' a tıklayın.

4. WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

### <a name="implementing-the-basic-layout"></a>Temel düzeni uygulama
 Konak uygulamasının [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] MainWindow. xaml ' de uygulanır. Bu dosya, düzeni tanımlayan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirme içerir ve Windows Forms denetimini barındırır. Uygulama üç bölgeye ayrılmıştır:

- Barındırılan denetimin çeşitli özelliklerini değiştirmek için kullanabileceğiniz seçenek düğmelerinin koleksiyonunu içeren **denetim özellikleri** paneli.

- Barındırılan denetimden döndürülen verileri görüntüleyen birkaç <xref:System.Windows.Controls.TextBlock> öğesi içeren denetim masası 'ndaki **veriler** .

- Barındırılan denetimin kendisi.

 Temel düzen aşağıdaki XAML 'de gösterilmiştir. `MyControl1` barındırmak için gereken biçimlendirme bu örnekte atlanır, ancak daha sonra ele alınacaktır.

 MainWindow. xaml içindeki XAML 'yi aşağıdakiler ile değiştirin. Visual Basic kullanıyorsanız, sınıfı `x:Class="MainWindow"`olarak değiştirin.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 İlk <xref:System.Windows.Controls.StackPanel> öğesi, barındırılan denetimin çeşitli varsayılan özelliklerini değiştirmenize olanak sağlayan birkaç <xref:System.Windows.Controls.RadioButton> denetim kümesi içerir. Bundan sonra `MyControl1`barındıran <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Son <xref:System.Windows.Controls.StackPanel> öğesi barındırılan denetim tarafından döndürülen verileri görüntüleyen birkaç <xref:System.Windows.Controls.TextBlock> öğesi içerir. Öğelerin ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarının sıralaması barındırılan denetimi, boşluk veya deformasyon olmadan pencereye katıştırır.

#### <a name="hosting-the-control"></a>Denetimi barındırma
 Önceki XAML 'nin aşağıdaki düzenlenmiş sürümü `MyControl1`barındırmak için gereken öğelere odaklanır.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `xmlns` ad alanı eşleme özniteliği barındırılan denetimi içeren `MyControls` ad alanına bir başvuru oluşturur. Bu eşleme, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `MyControl1` `<mcl:MyControl1>`olarak temsil etmenizi sağlar.

 XAML 'deki iki öğe barındırmayı işleme:

- `WindowsFormsHost`, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasında Windows Forms denetimini barındırmanızı sağlayan <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini temsil eder.

- `MyControl1`temsil eden `mcl:MyControl1`, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin alt koleksiyonuna eklenir. Sonuç olarak, bu Windows Forms denetimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] penceresinin bir parçası olarak işlenir ve uygulamadan denetimle iletişim kurabilirsiniz.

### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyasını uygulama
 MainWindow. xaml. vb veya MainWindow.xaml.cs arka plan kod dosyası, önceki bölümde açıklanan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] işlevlerini uygulayan yordamsal kodu içerir. Birincil görevler şunlardır:

- `MyControl1``OnButtonClick` olayına bir olay işleyicisi iliştirme.

- Seçenek düğmelerinin toplanması temelinde `MyControl1`çeşitli özelliklerini değiştirme.

- Denetim tarafından toplanan verileri görüntüleme.

#### <a name="initializing-the-application"></a>Uygulamayı başlatma
 Başlatma kodu, pencerenin <xref:System.Windows.FrameworkElement.Loaded> olayı için bir olay işleyicisinde bulunur ve denetimin `OnButtonClick` olayına bir olay işleyicisi ekler.

 MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, `MainWindow` sınıfına aşağıdaki kodu ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Daha önce açıklanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğe koleksiyonuna `MyControl1` eklendiğinden, <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> başvurusunu almak için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin `MyControl1`dönüştürebilirsiniz. Daha sonra bu başvuruyu, `OnButtonClick`bir olay işleyicisi iliştirmek için kullanabilirsiniz.

 <xref:System.Windows.Forms.Integration.WindowsFormsHost>, denetimin kendine başvuru sağlamaya ek olarak, uygulamanın içinden işleyebileceğiniz bir dizi denetimin özelliklerini kullanıma sunar. Başlatma kodu, bu değerleri uygulamada daha sonra kullanılmak üzere özel genel değişkenlere atar.

 `MyControls` DLL 'deki türlere kolayca erişebilmeniz için, dosyanın en üstüne aşağıdaki `Imports` veya `using` ifadesini ekleyin.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>OnButtonClick olayını işleme
 `MyControl1`, Kullanıcı denetimin düğmelerinden birini tıkladığında `OnButtonClick` olayını başlatır.

 Aşağıdaki kodu `MainWindow` sınıfına ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Metin kutularındaki veriler `MyControlEventArgs` nesnesine paketlenmiştir. Kullanıcı **Tamam** düğmesine tıkladığında, olay işleyicisi verileri ayıklar ve aşağıdaki panelde görüntüler `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Denetimin özelliklerini değiştirme
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, barındırılan denetimin varsayılan özelliklerinden birkaçını ortaya çıkarır. Sonuç olarak, denetimin görünümünü uygulamanızın stiliyle daha yakından eşleşecek şekilde değiştirebilirsiniz. Sol paneldeki seçenek düğmelerinin kümeleri, kullanıcının çeşitli renk ve yazı tipi özelliklerini değiştirmesini sağlar. Her düğme kümesi, kullanıcının seçenek düğmesi seçimlerini algılayan ve denetimdeki ilgili özelliği değiştiren <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir işleyiciye sahiptir.

 Aşağıdaki kodu `MainWindow` sınıfına ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Uygulamayı derleyin ve çalıştırın. Windows Forms Bileşik denetimine bir metin ekleyin ve ardından **Tamam**' a tıklayın. Metin, etiketlerde görüntülenir. Denetimdeki etkiyi görmek için farklı radyo düğmelerine tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
