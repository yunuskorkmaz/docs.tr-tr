---
title: 'İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: d38a9c67edb5df89554e9e02274410a825b3384b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654555"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu olabilir mevcut BT'nizi genişletin daha etkili [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ile uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerine baştan yeniden. Sık karşılaşılan bir senaryodur birini eklemek istediğiniz ya da daha fazla denetim ile uygulanan olduğunda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , Windows Forms uygulaması içinde. WPF denetimleri özelleştirme hakkında daha fazla bilgi için bkz. [denetimi özelleştirme](../controls/control-customization.md).  
  
 Bu izlenecek yolda barındıran aracılığıyla uygulama adımları bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimini Windows Forms uygulaması'nda veri girişi gerçekleştirmek için. Bileşik Denetim DLL içinde paketlenmiştir. Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu izlenecek yol Görünüm ve işlevselliği için neredeyse aynı olacak şekilde tasarlanan [izlenecek yol: WPF içinde Forms bileşik denetimini bir Windows barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Barındırma senaryo tersine, birincil farktır.  
  
 İzlenecek yol, iki bölüme ayrılmıştır. İlk bölüm uygulamasını kısaca açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim. İkinci bölümü, bileşik denetimini Windows Forms uygulamasında barındırmak, denetim olaylarını almak ve denetim özelliklerini bazılarına erişmek nasıl ayrıntılı olarak ele alınmaktadır.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   WPF bileşik denetimini uygulama.  
  
-   Windows Forms ana bilgisayar uygulaması oluşturma.  
  
 Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WPF bileşik denetimini Windows Forms örneğinde barındırma](https://go.microsoft.com/fwlink/?LinkID=159996).  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.  
  
## <a name="implementing-the-wpf-composite-control"></a>WPF bileşik denetimini uygulama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu örnekte kullanılan bileşik denetimdir kullanıcının adını ve adresini alan bir basit veri girişi formuna. Kullanıcı görevi tamamlandığını göstermek için iki düğme tıkladığında denetim konağa bu bilgileri döndürmek için özel bir olay başlatır. İşlenen denetimi aşağıda gösterilmektedir. 

 Aşağıdaki görüntüde, WPF bileşik denetimini gösterir: 

  
 ![Basit WPF denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Proje başlatmak için:  
  
1.  Başlatma [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]açın **yeni proje** iletişim kutusu.  
  
2.  Visual C# ve Windows kategorisi seçin **WPF kullanıcı denetimi Kitaplığı** şablonu.  
  
3.  Yeni proje adını `MyControls`.  
  
4.  Konum için bir kolayca adlandırılmış üst düzey klasör gibi belirtin `WindowsFormsHostingWpfControl`. Daha sonra ana bilgisayar uygulaması bu klasöre koyacaktır.  
  
5.  Tıklayın **Tamam** projeyi oluşturmak için. Varsayılan proje adlı tek bir denetim içeren `UserControl1`.  
  
6.  Çözüm Gezgini'nde, yeniden adlandırma `UserControl1` için `MyControl1`.  
  
 Projenize aşağıdaki sistem DLL'lerini başvuruları olması gerekir. Bu DLL'leri birini varsayılan olarak dahil edilmez, bunları projenize ekleyin.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   Sistem  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>Kullanıcı arabirimi oluşturma  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] İle bileşik denetim uygulanan için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Bileşik Denetim [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] beş oluşur <xref:System.Windows.Controls.TextBox> öğeleri. Her <xref:System.Windows.Controls.TextBox> öğeye sahip bir ilişkili <xref:System.Windows.Controls.TextBlock> etiket olarak hizmet veren öğesi. İki <xref:System.Windows.Controls.Button> altındaki öğeleri **Tamam** ve **iptal**. Kullanıcı ya da düğmesini tıkladığında denetim konağa bilgileri döndürmek için özel bir olay başlatır.  
  
#### <a name="basic-layout"></a>Temel düzeni  
 Çeşitli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeler olarak kapsanan bir <xref:System.Windows.Controls.Grid> öğesi. Kullanabileceğiniz <xref:System.Windows.Controls.Grid> bileşik içeriğini denetlemek çok aynı düzenlemek için şekilde kullanacağınız bir `Table` HTML öğesi. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca bir <xref:System.Windows.Documents.Table> öğesi, ancak <xref:System.Windows.Controls.Grid> daha basit ve basit düzene görevler için daha uygundur.  
  
 Aşağıdaki XAML temel düzeni gösterir. Bu XAML içinde satır ve sütun sayısını belirterek denetim genel yapısını tanımlar <xref:System.Windows.Controls.Grid> öğesi.  
  
 MyControl1.xaml içinde mevcut XAML aşağıdaki XAML ile değiştirin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Kılavuza TextBlock ve metin öğeleri ekleme  
 Yerleştirme bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesi öğenin ayarlayarak kılavuzunda <xref:System.Windows.Controls.Grid.RowProperty> ve <xref:System.Windows.Controls.Grid.ColumnProperty> öznitelikleri için uygun satır ve sütun numarası. Satır ve sütun numaralandırma sıfır tabanlı olduklarını unutmayın. Bir öğe ayarlayarak birden fazla sütuna yayılmış olabilir, <xref:System.Windows.Controls.Grid.ColumnSpanProperty> özniteliği. Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Grid> öğeler, bkz [kılavuz öğesi oluşturma](../controls/how-to-create-a-grid-element.md).  
  
 Bileşik Denetim aşağıdaki XAML gösterir <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> öğelerle kendi <xref:System.Windows.Controls.Grid.RowProperty> ve <xref:System.Windows.Controls.Grid.ColumnProperty> öğeleri kılavuzda düzgün şekilde yerleştirmek için ayarlanan öznitelikleri.  
  
 Aşağıdaki XAML içinde MyControl1.xaml içinde ekleme <xref:System.Windows.Controls.Grid> öğesi.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Kullanıcı Arabirimi öğeleri stil oluşturma  
 Veri girişi formuna öğelerin çoğu, aynı ayarları bazı özellikleri için sahip oldukları anlamına gelir benzer bir görünümü vardır. Önceki XAML kullanan her öğenin öznitelikleri ayrı olarak ayarlamak yerine <xref:System.Windows.Style> öğelerini öğelerin sınıflar için standart özellik ayarları tanımlamak için kullanırsınız. Bu yaklaşım, denetimin karmaşıklığını azaltır ve tek bir stil özniteliği aracılığıyla birden fazla öğelerin görünümünü değiştirmenize olanak tanır.  
  
 <xref:System.Windows.Style> Öğeler olarak kapsanan <xref:System.Windows.Controls.Grid> öğenin <xref:System.Windows.FrameworkElement.Resources%2A> denetimdeki tüm öğeler tarafından kullanılabilmesi için özellik. Bir stil ise, bir öğeye ekleyerek uygulamanız bir <xref:System.Windows.Style> öğesi stilin adına ayarlayın. Adlandırılmamış stilleri öğesi için varsayılan stili haline gelir. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stil, bakın [stil ve şablon oluşturma](../controls/styling-and-templating.md).  
  
 Aşağıdaki XAML gösterildiği <xref:System.Windows.Style> bileşik denetim için öğeleri. Stilleri öğelerine nasıl uygulandığını görmek için önceki XAML bakın. Örneğin, son <xref:System.Windows.Controls.TextBlock> öğesinin `inlineText` stil ve son <xref:System.Windows.Controls.TextBox> öğesini kullanan varsayılan stili.  
  
 Aşağıdaki XAML MyControl1.xaml içinde ekleme hemen sonrasına <xref:System.Windows.Controls.Grid> başlangıç öğesi.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Tamam ve İptal düğmeleri ekleme  
 Bileşik denetim üzerinde son öğeler **Tamam** ve **iptal** <xref:System.Windows.Controls.Button> son satırının ilk iki sütun kaplayan öğeleri <xref:System.Windows.Controls.Grid>. Ortak bir olay işleyicisi bu öğeleri kullanmak `ButtonClicked`ve varsayılan <xref:System.Windows.Controls.Button> önceki XAML içinde tanımlanmış stil.  
  
 MyControl1.xaml içinde son sonra aşağıdaki XAML ekleme <xref:System.Windows.Controls.TextBox> öğesi. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Bileşik denetim parçasıdır artık tamamlandı.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyası uygulama  
 Arka plan kod dosyası, MyControl1.xaml.cs, üç önemli görevleri gerçekleştirir:
  
1.  Kullanıcı düğmeleri tıkladığında gerçekleşen olayını işler.  
  
2.  Veri alır <xref:System.Windows.Controls.TextBox> öğeleri ve bir özel olay bağımsız değişkeni nesne paketleri.  
  
3.  Özel başlatır `OnButtonClick` ana kullanıcı tamamlandı ve verileri konağa geçirmeden olduğunu bildirir, olay.  
  
 Denetimin görünümünü değiştirebilmek için renk ve yazı tipi özellikleri sayısı da kullanıma sunar. Farklı <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir Windows Forms denetimini barındırmak için kullanılan sınıfı <xref:System.Windows.Forms.Integration.ElementHost> sınıfı gösterir denetimin <xref:System.Windows.Controls.Panel.Background%2A> yalnızca özellik. Bu kod örneği içinde açıklanan örneğin arasındaki benzerlik korumak için [izlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), denetimi doğrudan kalan özellikleri gösterir.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Arka plan kod dosyasının temel yapısı  
 Tek bir ad alanı arka plan kod dosyası oluşur `MyControls`, iki sınıf içerecek `MyControl1` ve `MyControlEventArgs`.  
  
```  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
```  
  
 İlk sınıf `MyControl1`, işlevselliğini uygulayan kod içeren bir kısmi sınıf [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] MyControl1.xaml içinde tanımlanır. MyControl1.xaml ayrıştırıldığında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı kısmi sınıf dönüştürülür ve iki parçalı sınıflar derlenmiş denetim oluşturmak üzere birleştirilir. Bu nedenle, sınıf adını arka plan kod dosyasında MyControl1.xaml için atanan sınıf adı eşleşmelidir ve denetimin kök öğesinden devralmalıdır. İkinci sınıfı `MyControlEventArgs`, konağa veri göndermek için kullanılan bir olay bağımsız değişkenleri sınıfıdır.  
  
 MyControl1.xaml.cs açın. Varolan sınıf bildirimini değiştirin, böylece şu ada sahip ve devralınan <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Denetimi başlatılıyor  
 Aşağıdaki kod, bazı temel görevleri uygular:  
  
-   Özel bir olay bildirir `OnButtonClick`ve onun ilişkili temsilci `MyControlEventHandler`.  
  
-   Kullanıcının verilerini depolayan çeşitli özel genel değişkenler oluşturur. Bu veriler, ilgili özellikleri aracılığıyla kullanıma sunulur.  
  
-   Bir işleyici uygulayan `Init`, denetim için <xref:System.Windows.FrameworkElement.Loaded> olay. Bu işleyici, MyControl1.xaml içinde tanımlanan değerlerden birisini atayarak genel değişkenleri başlatır. Bunu yapmak için kullandığı <xref:System.Windows.FrameworkElement.Name%2A> tipik bir atanmış <xref:System.Windows.Controls.TextBlock> öğesi `nameLabel`, o öğenin özellik ayarlarına erişmek için.  
  
 Var olan oluşturucu silin ve aşağıdaki kodu ekleyin, `MyControl1` sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Düğmeleri işleme tıklama olayları  
 Kullanıcı tıklayarak, veri girişi görevin tamamlandığını gösteren **Tamam** düğmesini veya **iptal** düğmesi. Her iki aynı düğmelerini <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi `ButtonClicked`. Her iki düğme bir adı vardır `btnOK` veya `btnCancel`, işleyicinin değerini inceleyerek hangi düğmesine tıklandığını belirleme sağlayan `sender` bağımsız değişken. İşleyici şunları yapar:  
  
-   Oluşturur bir `MyControlEventArgs` verilerini içeren nesne <xref:System.Windows.Controls.TextBox> öğeleri.  
  
-   Kullanıcı tıkladıysanız **iptal** Ayarlar düğmesini `MyControlEventArgs` nesnenin `IsOK` özelliğini `false`.  
  
-   Başlatır `OnButtonClick` konağa kullanıcı tamamlandıktan ve geçişleri geri toplanan verileri göstermek için olay.  
  
 Aşağıdaki kodu ekleyin, `MyControl1` sınıfı, sonra `Init` yöntemi.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Özellikleri oluşturma  
 Sınıfı geri kalanı, yukarıda bahsedilen genel değişkenlerine karşılık gelen özelliklerle yalnızca kullanıma sunar. Bir özellik değiştiğinde, set erişimcisine karşılık gelen öğe özelliklerini değiştirme ve temel alınan genel değişkenler güncelleştirerek denetiminin görünümünü değiştirir.  
  
 Aşağıdaki kodu ekleyin, `MyControl1` sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Konağa veri gönderme  
 Dosyanın son bileşeninde `MyControlEventArgs` toplanan verileri konağa geri göndermek için kullanılan sınıf.  
  
 Aşağıdaki kodu ekleyin, `MyControls` ad alanı. Uygulama, oldukça basittir ve daha ayrıntılı ele alınmamıştır.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Çözümü oluşturun. Derleme MyControls.dll adlı bir DLL oluşturur.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Windows Forms konak uygulamanın uygulama  
 Windows Forms ana bilgisayar, uygulamanız tarafından kullanılan bir <xref:System.Windows.Forms.Integration.ElementHost> konak nesnesine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim. Uygulama işleyen `OnButtonClick` bileşik denetim verileri almak için olay. Uygulama ayrıca bir dizi denetimin görünümünü değiştirmek için kullanabileceğiniz seçenek düğmesi vardır. Aşağıdaki çizim, uygulamayı gösterir.  

Aşağıdaki resimde, bir Windows Forms uygulamasında barındırılan bir WPF bileşik denetimini gösterir"  

 ![Bir Windows Form barındırma Avalon denetiminde Scteenshot.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Proje başlatmak için:  
  
1.  Başlatma [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]açın **yeni proje** iletişim kutusu.  
  
2.  Visual C# ve Windows kategorisi seçin **Windows Forms uygulaması** şablonu.  
  
3.  Yeni proje adını `WFHost`.  
  
4.  Konum için MyControls projesini içeren aynı üst düzey klasörü belirtin.  
  
5.  Tıklayın **Tamam** projeyi oluşturmak için.  
  
 Ayrıca içeren DLL başvuruları eklemek gereken `MyControl1` ve diğer derlemeler.  
  
1.  Çözüm Gezgini'nde proje adına sağ tıklayın ve seçin **Başvuru Ekle**.  
  
2.  Tıklayın **Gözat** sekmesini tıklatıp MyControls.dll içeren klasöre göz atın. Bu kılavuz için bu klasör MyControls\bin\Debug'dır.  
  
3.  MyControls.dll seçin ve ardından **Tamam**.  
  
4.  Aşağıdaki derlemelere başvurular ekleyin.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Uygulama için kullanıcı arabirimi uygulama  
 Windows Form uygulaması için kullanıcı Arabirimi ile WPF bileşik denetimini etkileşim kurmak için çeşitli denetimler içerir.  
  
1.  Form1 Windows Form Tasarımcısı'nda açın.  
  
2.  Form denetimleri uyum sağlayacak şekilde büyütün.  
  
3.  Formun sağ üst köşesinde bulunan ekleme bir <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> tutacak denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim.  
  
4.  Aşağıdaki <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> formu için denetimler.  
  
    |Ad|Metin|  
    |----------|----------|  
    |groupBox1|Arka plan rengi|  
    |groupBox2|Ön plan rengi|  
    |groupBox3|Yazı tipi boyutu|  
    |groupBox4|Yazı tipi ailesi|  
    |groupBox5|Yazı tipi stili|  
    |groupBox6|Yazı tipi genişliği|  
    |groupBox7|Denetim verileri|  
  
5.  Aşağıdaki <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> için denetimleri <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> kontrol eder.  
  
    |GroupBox|Ad|Metin|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Özgün|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Özgün|  
    |groupBox2|radioForegroundRed|Kırmızı|  
    |groupBox2|radioForegroundYellow|Sarı|  
    |groupBox3|radioSizeOriginal|Özgün|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Özgün|  
    |groupBox4|radioFamilyTimes|Georgia|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|İtalik|  
    |groupBox6|radioWeightOriginal|Özgün|  
    |groupBox6|radioWeightBold|Kalın|  
  
6.  Aşağıdaki <xref:System.Windows.Forms.Label?displayProperty=nameWithType> son denetimleri <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Bu denetimler tarafından döndürülen veriyi görüntüler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim.  
  
    |GroupBox|Ad|Metin|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Ad:|  
    |groupBox7|lblAddress|Posta adresi:|  
    |groupBox7|lblCity|Şehir:|  
    |groupBox7|lblState|Durum:|  
    |groupBox7|lblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Form başlatılıyor  
 Formun genellikle barındırma kodunu uygulamak <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Aşağıdaki kodda gösterildiği <xref:System.Windows.Forms.Form.Load> olay işleyicisi, işleyici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin <xref:System.Windows.FrameworkElement.Loaded> olay ve daha sonra kullanılan birkaç genel değişkenler için bildirimleri.  
  
 Windows Form Tasarımcısı'nda oluşturmak için formu bir <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Form1.cs üstüne aşağıdakileri ekleyin `using` deyimleri.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Mevcut içeriğini değiştirin `Form1` aşağıdaki kodla sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load` Önceki kodda yöntemi gösterir barındırmak için genel yordam bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi:  
  
1.  Yeni bir <xref:System.Windows.Forms.Integration.ElementHost> nesne.  
  
2.  Denetimin ayarlamak <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3.  Ekleme <xref:System.Windows.Forms.Integration.ElementHost> denetimini <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonu.  
  
4.  Bir örneğini oluşturmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi.  
  
5.  Bileşik denetim form üzerinde denetime atayarak konak <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği.  
  
 Kalan iki satırları `Form1_Load` yöntemi, iki denetim olaylarına işleyicileri ekleyin:  
  
-   `OnButtonClick` kullanıcı tıkladığında, bileşik denetim tarafından harekete geçirilen özel bir olaydır **Tamam** veya **iptal** düğmesi. Kullanıcının yanıt almak ve kullanıcının belirttiği herhangi bir veri toplamak için olay işleyin.  
  
-   <xref:System.Windows.FrameworkElement.Loaded> tarafından oluşturulan standart bir olay bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tam yüklü olduğunda denetim. Olayı, denetim özelliklerini kullanarak birden çok genel değişkenlerini başlatmak üzere örnek gerektiğinden burada kullanılır. Formun anında <xref:System.Windows.Forms.Form.Load> olayı, denetim tam yüklü değil ve bu değerleri hala ayarlanmış olan `null`. Denetimin kadar beklenecek ihtiyacınız <xref:System.Windows.FrameworkElement.Loaded> olay özelliklere erişebilmek için önce gerçekleşir.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Olay işleyicisi, yukarıdaki kodda gösterilmiştir. `OnButtonClick` İşleyicisi, sonraki bölümde ele alınmıştır.  
  
### <a name="handling-onbuttonclick"></a>OnButtonClick işleme  
 `OnButtonClick` Kullanıcı tıkladığında bir olay oluşursa **Tamam** veya **iptal** düğmesi.  
  
 Olay işleyicisi olay bağımsız değişkenin denetler `IsOK` hangi düğmesine tıklandığını belirleme özgüdür. `lbl` *Veri* değişkenleri karşılık <xref:System.Windows.Forms.Label> daha önce bahsedilen kontrol eder. Kullanıcı tıklarsa **Tamam** düğmesi, denetimin verilerden <xref:System.Windows.Controls.TextBox> denetimleri, karşılık gelen atandığı <xref:System.Windows.Forms.Label> denetimi. Kullanıcı tıklarsa **iptal**, <xref:System.Windows.Forms.Label.Text%2A> değerleri varsayılan dizeye ayarlayın.  
  
 Aşağıdaki düğmeye eklemek için olay işleyicisini tıklayın `Form1` sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Derleme ve uygulamayı çalıştırın. WPF bileşik denetimini içinde metin ekleyin ve ardından **Tamam**. Metin etiketler görünür. Bu noktada, kod radyo düğmeleri işlemek için eklenmedi.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Denetiminin görünümünü değiştirme  
 <xref:System.Windows.Forms.RadioButton> Form üzerinde denetimleri değiştirmesine izin etkinleştirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin ön ve arka plan renkleri de gibi birkaç yazıtipi özelliğini. Arka plan rengi tarafından sunulan <xref:System.Windows.Forms.Integration.ElementHost> nesne. Diğer özellikler, özel denetimin özelliklerini sunulur.  
  
 Her çift <xref:System.Windows.Forms.RadioButton> oluşturmak için form üzerindeki denetim <xref:System.Windows.Forms.RadioButton.CheckedChanged> olay işleyicileri. Değiştirin <xref:System.Windows.Forms.RadioButton.CheckedChanged> aşağıdaki kod ile olay işleyicileri.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Derleme ve uygulamayı çalıştırın. WPF bileşik denetimini üzerindeki etkisini görmek için farklı bir radyo düğmelerini tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: Bir 3B WPF bileşik denetimini Windows Forms içinde barındırma](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
