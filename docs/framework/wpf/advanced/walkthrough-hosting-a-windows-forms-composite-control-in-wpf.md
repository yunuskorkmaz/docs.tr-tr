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
ms.openlocfilehash: f9e0477b2c186ea9b23886f460caf965a5db0244
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174362"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu olabilir en az yeniden daha etkili kodda bazıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerine baştan yeniden. Mevcut Windows Forms denetimleri olduğunda en yaygın senaryodur. Bazı durumlarda, bile bu denetimleri için kaynak koduna erişim olmayabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi denetimleri barındırma için basit bir yordam sağlar bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Örneğin, kullanabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğu barındırırken, programlama için <xref:System.Windows.Forms.DataGridView> kontrol eder.  
  
 Bu izlenecek yolda veri girişi gerçekleştirmek için bir Windows Forms bileşik denetimini barındıran bir uygulama aracılığıyla adımları bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Bileşik Denetim DLL içinde paketlenmiştir. Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu izlenecek yol Görünüm ve işlevselliği için neredeyse aynı olacak şekilde tasarlanan [izlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Barındırma senaryo tersine, birincil farktır.  
  
 İzlenecek yol, iki bölüme ayrılmıştır. İlk bölüm, Windows Forms bileşik denetimini uygulamasını kısaca açıklanmaktadır. İkinci bölüm içinde bileşik denetimini barındırmak nasıl ayrıntılı olarak ele alınmaktadır bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama denetim olaylarını almak ve denetim özelliklerini bazılarına erişmek.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms bileşik denetimini uygulama.  
  
-   WPF ana bilgisayar uygulaması oluşturma.  
  
 Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [bir WPF Örneği'nde Windows Forms bileşik denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Windows Forms bileşik denetimini uygulama  
 Bu örnekte kullanılan Windows Forms bileşik denetimini basit veri girişi biçimidir. Bu form kullanıcının adı ve adresi alır ve ana bilgisayar için bu bilgileri döndürmek için bir özel olay kullanır. İşlenen denetimi aşağıda gösterilmektedir.  

 Aşağıdaki resimde, bir Windows Forms bileşik denetimini gösterir:  

 ![Basit bir Windows Forms denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Proje başlatmak için:  
  
1.  Başlatma [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]açın **yeni proje** iletişim kutusu.  
  
2.  Pencere kategorisinde seçin **Windows Forms Denetim Kitaplığı** şablonu.  
  
3.  Yeni proje adını `MyControls`.  
  
4.  Konum için bir kolayca adlandırılmış üst düzey klasör gibi belirtin `WpfHostingWindowsFormsControl`. Daha sonra ana bilgisayar uygulaması bu klasöre koyacaktır.  
  
5.  Tıklayın **Tamam** projeyi oluşturmak için. Varsayılan proje adlı tek bir denetim içeren `UserControl1`.  
  
6.  Çözüm Gezgini'nde, yeniden adlandırma `UserControl1` için `MyControl1`.  
  
 Projenize aşağıdaki sistem DLL'lerini başvuruları olması gerekir. Bu DLL'leri birini varsayılan olarak dahil edilmez, bunları projeye ekleyin.  
  
-   Sistem  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Formu için denetimler ekleme  
 Formu için denetimler eklemek için:  
  
-   Açık `MyControl1` Tasarımcısı'nda.  
  
 Beş ekleme <xref:System.Windows.Forms.Label> denetimleri ve bunlara karşılık gelen <xref:System.Windows.Forms.TextBox> denetimleri, boyutu ve formdaki yukarıdaki çizimin olduğu gibi düzenlenir. Örnekte, <xref:System.Windows.Forms.TextBox> denetimleri adlandırılır:  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 İki ekleme <xref:System.Windows.Forms.Button> etiketli denetimler **Tamam** ve **iptal**. Bu örnekte düğme adlarıdır `btnOK` ve `btnCancel`sırasıyla.  
  
### <a name="implementing-the-supporting-code"></a>Destek kodu uygulama  
 Formun kod Görünümü'nde açın. Ana bilgisayar için toplanan verileri özel yükselterek denetimini döndürür `OnButtonClick` olay. Verileri olay bağımsız değişkeni nesnesinde yer alır. Aşağıdaki kod, olay ve temsilci bildirimini gösterir.  
  
 Aşağıdaki kodu ekleyin `MyControl1` sınıfı.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs` Sınıfı konağa döndürülmesi gereken bilgileri içerir.

 Aşağıdaki sınıf formuna ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Kullanıcı tıkladığında **Tamam** veya **iptal** düğmesi <xref:System.Windows.Forms.Control.Click> olay işleyicileri oluşturma bir `MyControlEventArgs` veri içeren nesne ve başlatır `OnButtonClick` olay. Olay bağımsız değişkenin iki işleyiciler arasındaki tek fark, `IsOK` özelliği. Bu özellik ana bilgisayarın hangi düğmesine tıklandığını belirleme sağlar. Ayarlanmış `true` için **Tamam** düğmesi ve `false` için **iptal** düğmesi. Aşağıdaki kod, iki düğmesi işleyicileri gösterir.

 Aşağıdaki kodu ekleyin `MyControl1` sınıfı.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Derlemeyi güçlü bir isim verilmesi ve bütünleştirilmiş kod oluşturma
 Tarafından başvurulabilmesi derlemenin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, sağlam bir adı olmalıdır. Güçlü bir ad oluşturmak için bir anahtar dosyası ile Sn.exe oluşturun ve projenize ekleyin.

1.  Açık bir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] komut istemi. Bunu yapmak için tıklatın **Başlat** menüsüne ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**. Bu, özel ortam değişkenleriyle bir konsol penceresi açılır.

2.  Komut isteminde kullanmak `cd` proje klasörünüzün Git komutu.

3.  Aşağıdaki komutu çalıştırarak MyControls.snk adlı bir anahtar dosyası oluşturur.

    ```
    Sn.exe -k MyControls.snk
    ```

4.  Anahtar dosyası projenize eklemek için Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**. Proje Tasarımcısı'nda tıklatın **imzalama** sekmesinde **derlemeyi imzalamayı** onay kutusunu işaretleyin ve ardından, anahtar dosyasına gidin.

5.  Çözümü oluşturun. Derleme MyControls.dll adlı bir DLL oluşturur.

## <a name="implementing-the-wpf-host-application"></a>WPF ana bilgisayar uygulaması uygulama
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulamanız tarafından kullanılan ana <xref:System.Windows.Forms.Integration.WindowsFormsHost> barındırmak için `MyControl1`. Uygulama işleyen `OnButtonClick` denetimden verileri almak için olay. Ayrıca denetimin özelliklerinden bazıları değiştirebilmek için seçenek düğmeleri koleksiyonu vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Aşağıdaki resimde tamamlanmış uygulama gösterilir.

Aşağıdaki görüntüde, WPF uygulamasında katıştırılmış denetime dahil olmak üzere tüm uygulamanın gösterilmektedir:

 ![Bir denetimi gösteren ekran görüntüsü, bir WPF sayfasındaki katıştırılmış.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Projeyi Oluşturma
 Proje başlatmak için:

1.  Açık [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]seçip **yeni proje**.

2.  Pencere kategorisinde seçin **WPF uygulaması** şablonu.

3.  Yeni proje adını `WpfHost`.

4.  Konum için MyControls projesini içeren aynı üst düzey klasörü belirtin.

5.  Tıklayın **Tamam** projeyi oluşturmak için.

 Ayrıca içeren DLL başvuruları eklemek gereken `MyControl1` ve diğer derlemeler.

1.  Çözüm Gezgini'nde proje adına sağ tıklayıp **Başvuru Ekle**.

2.  Tıklayın **Gözat** sekmesini tıklatıp MyControls.dll içeren klasöre göz atın. Bu kılavuz için bu klasör MyControls\bin\Debug'dır.

3.  MyControls.dll seçin ve ardından **Tamam**.

4.  WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

### <a name="implementing-the-basic-layout"></a>Temel düzeni uygulama
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Ana bilgisayarının içinde MainWindow.xaml uygulama uygulanır. Bu dosyayı içeren [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] düzenini tanımlar ve Windows Forms denetimi barındıran biçimlendirmesi. Uygulamanın üç bölgelere ayrılmıştır:

-   **Denetim özelliklerini** paneli denetimden çeşitli özelliklerini değiştirmek için kullanabileceğiniz bir seçenek düğmeleri koleksiyonunu içerir.

-   **Denetiminden veri** paneli birkaç içerir <xref:System.Windows.Controls.TextBlock> verileri görüntüleyen öğeleri barındırılan denetiminden döndürdü.

-   Barındırılan denetim.

 Aşağıdaki XAML içinde temel düzen gösterilmektedir. Gerekli biçimlendirme konağa `MyControl1` Bu örnekte atlanmıştır, ancak daha sonra açıklanacaktır.

 XAML içinde MainWindow.xaml aşağıdakiyle değiştirin. Visual Basic kullanıyorsanız, sınıfa değiştirme `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 İlk <xref:System.Windows.Controls.StackPanel> öğeyi içeren birkaç kümesi <xref:System.Windows.Controls.RadioButton> denetimden çeşitli varsayılan özelliklerini değiştirmenize olanak sağlayan denetimler. Tarafından izlenen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, hangi konakların `MyControl1`. En son <xref:System.Windows.Controls.StackPanel> öğeyi içeren birkaç <xref:System.Windows.Controls.TextBlock> barındırılan denetim tarafından döndürülen verileri görüntüleyen öğeleri. Öğeleri sıralama ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarını boşluklar veya bozulma ile bu denetimden penceresine ekleme.

#### <a name="hosting-the-control"></a>Denetimi barındırma
 Önceki XAML aşağıdaki düzenlenmiş sürümü gereken öğeleri üzerinde odaklanır konağa `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `xmlns` Ad alanı eşleme özniteliği için bir başvuru oluşturur `MyControls` barındırılan denetimi içeren ad alanı. Bu eşlemeyi temsil sağlar `MyControl1` içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak `<mcl:MyControl1>`.

 XAML içinde iki öğe barındırma işler:

-   `WindowsFormsHost` temsil eden <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir Windows Forms denetiminde barındırmanıza olanak sağlayan öğe bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.

-   `mcl:MyControl1`, temsil eden `MyControl1`, eklenen <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt koleksiyonu. Sonuç olarak, bu Windows Forms denetimini bir parçası olarak işlenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencere ve uygulama denetimi ile kurabilir.

### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyası uygulama
 İşlevselliğini uygular yordam kodu MainWindow.xaml.vb veya MainWindow.xaml.cs, arka plan kod dosyasını içeren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] önceki bölümde açıklanan. Birincil görevler şunlardır:

-   Bir olay işleyici ekleme `MyControl1`'s `OnButtonClick` olay.

-   Çeşitli özelliklerini değiştirerek `MyControl1`seçeneği düğmelerinin koleksiyonunu nasıl ayarlanacağını göre.

-   Verileri görüntüleme denetim tarafından toplanır.

#### <a name="initializing-the-application"></a>Uygulamayı başlatma
 Başlatma kodu pencere için bir olay işleyicisi içindeki <xref:System.Windows.FrameworkElement.Loaded> olay ve denetim için bir olay işleyicisi ekler `OnButtonClick` olay.

 MainWindow.xaml.vb veya MainWindow.xaml.cs seçeneğinde, aşağıdaki kodu ekleyin `MainWindow` sınıfı.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Çünkü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden eklenen ele alınan `MyControl1` için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğe koleksiyonuna çevirebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> başvuru almak için `MyControl1`. Bir olay işleyicisi eklemek için bu başvuru sonra kullanabileceğiniz `OnButtonClick`.

 Denetim kendisine bir başvuru sağlamanın yanı sıra <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamadan değiştirebileceğiniz denetimin özelliklerini sayısını kullanıma sunar. Başlatma kodunu uygulama daha sonra kullanmak için özel genel değişkenler bu değerleri atar.

 Türlerini kolayca erişebilmeleri `MyControls` DLL, aşağıdaki `Imports` veya `using` deyimini dosyanın en üstüne.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>OnButtonClick olayını işleme
 `MyControl1` başlatır `OnButtonClick` kullanıcı herhangi bir denetimin düğmesini tıkladığında bir olay.

 Aşağıdaki kodu ekleyin `MainWindow` sınıfı.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Metin kutularına veri paketlenmiştir `MyControlEventArgs` nesne. Kullanıcı tıklarsa **Tamam** düğmesi olay işleyicisi, verileri ayıklayan ve panelinde görüntüler `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Denetimin özelliklerini değiştirme
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi birkaç barındırılan denetimin varsayılan özelliklerini gösterir. Sonuç olarak, uygulamanızı daha yakından ayarlamalar denetiminin görünümünü değiştirebilirsiniz. Seçenek düğmeleri sol bölmede kümesi birkaç rengini ve yazı tipi özelliklerini değiştirmek kullanıcının etkinleştirir. Her bir düğmeler kümesi için bir işleyici sahip <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kullanıcının seçenek düğmesi seçimlerini algılar ve karşılık gelen özelliği denetimde değiştiren olay.

 Aşağıdaki kodu ekleyin `MainWindow` sınıfı.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Derleme ve uygulamayı çalıştırın. Windows Forms bileşik denetimini içinde metin ekleyin ve ardından **Tamam**. Metin etiketler görünür. Farklı radyo düğmeleri, denetimin üzerindeki etkisini görmek için tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF içinde Windows Forms Denetimi Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
