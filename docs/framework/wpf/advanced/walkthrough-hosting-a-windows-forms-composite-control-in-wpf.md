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
ms.openlocfilehash: 5868ee8c5b781d5af75349a5950f7e1e1680d74d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548918"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu olabilir en az yeniden daha etkili kodda bazıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerine baştan yeniden. Var olan Windows Forms denetimleri olduğunda en yaygın senaryodur. Bazı durumlarda, bile bu denetimleri için kaynak koduna erişim sahip olmayabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu tür denetimlerinde barındırmak için basit bir yordam sağlar bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Örneğin, kullanabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğu barındırırken, programlama için <xref:System.Windows.Forms.DataGridView> kontrol eder.  
  
 Bu kılavuzda veri girişi gerçekleştirmek için bir Windows Forms Bileşik Denetim barındıran bir uygulama aracılığıyla adımlar bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Bileşik Denetim DLL'de paketlenmiştir. Bu genel yordam daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu kılavuzda görünümünü ve işlevini neredeyse aynı olacak şekilde tasarlanmıştır [izlenecek yol: Windows Forms içerisinde WPF bileşik denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Barındırma senaryo tersine çevrildi birincil farktır.  
  
 İzlenecek yol iki bölüme ayrılmıştır. İlk bölüm, Windows Forms Bileşik denetimi uyarlamasını kısaca açıklanmaktadır. İkinci bölümü, bileşik denetimi barındırmak nasıl ayrıntılı olarak anlatılmaktadır bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, denetim olaylarını almasını ve denetimin özelliklerini erişebilirsiniz.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms Bileşik Denetim uygulama.  
  
-   WPF konak uygulamanın uygulama.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [bir Windows Forms Bileşik Denetimi WPF örnek barındırma](http://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-windows-forms-composite-control"></a>Windows Forms Bileşik denetimi uygulama  
 Bu örnekte kullanılan Windows Forms Bileşik Denetim basit veri girişi biçimidir. Bu form kullanıcının adı ve adresini alır ve bu bilgileri ana bilgisayara döndürmek için özel bir olay kullanır. Aşağıdaki çizimde işlenen denetimi göstermektedir.  
  
 ![Basit Windows Forms denetimi](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")  
Bileşik Windows Forms denetimi  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1.  Başlatma [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], açarak **yeni proje** iletişim kutusu.  
  
2.  Penceresi kategorisindeki seçmek **Windows Forms Denetim Kitaplığı** şablonu.  
  
3.  Yeni proje adı `MyControls`.  
  
4.  Konum için uygun şekilde adlandırılmış bir üst düzey klasör gibi belirtin `WpfHostingWindowsFormsControl`. Daha sonra bu klasörde konak uygulama sokar.  
  
5.  Tıklatın **Tamam** projesi oluşturmak için. Varsayılan proje adlı tek bir denetim içerir `UserControl1`.  
  
6.  Çözüm Gezgini'nde, yeniden adlandırma `UserControl1` için `MyControl1`.  
  
 Projeniz aşağıdaki sistem DLL'leri başvurular olması gerekir. Bu DLL'ler birini varsayılan olarak dahil edilmezse, bunları projeye ekleyin.  
  
-   Sistem  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Forma denetim ekleme  
 Forma denetim eklemek için:  
  
-   Açık `MyControl1` Tasarımcısı'nda.  
  
 Beş eklemek <xref:System.Windows.Forms.Label> denetimleri ve karşılık gelen <xref:System.Windows.Forms.TextBox> boyutlandırılmış ve Yukarıdaki çizimde, formdaki oldukları gibi düzenlenmiş denetimleri. Örnekte, <xref:System.Windows.Forms.TextBox> denetimleri adlandırılır:  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 İki eklemek <xref:System.Windows.Forms.Button> etiketli denetimleri **Tamam** ve **iptal**. Örnekte, düğme adlardır `btnOK` ve `btnCancel`sırasıyla.  
  
### <a name="implementing-the-supporting-code"></a>Destek kodunu uygulama  
 Formu kod görünümünde açın. Denetimin toplanan verileri kendi konağına özel yükselterek döndürür `OnButtonClick` olay. Verileri olay bağımsız değişken nesnesinde yer alır. Aşağıdaki kod, olay ve temsilci bildirimi gösterir.  
  
 Aşağıdaki kodu ekleyin `MyControl1` sınıfı.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 `MyControlEventArgs` Sınıfı ana bilgisayara döndürülecek bilgileri içerir.  
  
 Aşağıdaki sınıf forma ekleyin.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 Kullanıcı tıkladığında **Tamam** veya **iptal** düğmesini <xref:System.Windows.Forms.Control.Click> olay işleyicileri oluşturma bir `MyControlEventArgs` verileri içeren nesne ve başlatır `OnButtonClick` olay. İki işleyicinin arasındaki tek fark olay bağımsız değişkeninin olduğu `IsOK` özelliği. Bu özelliği, hangi düğmenin tıklandığını belirleme için ana sağlar. Ayarlanır `true` için **Tamam** düğmesi ve `false` için **iptal** düğmesi. Aşağıdaki kod iki düğmesi işleyicileri gösterir.  
  
 Aşağıdaki kodu ekleyin `MyControl1` sınıfı.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Derleme güçlü bir ad verip ve bütünleştirilmiş kod oluşturma  
 Bu derleme tarafından başvurulan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, güçlü bir adı olması gerekir. Güçlü bir ad oluşturmak için Sn.exe ile bir anahtar dosyası oluşturun ve projenize ekleyin.  
  
1.  Açık bir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] komut istemi. Bunu yapmak için tıklatın **Başlat** menüsüne ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**. Bir konsol penceresi özelleştirilmiş ortam değişkenleri ile başlatır.  
  
2.  Komut isteminde kullanın `cd` proje klasörünüzdeki Git komutu.  
  
3.  Aşağıdaki komutu çalıştırarak MyControls.snk adlı bir anahtar dosyası oluşturur.  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  Anahtar dosyası projenize eklemek için Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**. Proje Tasarımcısı'nda tıklatın **imzalama** sekmesine **derlemeyi imzalamak** onay kutusunu işaretleyin ve ardından anahtar dosyanızı göz atın.  
  
5.  Çözümü oluşturun. Yapı MyControls.dll adlı bir DLL oluşturur.  
  
## <a name="implementing-the-wpf-host-application"></a>WPF konak uygulamayı uygulama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulamanız tarafından kullanılan ana bilgisayar <xref:System.Windows.Forms.Integration.WindowsFormsHost> barındırmak için `MyControl1`. Uygulama tanıtıcıları `OnButtonClick` denetimden verileri almak için olay. Denetimin özelliklerinden bazıları değiştirebilmek için seçenek düğmeleri koleksiyonu da sahip [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Aşağıdaki çizimde tamamlanmış uygulamayı gösterir.  
  
 ![Bir denetim katıştırılmış bir WPF sayfasında](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")  
Tam uygulama denetimi gösteren WPF uygulamasında katıştırılmış  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1.  Açık [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]seçip **yeni proje**.  
  
2.  Penceresi kategorisindeki seçmek **WPF uygulaması** şablonu.
  
3.  Yeni proje adı `WpfHost`.  
  
4.  Konum için MyControls projeyi içeren aynı üst düzey klasörü belirtin.  
  
5.  Tıklatın **Tamam** projesi oluşturmak için.  
  
 İçeren DLL başvurular ekleyin gerekir `MyControl1` ve diğer derlemeler.  
  
1.  Çözüm Gezgini'nde proje adına sağ tıklayıp **Başvuru Ekle**.  
  
2.  Tıklatın **Gözat** sekmesini tıklatın ve MyControls.dll içeren klasöre göz atın. Bu kılavuz için bu klasör MyControls\bin\Debug'dır.  
  
3.  MyControls.dll seçin ve ardından **Tamam**.  
  
4.  WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.  
  
### <a name="implementing-the-basic-layout"></a>Temel düzeni uygulama  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Ana uygulama MainWindow.xaml içinde uygulanır. Bu dosyayı içeren [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] düzenini tanımlar ve barındıran Windows Forms denetiminde biçimlendirme. Uygulama, üç bölgeye ayrılmıştır:  
  
-   **Denetim özelliklerini** paneli denetimden çeşitli özelliklerini değiştirmek için kullanabileceğiniz seçenek düğmeleri koleksiyonunu içerir.  
  
-   **Denetim verileri** birkaç içeren paneli <xref:System.Windows.Controls.TextBlock> verileri görüntülemek öğeleri barındırılan denetiminden döndürdü.  
  
-   Barındırılan denetimin kendisi.  
  
 Temel düzeni aşağıdaki XAML'de gösterilir. Gerekli biçimlendirme ana bilgisayara `MyControl1` Bu örnekte atlanır, ancak daha sonra açıklanacaktır.  
  
 MainWindow.xaml XAML'de aşağıdakiyle değiştirin. Visual Basic kullanıyorsanız, sınıf için değiştirme `x:Class="MainWindow"`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 İlk <xref:System.Windows.Controls.StackPanel> öğesi içeren birkaç kümesi <xref:System.Windows.Controls.RadioButton> denetimden çeşitli varsayılan özelliklerini değiştirmek etkinleştirmeniz kontrol eder. Tarafından izlenen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, hangi ana bilgisayarların `MyControl1`. En son <xref:System.Windows.Controls.StackPanel> öğesi içeren birkaç <xref:System.Windows.Controls.TextBlock> barındırılan denetim tarafından döndürülen verileri görüntüleyen öğeleri. Öğeleri sıralama ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarını boşluklar veya bozulma olmadan bu denetimden penceresine ekleme.  
  
#### <a name="hosting-the-control"></a>Denetimi barındırma  
 Önceki XAML aşağıdaki düzenlenmiş sürümü için gerekli olan öğeleri odaklanır ana bilgisayara `MyControl1`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 `xmlns` Ad alanı eşleme özniteliği için bir başvuru oluşturur `MyControls` barındırılan denetimi içeren ad alanı. Bu eşlemeyi temsil eden sağlar `MyControl1` içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak `<mcl:MyControl1>`.  
  
 XAML'de iki öğe barındırmayı işler:  
  
-   `WindowsFormsHost` temsil eden <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir Windows Forms denetimi barındırma olanak tanıyan öğe bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
-   `mcl:MyControl1`, temsil eden `MyControl1`, eklenen <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt koleksiyonu. Sonuç olarak, bu Windows Forms denetimini bir parçası olarak işlenir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencere ve iletişim kurabilen uygulama denetiminden.  
  
### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyası uygulama  
 Arka plan kodu dosyasını MainWindow.xaml.vb veya MainWindow.xaml.cs, işlevselliğini uygulayan yordam kodunu içeren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] önceki bölümde açıklanan. Birincil görevler şunlardır:  
  
-   Bir olay işleyicisi ekleme `MyControl1`'s `OnButtonClick` olay.  
  
-   Çeşitli özelliklerini değiştirme `MyControl1`bağlı olarak seçenek düğmeleri koleksiyonunu nasıl ayarlanır.  
  
-   Verileri görüntüleme denetim tarafından toplanır.  
  
#### <a name="initializing-the-application"></a>Uygulama başlatma  
 Bir pencere için olay işleyicisini başlatma kodu bulunan <xref:System.Windows.FrameworkElement.Loaded> olay ve bir olay işleyicisi denetimin ekler `OnButtonClick` olay.  
  
 MainWindow.xaml.vb veya MainWindow.xaml.cs, aşağıdaki kodu ekleyin `MainWindow` sınıfı.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 Çünkü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden eklenen ele alınan `MyControl1` için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğe koleksiyonunu çevirebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> başvuru almak için `MyControl1`. Bir olay işleyicisi eklemek için bu başvuru sonra kullanabileceğiniz `OnButtonClick`.  
  
 Denetim kendisine başvuru sağlamanın yanı sıra <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamadan işleyebileceğiniz denetimin özelliklerini sayısını kullanıma sunar. Başlangıç kodu özel genel değişkenler uygulama daha sonra kullanmak için bu değerleri atar.  
  
 Türler kolayca erişebilmeniz `MyControls` DLL, aşağıdakileri ekleyin `Imports` veya `using` dosyanın en üstüne ifadesine.  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a>OnButtonClick olayını işleme  
 `MyControl1` başlatır `OnButtonClick` kullanıcı ya da denetim düğmesini tıklattığında olay.  
  
 Aşağıdaki kodu ekleyin `MainWindow` sınıfı.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 Metin kutularındaki veri paketlenmiştir `MyControlEventArgs` nesnesi. Kullanıcı tıklarsa **Tamam** düğmesi olay işleyicisi verileri ayıklar ve panelinde görüntüler `MyControl1`.  
  
#### <a name="modifying-the-controls-properties"></a>Denetimin özelliklerini değiştirme  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi birkaç barındırılan denetimin varsayılan özelliklerini gösterir. Sonuç olarak, uygulamanızın stil daha yakından eşleşecek şekilde denetiminin görünümünü değiştirebilirsiniz. Sol bölmedeki seçenek düğmeleri kümesi birkaç renk ve yazı tipi özelliklerini değiştirmek kullanıcının etkinleştirir. Her düğme için bir işleyici olarak ayarlanmış <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kullanıcının seçenek düğmesi seçimlerini algılayan ve karşılık gelen özelliği denetimde değiştiren olay.  
  
 Aşağıdaki kodu ekleyin `MainWindow` sınıfı.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Derleme ve uygulamayı çalıştırın. Windows Forms Bileşik denetiminde biraz metin ekleyin ve ardından **Tamam**. Metin etiketler görünür. Denetim etkisini görmek için farklı radyo düğmelerini tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
