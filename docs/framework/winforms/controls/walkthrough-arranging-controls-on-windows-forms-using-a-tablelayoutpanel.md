---
title: "İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: cbd0eb3dfc8f4494bf9a8e96ff7c472622f135d8
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960334"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme

Bazı uygulamalar, kendisini formu yeniden boyutlandırıldığından veya içeriği boyutu değiştikçe uygun şekilde düzenler bir düzene sahip bir form gerektirir. Ne zaman dinamik bir düzen gerekir ve işlemek istemediğiniz <xref:System.Windows.Forms.Control.Layout> açıkça kodunuzda olayları, Düzen panelini kullanma göz önünde bulundurun.

<xref:System.Windows.Forms.FlowLayoutPanel> Denetimi ve <xref:System.Windows.Forms.TableLayoutPanel> denetimi, form üzerinde denetimleri düzenlemek için sezgisel yolu sağlayın. Her ikisini birden içerdiği alt denetimler göreli konumlarını denetlemek için otomatik, yapılandırılabilir bir yeteneği sağlar ve yeniden boyutlandırma ve alt denetimler üst formun boyutları yeniden konumlandırmak için hem de çalışma zamanında dinamik düzen özelliklerini size değiştirin. Düzen bölmeleri, gelişmiş kullanıcı arabirimleri gerçekleştirme etkinleştirmek için Düzen panelleri içinde yuvalanabilir.

<xref:System.Windows.Forms.FlowLayoutPanel> İçeriğini belirli bir akış yönünü ayarlar: yatay veya dikey. İçeriği sonraki bir satır veya sonraki bir sütun sarmalanabilir. Alternatif olarak, içeriğinin yerine kırpılmış DC'de sona erdi. Daha fazla bilgi için [izlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

<xref:System.Windows.Forms.TableLayoutPanel> İçeriğinin HTML benzer işlevsellik sağlayan bir kılavuzda düzenler \<Tablo > öğesi. <xref:System.Windows.Forms.TableLayoutPanel> Denetimi denetimleri tam olarak her denetim konumunu belirtmek gerek kalmadan bir kılavuz düzeni yerleştirmenize olanak sağlar. Satırları ve sütunları hücrelerinden düzenlenir ve bu farklı boyutlarda olabilir. Hücreler, satırlar ve sütunlar arasında birleştirilebilir. Hücre bir form içeren ve diğer birçok bakımdan kapsayıcı olarak davranır her şeyi içerebilir.

<xref:System.Windows.Forms.TableLayoutPanel> Denetimi ayrıca bir orantılı yeniden boyutlandırma özelliği sağlar çalışma zamanında, formunuzu yeniden boyutlandırıldığından düzeninizi sorunsuz bir şekilde değiştirebilirsiniz. Böylece <xref:System.Windows.Forms.TableLayoutPanel> denetimi de uygun veri girişi formlar ve yerelleştirilmiş uygulamalar gibi amaçlarla. Daha fazla bilgi için [izlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) ve [izlenecek yol: Yerelleştirilebilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

Genel olarak, kullanmamalısınız bir <xref:System.Windows.Forms.TableLayoutPanel> tüm düzen için bir kapsayıcı denetimi. Kullanım <xref:System.Windows.Forms.TableLayoutPanel> düzenini bölümlerini orantılı yeniden boyutlandırma özellikler sağlamak için kontrol eder.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

- Bir Windows Forms projesi oluşturma

- Satırlar ve sütunlar denetimleri düzenleme

- Ayar satır ve sütun özellikleri

- Kapsayıcı satırlar ve sütunlar bir denetimi ile

- Taşan otomatik işleme

- Araç kutusunda çift tıklayarak denetimler ekleme

- Anahattı çizerek bir denetim ekleme

- Mevcut denetimleri farklı bir üst öğeye yeniden atama

İşlemi tamamladığınızda, bu önemli bir düzen özellikleri tarafından oynadığı rol, bir anlayışa sahip olacaksınız.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="creating-the-project"></a>Projeyi Oluşturma

İlk adım projeyi oluşturmak ve formu ayarlamaktır.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. "TableLayoutPanelExample" adlı bir Windows uygulaması projesi oluşturun. Daha fazla bilgi için [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .

2. Formda seçin **Windows** **Form Tasarımcısı**.

## <a name="arranging-controls-in-rows-and-columns"></a>Satırlar ve sütunlar denetimleri düzenleme

<xref:System.Windows.Forms.TableLayoutPanel> Denetim kolayca denetimleri satırlar ve sütunlar halinde düzenleme olanak tanır.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Satırları ve sütunları TableLayoutPanel kullanarak denetimleri düzenlemek için

1. Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza. Varsayılan olarak, Not <xref:System.Windows.Forms.TableLayoutPanel> dört denetime sahiptir.

2. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve hücrelerden biri bırakın. Unutmayın <xref:System.Windows.Forms.Button> denetim seçili hücrede oluşturulur.

3. Daha fazla üç sürükleyin <xref:System.Windows.Forms.Button> denetimler **araç kutusu** içine <xref:System.Windows.Forms.TableLayoutPanel> her hücre bir düğme içeren denetim.

4. İki sütun arasında dikey boyutlandırma tutamacı alın ve sola taşı. Unutmayın <xref:System.Windows.Forms.Button> ilk sütunda denetimleri sırasında boyutu daha küçük bir genişliğe yeniden boyutlandırılır <xref:System.Windows.Forms.Button> ikinci sütunda denetimlerinde değişmez.

5. İki sütun arasında dikey boyutlandırma tutamacı yakalayın ve sağa taşıyın. Unutmayın <xref:System.Windows.Forms.Button> denetimleri ilk sütunda, özgün boyutuna döndürmek while <xref:System.Windows.Forms.Button> ikinci sütunda denetimlerinde sağa taşındı.

6. Artırma ve azaltma denetimleri panelinde etkisini görmek için yatay boyutlandırma tutamacı hareket ettirin.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Sabitleme ve yerleştirme kullanarak hücreleri içinde denetimleri konumlandırma

Alt öğe denetimlerini anchoring davranışını bir <xref:System.Windows.Forms.TableLayoutPanel> diğer kapsayıcı denetimlerinde davranışından farklıdır. Alt denetimler yerleştirme davranışını, diğer kapsayıcı denetimleri ile aynıdır.

#### <a name="positioning-controls-within-cells"></a>Hücrelerde denetimleri konumlandırma

1. İlk seçin <xref:System.Windows.Forms.Button> denetimi. Değerini değiştirebilir, <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>. Unutmayın <xref:System.Windows.Forms.Button> hücresini doldurmak için denetimi genişletir.

2. Diğer birini <xref:System.Windows.Forms.Button> kontrol eder. Değerini değiştirebilir, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.Right>. Böylece, sağ kenarlık hücrenin sağ kenarının, taşınır unutmayın. Kenarlıklar arasındaki uzaklığı toplamıdır <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliği ve bölmenin <xref:System.Windows.Forms.Control.Padding%2A> özelliği.

3. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.Right> ve <xref:System.Windows.Forms.AnchorStyles.Left>. Denetim ile hücrenin genişliğine boyutlandırılır Not <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> dikkate değer.

4. 2 ve 3 ile <xref:System.Windows.Forms.AnchorStyles.Top> ve <xref:System.Windows.Forms.AnchorStyles.Bottom> stilleri.

## <a name="setting-row-and-column-properties"></a>Ayar satır ve sütun özellikleri

Satırları ve sütunları özelliklerini kullanarak ayarlayabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonları.

#### <a name="to-set-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlamak için

1. Seçin <xref:System.Windows.Forms.TableLayoutPanel> denetim **Windows Form Tasarımcısı**.

2. İçinde **özellikleri** açık pencerelerin <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> üç nokta simgesine tıklayarak, koleksiyon (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) düğmesinin yanındaki  **Sütunları** girişi.

3. İlk sütunu seçin ve değeri değiştirin, <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğini <xref:System.Windows.Forms.SizeType.AutoSize>. Tıklayın **Tamam** değişikliği kabul etmek için. İlk sütun genişliğini uyacak şekilde azalır Not <xref:System.Windows.Forms.Button> denetimi. Ayrıca, bir sütunun genişliğini yeniden boyutlandırılabilir olmadığını unutmayın.

4. İçinde **özellikleri** penceresini açık <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonu ve ilk sütunu seçin. Değerini değiştirebilir, <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğini <xref:System.Windows.Forms.SizeType.Percent>. Tıklayın **Tamam** değişikliği kabul etmek için. Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetlemek için daha büyük bir genişlik ve ilk sütun genişliğini genişletir olduğunu unutmayın. Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetim daha küçük bir genişliğe ve düğmelerin ilk sütunundaki hücrenin sığdırmak için boyutlandırılır not edin. Ayrıca, bir sütunun genişliğini yeniden boyutlandırılabilir olduğunu unutmayın.

5. İçinde **özellikleri** penceresini açık <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> toplama ve listelenen tüm sütunları seçin. Değerini her <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğini <xref:System.Windows.Forms.SizeType.Percent>. Tıklayın **Tamam** değişikliği kabul etmek için. Yineleme ile <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> koleksiyonu.

6. Yeniden boyutlandırma tutamaçları köşe birini alın ve genişliğini ve yüksekliğini yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetimi. Satırları ve sütunları olarak yeniden boyutlandırılıyor Not <xref:System.Windows.Forms.TableLayoutPanel> denetimin boyutunu değişiklikler. Ayrıca satırları ve sütunları yeniden boyutlandırılabilir yatay ve dikey tutamaçlarını olduğunu unutmayın.

## <a name="spanning-rows-and-columns-with-a-control"></a>Kapsayıcı satırlar ve sütunlar bir denetimi ile

<xref:System.Windows.Forms.TableLayoutPanel> Denetimi tasarım zamanında denetimler için çeşitli yeni özellikler ekler. Bu özelliklerin iki `RowSpan` ve `ColumnSpan`. Bu özellikler, bir denetim yayılma birden fazla bir satır veya sütun yapmak için kullanabilirsiniz.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Satırları ve sütunları denetimiyle yaymasına izin

1. Seçin <xref:System.Windows.Forms.Button> ilk satır ve ilk sütun denetimi.

2. İçinde **özellikleri** windows değerini değiştirin `ColumnSpan` özelliğini **2**. Unutmayın <xref:System.Windows.Forms.Button> ilk sütunu ve ikinci sütun denetimi doldurur. Bu değişikliğe uyum sağlamak için fazladan bir satır eklendi daha da unutmayın.

3. Yineleme 2. adım için `RowSpan` özelliği.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetimler ekleme

Doldurabilirsiniz, <xref:System.Windows.Forms.TableLayoutPanel> denetimlerinde çift tıklayarak denetim **araç kutusu**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetim eklemek için

1. Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.

2. Çift <xref:System.Windows.Forms.Button> denetim simgesini **araç kutusu**. Yeni bir düğme denetimi görünür Not <xref:System.Windows.Forms.TableLayoutPanel> denetimin ilk hücrenin.

3. Daha fazla denetimlerinde çift **araç kutusu**. Yeni denetimler sırayla da göründüğünü fark <xref:System.Windows.Forms.TableLayoutPanel> denetimin boş hücreler. Ayrıca <xref:System.Windows.Forms.TableLayoutPanel> açık hücre mevcutsa, yeni denetimler uyum sağlamak için denetimi genişletir.

## <a name="automatic-handling-of-overflows"></a>Taşan otomatik işleme

Ne zaman, ekleme denetimlere <xref:System.Windows.Forms.TableLayoutPanel> denetimi dışında boş hücre, yeni denetimler için çalışabilir. <xref:System.Windows.Forms.TableLayoutPanel> Denetim işleme bu durumu otomatik olarak hücre sayısını artırarak.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Taşan otomatik işlenmesini gözlemleyin

1. Hala boş hücrelere varsa <xref:System.Windows.Forms.TableLayoutPanel> denetlemek, yeni eklemeden devam <xref:System.Windows.Forms.Button> kadar denetimleri <xref:System.Windows.Forms.TableLayoutPanel> denetim dolu.

2. Bir kez <xref:System.Windows.Forms.TableLayoutPanel> kontrolü tam, çift <xref:System.Windows.Forms.Button> simgesini **araç kutusu** diğerine eklemek için <xref:System.Windows.Forms.Button> denetimi. Unutmayın <xref:System.Windows.Forms.TableLayoutPanel> yeni denetim uyum sağlamak için yeni bir hücre denetimi oluşturur. Birkaç daha fazla denetim ekleme ve yeniden boyutlandırma davranışını gözlemleyin.

3. Değiştirin <xref:System.Windows.Forms.TableLayoutPanel> denetimin <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özelliğini <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Çift <xref:System.Windows.Forms.Button> simgesini **araç kutusu** eklemek için <xref:System.Windows.Forms.Button> kadar denetler <xref:System.Windows.Forms.TableLayoutPanel> denetim dolu. Çift <xref:System.Windows.Forms.Button> simgesini **araç kutusu** yeniden. Not hata iletisi alırsınız **Windows Form Tasarımcısı** size bildiren ek satırları ve sütunları oluşturulamaz.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim ekleme

Bir denetime eklemek bir <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve bir hücrede anahattı çizerek boyutunu belirtin.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim eklemek için

1. Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.

2. İçinde **araç kutusu**, tıklayın <xref:System.Windows.Forms.Button> denetim simgesi. Form üzerine sürükleyin değil.

3. Fare işaretçisi taşıyabiliyor <xref:System.Windows.Forms.TableLayoutPanel> denetimi. Bir artı işareti ile işaretçi Not <xref:System.Windows.Forms.Button> bağlı denetim simgesi.

4. ' A tıklayın ve fare düğmesini basılı tutun.

5. Fare işaretçisi ana hat çizmek için sürükleyin <xref:System.Windows.Forms.Button> denetimi. Boyutu ile memnun kaldığınızda, fare düğmesini bırakın. Unutmayın <xref:System.Windows.Forms.Button> denetimi içinde u çizdiğini denetimin ana hat hücre içinde oluşturulur.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Birden çok denetim hücreleri içinde izin verilmez

<xref:System.Windows.Forms.TableLayoutPanel> Denetim hücre başına yalnızca bir alt denetimin içerebilir.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Hücreleri içinde birden çok denetim verilmeyen göstermek için

- Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve dolu hücrelerden biri bırakın. Unutmayın <xref:System.Windows.Forms.TableLayoutPanel> denetimi izin vermemektedir bırakmak <xref:System.Windows.Forms.Button> dolu hücresine denetimi.

## <a name="swapping-controls"></a>Denetimleri değiştirme

<xref:System.Windows.Forms.TableLayoutPanel> Denetimi iki farklı hücresini kaplayan denetimleri takas etmenizi sağlar.

#### <a name="to-swap-controls"></a>Denetimleri değiştirmek için

- Sürükleyin <xref:System.Windows.Forms.Button> bir dolu hücre ve başka bir dolu hücre üzerine içine bırak denetimleri. İki denetimi bir hücreden diğer taşınan olduğunu unutmayın.

## <a name="next-steps"></a>Sonraki Adımlar

Düzen bölmeleri ve denetimleri kullanarak karmaşık Düzen elde edebilirsiniz. Daha fazla araştırma için öneriler şunlardır:

- Aşağıdakilerden birini yeniden boyutlandırmaya çalışın <xref:System.Windows.Forms.Button> büyük boyut ve düzenini üzerindeki etkisini Not denetimleri.

- Birden çok denetimlere seçimi yapıştırın <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve denetimlerin nasıl eklenir not edin.

- Düzen bölmelerini diğer düzen bölmeleri içerebilir. Bırakma ile deneme bir <xref:System.Windows.Forms.TableLayoutPanel> denetime varolan bir denetimi.

- Dock <xref:System.Windows.Forms.TableLayoutPanel> üst form denetimi. Formu yeniden boyutlandırmak ve düzeni üzerindeki etkisini dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricileri ve tasarımcıları için resmi yönergeleri. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [İzlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [İzlenecek yol: Yerelleştirilebilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel Denetimi için En İyi Yöntemler](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms'da denetimleri yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms'da denetimleri](how-to-anchor-controls-on-windows-forms.md)
- [İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme](windows-forms-controls-padding-autosize.md)
