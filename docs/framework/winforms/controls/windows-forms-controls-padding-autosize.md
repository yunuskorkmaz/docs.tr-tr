---
title: 'İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Formları Denetimlerini Düzenleme'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
ms.openlocfilehash: 52bc75135e4f8cf5b9c1888b2ad9f5e278c1d6e2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597868"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Formları Denetimlerini Düzenleme
Formunuzdaki denetimleri kesin yerleşimini birçok uygulama için yüksek öncelik taşır. **Windows Form Tasarımcısı** , bunu gerçekleştirmek için çok sayıda düzen araçları sağlar. En önemli üç olan <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, ve <xref:System.Windows.Forms.Control.AutoSize%2A> tüm Windows Forms denetimleri var olan özellikleri.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Tutar diğer denetimleri belirtilen bir denetimin kenarlık uzaklıkta çevresindeki boşluk özelliği tanımlar.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Özelliği, denetimin içeriği tutan bir denetimin iç alanı tanımlar (örneğin, değerini kendi <xref:System.Windows.Forms.Control.Text%2A> özelliği) belirtilen bir denetimin kenarlık uzaklığı.  
  
 Aşağıdaki çizimde gösterildiği <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> denetim özellikleri.  
  
 ![Doldurma ve kenar boşlukları için Windows Forms denetimlerine](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Özelliği bir denetim kendi boyutunu içeriğine otomatik olarak bildirir. Kendi özgün değerinden daha küçük olacak şekilde boyutlandırılmayacağını <xref:System.Windows.Forms.Control.Size%2A> özelliği ve değerini hesap, <xref:System.Windows.Forms.Control.Padding%2A> özelliği.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Bir Windows Forms projesi oluşturma  
  
-   İçin Denetim kenar boşluklarını ayarlama  
  
-   Doldurma için denetimleri ayarlama  
  
-   Denetimleri otomatik boyutlandırma  
  
 İşlemi tamamladığınızda, bu önemli bir düzen özellikleri tarafından oynadığı rol, bir anlayışa sahip olacaksınız.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım projeyi oluşturmak ve formu ayarlamaktır.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Oluşturma bir **Windows uygulama** adlı proje `LayoutExample`. Daha fazla bilgi için [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Formda seçin **Windows Form Tasarımcısı**.  
  
## <a name="setting-margins-for-your-controls"></a>İçin Denetim kenar boşluklarını ayarlama  
 Varsayılan uzaklığını kullanarak, denetimler arasında ayarlayabilirsiniz <xref:System.Windows.Forms.Control.Margin%2A> özelliği. Bir denetimi taşıdığınızda, başka bir denetim için yeterli kapatın, iki denetim kenar boşluklarını gösteren bir snapline görürsünüz. Taşınan bir denetim kenar boşluklarını tarafından tanımlanan uzaklığı için de yaslanacak.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Margin özelliği kullanarak, form üzerindeki denetimleri düzenlemek için  
  
1.  İki <xref:System.Windows.Forms.Button> denetimler **araç kutusu** formunuza.  
  
2.  Birini <xref:System.Windows.Forms.Button> denetler ve bunu diğer yakın temas neredeyse kadar.  
  
     Bunlar arasında görünür snapline gözlemleyin. Bu uzaklık iki denetimi toplamıdır <xref:System.Windows.Forms.Control.Margin%2A> değerleri. Bu uzaklık taşıdığınız denetim yapıştırır. Ayrıntılar için bkz [izlenecek yol: Windows Forms dayama çizgileri kullanarak düzenleme denetimlerinde](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Değişiklik <xref:System.Windows.Forms.Control.Margin%2A> özelliği genişleterek denetimlerden birini <xref:System.Windows.Forms.Control.Margin%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 20 özelliği.  
  
4.  Birini <xref:System.Windows.Forms.Button> denetler ve diğer yakın taşıyın.  
  
     Snapline kenar boşluğu değerlerinin toplamı uzun ve denetim diğer denetiminden daha büyük bir uzaklık yaslanıp tanımlama.  
  
5.  Değişiklik <xref:System.Windows.Forms.Control.Margin%2A> genişleterek seçilen denetimin özellik <xref:System.Windows.Forms.Control.Margin%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.Top%2A> 5 özelliği.  
  
6.  Seçili denetimin diğer denetim altına taşıyın ve snapline kısa olup olmadığına bakın. Seçili denetimin diğer denetimi sola taşı ve snapline 4. adımda gözlenen değer saklar gözlemleyin.  
  
7.  Her yönlerinin ayarlayabilirsiniz <xref:System.Windows.Forms.Control.Margin%2A> özelliği <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, farklı değerler veya bunları tüm ile aynı değeri ayarlayabilirsiniz <xref:System.Windows.Forms.Padding.All%2A> özelliği.  
  
## <a name="setting-padding-for-your-controls"></a>Doldurma için denetimleri ayarlama  
 Uygulamanız için gereken kesin düzenini elde etmek için denetimlerinizi genellikle alt denetimler içerir. Alt denetimin kenarlığının yakınlık üst Denetimin kenarlık belirtmek istediğinizde, üst denetimin kullanın <xref:System.Windows.Forms.Control.Padding%2A> alt denetimin birlikte özelliği <xref:System.Windows.Forms.Control.Margin%2A> özelliği. <xref:System.Windows.Forms.Control.Padding%2A> Özelliği yakınlık denetimin içeriğini denetlemek için de kullanılır (örneğin, bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliği) kenarlıkları için.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Formunuzdaki doldurmayı kullanarak denetimleri düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza.  
  
2.  Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`.  
  
3.  Değişiklik <xref:System.Windows.Forms.Control.Padding%2A> özelliği genişleterek <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 5 özelliği.  
  
     Yeni doldurma yer sağlamak için denetimi genişletir.  
  
4.  Sürükleme bir <xref:System.Windows.Forms.GroupBox> denetimi **araç kutusu** formunuza. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.GroupBox> denetimi. Konum <xref:System.Windows.Forms.Button> ile sağ alt köşesindeki biter denetlemesini <xref:System.Windows.Forms.GroupBox> denetimi.  
  
     Görünür dayama çizgileri gözlemleyin <xref:System.Windows.Forms.Button> denetim yaklaştığında alt ve sağ kenarları <xref:System.Windows.Forms.GroupBox> denetimi. Bu dayama çizgileri karşılık <xref:System.Windows.Forms.Control.Margin%2A> özelliği <xref:System.Windows.Forms.Button>.  
  
5.  Değişiklik <xref:System.Windows.Forms.GroupBox> denetimin <xref:System.Windows.Forms.Control.Padding%2A> genişleterek özelliği <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 20 özelliği.  
  
6.  Seçin <xref:System.Windows.Forms.Button> denetimine <xref:System.Windows.Forms.GroupBox> denetlemek ve ortasına doğru taşıma <xref:System.Windows.Forms.GroupBox>.  
  
     Dayama çizgileri kenarlıklarını daha büyük bir uzaklık görünür <xref:System.Windows.Forms.GroupBox> denetimi. Bu uzaklık toplamıdır <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliği ve <xref:System.Windows.Forms.GroupBox> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliği.  
  
## <a name="automatically-sizing-your-controls"></a>Denetimleri otomatik boyutlandırma  
 Tasarım zamanında olduğu gibi bazı uygulamalarda, bir denetimin boyutunu aynı çalışma zamanında olacaktır değil. Metnin bir <xref:System.Windows.Forms.Button> denetimi, örneğin, alınması bir veritabanından ve uzunluğunu önceden bilinmeyen.  
  
 Zaman <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği `true`, Denetim kendisini içeriğine göre boyutlanır. Daha fazla bilgi için [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>AutoSize özelliği kullanarak, bir form üzerinde denetimleri düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza.  
  
2.  Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`.  
  
3.  Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğini "**bu düğmeye sahip bir uzun dize metin özelliğini**."  
  
     Değişiklik yaparsanız <xref:System.Windows.Forms.Button> denetim kendisini yeni metin sığacak şekilde yeniden boyutlandırır.  
  
4.  Başka bir sürükleyin <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza.  
  
5.  Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğini "**bu düğme metin özelliğini uzun bir dize içeriyor.**"  
  
     Değişiklik yaparsanız <xref:System.Windows.Forms.Button> denetimi değil yeniden boyutlandırma kendisi ve metin ile denetimin sağ kenarı kırpılır.  
  
6.  Değişiklik <xref:System.Windows.Forms.Control.Padding%2A> özelliği genişleterek <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 5 özelliği.  
  
     Denetimin iç metindeki tüm dört yüzüne kırpılır.  
  
7.  Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`.  
  
     <xref:System.Windows.Forms.Button> Denetim kendisini dizenin tamamını kapsayacak şekilde yeniden boyutlandırır. Metin etrafına doldurma ayrıca, eklenmiş neden <xref:System.Windows.Forms.Button> tüm dört yönde genişletmek için denetimi.  
  
8.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza. Formun sağ alt köşenin yakınında bulunan konumlandırın.  
  
9. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`.  
  
10. Ayarlama <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğini "**bu düğme metin özelliğini uzun bir dize içeriyor.**"  
  
     Değişiklik yaparsanız <xref:System.Windows.Forms.Button> denetimi yeniden boyutlandırır sola doğru kendisi. Genel olarak, otomatik boyutlandırma ters yönde bir denetimin boyutunu artırır, <xref:System.Windows.Forms.Control.Anchor%2A> özellik ayarı.  
  
## <a name="autosize-and-autosizemode-properties"></a>AutoSize ve AutoSizeMode özellikleri  
 Bazı denetimler Destek `AutoSizeMode` özelliği bir denetimin otomatik boyutlandırma davranışı üzerinde daha ayrıntılı denetim sağlar.  
  
#### <a name="to-use-the-autosizemode-property"></a>AutoSizeMode özelliği kullanmak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Panel> denetimi **araç kutusu** formunuza.  
  
2.  Değerini <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.Panel> denetimi.  
  
4.  Bir yerde <xref:System.Windows.Forms.Button> sağ alt köşenin yakınında bulunan denetim <xref:System.Windows.Forms.Panel> denetimi.  
  
5.  Seçin <xref:System.Windows.Forms.Panel> denetlemek ve sağ alt boyutlandırma tutamacı alın. Yeniden boyutlandırma <xref:System.Windows.Forms.Panel> büyük ve küçük olacak şekilde denetim.  
  
    > [!NOTE]
    >  Özgürce boyutlandırabilirsiniz <xref:System.Windows.Forms.Panel> denetimidir, ancak olamaz boyutunu, konumunu daha küçük <xref:System.Windows.Forms.Button> denetimin sağ alt köşedeki. Bu davranış, varsayılan değeri tarafından belirtilen `AutoSizeMode` özelliğinin <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Değerini <xref:System.Windows.Forms.Panel> denetimin `AutoSizeMode` özelliğini <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     <xref:System.Windows.Forms.Panel> Denetim boyutları çevreleyen kendisine <xref:System.Windows.Forms.Button> denetimi. Yeniden boyutlandıramazsınız <xref:System.Windows.Forms.Panel> denetimi.  
  
7.  Sürükleme <xref:System.Windows.Forms.Button> denetimi sol üst köşesinde doğru <xref:System.Windows.Forms.Panel> denetimi.  
  
     <xref:System.Windows.Forms.Panel> Denetimi yeniden boyutlandırır için <xref:System.Windows.Forms.Button> denetiminin yeni konumu.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Windows Forms uygulamalarındaki denetimleri düzenleme için birçok diğer düzen özelliği vardır. Deneyebilecekleriniz bazı birleşimleri şunlardır:  
  
-   Form kullanarak bir derleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi. Ayrıntılar için bkz [izlenecek yol: Windows Forms kullanarak TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Değerini değiştirmeyi deneyin <xref:System.Windows.Forms.TableLayoutPanel> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin yanı sıra <xref:System.Windows.Forms.Control.Margin%2A> , alt denetimlerini özelliği.  
  
-   Kullanarak aynı denemeyi deneyin bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimi. Ayrıntılar için bkz [izlenecek yol: Windows Forms kullanarak FlowLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Alt denetimleri yerleştirme ile deneme bir <xref:System.Windows.Forms.Panel> denetimi. <xref:System.Windows.Forms.Control.Padding%2A> Özelliği, daha fazla genel gerçekleştirme <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> özelliğini karşılamak kendinizi bu durumun bir alt denetimin koyarak geçerli olup olmadığını bir <xref:System.Windows.Forms.Panel> denetimi ve alt denetim ayarı <xref:System.Windows.Forms.Control.Dock%2A> özelliğini<xref:System.Windows.Forms.DockStyle.Fill>. Ayarlama <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğini çeşitli değerleri ve Not etkisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [AutoSize Özelliğine Genel Bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
