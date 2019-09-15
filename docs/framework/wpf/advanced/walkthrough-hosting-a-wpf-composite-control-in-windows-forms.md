---
title: 'İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: a062095885e6c1fc8816a78847968b1c250eabf8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991452"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, kod içinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] önemli bir yatırımınız olduğunda, sıfırdan yazmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerine mevcut [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamanızı genişletmek daha etkili olabilir. Yaygın bir senaryo, Windows Forms uygulamanızda uygulanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir veya daha fazla denetimi eklemek istediğinizde. WPF denetimlerini özelleştirme hakkında daha fazla bilgi için bkz. [Denetim özelleştirmesi](../controls/control-customization.md).  
  
 Bu izlenecek yol, bir Windows Forms uygulamasında veri girişi gerçekleştirmek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üzere bileşik bir denetim barındıran bir uygulamada size kılavuzluk ediyor. Bileşik denetim bir DLL içinde paketlenmiştir. Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir. Bu izlenecek yol, görünümü ve işlevselliği [gözden geçirmede neredeyse özdeş olacak şekilde tasarlanmıştır: WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)'de Windows Forms Bileşik denetim barındırma. Birincil fark, barındırma senaryosunun tersine çevrilme olur.  
  
 İzlenecek yol iki bölüme ayrılmıştır. İlk bölüm, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin uygulamasını kısaca açıklar. İkinci bölüm, bileşik denetimin Windows Forms bir uygulamada nasıl barındırılacağını, denetimden olayları nasıl alacağını ve denetimin bazı özelliklerine nasıl erişebileceğini açıklamaktadır.  
  
 Bu izlenecek yolda gösterilen görevler şunlardır:  
  
- WPF bileşik denetimini uygulama.  
  
- Windows Forms ana bilgisayar uygulaması uygulama.  
  
 Bu kılavuzda gösterilen görevlerin tüm kod listesi için, bkz. [Windows Forms örnek IÇINDE WPF bileşik denetimi barındırma](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu yönergeyi tamamlamak için Visual Studio gerekir.  
  
## <a name="implementing-the-wpf-composite-control"></a>WPF bileşik denetimini uygulama  
 Bu örnekte kullanılan bileşik denetim, kullanıcının adını ve adresini alan basit bir veri girişi biçimidir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kullanıcı görevin bittiğini göstermek için iki düğmeden birini tıkladığında, denetim bu bilgileri konağa döndürecek özel bir olay başlatır. Aşağıdaki çizimde işlenmiş denetim gösterilmektedir. 

 Aşağıdaki görüntüde bir WPF bileşik denetimi gösterilmektedir: 

 ![Basit bir WPF denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Başlatın [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ve **Yeni proje** iletişim kutusunu açın.  
  
2. Görsel C# ve Windows kategorisinde, **WPF Kullanıcı denetimi kitaplık** şablonunu seçin.  
  
3. Yeni projeyi `MyControls`adlandırın.  
  
4. Konum için, gibi kolay adlandırılmış bir üst düzey klasör `WindowsFormsHostingWpfControl`belirtin. Daha sonra, ana bilgisayar uygulamasını bu klasöre yerleştirebilirsiniz.  
  
5. Projeyi oluşturmak için **Tamam** ' ı tıklatın. Varsayılan proje adlı `UserControl1`tek bir denetim içerir.  
  
6. Çözüm Gezgini ' de, `UserControl1` olarak `MyControl1`yeniden adlandırın.  
  
 Projenizin aşağıdaki sistem dll 'Lerine başvuruları olmalıdır. Bu dll 'Lerden herhangi biri varsayılan olarak dahil edilmemelidir, bunları projenize ekleyin.  
  
- PresentationCore  
  
- PresentationFramework  
  
- Sistem  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Kullanıcı arabirimi oluşturma  
 Bileşik denetim [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]için ile uygulanır. [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Bileşik denetim [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] beş <xref:System.Windows.Controls.TextBox> öğeden oluşur. Her <xref:System.Windows.Controls.TextBox> öğe, etiket görevi <xref:System.Windows.Controls.TextBlock> gören ilişkili bir öğesi vardır. En altta iki <xref:System.Windows.Controls.Button> öğe bulunur, **Tamam** ve **iptal et**. Kullanıcı her iki düğmeye tıkladığında, denetim, bilgileri konağa döndürmek için özel bir olay başlatır.  
  
#### <a name="basic-layout"></a>Temel düzen  
 Çeşitli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeler bir <xref:System.Windows.Controls.Grid> öğesi içinde bulunur. Bileşik denetimin içeriğini <xref:System.Windows.Controls.Grid> HTML içindeki bir `Table` öğeyi kullandığınız şekilde düzenlemek için ' i kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca bir <xref:System.Windows.Documents.Table> öğesi vardır, ancak <xref:System.Windows.Controls.Grid> basit düzen görevleri için daha hafif ve daha uygundur.  
  
 Aşağıdaki XAML temel düzeni göstermektedir. Bu XAML, <xref:System.Windows.Controls.Grid> öğesindeki sütun ve satır sayısını belirterek denetimin genel yapısını tanımlar.  
  
 MyControl1. xaml içinde, var olan XAML 'yi aşağıdaki XAML ile değiştirin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Kılavuza TextBlock ve TextBox öğeleri ekleme  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğe ve özniteliklerini<xref:System.Windows.Controls.Grid.ColumnProperty> uygun satır ve sütun numarası olarak ayarlayarak kılavuza bir öğe yerleştirebilirsiniz <xref:System.Windows.Controls.Grid.RowProperty> . Satır ve sütun numaralandırmasının sıfır tabanlı olduğunu unutmayın. <xref:System.Windows.Controls.Grid.ColumnSpanProperty> Özniteliğini ayarlayarak bir öğe birden çok sütuna yayılabilmeniz gerekir. Öğeler hakkında <xref:System.Windows.Controls.Grid> daha fazla bilgi için bkz. [Grid öğesi oluşturma](../controls/how-to-create-a-grid-element.md).  
  
 Aşağıdaki XAML, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Grid.RowProperty> ve <xref:System.Windows.Controls.TextBlock> özniteliklerini<xref:System.Windows.Controls.Grid.ColumnProperty> kullanarak öğeleri kılavuza doğru yerleştirmek için ayarlanan bileşik denetimin ve öğelerini gösterir.  
  
 MyControl1. xaml içinde, aşağıdaki xaml <xref:System.Windows.Controls.Grid> öğesini öğesine ekleyin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>UI öğelerini Stillendirme  
 Veri girişi formundaki öğelerin birçoğu benzer bir görünüme sahiptir ve bu, özelliklerinin birkaçı için aynı ayarlara sahip oldukları anlamına gelir. Her bir öğenin özniteliğini ayrı olarak ayarlamak yerine, önceki xaml öğeleri sınıfları <xref:System.Windows.Style> için standart özellik ayarlarını tanımlamak üzere öğeleri kullanır. Bu yaklaşım, denetimin karmaşıklığını azaltır ve tek bir stil özniteliğiyle birden çok öğenin görünümünü değiştirmenize olanak sağlar.  
  
 <xref:System.Windows.Style> Öğeler <xref:System.Windows.Controls.Grid> öğenin özelliğinde<xref:System.Windows.FrameworkElement.Resources%2A> bulunur, bu nedenle denetimdeki tüm öğeler tarafından kullanılabilirler. Bir stil adlandırılmışsa, stilin adına bir <xref:System.Windows.Style> öğe kümesi ekleyerek onu bir öğeye uygularsınız. Adında olmayan stiller öğesi için varsayılan stil olur. Stiller hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.  
  
 Aşağıdaki XAML bileşik denetim için <xref:System.Windows.Style> öğeleri gösterir. Stillerin öğelere nasıl uygulandığını görmek için önceki XAML 'ye bakın. Örneğin, son <xref:System.Windows.Controls.TextBlock> öğe `inlineText` stile sahiptir ve son <xref:System.Windows.Controls.TextBox> öğe varsayılan stili kullanır.  
  
 MyControl1. xaml içinde, <xref:System.Windows.Controls.Grid> başlangıç öğesinden hemen sonra aşağıdaki xaml 'yi ekleyin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Tamam ve Iptal düğmeleri ekleme  
 Bileşik denetimdeki son öğeler, öğesinin <xref:System.Windows.Controls.Grid>son satırının ilk iki sütununu kaplayan **Tamam** ve **iptal** <xref:System.Windows.Controls.Button> öğeleri olur. Bu öğeler, önceki xaml 'de tanımlanan ortak `ButtonClicked`olay işleyicisini, ve <xref:System.Windows.Controls.Button> varsayılan stili kullanır.  
  
 MyControl1. xaml içinde, son <xref:System.Windows.Controls.TextBox> öğeden sonra aşağıdaki xaml 'yi ekleyin. Bileşik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] denetimin bölümü artık tamamlanmıştır.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Arka plan kod dosyasını uygulama  
 Arka plan kod dosyası olan MyControl1.xaml.cs, üç önemli görevi uygular:
  
1. Kullanıcı düğmelerden birine tıkladığında oluşan olayı işler.  
  
2. <xref:System.Windows.Controls.TextBox> Öğelerden verileri alır ve özel bir olay bağımsız değişkeni nesnesi içinde paketler.  
  
3. Ana bilgisayara kullanıcının `OnButtonClick` tamamlandığını bildiren ve verileri konağa geri geçiren özel olayı başlatır.  
  
 Denetim Ayrıca, görünümü değiştirmenizi sağlayan bir dizi renk ve yazı tipi özelliği de sunar. Bir Windows Forms denetimini barındırmak için kullanılan <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Controls.Panel.Background%2A> sınıfının aksine, sınıfı yalnızca denetimin özelliğini kullanıma sunar. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Bu kod örneği ile [izlenecek yol arasındaki benzerliği sürdürmek için: WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)'de Windows Forms Bileşik denetim barındırma, denetim kalan özellikleri doğrudan kullanıma sunar.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Arka plan kod dosyasının temel yapısı  
 Arka plan kod dosyası, iki `MyControls` `MyControl1` sınıf içeren tek bir ad alanından oluşur ve `MyControlEventArgs`.  
  
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
  
 Birinci sınıf `MyControl1`, MyControl1. xaml içinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tanımlanan işlevselliği uygulayan kodu içeren kısmi bir sınıftır. MyControl1. xaml ayrıştırıldığında,,, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı kısmi sınıfa dönüştürülür ve iki kısmi sınıf derlenmiş denetimi oluşturacak şekilde birleştirilir. Bu nedenle, arka plan kod dosyasındaki sınıf adı, MyControl1. xaml öğesine atanan sınıf adıyla eşleşmelidir ve denetimin kök öğesinden devralması gerekir. İkinci sınıfı `MyControlEventArgs`, verileri konağa geri göndermek için kullanılan bir olay bağımsız değişkeni sınıfıdır.  
  
 MyControl1.xaml.cs 'i açın. Mevcut sınıf bildirimini aşağıdaki adı ve öğesinden devralınacak <xref:System.Windows.Controls.Grid>şekilde değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Denetim başlatılıyor  
 Aşağıdaki kod birkaç temel görev uygular:  
  
- Özel bir olay, `OnButtonClick`ve ilişkili `MyControlEventHandler`temsilcisini bildirir.  
  
- Kullanıcının verilerini depolayan birkaç özel genel değişken oluşturur. Bu veriler ilgili özellikler aracılığıyla sunulur.  
  
- Denetimin olayı için bir `Init`işleyici uygular.<xref:System.Windows.FrameworkElement.Loaded> Bu işleyici, MyControl1. xaml içinde tanımlanan değerleri atayarak genel değişkenleri başlatır. Bunu yapmak için, bu öğenin özellik <xref:System.Windows.FrameworkElement.Name%2A> ayarlarına erişmek için tipik <xref:System.Windows.Controls.TextBlock> bir öğesine `nameLabel`atanan ' ı kullanır.  
  
 Mevcut oluşturucuyu silin ve aşağıdaki kodu sınıfınıza `MyControl1` ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Düğmelerin tıklama olaylarını işleme  
 Kullanıcı, **Tamam** düğmesine veya **iptal** düğmesine tıklayarak veri girişi görevinin tamamlandığını gösterir. Her iki düğme de aynı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay `ButtonClicked`işleyicisini kullanır. Her iki düğme de bir ada `btnOK` `btnCancel`sahiptir. Bu, işleyicinin `sender` bağımsız değişkenin değerini inceleyerek hangi düğmenin tıklandığını belirlemesine olanak sağlar. İşleyici şunları yapar:  
  
- Öğelerden<xref:System.Windows.Controls.TextBox> verileri `MyControlEventArgs` içeren bir nesne oluşturur.  
  
- Kullanıcı **iptal** düğmesine tıkladıysanız `MyControlEventArgs` nesnenin `IsOK` özelliğini olarak `false`ayarlar.  
  
- , Kullanıcının tamamlandığını ana bilgisayara göstermek için olayıbaşlatırvetoplananverilerigerigeçirir.`OnButtonClick`  
  
 Yönteminden sonra sınıfınıza `MyControl1` aşağıdaki kodu ekleyin. `Init`  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Özellikler oluşturma  
 Sınıfın geri kalanı, daha önce ele alınan genel değişkenlere karşılık gelen özellikleri gösterir. Bir özellik değiştiğinde, küme erişimcisi ilgili öğe özelliklerini değiştirerek ve temel alınan genel değişkenleri güncelleştirerek denetimin görünümünü değiştirir.  
  
 Sınıfınıza `MyControl1` aşağıdaki kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Veriler konağa geri gönderiliyor  
 Dosyadaki son bileşen, toplanan verileri konağa geri `MyControlEventArgs` göndermek için kullanılan sınıftır.  
  
 Aşağıdaki kodu `MyControls` ad alanına ekleyin. Uygulama basittir ve daha fazla açıklanmaz.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Çözümü oluşturun. Derleme MyControls. dll adlı bir DLL üretecektir.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Windows Forms ana bilgisayar uygulamasını uygulama  
 Windows Forms ana bilgisayar uygulaması <xref:System.Windows.Forms.Integration.ElementHost> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimi barındırmak için bir nesne kullanır. Uygulama, bileşik denetimden `OnButtonClick` verileri almak için olayı işler. Uygulamanın Ayrıca, denetimin görünümünü değiştirmek için kullanabileceğiniz bir seçenek düğmeleri kümesi vardır. Aşağıdaki çizimde uygulama gösterilmektedir.  

Aşağıdaki görüntüde, bir Windows Forms uygulamasında barındırılan bir WPF bileşik denetimi gösterilmektedir "  

 ![Avalon denetimini barındıran bir Windows formunu gösteren scershot.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Başlatın [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]ve **Yeni proje** iletişim kutusunu açın.  
  
2. Görsel C# ve Windows kategorisinde **Windows Forms uygulama** şablonu ' nu seçin.  
  
3. Yeni projeyi `WFHost`adlandırın.  
  
4. Konum için, MyControls projesini içeren en üst düzey klasörü belirtin.  
  
5. Projeyi oluşturmak için **Tamam** ' ı tıklatın.  
  
 Ayrıca, ve diğer derlemeler içeren `MyControl1` dll 'ye başvurular eklemeniz gerekir.  
  
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
  
3. Formun sağ üst köşesinde, <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimi tutacak bir denetim ekleyin.  
  
4. Forma aşağıdaki <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> denetimleri ekleyin.  
  
    |Ad|Metin|  
    |----------|----------|  
    |groupBox1|Arka plan rengi|  
    |groupBox2|Ön plan rengi|  
    |groupBox3|Yazı tipi boyutu|  
    |groupBox4|Yazı tipi ailesi|  
    |groupBox5|Yazı tipi stili|  
    |groupBox6|Yazı tipi genişliği|  
    |groupBox7|Denetimdeki veriler|  
  
5. <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> Denetimlere aşağıdaki <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> denetimleri ekleyin.  
  
    |GroupBox|Ad|Metin|  
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
  
6. <xref:System.Windows.Forms.Label?displayProperty=nameWithType> Son<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>' a aşağıdaki denetimleri ekleyin. Bu denetimler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim tarafından döndürülen verileri görüntüler.  
  
    |GroupBox|Ad|Metin|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Ad:|  
    |groupBox7|lblAddress|Sokak adresi:|  
    |groupBox7|lblCity|Baş|  
    |groupBox7|lblState|Durumunda|  
    |groupBox7|lblZip|Zip|  
  
### <a name="initializing-the-form"></a>Form başlatılıyor  
 Genellikle barındırma kodunu formun <xref:System.Windows.Forms.Form.Load> olay işleyicisine uygulayamazsınız. Aşağıdaki kod, <xref:System.Windows.Forms.Form.Load> olay işleyicisini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin <xref:System.Windows.FrameworkElement.Loaded> olayı için bir işleyiciyi ve daha sonra kullanılan çeşitli genel değişkenlerin bildirimlerini gösterir.  
  
 Windows Form Tasarımcısı, bir <xref:System.Windows.Forms.Form.Load> olay işleyicisi oluşturmak için forma çift tıklayın. Form1.cs 'in en üstünde aşağıdaki `using` deyimleri ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Mevcut `Form1` sınıfın içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Yukarıdaki kodda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yöntemi bir denetimi barındırmak için genel prosedürü gösterir: `Form1_Load`  
  
1. Yeni <xref:System.Windows.Forms.Integration.ElementHost> bir nesne oluşturun.  
  
2. Denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini olarak <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>ayarlayın.  
  
3. <xref:System.Windows.Forms.Integration.ElementHost> Denetimi<xref:System.Windows.Forms.Control.Controls%2A>denetimin koleksiyonuna ekleyin. <xref:System.Windows.Forms.Panel>  
  
4. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Denetimin bir örneğini oluşturun.  
  
5. <xref:System.Windows.Forms.Integration.ElementHost> Denetimi<xref:System.Windows.Forms.Integration.ElementHost.Child%2A> denetimin özelliğine atayarak bileşik denetimi form üzerinde barındırın.  
  
 `Form1_Load` Yöntemdeki kalan iki satır, işleyicileri iki denetim olayına ekler:  
  
- `OnButtonClick`Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında bileşik denetim tarafından tetiklenen özel bir olaydır. Kullanıcının yanıtını almak ve Kullanıcı tarafından belirtilen verileri toplamak için olayını işleyebilirsiniz.  
  
- <xref:System.Windows.FrameworkElement.Loaded>, tam olarak yüklendiğinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim tarafından oluşturulan standart bir olaydır. Örnek, denetimin özelliklerini kullanarak birkaç genel değişken başlatması gerektiğinden olay burada kullanılır. Formun <xref:System.Windows.Forms.Form.Load> olayı sırasında, denetim tam olarak yüklenmez ve bu değerler olarak `null`ayarlanır. Bu özelliklere erişebilmek için denetimin <xref:System.Windows.FrameworkElement.Loaded> olayının gerçekleşene kadar beklemeniz gerekir.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Olay işleyicisi önceki kodda gösterilmiştir. `OnButtonClick` İşleyici, sonraki bölümde ele alınmıştır.  
  
### <a name="handling-onbuttonclick"></a>OnButtonClick işleme  
 Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında olayoluşur.`OnButtonClick`  
  
 Olay işleyicisi, hangi düğmenin tıklandığını belirleyen `IsOK` olay bağımsız değişkeninin alanını denetler. `lbl` Veri<xref:System.Windows.Forms.Label> değişkenleri, daha önce ele alınan denetimlere karşılık gelir. Kullanıcı **Tamam** düğmesine tıkladığında, denetimin <xref:System.Windows.Controls.TextBox> denetimlerindeki veriler ilgili <xref:System.Windows.Forms.Label> denetime atanır. Kullanıcı **iptal**' i tıklarsa, <xref:System.Windows.Forms.Label.Text%2A> değerler varsayılan dizelere ayarlanır.  
  
 Aşağıdaki düğmeye tıklayarak `Form1` sınıfına olay işleyicisi kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Uygulamayı derleyin ve çalıştırın. WPF bileşik denetimine biraz metin ekleyin ve ardından **Tamam**' a tıklayın. Metin, etiketlerde görüntülenir. Bu noktada radyo düğmelerini işlemek için kod eklenmedi.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Denetimin görünümünü değiştirme  
 Formdaki denetimler, kullanıcının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin ön plan ve arka plan renklerini ve çeşitli yazı tipi özelliklerini değiştirmesine olanak sağlar. <xref:System.Windows.Forms.RadioButton> Arka plan rengi <xref:System.Windows.Forms.Integration.ElementHost> nesnesi tarafından gösterilir. Kalan özellikler, denetimin özel özellikleri olarak gösterilir.  
  
 Olay işleyicileri oluşturmak <xref:System.Windows.Forms.RadioButton.CheckedChanged> için <xref:System.Windows.Forms.RadioButton> formdaki her denetime çift tıklayın. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Olay işleyicilerini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Uygulamayı derleyin ve çalıştırın. WPF bileşik denetimindeki etkiyi görmek için farklı radyo düğmelerine tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF 'de Windows Forms Bileşik denetim barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: Windows Forms 3-b WPF bileşik denetimini barındırma](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
