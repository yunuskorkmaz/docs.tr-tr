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
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991880"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, kod içinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] önemli bir yatırımınız olduğunda, sıfırdan yazmak yerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanızda bu kodun en az bir kısmını yeniden kullanmak daha etkili olabilir. En yaygın senaryo, Windows Forms denetimlerinizi var. Bazı durumlarda, bu denetimlerin kaynak koduna bile erişiminiz olmayabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada bu denetimleri barındırmak için kolay bir yordam sağlar. Örneğin, özelleştirilmiş <xref:System.Windows.Forms.DataGridView> denetimlerinizi barındırırken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birçok programlama için kullanabilirsiniz.  
  
 Bu izlenecek yol, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada veri girişi gerçekleştirmek üzere Windows Forms Bileşik denetim barındıran bir uygulamada size kılavuzluk ediyor. Bileşik denetim bir DLL içinde paketlenmiştir. Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu izlenecek yol, görünümü ve işlevselliği [gözden geçirmede neredeyse özdeş olacak şekilde tasarlanmıştır: Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)Içinde WPF bileşik denetimi barındırma. Birincil fark, barındırma senaryosunun tersine çevrilme olur.  
  
 İzlenecek yol iki bölüme ayrılmıştır. İlk bölüm Windows Forms Bileşik denetimin uygulamasını kısaca açıklar. İkinci bölümde, bileşik denetimin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada nasıl barındırılabileceği, denetimden olayların nasıl alınacağı ve denetimin özelliklerinden bazılarına erişme hakkında ayrıntılı bilgi yer almaktadır.  
  
 Bu izlenecek yolda gösterilen görevler şunlardır:  
  
- Windows Forms Bileşik denetimi uygulama.  
  
- WPF konak uygulamasını uygulama.  
  
 Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms Bileşik denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu yönergeyi tamamlamak için Visual Studio gerekir.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Windows Forms Bileşik denetimi uygulama  
 Bu örnekte kullanılan Windows Forms Bileşik denetim basit bir veri girişi biçimidir. Bu form kullanıcının adını ve adresini alır ve bu bilgileri konağa döndürmek için özel bir olay kullanır. Aşağıdaki çizimde işlenmiş denetim gösterilmektedir.  

 Aşağıdaki görüntüde Windows Forms Bileşik bir denetim gösterilmektedir:  

 ![Basit bir Windows Forms denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Başlatın [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ve **Yeni proje** iletişim kutusunu açın.  
  
2. Pencere kategorisinde **Windows Forms denetim kitaplığı** şablonunu seçin.  
  
3. Yeni projeyi `MyControls`adlandırın.  
  
4. Konum için, gibi kolay adlandırılmış bir üst düzey klasör `WpfHostingWindowsFormsControl`belirtin. Daha sonra, ana bilgisayar uygulamasını bu klasöre yerleştirebilirsiniz.  
  
5. Projeyi oluşturmak için **Tamam** ' ı tıklatın. Varsayılan proje adlı `UserControl1`tek bir denetim içerir.  
  
6. Çözüm Gezgini ' de, `UserControl1` olarak `MyControl1`yeniden adlandırın.  
  
 Projenizin aşağıdaki sistem dll 'Lerine başvuruları olmalıdır. Bu dll 'Lerden herhangi biri varsayılan olarak dahil edilmez, bunları projeye ekleyin.  
  
- Sistem  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Forma denetim ekleme  
 Forma denetim eklemek için:  
  
- Tasarımcıda `MyControl1` açın.  
  
 Formda, <xref:System.Windows.Forms.Label> önceki çizimde oldukları gibi <xref:System.Windows.Forms.TextBox> boyutlandırılmış ve düzenlenmiş beş denetim ve bunlara karşılık gelen denetimleri ekleyin. Örnekte, <xref:System.Windows.Forms.TextBox> denetimler şu şekilde adlandırılır:  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 Tamam ve <xref:System.Windows.Forms.Button> **iptal**etiketli iki denetim ekleyin. Örnekte, düğme adları sırasıyla ve `btnOK` `btnCancel`' dir.  
  
### <a name="implementing-the-supporting-code"></a>Destekleyici kodu uygulama  
 Formu kod görünümünde açın. Denetim, toplanan verileri özel `OnButtonClick` olayı yükselterek ana bilgisayarına döndürür. Veriler, olay bağımsız değişkeni nesnesinde yer alır. Aşağıdaki kod, olay ve temsilci bildirimini gösterir.  
  
 `MyControl1` Sınıfına aşağıdaki kodu ekleyin.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs` Sınıfı, konağa döndürülecek bilgileri içerir.

 Aşağıdaki sınıfı forma ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Kullanıcı **Tamam** veya **iptal** <xref:System.Windows.Forms.Control.Click> düğmesine tıkladığında, olay işleyicileri verileri içeren bir `MyControlEventArgs` nesne oluşturur ve `OnButtonClick` olayı başlatır. İki işleyici arasındaki tek fark, olay bağımsız değişkeninin `IsOK` özelliğidir. Bu özellik, ana bilgisayarın hangi düğmeye tıklandığını belirlemesine olanak sağlar. `true` **Tamam** düğmesi ve`false` **iptal** düğmesi için olarak ayarlanır. Aşağıdaki kod iki düğme işleyicisini gösterir.

 `MyControl1` Sınıfına aşağıdaki kodu ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Derlemeye tanımlayıcı bir ad verme ve derlemeyi oluşturma
 Bu derlemeye bir uygulama tarafından başvurulması için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir tanımlayıcı adı olması gerekir. Güçlü bir ad oluşturmak için sn. exe ile bir anahtar dosyası oluşturun ve bunu projenize ekleyin.

1. Bir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] komut istemi açın. Bunu yapmak için **Başlat** menüsüne tıklayın ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**' ni seçin. Bu, özelleştirilmiş ortam değişkenleriyle bir konsol penceresi başlatır.

2. Komut isteminde, proje klasörünüze gitmek için `cd` komutunu kullanın.

3. Aşağıdaki komutu çalıştırarak MyControls. snk adlı bir anahtar dosya oluşturun.

    ```console
    Sn.exe -k MyControls.snk
    ```

4. Projenize anahtar dosyasını dahil etmek için Çözüm Gezgini ' de proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın. Proje tasarımcısında **imzalama** sekmesine tıklayın, **derlemeyi imzala** onay kutusunu seçin ve ardından anahtar dosyanıza göz atın.

5. Çözümü oluşturun. Derleme MyControls. dll adlı bir DLL üretecektir.

## <a name="implementing-the-wpf-host-application"></a>WPF ana bilgisayar uygulamasını uygulama
 Konak uygulama, barındırmak <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1`için denetimi kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulama, denetimden verileri `OnButtonClick` almak için olayı işler. Ayrıca, bazı denetim özelliklerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamadan değiştirmenize olanak sağlayan bir seçenek düğmeleri koleksiyonuna sahiptir. Aşağıdaki çizimde tamamlanmış uygulama gösterilmektedir.

Aşağıdaki görüntüde WPF uygulamasına katıştırılmış denetim dahil olmak üzere tüm uygulama gösterilmektedir:

 ![WPF sayfasında gömülü bir denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Projeyi Oluşturma
 Projeyi başlatmak için:

1. Açın [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]ve **Yeni proje**' yi seçin.

2. Pencere kategorisinde, **WPF uygulama** şablonunu seçin.

3. Yeni projeyi `WpfHost`adlandırın.

4. Konum için, MyControls projesini içeren en üst düzey klasörü belirtin.

5. Projeyi oluşturmak için **Tamam** ' ı tıklatın.

 Ayrıca, ve diğer derlemeler içeren `MyControl1` dll 'ye başvurular eklemeniz gerekir.

1. Çözüm Gezgini ' de proje adına sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. **Araştır** sekmesine tıklayın ve MyControls. dll dosyasını içeren klasöre gidin. Bu izlenecek yol için, bu klasör Mycontrols\bin\debugklasörüdür.

3. MyControls. dll ' yi seçin ve ardından **Tamam**' a tıklayın.

4. WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

### <a name="implementing-the-basic-layout"></a>Temel düzeni uygulama
 Konak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uygulamanın, MainWindow. xaml ' de uygulanması. Bu dosya, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] düzeni tanımlayan biçimlendirmeyi içerir ve Windows Forms denetimi barındırır. Uygulama üç bölgeye ayrılmıştır:

- Barındırılan denetimin çeşitli özelliklerini değiştirmek için kullanabileceğiniz seçenek düğmelerinin koleksiyonunu içeren **denetim özellikleri** paneli.

- Barındırılan denetimden döndürülen verileri görüntüleyen çeşitli <xref:System.Windows.Controls.TextBlock> öğeleri içeren denetim masası 'ndaki veriler.

- Barındırılan denetimin kendisi.

 Temel düzen aşağıdaki XAML 'de gösterilmiştir. Barındırmak `MyControl1` için gereken biçimlendirme bu örnekte atlanır, ancak daha sonra ele alınacaktır.

 MainWindow. xaml içindeki XAML 'yi aşağıdakiler ile değiştirin. Visual Basic kullanıyorsanız, sınıfını olarak `x:Class="MainWindow"`değiştirin.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 İlk <xref:System.Windows.Controls.StackPanel> öğe, barındırılan denetimin çeşitli varsayılan <xref:System.Windows.Controls.RadioButton> özelliklerini değiştirmenize olanak tanıyan birkaç denetim kümesini içerir. Bu, ardından barındıran <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1`bir öğesi. Son <xref:System.Windows.Controls.StackPanel> öğesi, barındırılan denetim <xref:System.Windows.Controls.TextBlock> tarafından döndürülen verileri görüntüleyen çeşitli öğeler içerir. Öğelerin ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarının sıralaması barındırılan denetimi, boşluk veya deformasyon olmadan pencereye katıştırır.

#### <a name="hosting-the-control"></a>Denetimi barındırma
 Önceki XAML 'nin aşağıdaki düzenlenmiş sürümü barındırmak `MyControl1`için gereken öğelere odaklanır.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 Ad alanı eşleme özniteliği barındırılan denetimi içeren `MyControls` ad alanına bir başvuru oluşturur. `xmlns` Bu eşleme, içinde `MyControl1` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak `<mcl:MyControl1>`temsil etmenizi sağlar.

 XAML 'deki iki öğe barındırmayı işleme:

- `WindowsFormsHost`<xref:System.Windows.Forms.Integration.WindowsFormsHost> bir[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada Windows Forms denetimini barındırmanızı sağlayan öğeyi temsil eder.

- `mcl:MyControl1`öğesini temsil `MyControl1`eden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi öğenin alt koleksiyonuna eklenir. Sonuç olarak, bu Windows Forms denetimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencerenin bir parçası olarak işlenir ve uygulamadan denetimle iletişim kurabilirsiniz.

### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyasını uygulama
 MainWindow. xaml. vb veya MainWindow.xaml.cs arka plan kod dosyası, önceki bölümde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] açıklanan işlevleri uygulayan yordamsal kodu içerir. Birincil görevler şunlardır:

- Olayına bir olay işleyicisi `MyControl1` `OnButtonClick` iliştirme.

- Seçenek düğmelerinin toplanması temelinde `MyControl1`' nin çeşitli özelliklerini değiştirme.

- Denetim tarafından toplanan verileri görüntüleme.

#### <a name="initializing-the-application"></a>Uygulamayı başlatma
 Başlatma kodu, pencerenin <xref:System.Windows.FrameworkElement.Loaded> olayı için bir olay işleyicisinde bulunur ve `OnButtonClick` denetimin olayına bir olay işleyicisi ekler.

 MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, `MainWindow` sınıfına aşağıdaki kodu ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1` Dahaönce<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> , `MyControl1` öğenin<xref:System.Windows.Forms.Integration.WindowsFormsHost> alt öğe koleksiyonuna eklenmiş olduğundan, başvurusunu almak için öğesini çevirebilirsiniz. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Daha sonra bu başvuruyu, ' a bir olay işleyicisi `OnButtonClick`iliştirmek için kullanabilirsiniz.

 Denetimin kendine başvuru sağlamaya ek olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamanın içinden işleyebileceğiniz bir dizi denetimin özelliklerini gösterir. Başlatma kodu, bu değerleri uygulamada daha sonra kullanılmak üzere özel genel değişkenlere atar.

 `MyControls` Dll 'deki türlere kolayca erişebilmeniz için, dosyanın en üstüne aşağıdaki `Imports` veya `using` ifadesini ekleyin.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>OnButtonClick olayını işleme
 `MyControl1`Kullanıcı, denetim düğmelerinden birini tıkladığında olayıbaşlatır.`OnButtonClick`

 `MainWindow` Sınıfına aşağıdaki kodu ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Metin kutularındaki veriler `MyControlEventArgs` nesnesine paketlenmiştir. Kullanıcı **Tamam** düğmesine tıkladığında, olay işleyicisi verileri ayıklar ve aşağıdaki `MyControl1`panelde görüntüler.

#### <a name="modifying-the-controls-properties"></a>Denetimin özelliklerini değiştirme
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, barındırılan denetimin varsayılan özelliklerinden birkaçını gösterir. Sonuç olarak, denetimin görünümünü uygulamanızın stiliyle daha yakından eşleşecek şekilde değiştirebilirsiniz. Sol paneldeki seçenek düğmelerinin kümeleri, kullanıcının çeşitli renk ve yazı tipi özelliklerini değiştirmesini sağlar. Her düğme kümesi, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay için kullanıcının seçenek düğmesi seçimlerini algılayan ve denetimdeki ilgili özelliği değiştiren bir işleyicisine sahiptir.

 `MainWindow` Sınıfına aşağıdaki kodu ekleyin.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Uygulamayı derleyin ve çalıştırın. Windows Forms Bileşik denetimine bir metin ekleyin ve ardından **Tamam**' a tıklayın. Metin, etiketlerde görüntülenir. Denetimdeki etkiyi görmek için farklı radyo düğmelerine tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF 'de Windows Forms denetimini barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: Windows Forms WPF bileşik denetimini barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
