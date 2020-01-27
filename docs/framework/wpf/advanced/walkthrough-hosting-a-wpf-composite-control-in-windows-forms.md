---
title: Windows Forms WPF bileşik denetimini barındırma
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 59243e1810757ff0ff58a60ac3eb007bbc227be0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742691"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodda önemli bir yatırımınız varsa, sıfırdan yazmak yerine mevcut [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamanızı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genişletmek daha etkili olabilir. Yaygın bir senaryo, Windows Forms uygulamanızda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanmış bir veya daha fazla denetim eklemek istemeniz durumunda olur. WPF denetimlerini özelleştirme hakkında daha fazla bilgi için bkz. [Denetim özelleştirmesi](../controls/control-customization.md).  
  
 Bu izlenecek yol, bir Windows Forms uygulamasında veri girişi gerçekleştirmek üzere [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik bir denetim barındıran bir uygulamada size kılavuzluk ediyor. Bileşik denetim bir DLL içinde paketlenmiştir. Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu izlenecek yol, görünüm ve işlevlerle neredeyse özdeş olacak şekilde tasarlanmıştır [: WPF 'de Windows Forms Bileşik bir denetim barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Birincil fark, barındırma senaryosunun tersine çevrilme olur.  
  
 İzlenecek yol iki bölüme ayrılmıştır. İlk bölüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin uygulamasını kısaca açıklar. İkinci bölüm, bileşik denetimin Windows Forms bir uygulamada nasıl barındırılacağını, denetimden olayları nasıl alacağını ve denetimin bazı özelliklerine nasıl erişebileceğini açıklamaktadır.  
  
 Bu izlenecek yolda gösterilen görevler şunlardır:  
  
- WPF bileşik denetimini uygulama.  
  
- Windows Forms ana bilgisayar uygulaması uygulama.  
  
 Bu kılavuzda gösterilen görevlerin tüm kod listesi için, bkz. [Windows Forms örnek IÇINDE WPF bileşik denetimi barındırma](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Prerequisites  

Bu yönergeyi tamamlamak için Visual Studio gerekir.  
  
## <a name="implementing-the-wpf-composite-control"></a>WPF bileşik denetimini uygulama  
 Bu örnekte kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim, kullanıcının adını ve adresini alan basit bir veri girişi biçimidir. Kullanıcı görevin bittiğini göstermek için iki düğmeden birini tıkladığında, denetim bu bilgileri konağa döndürecek özel bir olay başlatır. Aşağıdaki çizimde işlenmiş denetim gösterilmektedir. 

 Aşağıdaki görüntüde bir WPF bileşik denetimi gösterilmektedir: 

 ![Basit bir WPF denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Visual Studio 'yu başlatın ve **Yeni proje** iletişim kutusunu açın.  
  
2. Görsel C# ve Windows kategorisinde, **WPF Kullanıcı denetimi kitaplık** şablonunu seçin.  
  
3. Yeni proje `MyControls`adlandırın.  
  
4. Konum için `WindowsFormsHostingWpfControl`gibi kolay adlandırılmış bir üst düzey klasör belirtin. Daha sonra, ana bilgisayar uygulamasını bu klasöre yerleştirebilirsiniz.  
  
5. Projeyi oluşturmak için **Tamam** ' ı tıklatın. Varsayılan proje, `UserControl1`adlı tek bir denetim içerir.  
  
6. Çözüm Gezgini `UserControl1` `MyControl1`olarak yeniden adlandırın.  
  
 Projenizin aşağıdaki sistem dll 'Lerine başvuruları olmalıdır. Bu dll 'Lerden herhangi biri varsayılan olarak dahil edilmemelidir, bunları projenize ekleyin.  
  
- PresentationCore  
  
- PresentationFramework  
  
- Sistem  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Kullanıcı arabirimi oluşturma  
 Bileşik denetimin [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ile uygulanır. Bileşik denetim [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] beş <xref:System.Windows.Controls.TextBox> öğeden oluşur. Her <xref:System.Windows.Controls.TextBox> öğesi, etiket görevi gören ilişkili bir <xref:System.Windows.Controls.TextBlock> öğesi içerir. En altta iki <xref:System.Windows.Controls.Button> öğesi vardır ve **Tamam** ve **iptal et**. Kullanıcı her iki düğmeye tıkladığında, denetim, bilgileri konağa döndürmek için özel bir olay başlatır.  
  
#### <a name="basic-layout"></a>Temel düzen  
 Çeşitli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri bir <xref:System.Windows.Controls.Grid> öğesinde yer alır. Bileşik denetimin içeriğini HTML içindeki bir `Table` öğesini kullandığınız şekilde düzenlemek için <xref:System.Windows.Controls.Grid> kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca bir <xref:System.Windows.Documents.Table> öğesi vardır ancak <xref:System.Windows.Controls.Grid> basit düzen görevlerine daha hafif ve daha uygundur.  
  
 Aşağıdaki XAML temel düzeni göstermektedir. Bu XAML, <xref:System.Windows.Controls.Grid> öğesindeki sütun ve satır sayısını belirterek denetimin genel yapısını tanımlar.  
  
 MyControl1. xaml içinde, var olan XAML 'yi aşağıdaki XAML ile değiştirin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Kılavuza TextBlock ve TextBox öğeleri ekleme  
 Öğenin <xref:System.Windows.Controls.Grid.RowProperty> ve <xref:System.Windows.Controls.Grid.ColumnProperty> özniteliklerini uygun satır ve sütun numarasına ayarlayarak kılavuza [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesi yerleştirebilirsiniz. Satır ve sütun numaralandırmasının sıfır tabanlı olduğunu unutmayın. <xref:System.Windows.Controls.Grid.ColumnSpanProperty> özniteliğini ayarlayarak bir öğe birden çok sütuna yayılabilmeniz gerekir. <xref:System.Windows.Controls.Grid> öğeleri hakkında daha fazla bilgi için bkz. [Grid öğesi oluşturma](../controls/how-to-create-a-grid-element.md).  
  
 Aşağıdaki XAML bileşik denetimin <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> öğelerini <xref:System.Windows.Controls.Grid.RowProperty> ve <xref:System.Windows.Controls.Grid.ColumnProperty> öznitelikleriyle gösterir ve öğeleri kılavuza doğru yerleştirmek için ayarlanır.  
  
 MyControl1. xaml içinde, <xref:System.Windows.Controls.Grid> öğesinde aşağıdaki XAML 'yi ekleyin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>UI öğelerini Stillendirme  
 Veri girişi formundaki öğelerin birçoğu benzer bir görünüme sahiptir ve bu, özelliklerinin birkaçı için aynı ayarlara sahip oldukları anlamına gelir. Her öğenin özniteliklerini ayrı olarak ayarlamak yerine, önceki XAML öğelerin sınıfları için standart özellik ayarlarını tanımlamak üzere <xref:System.Windows.Style> öğelerini kullanır. Bu yaklaşım, denetimin karmaşıklığını azaltır ve tek bir stil özniteliğiyle birden çok öğenin görünümünü değiştirmenize olanak sağlar.  
  
 <xref:System.Windows.Style> öğeleri <xref:System.Windows.Controls.Grid> öğenin <xref:System.Windows.FrameworkElement.Resources%2A> özelliğinde bulunur, bu nedenle denetimdeki tüm öğeler tarafından kullanılabilirler. Bir stil adlandırılmışsa, stilin adına ayarlanmış bir <xref:System.Windows.Style> öğesi ekleyerek onu bir öğeye uygularsınız. Adında olmayan stiller öğesi için varsayılan stil olur. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stilleri hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.  
  
 Aşağıdaki XAML bileşik denetim için <xref:System.Windows.Style> öğelerini gösterir. Stillerin öğelere nasıl uygulandığını görmek için önceki XAML 'ye bakın. Örneğin, son <xref:System.Windows.Controls.TextBlock> öğesi `inlineText` stiline sahiptir ve son <xref:System.Windows.Controls.TextBox> öğesi varsayılan stili kullanır.  
  
 MyControl1. xaml içinde, <xref:System.Windows.Controls.Grid> start öğesinden hemen sonra aşağıdaki XAML 'yi ekleyin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Tamam ve Iptal düğmeleri ekleme  
 Bileşik denetimdeki son öğeler, <xref:System.Windows.Controls.Grid>son satırının ilk iki sütununu kaplayan **ok** ve **Cancel**<xref:System.Windows.Controls.Button> öğeleridir. Bu öğeler, önceki XAML 'de tanımlanan ortak bir olay işleyicisini, `ButtonClicked`ve varsayılan <xref:System.Windows.Controls.Button> stilini kullanır.  
  
 MyControl1. xaml içinde, son <xref:System.Windows.Controls.TextBox> öğesinden sonra aşağıdaki XAML 'yi ekleyin. Bileşik denetimin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bölümü artık tamamlanmıştır.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyasını uygulama  
 Arka plan kod dosyası olan MyControl1.xaml.cs, üç önemli görevi uygular:
  
1. Kullanıcı düğmelerden birine tıkladığında oluşan olayı işler.  
  
2. <xref:System.Windows.Controls.TextBox> öğelerinden verileri alır ve özel bir olay bağımsız değişkeni nesnesi içinde paketler.  
  
3. Ana bilgisayara kullanıcının tamamlandığını bildiren ve verileri konağa geri geçiren özel `OnButtonClick` olayını oluşturur.  
  
 Denetim Ayrıca, görünümü değiştirmenizi sağlayan bir dizi renk ve yazı tipi özelliği de sunar. Windows Forms denetimini barındırmak için kullanılan <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfından farklı olarak <xref:System.Windows.Forms.Integration.ElementHost> sınıfı yalnızca denetimin <xref:System.Windows.Controls.Panel.Background%2A> özelliğini kullanıma sunar. Bu kod örneği arasındaki benzerliği ve [Izlenecek yol: WPF 'de Windows Forms Bileşik denetim barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)bölümünde açıklanan örnek, denetim kalan özellikleri doğrudan kullanıma sunar.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Arka plan kod dosyasının temel yapısı  
 Arka plan kod dosyası, `MyControl1` ve `MyControlEventArgs`iki sınıf içeren `MyControls`tek bir ad alanından oluşur.  
  
```csharp  
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
  
 İlk sınıf `MyControl1`, MyControl1. xaml içinde tanımlanan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] işlevselliğini uygulayan kodu içeren kısmi bir sınıftır. MyControl1. xaml ayrıştırıldığında, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı kısmi sınıfa dönüştürülür ve iki kısmi sınıf derlenmiş denetimi oluşturacak şekilde birleştirilir. Bu nedenle, arka plan kod dosyasındaki sınıf adı, MyControl1. xaml öğesine atanan sınıf adıyla eşleşmelidir ve denetimin kök öğesinden devralması gerekir. `MyControlEventArgs`ikinci sınıfı, verileri konağa geri göndermek için kullanılan bir olay bağımsız değişkeni sınıfıdır.  
  
 MyControl1.xaml.cs 'i açın. Mevcut sınıf bildirimini aşağıdaki ada sahip olacak şekilde değiştirin ve <xref:System.Windows.Controls.Grid>devralır.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Denetim başlatılıyor  
 Aşağıdaki kod birkaç temel görev uygular:  
  
- Özel bir olay, `OnButtonClick`ve ilişkili temsilcisini `MyControlEventHandler`bildirir.  
  
- Kullanıcının verilerini depolayan birkaç özel genel değişken oluşturur. Bu veriler ilgili özellikler aracılığıyla sunulur.  
  
- Denetimin <xref:System.Windows.FrameworkElement.Loaded> olayı için bir işleyici `Init`uygular. Bu işleyici, MyControl1. xaml içinde tanımlanan değerleri atayarak genel değişkenleri başlatır. Bunu yapmak için, `nameLabel`, bu öğenin özellik ayarlarına erişmek için tipik bir <xref:System.Windows.Controls.TextBlock> öğesine atanan <xref:System.Windows.FrameworkElement.Name%2A> kullanır.  
  
 Mevcut oluşturucuyu silin ve `MyControl1` Sınıfınıza aşağıdaki kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Düğmelerin tıklama olaylarını işleme  
 Kullanıcı, **Tamam** düğmesine veya **iptal** düğmesine tıklayarak veri girişi görevinin tamamlandığını gösterir. Her iki düğme de aynı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisini kullanır `ButtonClicked`. Her iki düğme de, işleyicinin `sender` bağımsız değişkeninin değerini inceleyerek hangi düğmenin tıklandığını belirlemesine olanak sağlayan bir ada, `btnOK` veya `btnCancel`sahiptir. İşleyici şunları yapar:  
  
- <xref:System.Windows.Controls.TextBox> öğelerinden verileri içeren bir `MyControlEventArgs` nesnesi oluşturur.  
  
- Kullanıcı **iptal** düğmesine tıklamıştır `MyControlEventArgs` nesnenin `IsOK` özelliğini `false`olarak ayarlar.  
  
- , Kullanıcının tamamlandığını ana bilgisayara göstermek için `OnButtonClick` olayını yükseltir ve toplanan verileri geri geçirir.  
  
 `Init` yönteminden sonra `MyControl1` Sınıfınıza aşağıdaki kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Özellikler oluşturma  
 Sınıfın geri kalanı, daha önce ele alınan genel değişkenlere karşılık gelen özellikleri gösterir. Bir özellik değiştiğinde, küme erişimcisi ilgili öğe özelliklerini değiştirerek ve temel alınan genel değişkenleri güncelleştirerek denetimin görünümünü değiştirir.  
  
 `MyControl1` Sınıfınıza aşağıdaki kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Veriler konağa geri gönderiliyor  
 Dosyadaki son bileşen, toplanan verileri konağa geri göndermek için kullanılan `MyControlEventArgs` sınıfıdır.  
  
 Aşağıdaki kodu `MyControls` ad alanına ekleyin. Uygulama basittir ve daha fazla açıklanmaz.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Çözümü oluşturun. Derleme MyControls. dll adlı bir DLL üretecektir.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Windows Forms ana bilgisayar uygulamasını uygulama  
 Windows Forms ana bilgisayar uygulaması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimi barındırmak için bir <xref:System.Windows.Forms.Integration.ElementHost> nesnesi kullanır. Uygulama, bileşik denetimden verileri almak için `OnButtonClick` olayını işler. Uygulamanın Ayrıca, denetimin görünümünü değiştirmek için kullanabileceğiniz bir seçenek düğmeleri kümesi vardır. Aşağıdaki çizimde uygulama gösterilmektedir.  

Aşağıdaki görüntüde, bir Windows Forms uygulamasında barındırılan bir WPF bileşik denetimi gösterilmektedir "  

 ![Avalon denetimini barındıran bir Windows formunu gösteren scershot.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Visual Studio 'yu başlatın ve **Yeni proje** iletişim kutusunu açın.  
  
2. Görsel C# ve Windows kategorisinde **Windows Forms uygulama** şablonu ' nu seçin.  
  
3. Yeni proje `WFHost`adlandırın.  
  
4. Konum için, MyControls projesini içeren en üst düzey klasörü belirtin.  
  
5. Projeyi oluşturmak için **Tamam** ' ı tıklatın.  
  
 Ayrıca, `MyControl1` ve diğer derlemeleri içeren DLL 'ye başvurular eklemeniz gerekir.  
  
1. Çözüm Gezgini ' de proje adına sağ tıklayın ve **Başvuru Ekle**' yi seçin.  
  
2. **Araştır** sekmesine tıklayın ve MyControls. dll dosyasını içeren klasöre gidin. Bu izlenecek yol için, bu klasör Mycontrols\bin\debugklasörüdür.  
  
3. MyControls. dll ' yi seçin ve ardından **Tamam**' a tıklayın.  
  
4. Aşağıdaki derlemelere başvurular ekleyin.  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - System.Xaml  
  
    - WindowsBase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Uygulama için Kullanıcı arabirimini uygulama  
 Windows form uygulaması için Kullanıcı arabirimi, WPF bileşik denetimiyle etkileşim kurmak için çeşitli denetimler içerir.  
  
1. Windows form tasarımcısında Form1 ' i açın.  
  
2. Form, denetimleri kapsayacak şekilde büyütün.  
  
3. Formun sağ üst köşesinde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimi tutmak için bir <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> denetimi ekleyin.  
  
4. Aşağıdaki <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> denetimlerini forma ekleyin.  
  
    |Name|Metin|  
    |----------|----------|  
    |groupBox1|Arka plan rengi|  
    |groupBox2|Ön plan rengi|  
    |groupBox3|Yazı tipi boyutu|  
    |groupBox4|Yazı tipi ailesi|  
    |groupBox5|Yazı tipi stili|  
    |groupBox6|Yazı tipi genişliği|  
    |groupBox7|Denetimdeki veriler|  
  
5. Aşağıdaki <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> denetimlerini <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> denetimlerine ekleyin.  
  
    |GroupBox|Name|Metin|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Özgün|  
    |groupBox1|radioBackgroundLightGreen|Açık yeşil|  
    |groupBox1|radioBackgroundLightSalmon|Açık somon|  
    |groupBox2|radioForegroundOriginal|Özgün|  
    |groupBox2|radioForegroundRed|Kırmızı|  
    |groupBox2|radioForegroundYellow|Renkle|  
    |groupBox3|radioSizeOriginal|Özgün|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Özgün|  
    |groupBox4|Radiofamili|Times New Roman|  
    |groupBox4|Radiofamilswingdings|Simgesine|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|İtalik|  
    |groupBox6|radioWeightOriginal|Özgün|  
    |groupBox6|radioWeightBold|Kalın|  
  
6. Aşağıdaki <xref:System.Windows.Forms.Label?displayProperty=nameWithType> denetimlerini son <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>ekleyin. Bu denetimler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimi tarafından döndürülen verileri görüntüler.  
  
    |GroupBox|Name|Metin|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Ad:|  
    |groupBox7|lblAddress|Sokak adresi:|  
    |groupBox7|lblCity|Baş|  
    |groupBox7|lblState|Durum:|  
    |groupBox7|lblZip|Zip|  
  
### <a name="initializing-the-form"></a>Form başlatılıyor  
 Genellikle barındırma kodunu formun <xref:System.Windows.Forms.Form.Load> olay işleyicisine uygulayamazsınız. Aşağıdaki kod <xref:System.Windows.Forms.Form.Load> olay işleyicisini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin <xref:System.Windows.FrameworkElement.Loaded> olayına yönelik bir işleyiciyi ve daha sonra kullanılan çeşitli genel değişkenlerin bildirimlerini gösterir.  
  
 Windows Form Tasarımcısı, bir <xref:System.Windows.Forms.Form.Load> olay işleyicisi oluşturmak için forma çift tıklayın. Form1.cs 'in en üstünde aşağıdaki `using` deyimlerini ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Varolan `Form1` sınıfının içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Önceki koddaki `Form1_Load` yöntemi, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini barındırmak için genel prosedürü gösterir:  
  
1. Yeni bir <xref:System.Windows.Forms.Integration.ElementHost> nesnesi oluşturun.  
  
2. Denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>olarak ayarlayın.  
  
3. <xref:System.Windows.Forms.Integration.ElementHost> denetimini <xref:System.Windows.Forms.Panel> denetiminin <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonuna ekleyin.  
  
4. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminin bir örneğini oluşturun.  
  
5. Denetimi <xref:System.Windows.Forms.Integration.ElementHost> denetiminin <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğine atayarak bileşik denetimi barındırın.  
  
 `Form1_Load` yönteminde kalan iki satır, işleyicileri iki denetim olayına ekler:  
  
- `OnButtonClick`, Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında bileşik denetim tarafından tetiklenen özel bir olaydır. Kullanıcının yanıtını almak ve Kullanıcı tarafından belirtilen verileri toplamak için olayını işleyebilirsiniz.  
  
- <xref:System.Windows.FrameworkElement.Loaded>, tam olarak yüklendiğinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi tarafından oluşturulan standart bir olaydır. Örnek, denetimin özelliklerini kullanarak birkaç genel değişken başlatması gerektiğinden olay burada kullanılır. Formun <xref:System.Windows.Forms.Form.Load> olayı sırasında denetim tam olarak yüklenmez ve bu değerler hala `null`olarak ayarlanmıştır. Bu özelliklere erişebilmek için denetimin <xref:System.Windows.FrameworkElement.Loaded> olayının gerçekleşene kadar beklemeniz gerekir.  
  
 <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi önceki kodda gösterilmektedir. `OnButtonClick` işleyicisi bir sonraki bölümde ele alınmıştır.  
  
### <a name="handling-onbuttonclick"></a>OnButtonClick işleme  
 `OnButtonClick` olay, Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında oluşur.  
  
 Olay işleyicisi, hangi düğmenin tıklandığını belirleyen olay bağımsız değişkeninin `IsOK` alanını denetler. `lbl`*veri* değişkenleri, daha önce ele alınan <xref:System.Windows.Forms.Label> denetimlerine karşılık gelir. Kullanıcı **Tamam** düğmesine tıkladığında, denetimin <xref:System.Windows.Controls.TextBox> denetimlerinin verileri ilgili <xref:System.Windows.Forms.Label> denetimine atanır. Kullanıcı **iptal**' i tıklarsa <xref:System.Windows.Forms.Label.Text%2A> değerleri varsayılan dizelere ayarlanır.  
  
 `Form1` sınıfına aşağıdaki düğmeyi tıklayıp olay işleyicisi kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Uygulamayı derleyin ve çalıştırın. WPF bileşik denetimine biraz metin ekleyin ve ardından **Tamam**' a tıklayın. Metin, etiketlerde görüntülenir. Bu noktada radyo düğmelerini işlemek için kod eklenmedi.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Denetimin görünümünü değiştirme  
 Formdaki <xref:System.Windows.Forms.RadioButton> denetimleri, kullanıcının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin ön plan ve arka plan renklerini ve çeşitli yazı tipi özelliklerini değiştirmesine olanak sağlar. Arka plan rengi <xref:System.Windows.Forms.Integration.ElementHost> nesnesi tarafından gösterilir. Kalan özellikler, denetimin özel özellikleri olarak gösterilir.  
  
 <xref:System.Windows.Forms.RadioButton.CheckedChanged> olay işleyicileri oluşturmak için formdaki her bir <xref:System.Windows.Forms.RadioButton> denetimine çift tıklayın. <xref:System.Windows.Forms.RadioButton.CheckedChanged> olay işleyicilerini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Uygulamayı derleyin ve çalıştırın. WPF bileşik denetimindeki etkiyi görmek için farklı radyo düğmelerine tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
