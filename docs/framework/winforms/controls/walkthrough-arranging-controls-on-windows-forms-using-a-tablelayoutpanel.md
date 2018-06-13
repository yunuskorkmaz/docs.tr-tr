---
title: "İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 6b98495fb967b7f3b5885f940c348b5cba33cb18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541826"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme
Bazı uygulamalar kendisini formun boyutlandırıldığında veya içeriği boyutunu değiştirmek gibi uygun şekilde düzenler bir düzen formla gerektirir. Ne zaman dinamik düzen gerekir ve işlemek istemediğiniz <xref:System.Windows.Forms.Control.Layout> açıkça kodunuzda olayları, bir düzen panel kullanmayı düşünün.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Denetim ve <xref:System.Windows.Forms.TableLayoutPanel> denetimi, form üzerinde denetimleri düzenlemek için sezgisel yollar sağlar. Her ikisini birden içerdiği alt denetimleri göreli konumları denetlemek için otomatik, yapılandırılabilir bir beceri sağlar ve yeniden boyutlandırma ve alt denetimleri üst formu boyutları olarak yeniden konumlandırmak için her ikisi de, çalışma zamanında dinamik düzen özelliklerini verin değiştirin. Düzen panelleri gelişmiş kullanıcı arabirimleri gerçekleştirme etkinleştirmek için Düzen panelleri içinde iç içe.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> İçeriğini belirli akış yönü düzenler: yatay veya dikey. İçeriği, bir sonraki satıra veya sonraki bir sütuna sarmalamak. Alternatif olarak, içeriği yerine kırpılmış gibi sarılır. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms FlowLayoutPanel kullanarak düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 <xref:System.Windows.Forms.TableLayoutPanel> İçeriğini HTML benzer işlevsellik sağlayan bir kılavuz düzenler \<Tablo > öğesi. <xref:System.Windows.Forms.TableLayoutPanel> Denetim tam olarak her denetim konumunu belirtmek gerek kalmadan bir kılavuz düzeni denetimleri yerleştirin olanak tanır. Satırları ve sütunları hücrelerinden düzenlenir ve bunlar farklı boyutlarda olabilir. Hücreler, satırlar ve sütunlar üzerinde birleştirilebilir. Hücreleri herhangi bir şey bir form içeren ve diğer birçok bakımdan kapsayıcı olarak davranır içerebilir.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi de sağlar orantılı yeniden boyutlandırma yeteneği çalışma zamanında formunuz boyutlandırıldığında düzeninizi sorunsuz değiştirebilmeniz için. Böylece <xref:System.Windows.Forms.TableLayoutPanel> denetimi de uygun veri girişi formları ve yerelleştirilmiş uygulamalar gibi amaçlarla. Daha fazla bilgi için bkz: [izlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab) ve [izlenecek yol: bir yerelleştirilebilir Windows formu oluşturma](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c).  
  
 Genel olarak, kullanılamaz bir <xref:System.Windows.Forms.TableLayoutPanel> tam yerleşimi için bir kapsayıcı olarak denetim. Kullanım <xref:System.Windows.Forms.TableLayoutPanel> düzeni bölümlerini orantılı yeniden boyutlandırma olanağı sağlamak için kontrol eder.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms projesi oluşturma  
  
-   Satır ve sütunları denetimleri düzenleme  
  
-   Ayar satır ve sütun özellikleri  
  
-   Kapsayıcı satırlar ve sütunlar denetimiyle  
  
-   Taşan otomatik işlenmesi  
  
-   Araç kutusunda çift tıklatarak denetimler ekleme  
  
-   Anahattı çizerek bir denetim ekleme  
  
-   Mevcut denetimleri farklı bir üst öğeye yeniden atama  
  
 İşiniz bittiğinde, bu önemli yerleşim özellikleri tarafından oynadığı rol anlaşılması gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  "TableLayoutPanelExample" adlı bir Windows uygulaması projesi oluşturun. Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Formda seçin **Windows** **Forms Tasarımcısı**.  
  
## <a name="arranging-controls-in-rows-and-columns"></a>Satır ve sütunları denetimleri düzenleme  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi kolayca denetimlerini satırlar ve sütunlar halinde düzenlemek sağlar.  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Satırları ve sütunları TableLayoutPanel kullanarak denetimlerinde düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza. Varsayılan olarak, Not <xref:System.Windows.Forms.TableLayoutPanel> denetim dört sahiptir.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve hücrelerden biri bırakın. Unutmayın <xref:System.Windows.Forms.Button> denetimi, seçtiğiniz hücre içinde oluşturulur.  
  
3.  Daha fazla üç sürükleyin <xref:System.Windows.Forms.Button> gelen denetimleri **araç kutusu** içine <xref:System.Windows.Forms.TableLayoutPanel> kontrol böylece her hücre bir düğme içerir.  
  
4.  İki sütun arasında dikey boyutlandırma tutamacını tutun ve sola taşıyın. Unutmayın <xref:System.Windows.Forms.Button> ilk sütun denetimlerinde boyutunu çalışırken daha küçük bir genişliğe yeniden boyutlandırılır <xref:System.Windows.Forms.Button> denetimleri ikinci sütundaki değiştirilmemiş.  
  
5.  İki sütun arasında dikey boyutlandırma tutamacını yakalayın ve sağa taşıyın. Unutmayın <xref:System.Windows.Forms.Button> ilk sütun denetimlerinde kendi özgün durumuna döndürmek while <xref:System.Windows.Forms.Button> ikinci sütundaki denetimleri sağa taşınır.  
  
6.  Yukarı ve aşağı Denetim Masası'nda üzerindeki etkisini görmek için yatay boyutlandırma tutamacını taşıyın.  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Sabitleme ve yerleştirme kullanarak hücreleri içinde denetimleri konumlandırma  
 Alt denetimler anchoring davranışını bir <xref:System.Windows.Forms.TableLayoutPanel> diğer kapsayıcı denetimleri davranış farklıdır. Alt denetimler yerleştirme davranışını diğer kapsayıcı denetimleri ile aynıdır.  
  
#### <a name="positioning-controls-within-cells"></a>Hücrelerde denetimleri konumlandırma  
  
1.  İlk seçin <xref:System.Windows.Forms.Button> denetim. Değerini değiştirmek kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>. Unutmayın <xref:System.Windows.Forms.Button> denetimini genişleten hücresini doldurmak için.  
  
2.  Başka birini seçin <xref:System.Windows.Forms.Button> kontrol eder. Değerini değiştirmek kendi <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine <xref:System.Windows.Forms.AnchorStyles.Right>. Sağ kenarlığın hücrenin sağ kenarlığın olmasını sağlamak, taşınır unutmayın. Kenarlıkları arasındaki uzaklığı toplamıdır <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliği ve bölmenin <xref:System.Windows.Forms.Control.Padding%2A> özelliği.  
  
3.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine <xref:System.Windows.Forms.AnchorStyles.Right> ve <xref:System.Windows.Forms.AnchorStyles.Left>. Denetim ile boyuta sahip olmadığından, hücre genişliğini Not <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> hesaba değerleri.  
  
4.  2 ve 3 ile <xref:System.Windows.Forms.AnchorStyles.Top> ve <xref:System.Windows.Forms.AnchorStyles.Bottom> stilleri.  
  
## <a name="setting-row-and-column-properties"></a>Ayar satır ve sütun özellikleri  
 Satırları ve sütunları tek tek özellikleri kullanarak ayarlayabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonları.  
  
#### <a name="to-set-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlamak için  
  
1.  Seçin <xref:System.Windows.Forms.TableLayoutPanel> denetim **Windows Form Tasarımcısı**.  
  
2.  İçinde **özellikleri** windows, açık <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> üç nokta işaretine tıklayarak koleksiyonu (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesine yanına **sütunları** girişi.  
  
3.  İlk sütun seçin ve değeri değiştirin, <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğine <xref:System.Windows.Forms.SizeType.AutoSize>. Tıklatın **Tamam** değişikliği kabul etmek için. İlk sütunun genişliği uyacak şekilde azalır Not <xref:System.Windows.Forms.Button> denetim. Ayrıca sütunun genişliği yeniden boyutlandırılabilir olmadığını unutmayın.  
  
4.  İçinde **özellikleri** penceresi açık <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonu ve ilk sütunu seçin. Değerini değiştirmek kendi <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğine <xref:System.Windows.Forms.SizeType.Percent>. Tıklatın **Tamam** değişikliği kabul etmek için. Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetlemek için daha büyük bir genişlik ve ilk sütunun genişliği genişletir not edin. Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetim daha küçük bir genişliğe ve ilk sütununda düğmeleri hücre sığacak şekilde boyutlandırılır not edin. Ayrıca sütunun genişliği yeniden boyutlandırılabilir olduğuna dikkat edin.  
  
5.  İçinde **özellikleri** penceresi açık <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> toplama ve listelenen tüm sütunları seçin. Değerini her <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğine <xref:System.Windows.Forms.SizeType.Percent>. Tıklatın **Tamam** değişikliği kabul etmek için. Yineleme ile <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> koleksiyonu.  
  
6.  Tanıtıcıları yeniden boyutlandırma köşe birini alın ve genişlik ve yüksekliğini yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetim. Satırları ve sütunları olarak yeniden boyutlandırılıyor Not <xref:System.Windows.Forms.TableLayoutPanel> denetimin boyut değişiklikleri. Ayrıca, satırları ve sütunları yeniden boyutlandırılabilir yatay ve dikey boyutlandırma unutmayın.  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>Kapsayıcı satırlar ve sütunlar denetimiyle  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi tasarım zamanında denetimleri için birkaç yeni özellikleri ekler. Bu özellikleri ikisidir `RowSpan` ve `ColumnSpan`. Bir denetim aralık birden fazla bir satır veya sütun yapmak için bu özellikleri kullanabilirsiniz.  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>Satırları ve sütunları denetimiyle kapsanacak  
  
1.  Seçin <xref:System.Windows.Forms.Button> denetim ilk satır ve ilk sütun.  
  
2.  İçinde **özellikleri** windows değerini değiştirin `ColumnSpan` özelliğine **2**. Unutmayın <xref:System.Windows.Forms.Button> denetim ilk sütun ve ikinci sütunda doldurur. Ayrıca, bu değişikliği karşılamak için fazladan bir satır eklendi daha unutmayın.  
  
3.  Yineleme için 2 `RowSpan` özelliği.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklatarak denetimler ekleme  
 Doldurmak, <xref:System.Windows.Forms.TableLayoutPanel> denetimlerinde çift tıklatarak denetim **araç**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusunda çift tıklatarak denetim eklemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.  
  
2.  Çift <xref:System.Windows.Forms.Button> denetim simgesinde **araç**. Yeni bir düğme denetimi görünür Not <xref:System.Windows.Forms.TableLayoutPanel> denetimin ilk hücre.  
  
3.  Daha fazla denetimlerinde çift **araç**. Yeni denetimleri sırayla içinde göründüğüne dikkat edin <xref:System.Windows.Forms.TableLayoutPanel> denetimin boş hücreler. Ayrıca <xref:System.Windows.Forms.TableLayoutPanel> denetimini genişleten hiçbir açık hücreleri mevcutsa, yeni denetimler uyum sağlamak için.  
  
## <a name="automatic-handling-of-overflows"></a>Taşan otomatik işlenmesi  
 Ne zaman, ekleme denetimlere <xref:System.Windows.Forms.TableLayoutPanel> denetim, yeni denetimler için boş hücrelerin dışında çalışabilir. <xref:System.Windows.Forms.TableLayoutPanel> Denetim işleme bu durumu otomatik olarak hücre sayısını artırarak.  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>Taşan otomatik işlenmesini izlemek için  
  
1.  Hala boş hücrelere varsa <xref:System.Windows.Forms.TableLayoutPanel> denetlemek, yeni eklemeden devam <xref:System.Windows.Forms.Button> kadar denetimleri <xref:System.Windows.Forms.TableLayoutPanel> denetim dolu.  
  
2.  Bir kez <xref:System.Windows.Forms.TableLayoutPanel> denetim tam, çift <xref:System.Windows.Forms.Button> simgesine **araç** başka eklemek için <xref:System.Windows.Forms.Button> denetim. Unutmayın <xref:System.Windows.Forms.TableLayoutPanel> denetimi yeni denetimi kapsayacak şekilde yeni hücre oluşturur. Birkaç daha fazla denetim takın ve yeniden boyutlandırma davranışı inceleyin.  
  
3.  Değerini değiştirme <xref:System.Windows.Forms.TableLayoutPanel> denetimin <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özelliğine <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Çift <xref:System.Windows.Forms.Button> simgesine **araç** eklemek için <xref:System.Windows.Forms.Button> kadar denetimleri <xref:System.Windows.Forms.TableLayoutPanel> denetim dolu. Çift <xref:System.Windows.Forms.Button> simgesine **araç** yeniden. Not hata iletisi alırsınız **Windows Form Tasarımcısı** size bildiren ek satırları ve sütunları oluşturulamaz.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim ekleme  
 Bir denetime ekleyebilirsiniz bir <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve bir hücreye anahattı çizerek boyutunu belirtin.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim eklemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.  
  
2.  İçinde **araç**, tıklatın <xref:System.Windows.Forms.Button> denetimi simgesi. Bu form üzerine sürükleyin değil.  
  
3.  Fare işaretçisini taşıyamazsınız <xref:System.Windows.Forms.TableLayoutPanel> denetim. Bir artı kıl ile işaretçi Not <xref:System.Windows.Forms.Button> bağlı denetimi simgesi.  
  
4.  ' A tıklayın ve fare düğmesini basılı tutun.  
  
5.  Özetini çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.Button> denetim. Boyutuyla memnun kaldığınızda, fare düğmesini bırakın. Unutmayın <xref:System.Windows.Forms.Button> denetimi içinde u çizdiğini denetimin anahat hücresinde oluşturulur.  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>Birden çok denetim hücreleri içinde izin verilmiyor  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetim hücre başına yalnızca bir alt denetim içerebilir.  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Hücreleri içinde birden çok denetim verilmeyen göstermek için  
  
-   Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve dolu hücrelerden biri bırakın. Unutmayın <xref:System.Windows.Forms.TableLayoutPanel> denetim izin vermez bırakma <xref:System.Windows.Forms.Button> dolu hücresine denetim.  
  
## <a name="swapping-controls"></a>Denetimleri değiştirme  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetim iki farklı hücre kaplayan denetimleri takas olanak sağlar.  
  
#### <a name="to-swap-controls"></a>Denetimleri değiştirmek için  
  
-   Aşağıdakilerden birini sürükleyin <xref:System.Windows.Forms.Button> dolu hücre ve başka bir dolu hücre üzerine içine açılan denetimler. İki denetim bir hücreden diğer taşınması unutmayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Düzen panelleri ve denetimleri birleşimini kullanarak karmaşık bir düzen elde edebilirsiniz. Daha fazla araştırması için öneriler şunlardır:  
  
-   Aşağıdakilerden birini yeniden boyutlandırmayı deneyin <xref:System.Windows.Forms.Button> denetimleri büyük boyutuna ve Not yerleşim üzerinde etkisi.  
  
-   Birden çok denetimlere seçimi Yapıştır <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve denetimlerin nasıl eklenir not edin.  
  
-   Düzen panelleri diğer düzen panelleri içerebilir. Deneme bırakma ile bir <xref:System.Windows.Forms.TableLayoutPanel> varolan denetimine denetim.  
  
-   Yerleştirme <xref:System.Windows.Forms.TableLayoutPanel> üst form denetimi. Formu yeniden boyutlandırma ve yerleşim üzerinde etkisi not edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricilerin ve tasarımcıların resmi yönergeleri. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [İzlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab)  
 [İzlenecek yol: bir yerelleştirilebilir Windows formu oluşturma](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c)  
 [TableLayoutPanel Denetimi için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 [AutoSize Özelliğine Genel Bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Nasıl yapılır: Windows Forms’da Denetimleri Bağlama](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
