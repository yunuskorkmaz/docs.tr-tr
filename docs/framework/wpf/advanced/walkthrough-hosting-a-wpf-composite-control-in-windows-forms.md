---
title: "İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5dc0a0f7b579feca6150e299cd7f0ef3a6e7a5e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu olabilir varolan genişletmek için daha etkili [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerine baştan yeniden. Yaygın bir senaryo, bir eklemek istediğiniz ya da daha fazla denetim ile uygulanan olduğunda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] uygulama. WPF denetimlerini özelleştirme hakkında daha fazla bilgi için bkz: [denetim özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md).  
  
 Bu kılavuzda barındıran aracılığıyla bir uygulama adımları bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri girişi gerçekleştirmek için bileşik denetim bir [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] uygulama. Bileşik Denetim DLL'de paketlenmiştir. Bu genel yordam daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu kılavuzda görünümünü ve işlevini neredeyse aynı olacak şekilde tasarlanmıştır [izlenecek yol: bir Windows Forms Bileşik Denetimi WPF barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Barındırma senaryo tersine çevrildi birincil farktır.  
  
 İzlenecek yol iki bölüme ayrılmıştır. Uygulamasını ilk bölümü kısaca açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim. İkinci bölümü, bileşik denetimi barındırmak nasıl ayrıntılı olarak anlatılmaktadır bir [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] uygulama, denetim olaylarını almasını ve denetimin özelliklerini erişebilirsiniz.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   WPF bileşik denetim uygulama.  
  
-   Windows Forms konak uygulamanın uygulama.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [Windows Forms örnek bir WPF bileşik denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=159996).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-wpf-composite-control"></a>WPF bileşik denetim uygulama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu örnekte kullanılan bileşik denetim olan kullanıcının kullanıcı adı ve adres alan basit veri girişi form. Kullanıcı görevi tamamlandığını göstermek için iki düğme tıklattığında denetimi ana bilgisayara bu bilgileri döndürmek için özel bir olay başlatır. Aşağıdaki çizimde işlenen denetimi göstermektedir.  
  
 ![Basit WPF denetimi](../../../../docs/framework/wpf/advanced/media/avaloncontrol.png "AvalonControl")  
WPF bileşik denetim  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1.  Başlatma [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], açarak **yeni proje** iletişim kutusu.  
  
2.  Visual C# ve Windows kategorisi seçin **WPF kullanıcı denetimi Kitaplığı** şablonu.  
  
3.  Yeni proje adı `MyControls`.  
  
4.  Konum için uygun şekilde adlandırılmış bir üst düzey klasör gibi belirtin `WindowsFormsHostingWpfControl`. Daha sonra bu klasörde konak uygulama sokar.  
  
5.  Tıklatın **Tamam** projesi oluşturmak için. Varsayılan proje adlı tek bir denetim içerir `UserControl1`.  
  
6.  Çözüm Gezgini'nde, yeniden adlandırma `UserControl1` için `MyControl1`.  
  
 Projeniz aşağıdaki sistem DLL'leri başvurular olması gerekir. Bu DLL'ler birini varsayılan olarak dahil edilmezse, bunları projenize ekleyin.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   Sistem  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>Kullanıcı arabirimi oluşturma  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] İle bileşik denetim uygulanması için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Bileşik Denetim [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] beş oluşur <xref:System.Windows.Controls.TextBox> öğeleri. Her <xref:System.Windows.Controls.TextBox> öğeye sahip bir ilişkili <xref:System.Windows.Controls.TextBlock> etiketi görevini gören öğesi. Var olan iki <xref:System.Windows.Controls.Button> alt öğeler **Tamam** ve **iptal**. Kullanıcı ya da düğmesine tıkladığında, denetim ana bilgisayara bilgileri döndürmek için özel bir olay başlatır.  
  
#### <a name="basic-layout"></a>Temel düzeni  
 Çeşitli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri içerdiği bir <xref:System.Windows.Controls.Grid> öğesi. Kullanabileceğiniz <xref:System.Windows.Controls.Grid> bileşik içeriğini kontrol çok aynı düzenlemeyi şekilde kullanacağınız bir `Table` HTML öğesi. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca bir <xref:System.Windows.Documents.Table> öğesi, ancak <xref:System.Windows.Controls.Grid> daha basit ve Basit Düzen görevler için daha iyi uygun.  
  
 Aşağıdaki XAML temel düzeni gösterilir. Bu XAML sütun sayısını belirterek denetiminin genel yapısını tanımlar ve içinde satırları <xref:System.Windows.Controls.Grid> öğesi.  
  
 MyControl1.xaml içinde varolan XAML aşağıdaki XAML ile değiştirin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Kılavuza TextBlock ve metin kutusu öğeleri ekleme  
 Yerleştirdiğiniz bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğenin ayarlayarak kılavuzunda öğesini <xref:System.Windows.Controls.Grid.RowProperty> ve <xref:System.Windows.Controls.Grid.ColumnProperty> öznitelikleri için uygun satır ve sütun numarası. Satır ve sütun numaralandırma sıfır tabanlı olduğunu unutmayın. Birden çok sütun ayarlayarak span öğesi olabilir, <xref:System.Windows.Controls.Grid.ColumnSpanProperty> özniteliği. Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Grid> öğeler, bkz [kılavuz öğesi oluşturma](../../../../docs/framework/wpf/controls/how-to-create-a-grid-element.md).  
  
 Bileşik Denetim aşağıdaki XAML gösterir <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> öğeleriyle kendi <xref:System.Windows.Controls.Grid.RowProperty> ve <xref:System.Windows.Controls.Grid.ColumnProperty> öğeleri düzgün yerleştirmek için ayarlanmış olan öznitelikler.  
  
 İçinde aşağıdaki XAML MyControl1.xaml içinde eklemek <xref:System.Windows.Controls.Grid> öğesi.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Kullanıcı Arabirimi öğeleri stil oluşturma  
 Veri girişi formda öğeleri çoğunun özelliklerinin bazıları için aynı ayarları sahip oldukları anlamına gelir benzer bir görünüm vardır. Her öğenin özniteliklerini ayrı olarak ayarlamak yerine, önceki XAML kullanan <xref:System.Windows.Style> öğe sınıfı için standart özellik ayarları belirlemek için öğeleri. Bu yaklaşım denetimi karmaşıklığını azaltır ve tek bir stil özniteliği aracılığıyla birden çok öğe görünümünü değiştirmenizi sağlar.  
  
 <xref:System.Windows.Style> Öğeleri içerdiği <xref:System.Windows.Controls.Grid> öğenin <xref:System.Windows.FrameworkElement.Resources%2A> denetimdeki tüm öğeler tarafından kullanılabilmesi için özellik. Stil olarak adlandırılmışsa, bir öğe olarak ekleyerek uygulamadan bir <xref:System.Windows.Style> öğesi stili 's adına ayarlayın. Adlandırılmamış stilleri öğesinin varsayılan stilini olur. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stilleri bkz [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Aşağıdaki XAML gösterildiği <xref:System.Windows.Style> bileşik denetim için öğeleri. Stilleri öğelerine nasıl uygulandığını görmek için önceki XAML bakın. Örneğin, son <xref:System.Windows.Controls.TextBlock> öğeye sahip `inlineText` stili ve son <xref:System.Windows.Controls.TextBox> öğesini kullanan varsayılan stili.  
  
 Aşağıdaki XAML MyControl1.xaml içinde eklemek hemen sonra <xref:System.Windows.Controls.Grid> start öğesi.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Tamam ve İptal düğmeleri ekleme  
 Bileşik denetim üzerinde son öğeler **Tamam** ve **iptal** <xref:System.Windows.Controls.Button> son satırının ilk iki sütun kaplayan öğeleri <xref:System.Windows.Controls.Grid>. Bu öğeleri bir ortak olay işleyicisi kullanmak `ButtonClicked`ve varsayılan <xref:System.Windows.Controls.Button> önceki XAML içinde tanımlanan stili.  
  
 MyControl1.xaml içinde son sonra aşağıdaki XAML eklemek <xref:System.Windows.Controls.TextBox> öğesi. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Bileşik denetim parçasıdır şimdi tamamlandı.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyası uygulama  
 Arka plan kodu dosyanın MyControl1.xaml.cs, üç önemli görevleri gerçekleştirir:
  
1.  Kullanıcı düğmeleri birini tıklattığında oluşan olayını işler.  
  
2.  Veri alır <xref:System.Windows.Controls.TextBox> öğeleri ve bir özel olay bağımsız değişkeni nesnesinde paketler.  
  
3.  Özel başlatır `OnButtonClick` kullanıcı tamamlandı ve ana bilgisayara verileri geçirmeden konak bildirir olay.  
  
 Denetim ayrıca bir dizi görünümünü değiştirebilmek için renk ve yazı tipi özellikleri kullanıma sunar. Aksine <xref:System.Windows.Forms.Integration.WindowsFormsHost> kullanılan sınıfı barındırmak için bir [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] denetimi <xref:System.Windows.Forms.Integration.ElementHost> sınıfı gösterir ve Denetim <xref:System.Windows.Controls.Panel.Background%2A> yalnızca özelliği. Bu kod örneği içinde açıklanan örneğin arasındaki benzerlik korumak için [izlenecek yol: bir Windows Forms Bileşik Denetimi WPF barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), Denetim doğrudan kalan özellikleri sunar.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Arka plan kod dosyasının temel yapısı  
 Arka plan kodu dosyasından tek bir ad alanı oluşur `MyControls`, iki sınıf içerecek `MyControl1` ve `MyControlEventArgs`.  
  
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
  
 İlk sınıf `MyControl1`, işlevselliğini uygulayan kod içeren kısmi bir sınıf [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] MyControl1.xaml tanımlanmış. MyControl1.xaml ayrıştırıldığında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı kısmi sınıfına dönüştürülür ve iki parçalı sınıflar derlenmiş denetim oluşturmak için birleştirilir. Bu nedenle, arka plan kod dosyasına sınıf adı için MyControl1.xaml atanan sınıf adı eşleşmelidir ve denetimi kök öğesinden devralmalıdır. İkinci sınıfı `MyControlEventArgs`, ana bilgisayara veri göndermek için kullanılan bir olay bağımsız değişkenleri sınıfıdır.  
  
 MyControl1.xaml.cs açın. Böylece şu ada sahip ve devraldığı varolan sınıf bildirimi değiştirme <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Denetimi başlatma  
 Aşağıdaki kod birkaç temel görevleri uygular:  
  
-   Özel olay bildirir `OnButtonClick`ve onun ilişkili temsilci `MyControlEventHandler`.  
  
-   Kullanıcı verilerini depolamak birkaç özel genel değişkenler oluşturur. Bu veriler karşılık gelen özelliklere sunulur.  
  
-   Bir işleyici uygulayan `Init`, denetimin için <xref:System.Windows.FrameworkElement.Loaded> olay. Bu işleyici, MyControl1.xaml içinde tanımlanan değerlerden birisini atayarak genel değişkenler başlatır. Bunu yapmak için onu kullanır <xref:System.Windows.FrameworkElement.Name%2A> tipik bir atanan <xref:System.Windows.Controls.TextBlock> öğesi, `nameLabel`, bu öğenin özellik ayarlarına erişmek için.  
  
 Varolan Oluşturucusu silin ve aşağıdaki kodu ekleyin, `MyControl1` sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Düğmeleri işleme tıklama olayları  
 Kullanıcı ya da tıklayarak, veri girişi görev tamamlandığını gösteren **Tamam** düğmesini veya **iptal** düğmesi. Her iki aynı düğmelerini <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi `ButtonClicked`. Her iki düğmeleri bir ada sahip `btnOK` veya `btnCancel`, hangi düğmesi değerini inceleyerek tıklandığını belirleme işleyicinin sağlayan `sender` bağımsız değişkeni. İşleyici şunları yapar:  
  
-   Oluşturur bir `MyControlEventArgs` verilerini içeren nesne <xref:System.Windows.Controls.TextBox> öğeleri.  
  
-   Kullanıcı tıkladıysanız **iptal** button, ayarlar `MyControlEventArgs` nesnenin `IsOK` özelliğine `false`.  
  
-   Başlatır `OnButtonClick` ana bilgisayara kullanıcı tamamlandı ve geçişleri geri toplanan verileri belirtmek için olay.  
  
 Aşağıdaki kodu ekleyin, `MyControl1` sınıfı, sonra `Init` yöntemi.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Özellikleri oluşturma  
 Sınıfı geri kalanı, yalnızca daha önce ele alınan genel değişkenler karşılık özellikleri sunar. Bir özellik değiştiğinde, set erişimcisine karşılık gelen öğe özelliklerini değiştirme ve temel alınan genel değişkenler güncelleştirme denetiminin görünümünü değiştirir.  
  
 Aşağıdaki kodu ekleyin, `MyControl1` sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Ana bilgisayara verileri gönderme  
 Dosyanın son bileşeninde `MyControlEventArgs` toplanan verileri konağa geri göndermek için kullanılan sınıf.  
  
 Aşağıdaki kodu ekleyin, `MyControls` ad alanı. Uygulama basittir ve daha ayrıntılı ele alınmamıştır.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Çözümü oluşturun. Yapı MyControls.dll adlı bir DLL oluşturur.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Windows Forms konak uygulamayı uygulama  
 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] Konak uygulamanız tarafından kullanılan bir <xref:System.Windows.Forms.Integration.ElementHost> ana bilgisayar nesnesine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim. Uygulama tanıtıcıları `OnButtonClick` bileşik denetim verileri almak için olay. Uygulama denetimin görünümünü değiştirmek için kullanabileceğiniz seçenek düğmeleri kümesi de sahiptir. Aşağıdaki çizimde uygulamayı gösterir.  
  
 ![Windows Form Avalon Denetimi Barındırma](../../../../docs/framework/wpf/advanced/media/wfhost.png "WFHost")  
Bir Windows Forms uygulaması'nda barındırılan WPF bileşik denetim  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1.  Başlatma [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], açarak **yeni proje** iletişim kutusu.  
  
2.  Visual C# ve Windows kategorisi seçin **Windows Forms uygulaması** şablonu.  
  
3.  Yeni proje adı `WFHost`.  
  
4.  Konum için MyControls projeyi içeren aynı üst düzey klasörü belirtin.  
  
5.  Tıklatın **Tamam** projesi oluşturmak için.  
  
 İçeren DLL başvurular ekleyin gerekir `MyControl1` ve diğer derlemeler.  
  
1.  Çözüm Gezgini'nde proje adına sağ tıklayın ve seçin **Başvuru Ekle**.  
  
2.  Tıklatın **Gözat** sekmesini tıklatın ve MyControls.dll içeren klasöre göz atın. Bu kılavuz için bu klasör MyControls\bin\Debug'dır.  
  
3.  MyControls.dll seçin ve ardından **Tamam**.  
  
4.  Aşağıdaki derlemeler başvurular ekleyin.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Uygulama için kullanıcı arabirimi uygulama  
 Windows Form uygulaması için kullanıcı Arabirimi WPF bileşik denetim ile etkileşim kurmak için çeşitli denetimleri içerir.  
  
1.  Windows Form Tasarımcısı'nda Form1 açın.  
  
2.  Denetimlerin sığması için form büyütün.  
  
3.  Formun sağ üst köşesinde eklemek bir <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> tutmak üzere Denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim.  
  
4.  Aşağıdakileri ekleyin <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> formu denetimleri.  
  
    |Ad|Metin|  
    |----------|----------|  
    |groupBox1|Arka plan rengi|  
    |groupBox2|Ön plan rengi|  
    |groupBox3|Yazı tipi boyutu|  
    |groupBox4|Yazı tipi ailesi|  
    |groupBox5|Yazı tipi stili|  
    |groupBox6|Yazı tipi ağırlığı|  
    |groupBox7|Denetim verileri|  
  
5.  Aşağıdakileri ekleyin <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> için denetimler <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> kontrol eder.  
  
    |GroupBox|Ad|Metin|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Özgün|  
    |groupBox1|radioBackgroundLightGreen|Açık yeşil|  
    |groupBox1|radioBackgroundLightSalmon|Açık Somon|  
    |groupBox2|radioForegroundOriginal|Özgün|  
    |groupBox2|radioForegroundRed|kırmızı|  
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
  
6.  Aşağıdakileri ekleyin <xref:System.Windows.Forms.Label?displayProperty=nameWithType> son denetimleri <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Bu denetimler tarafından döndürülen verileri görüntüleyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim.  
  
    |GroupBox|Ad|Metin|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Ad:|  
    |groupBox7|lblAddress|Sokak adresi:|  
    |groupBox7|lblCity|Şehir:|  
    |groupBox7|lblState|Durum:|  
    |groupBox7|lblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Formun başlatma  
 Formun genellikle barındırma kodunu uygulamak <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Aşağıdaki kodda gösterildiği <xref:System.Windows.Forms.Form.Load> olay işleyicisi, bir işleyici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin <xref:System.Windows.FrameworkElement.Loaded> olay ve daha sonra kullanılan birkaç genel değişkenler için bildirimler.  
  
 Windows Forms Tasarımcısı'nda oluşturmak için formu bir <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Form1.cs üst kısmında, aşağıdaki ekleyin `using` deyimleri.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Var olan Değiştir `Form1` aşağıdaki kodla sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load` Önceki kod yönteminde gösterir barındırmak için genel yordam bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi:  
  
1.  Yeni bir <xref:System.Windows.Forms.Integration.ElementHost> nesnesi.  
  
2.  Denetimin ayarlamak <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3.  Ekleme <xref:System.Windows.Forms.Integration.ElementHost> denetimini <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonu.  
  
4.  Bir örneğini oluşturmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim.  
  
5.  Bileşik denetim form üzerinde denetime atayarak konak <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği.  
  
 Kalan iki satırları `Form1_Load` yöntemi işleyiciler iki denetim olaylarına ekleyin:  
  
-   `OnButtonClick`kullanıcı tıkladığında, bileşik denetim tarafından tetiklenen özel bir olaydır **Tamam** veya **iptal** düğmesi. Kullanıcının yanıtını alma ve kullanıcı tarafından belirtilen herhangi bir veri toplamak için olay işleyin.  
  
-   <xref:System.Windows.FrameworkElement.Loaded>tarafından gerçekleştirilen standart bir olaydır bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tam yüklü olduğunda denetim. Örnek denetim özelliklerinden kullanarak birkaç genel değişkenler başlatması gerekir çünkü olay burada kullanılır. Formun zaman <xref:System.Windows.Forms.Form.Load> olayı denetimi tam olarak yüklü değil ve bu değerleri hala ayarlamak `null`. Denetimin kadar beklemeniz gerekir <xref:System.Windows.FrameworkElement.Loaded> olayı, bu özellikleri erişmeden önce oluşur.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Olay işleyicisi, önceki kodda gösterilir. `OnButtonClick` İşleyici bir sonraki bölümde ele alınmıştır.  
  
### <a name="handling-onbuttonclick"></a>OnButtonClick işleme  
 `OnButtonClick` Olaylarının kullanıcı tıklattığında **Tamam** veya **iptal** düğmesi.  
  
 Olay işleyicisi olay bağımsız değişken denetler `IsOK` alan hangi düğmenin tıklandığını belirleme. `lbl` *Veri* değişkenleri karşılık <xref:System.Windows.Forms.Label> daha önce bahsedilen kontrol eder. Kullanıcı tıklarsa **Tamam** button, denetimin verilerden <xref:System.Windows.Controls.TextBox> denetimleri, karşılık gelen atandığı <xref:System.Windows.Forms.Label> denetim. Kullanıcı tıklarsa **iptal**, <xref:System.Windows.Forms.Label.Text%2A> değerler varsayılan dizelere ayarlanır.  
  
 Aşağıdaki düğmeye eklemek için olay işleyicisini tıklatın `Form1` sınıfı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Derleme ve uygulamayı çalıştırın. WPF bileşik denetiminde biraz metin ekleyin ve ardından **Tamam**. Metin etiketler görünür. Bu noktada, kod radyo düğmeleri işlemek için eklenmedi.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Denetiminin görünümünü değiştirme  
 <xref:System.Windows.Forms.RadioButton> Form üzerinde denetimleri değiştirmek kullanıcı etkinleştirecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin ön ve arka plan renkleri de birkaç yazı tipi özellikleri. Arka plan rengi tarafından sunulan <xref:System.Windows.Forms.Integration.ElementHost> nesnesi. Diğer özellikler, özel denetimin özelliklerini sunulur.  
  
 Her birini çift <xref:System.Windows.Forms.RadioButton> denetimi oluşturmak için form üzerinde <xref:System.Windows.Forms.RadioButton.CheckedChanged> olay işleyicileri. Değiştir <xref:System.Windows.Forms.RadioButton.CheckedChanged> aşağıdaki kod ile olay işleyicileri.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Derleme ve uygulamayı çalıştırın. WPF bileşik denetim etkisini görmek için farklı radyo düğmelerini tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [İzlenecek yol: bir Windows Forms Bileşik Denetimi WPF barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: Windows Forms'ta 3-b WPF bileşik denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
