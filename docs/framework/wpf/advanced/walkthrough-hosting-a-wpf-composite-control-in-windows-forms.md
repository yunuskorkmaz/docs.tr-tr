---
title: Windows Formlarında WPF bileşik denetimi barındır
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: e3326f654e05ef7d487a76f076f8ad0da3637096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187241"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamaları oluşturmak için zengin bir ortam sağlar. Ancak, Windows Forms koduna önemli bir yatırımınız olduğunda, mevcut Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanızı sıfırdan yeniden yazmak yerine genişletmek daha etkili olabilir. Yaygın bir senaryo, Windows Forms uygulamanızda uygulanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir veya daha fazla denetimi katıştırmak istediğinizde olur. WPF denetimlerini özelleştirme hakkında daha fazla bilgi için [bkz.](../controls/control-customization.md)  
  
 Bu iz, Windows Forms uygulamasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri girişi gerçekleştirmek için bileşik denetim barındıran bir uygulama boyunca size adım atar. Kompozit kontrol bir DLL olarak paketlenmiştir. Bu genel yordam daha karmaşık uygulamalara ve denetimlere genişletilebilir. Bu izlenecek yol, Görünüm ve İşlevsellik açısından [Walkthrough: Hosting a Windows Forms Bileşik Denetimi'nin WPF'de](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)neredeyse aynı olması için tasarlanmıştır. Birincil fark, barındırma senaryosunun tersine çevrilmiş olmasıdır.  
  
 Geçiş bölümü iki bölüme ayrılmıştır. İlk bölümde kısaca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimin uygulanması açıklanır. İkinci bölümde, bir Windows Forms uygulamasında bileşik denetimin nasıl barındırılabildiğini, denetimden olayları nasıl alacağı ve denetimin bazı özelliklerine nasıl erişilen ayrıntılı olarak açıklanmıştır.  
  
 Bu gözden geçirmede gösterilen görevler şunlardır:  
  
- WPF bileşik denetimi nin uygulanması.  
  
- Windows Forms ana bilgisayar uygulamasını uygulama.  
  
 Bu izbarada gösterilen görevlerin tam kod listesi için Windows [Formlar Örneğinde WPF Bileşik Denetimi Barındırma](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl)bölümüne bakın.  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu walkthrough tamamlamak için Visual Studio gerekir.  
  
## <a name="implementing-the-wpf-composite-control"></a>WPF Kompozit Denetiminin Uygulanması  
 Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örnekte kullanılan bileşik denetim, kullanıcının adını ve adresini alan basit bir veri giriş formudur. Kullanıcı görevin tamamladığını belirtmek için iki düğmeden birini tıklattığında, denetim bu bilgileri ana bilgisayara döndürmek için özel bir olay yükseltir. Aşağıdaki resimde işlenen denetim gösterilmektedir.

 Aşağıdaki resimde WPF bileşik denetimi gösterilmektedir:

 ![Basit bir WPF denetimini gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Visual Studio'yu başlatın ve **Yeni Proje** iletişim kutusunu açın.  
  
2. Visual C# ve Windows kategorisinde **WPF Kullanıcı Denetim Kitaplığı** şablonu'nu seçin.  
  
3. Yeni projeyi `MyControls`adlandırın.  
  
4. Konum için, uygun şekilde adlandırılmış üst düzey `WindowsFormsHostingWpfControl`bir klasör belirtin, örneğin. Daha sonra, ana bilgisayar uygulamasını bu klasöre koyarsınız.  
  
5. Projeyi oluşturmak için **Tamam**'a tıklayın. Varsayılan proje adlı `UserControl1`tek bir denetim içerir.  
  
6. Çözüm Gezgini'nde, `MyControl1`''yi yeniden adlandırın. `UserControl1`  
  
 Projenizde aşağıdaki sistem DLs referansları olmalıdır. Bu DL'lerden herhangi biri varsayılan olarak dahil değilse, bunları projenize ekleyin.  
  
- Presentationcore  
  
- Presentationframework  
  
- Sistem  
  
- Windowsbase  
  
### <a name="creating-the-user-interface"></a>Kullanıcı Arabirimini Oluşturma  
 Kompozit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] denetim için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]uygulanır. Bileşik kontrol [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] beş <xref:System.Windows.Controls.TextBox> elementten oluşur. Her <xref:System.Windows.Controls.TextBox> öğenin <xref:System.Windows.Controls.TextBlock> etiket olarak hizmet veren ilişkili bir öğesi vardır. Alt kısmında <xref:System.Windows.Controls.Button> iki öğe vardır, **Tamam** ve **İptal**. Kullanıcı her iki düğmeyi tıklattığında, denetim bilgileri ana bilgisayara döndürmek için özel bir olay yükseltir.  
  
#### <a name="basic-layout"></a>Temel Düzen  
 Çeşitli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeler bir <xref:System.Windows.Controls.Grid> öğe içinde yer almaktadır. Bileşik denetimin içeriğini HTML'de bir <xref:System.Windows.Controls.Grid> `Table` öğeyi kullandığınız gibi düzenlemek için kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ayrıca bir <xref:System.Windows.Documents.Table> öğeye <xref:System.Windows.Controls.Grid> sahiptir, ancak daha hafif tir ve basit düzen görevleri için daha uygundur.  
  
 Aşağıdaki XAML temel düzeni gösterir. Bu <xref:System.Windows.Controls.Grid> XAML, öğedeki sütun ve satır sayısını belirterek denetimin genel yapısını tanımlar.  
  
 MyControl1.xaml'da, varolan XAML'yi aşağıdaki XAML ile değiştirin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Izgaraya TextBlock ve TextBox Öğeleri Ekleme  
 Öğenin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Grid.RowProperty> ve özniteliklerini uygun satır ve <xref:System.Windows.Controls.Grid.ColumnProperty> sütun numarasına ayarlayarak ızgaraya bir öğe yer. Satır ve sütun numaralandırmanın sıfır tabanlı olduğunu unutmayın. Bir öğenin özniteliğini ayarlayarak <xref:System.Windows.Controls.Grid.ColumnSpanProperty> birden çok sütuna yayılmasını sağlayabilirsiniz. Öğeler hakkında <xref:System.Windows.Controls.Grid> daha fazla bilgi için [bkz.](../controls/how-to-create-a-grid-element.md)  
  
 Aşağıdaki XAML, öğeleri ızgaraya <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBlock> düzgün bir <xref:System.Windows.Controls.Grid.RowProperty> <xref:System.Windows.Controls.Grid.ColumnProperty> şekilde yerleştirmek üzere ayarlanmış bileşik denetimin ve elemanlarıve özniteliklerini gösterir.  
  
 MyControl1.xaml'da, öğenin içine aşağıdaki <xref:System.Windows.Controls.Grid> XAML'yi ekleyin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>UI Öğelerini Şekillendirme  
 Veri giriş formundaki öğelerin çoğu benzer bir görünüme sahiptir, bu da özelliklerinin birkaçı için aynı ayarlara sahip oldukları anlamına gelir. Önceki XAML, her öğenin özniteliklerini ayrı <xref:System.Windows.Style> ayrı ayarlamak yerine, öğe sınıfları için standart özellik ayarlarını tanımlamak için öğeler kullanır. Bu yaklaşım, denetimin karmaşıklığını azaltır ve tek bir stil özniteliği ile birden çok öğenin görünümünü değiştirmenize olanak tanır.  
  
 Öğeler <xref:System.Windows.Style> öğenin <xref:System.Windows.Controls.Grid> <xref:System.Windows.FrameworkElement.Resources%2A> özelliğinde bulunur, böylece denetimdeki tüm öğeler tarafından kullanılabilirler. Bir stil adlandırılmışsa, stiladına bir <xref:System.Windows.Style> öğe kümesi ekleyerek bir öğeye uygularsınız. Adlandırılmış olmayan stiller öğeiçin varsayılan stil olur. Stiller hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha fazla bilgi için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.  
  
 Aşağıdaki XAML bileşik <xref:System.Windows.Style> denetim için öğeleri gösterir. Stillerin öğelere nasıl uygulandığını görmek için önceki XAML'ye bakın. Örneğin, son <xref:System.Windows.Controls.TextBlock> öğe `inlineText` stili vardır ve <xref:System.Windows.Controls.TextBox> son öğe varsayılan stili kullanır.  
  
 MyControl1.xaml'da, başlangıç öğesinden hemen <xref:System.Windows.Controls.Grid> sonra aşağıdaki XAML'yi ekleyin.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Tamam ve İptal Düğmelerini Ekleme  
 Bileşik denetimdeki son öğeler, <xref:System.Windows.Controls.Grid>son satırın ilk iki sütunundan oluşan **Tamam** ve **İptal** <xref:System.Windows.Controls.Button> öğeleridir. Bu öğeler, `ButtonClicked`ortak bir olay işleyicisi ve önceki XAML tanımlanan varsayılan <xref:System.Windows.Controls.Button> stil kullanın.  
  
 MyControl1.xaml'da son <xref:System.Windows.Controls.TextBox> öğeden sonra aşağıdaki XAML'yi ekleyin. Kompozit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kontrolün bir parçası tamamlandı.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Kod Arkası Dosyasını Uygulama  
 kod arkası dosyası, MyControl1.xaml.cs, üç temel görevleri uygular:
  
1. Kullanıcı düğmelerden birini tıklattığında meydana gelen olayı işler.  
  
2. <xref:System.Windows.Controls.TextBox> Öğelerden verileri alır ve özel bir olay bağımsız değişken nesnesi içinde paketler.  
  
3. Kullanıcının `OnButtonClick` bittiğini ana bilgisayara belirten özel olayı yükseltir ve verileri ana bilgisayara geri aktarın.  
  
 Denetim, görünümü değiştirmenizi sağlayan bir dizi renk ve yazı tipi özelliğini de ortaya çıkarır. Windows <xref:System.Windows.Forms.Integration.WindowsFormsHost> Forms denetimini barındırmak için kullanılan <xref:System.Windows.Forms.Integration.ElementHost> sınıfın aksine, sınıf <xref:System.Windows.Controls.Panel.Background%2A> yalnızca denetimin özelliğini ortaya çıkarır. Bu kod örneği ile Walkthrough'da tartışılan örnek arasındaki benzerliği korumak [için: WPF'de Windows Forms Bileşik Denetimi](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)barındırma, denetim kalan özellikleri doğrudan ortaya çıkarır.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Kod Arkası Dosyasının Temel Yapısı  
 Kod arkası dosyası, `MyControls`iki sınıf `MyControl1` içeren tek bir ad alanı `MyControlEventArgs`ve .  
  
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
  
 Birinci sınıf, `MyControl1`MyControl1.xaml [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tanımlanan işlevselliğini uygulayan kodu içeren kısmi bir sınıftır. MyControl1.xaml ayrıştırıldığında, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı kısmi sınıfa dönüştürülür ve iki kısmi sınıf derlenmiş denetimi oluşturmak üzere birleştirilir. Bu nedenle, kod arkasındaki dosyadaki sınıf adı MyControl1.xaml atanan sınıf adı eşleşmesi gerekir ve denetimin kök öğesinden devralmak gerekir. İkinci sınıf, `MyControlEventArgs`verileri ana bilgisayara geri göndermek için kullanılan bir olay bağımsız değişkenleri sınıfıdır.  
  
 Açık MyControl1.xaml.cs. Varolan sınıf bildirimini aşağıdaki adı ve 'den <xref:System.Windows.Controls.Grid>devralabilecek şekilde değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Denetimi Başlatma  
 Aşağıdaki kod birkaç temel görevi uygular:  
  
- Özel bir olayı `OnButtonClick`ve ilgili temsilcisini `MyControlEventHandler`bildirir.  
  
- Kullanıcının verilerini depolayan birkaç özel genel değişken oluşturur. Bu veriler karşılık gelen özellikler aracılığıyla ortaya çıkarır.  
  
- Denetimin <xref:System.Windows.FrameworkElement.Loaded> olayı için `Init`bir işleyici uygular. Bu işleyici, MyControl1.xaml'da tanımlanan değerleri atayarak genel değişkenleri başolarak ele verir. Bunu yapmak için, <xref:System.Windows.FrameworkElement.Name%2A> bu öğenin <xref:System.Windows.Controls.TextBlock> özellik `nameLabel`ayarlarına erişmek için tipik bir öğe, atanan kullanır.  
  
 Varolan oluşturucuyu silin ve sınıfınıza `MyControl1` aşağıdaki kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Düğmelerin Tıklama Olaylarını İşleme  
 Kullanıcı, **Tamam** düğmesini veya **İptal** düğmesini tıklatarak veri girişi görevinin tamamlanır olduğunu belirtir. Her iki düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> de aynı `ButtonClicked`olay işleyicisi kullanır. Her iki düğmede `btnOK` de `btnCancel`bir ad veya, işleyicinin `sender` bağımsız değişkenin değerini inceleyerek hangi düğmenin tıklatıldığını belirlemesini sağlar. Işleyici aşağıdakileri yapar:  
  
- Öğelerden `MyControlEventArgs` verileri içeren bir nesne oluşturur. <xref:System.Windows.Controls.TextBox>  
  
- Kullanıcı **İptal** düğmesini tıklattıysa, `MyControlEventArgs` nesnenin `IsOK` özelliğini ' olarak `false`ayarlar.  
  
- Kullanıcının `OnButtonClick` bittiğini ana bilgisayara göstermek için olayı yükseltir ve toplanan verileri geri geçirir.  
  
 Yöntemden sonra sınıfınıza `MyControl1` aşağıdaki kodu ekleyin. `Init`  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Özellikler Oluşturma  
 Sınıfın geri kalanı, daha önce tartışılan genel değişkenlere karşılık gelen özellikleri ortaya çıkarır. Bir özellik değiştiğinde, ayarlanan erişimci, ilgili öğe özelliklerini değiştirerek ve temel global değişkenleri güncelleştirerek denetimin görünümünü değiştirir.  
  
 Sınıfınıza `MyControl1` aşağıdaki kodu ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Verileri Ana Bilgisayara Geri Gönderme  
 Dosyadaki son bileşen, `MyControlEventArgs` toplanan verileri ana bilgisayara geri göndermek için kullanılan sınıftır.  
  
 Ad alanınıza `MyControls` aşağıdaki kodu ekleyin. Uygulama basittir ve daha fazla tartışılmadı.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Çözümü derleyin. Yapı MyControls.dll adlı bir DLL üretecek.  
  
<a name="winforms_host_section"></a>
## <a name="implementing-the-windows-forms-host-application"></a>Windows Forms Host Uygulamasını Uygulama  
 Windows Forms ana bilgisayar <xref:System.Windows.Forms.Integration.ElementHost> uygulaması, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimi barındırmak için bir nesne kullanır. Uygulama, bileşik `OnButtonClick` denetimden verileri almak için olayı işler. Uygulama da denetimgörünümünü değiştirmek için kullanabileceğiniz seçenek düğmeleri kümesi vardır. Aşağıdaki resimde uygulama gösterilmektedir.  

Aşağıdaki resimde, Windows Forms uygulamasında barındırılan bir WPF bileşik denetimi gösterilmektedir"  

 ![Avalon denetimini barındıran bir Windows Formu gösteren scteenshot.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi başlatmak için:  
  
1. Visual Studio'yu başlatın ve **Yeni Proje** iletişim kutusunu açın.  
  
2. Visual C# ve Windows kategorisinde **Windows Forms Uygulama** şablonu'nu seçin.  
  
3. Yeni projeyi `WFHost`adlandırın.  
  
4. Konum için, MyControls projesini içeren aynı üst düzey klasörü belirtin.  
  
5. Projeyi oluşturmak için **Tamam**'a tıklayın.  
  
 Ayrıca, içeren DLL `MyControl1` ve diğer derlemeler başvurular eklemeniz gerekir.  
  
1. Çözüm Gezgini'nde proje adını sağ tıklatın ve **Başvuru Ekle'yi**seçin.  
  
2. **Gözat** sekmesini tıklatın ve MyControls.dll içeren klasöre göz atın. Bu gözden geçirme için bu klasör MyControls\bin\Debug'dir.  
  
3. MyControls.dll'yi seçin ve ardından **Tamam'ı**tıklatın.  
  
4. Aşağıdaki derlemelere başvurular ekleyin.  
  
    - Presentationcore  
  
    - Presentationframework  
  
    - Sistem.Xaml  
  
    - Windowsbase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Uygulama için Kullanıcı Arabiriminin Uygulanması  
 Windows Form uygulaması için Kullanıcı Arabirimi, WPF bileşik denetimiyle etkileşimde kalmak için çeşitli denetimler içerir.  
  
1. Windows Form Tasarımcısı'nda Form1'i açın.  
  
2. Denetimleri karşılamak için formu büyütün.  
  
3. Formun sağ üst köşesinde, <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimi tutmak için bir denetim ekleyin.  
  
4. Forma aşağıdaki <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> denetimleri ekleyin.  
  
    |Adı|Metin|  
    |----------|----------|  
    |grupBox1|Arka Plan Rengi|  
    |grupBox2|Ön Plan Rengi|  
    |grupBox3|Yazı Tipi Boyutu|  
    |grupBox4|Font Ailesi|  
    |grupBox5|Yazı Tipi Stili|  
    |grupBox6|Yazı Tipi Ağırlığı|  
    |grupBox7|Denetimden gelen veriler|  
  
5. Denetimlere <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> aşağıdaki denetimleri <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> ekleyin.  
  
    |GroupBox|Adı|Metin|  
    |--------------|----------|----------|  
    |grupBox1|radioBackgroundOrijinal|Özgün|  
    |grupBox1|radyoBackgroundLightGreen|Işık Yeşili|  
    |grupBox1|radyoBackgroundLightSalmon|LightSalmon|  
    |grupBox2|radioForegroundOrijinal|Özgün|  
    |grupBox2|radioForegroundRed|Red|  
    |grupBox2|radioForegroundSarı|Yellow|  
    |grupBox3|radioSizeOriginal|Özgün|  
    |grupBox3|radioSizeTen|10|  
    |grupBox3|radioSizeTwelve|12|  
    |grupBox4|radioFamilyOriginal|Özgün|  
    |grupBox4|radyoFamilyTimes|Times Yeni Roma|  
    |grupBox4|radioFamilyWingDings|Wingdings|  
    |grupBox5|radioStyleOriginal|Normal|  
    |grupBox5|radyoStyleItalic|İtalik|  
    |grupBox6|radioWeightOriginal|Özgün|  
    |grupBox6|radyoWeightBold|Kalın|  
  
6. Aşağıdaki <xref:System.Windows.Forms.Label?displayProperty=nameWithType> denetimleri sonuncuya <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>ekleyin. Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimler, bileşik denetim tarafından döndürülen verileri görüntüler.  
  
    |GroupBox|Adı|Metin|  
    |--------------|----------|----------|  
    |grupBox7|lblName|Ad:|  
    |grupBox7|lblAddress|Sokak Adresi:|  
    |grupBox7|lblCity|Şehir:|  
    |grupBox7|lblState|Durum:|  
    |grupBox7|lblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Formu başlatma  
 Genellikle formun <xref:System.Windows.Forms.Form.Load> olay işleyicisinde barındırma kodunu uygularsınız. Aşağıdaki kod, <xref:System.Windows.Forms.Form.Load> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetimolayıiçin <xref:System.Windows.FrameworkElement.Loaded> bir işleyici ve daha sonra kullanılan birkaç genel değişkenin bildirimlerini olay işleyicisini gösterir.  
  
 Windows Forms Designer'da, <xref:System.Windows.Forms.Form.Load> olay işleyicisi oluşturmak için formu çift tıklatın. Form1.cs üst kısmında, aşağıdaki `using` ifadeleri ekleyin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Varolan `Form1` sınıfın içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Önceki `Form1_Load` koddaki yöntem, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi barındırmak için genel yordamı gösterir:  
  
1. Yeni <xref:System.Windows.Forms.Integration.ElementHost> bir nesne oluşturun.  
  
2. Denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3. <xref:System.Windows.Forms.Integration.ElementHost> Denetimi <xref:System.Windows.Forms.Control.Controls%2A> denetimin <xref:System.Windows.Forms.Panel> koleksiyonuna ekleyin.  
  
4. Denetimin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örneğini oluşturun.  
  
5. Denetimi denetimin <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğine atayarak formdaki bileşik denetimi barındırın.  
  
 `Form1_Load` Yöntemde kalan iki satır işleyicileri iki denetim olaylarına ataştırın:  
  
- `OnButtonClick`kullanıcı **Tamam** veya **İptal** düğmesini tıklattığında bileşik denetim tarafından ateşlenen özel bir olaydır. Kullanıcının yanıtını almak ve kullanıcının belirttiği verileri toplamak için olayı işlersiniz.  
  
- <xref:System.Windows.FrameworkElement.Loaded>tam olarak yüklendiğinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim tarafından yükseltilen standart bir olaydır. Örnek denetim özellikleri kullanarak birkaç genel değişkenler başlatılması gerektiğinden olay burada kullanılır. Formun <xref:System.Windows.Forms.Form.Load> olay sırasında, denetim tam olarak yüklenmez ve bu değerler `null`hala . Bu özelliklere erişebilmeniz için <xref:System.Windows.FrameworkElement.Loaded> denetimin olayının oluşmasını beklemeniz gerekir.  
  
 Olay <xref:System.Windows.FrameworkElement.Loaded> işleyicisi önceki kodda gösterilir. Işleyici `OnButtonClick` sonraki bölümde ele alınmıştır.  
  
### <a name="handling-onbuttonclick"></a>İşleme OnButtonClick  
 Olay, `OnButtonClick` kullanıcı **Tamam** veya **İptal** düğmesini tıklattığında oluşur.  
  
 Olay işleyicisi, hangi `IsOK` düğmenin tıklatıldığını belirlemek için olay bağımsız değişkeninin alanını denetler. `lbl` *Veri* değişkenleri daha <xref:System.Windows.Forms.Label> önce tartışılan denetimlere karşılık gelir. Kullanıcı **Tamam** düğmesini tıklatarsa, denetim <xref:System.Windows.Controls.TextBox> denetimlerinden elde edilen veriler <xref:System.Windows.Forms.Label> ilgili denetime atanır. Kullanıcı **İptal'i**tıklatıyorsa, <xref:System.Windows.Forms.Label.Text%2A> değerler varsayılan dizeleri olarak ayarlanır.  
  
 `Form1` Sınıfa olay işleyicisi kodunu aşağıdaki düğmeyi tıklatın.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Uygulamayı derleyin ve çalıştırın. WPF bileşik denetimine bazı metin ekleyin ve ardından **Tamam'ı**tıklatın. Metin etiketlerde görünür. Bu noktada, radyo düğmelerini işlemek için kod eklenmedi.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Denetimin Görünümünü Değiştirme  
 Formüzerindeki <xref:System.Windows.Forms.RadioButton> denetimler, kullanıcının bileşik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimin ön planını ve arka plan renklerini ve birkaç yazı tipi özelliğini değiştirmesini sağlar. Arka plan rengi <xref:System.Windows.Forms.Integration.ElementHost> nesne tarafından açıktakalır. Kalan özellikler denetimin özel özellikleri olarak ortaya çıkarır.  
  
 Olay işleyicileri oluşturmak <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.RadioButton.CheckedChanged> için formdaki her denetimi çift tıklatın. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Olay işleyicilerini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Uygulamayı derleyin ve çalıştırın. WPF bileşik denetimi üzerindeki etkisini görmek için farklı radyo düğmelerini tıklatın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
