---
title: "İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 7b7380690d8668f46b98272e1d42640f23679b19
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799119"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme

Bazı uygulamalar, form yeniden boyutlandırıldığı veya içeriklerin boyutu değiştikçe kendisini uygun şekilde değiştiren düzen içeren bir form gerektirir. Dinamik bir düzene ihtiyacınız olduğunda ve kodunuzda açıkça <xref:System.Windows.Forms.Control.Layout> olaylarını işlemek istemiyorsanız, bir Düzen paneli kullanmayı düşünün.

<xref:System.Windows.Forms.FlowLayoutPanel> denetimi ve <xref:System.Windows.Forms.TableLayoutPanel> denetimi, formunuzdaki denetimleri düzenlemek için sezgisel yollar sağlar. Her ikisi de içindeki alt denetimlerin göreli konumlarını denetlemek için otomatik, yapılandırılabilir bir özellik sağlar ve her ikisi de çalışma zamanında dinamik düzen özellikleri sunduklarında, ana formun boyutları olarak alt denetimleri yeniden boyutlandırabilir ve yeniden konumlandırabilirsiniz değişebilir. Düzen bölmeleri, gelişmiş kullanıcı arabirimlerinin yerine geçme özelliğini etkinleştirmek için Düzen panelleri içinde iç içe olabilir.

<xref:System.Windows.Forms.FlowLayoutPanel>, içeriğini belirli bir akış yönünde düzenler: yatay veya dikey. İçeriği bir satırdan sonrakine veya bir sütundan sonrakine kaydırılmış olabilir. Alternatif olarak, içeriği sarmalanabilir yerine kırpılabilir. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir FlowLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

<xref:System.Windows.Forms.TableLayoutPanel>, HTML \<Tablo > öğesine benzer işlevler sağlayarak içeriğini bir kılavuza yerleştirir. <xref:System.Windows.Forms.TableLayoutPanel> denetimi, denetimleri her bir denetimin konumunu tam olarak belirtmenize gerek kalmadan kılavuz düzenine yerleştirmenize olanak sağlar. Hücreleri satırlar ve sütunlar halinde düzenlenir ve bunlar farklı boyutlarda olabilir. Hücreler, satırlar ve sütunlar arasında birleştirilebilir. Hücreler, bir form içerebilen ve kapsayıcı olarak birçok yönden davranan her şeyi içerebilir.

<xref:System.Windows.Forms.TableLayoutPanel> denetimi çalışma zamanında orantılı bir yeniden boyutlandırma özelliği de sağlar, böylece formunuz yeniden boyutlandırıldığından düzen sorunsuz bir şekilde değiştirilebilir. Bu, <xref:System.Windows.Forms.TableLayoutPanel> denetimini veri girişi formları ve yerelleştirilmiş uygulamalar gibi amaçlarla uygun hale getirir. Daha fazla bilgi için bkz. [Izlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) ve [izlenecek yol: bir yerelleştirilebilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

Genel olarak, tüm düzen için kapsayıcı olarak <xref:System.Windows.Forms.TableLayoutPanel> denetimi kullanmamalısınız. Düzenin bölümlerine orantılı yeniden boyutlandırma özellikleri sağlamak için <xref:System.Windows.Forms.TableLayoutPanel> denetimleri kullanın.

Bu izlenecek yolda gösterilen görevler şunlardır:

- Windows Forms projesi oluşturma

- Satırlarda ve sütunlarda denetimleri düzenleme

- Satır ve sütun özelliklerini ayarlama

- Satırları ve sütunları bir denetimle yayma

- Taşmaları otomatik Işleme

- Araç kutusunda çift tıklayarak denetim ekleme

- Ana hattını çizerek bir denetim ekleme

- Varolan denetimleri farklı bir üst öğeye yeniden atama

İşiniz bittiğinde, bu önemli düzen özellikleri tarafından yürütülen rolü anlayacaksınız.

## <a name="creating-the-project"></a>Projeyi Oluşturma

İlk adım projeyi oluşturmak ve formu kurmak olur.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. "TableLayoutPanelExample" adlı bir Windows uygulaması projesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .

2. **Windows** **form tasarımcısında**formu seçin.

## <a name="arranging-controls-in-rows-and-columns"></a>Satırlarda ve sütunlarda denetimleri düzenleme

<xref:System.Windows.Forms.TableLayoutPanel> denetimi denetimleri satırlar ve sütunlar halinde kolayca düzenlemenizi sağlar.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>TableLayoutPanel kullanarak satırlarda ve sütunlarda denetimleri düzenlemek için

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin. Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> denetiminin dört hücre olduğunu unutmayın.

2. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.TableLayoutPanel> denetimine sürükleyin ve hücrelerden birine bırakın. <xref:System.Windows.Forms.Button> denetiminin seçtiğiniz hücre içinde oluşturulduğunu unutmayın.

3. **Araç kutusundan** üç <xref:System.Windows.Forms.Button> denetimi <xref:System.Windows.Forms.TableLayoutPanel> denetimine sürükleyin, böylece her hücrede bir düğme bulunur.

4. İki sütun arasında dikey boyutlandırma tutamacını alın ve sola taşıyın. İlk sütundaki <xref:System.Windows.Forms.Button> denetimlerinin daha küçük bir genişliğe yeniden boyutlandırıldığını ve ikinci sütundaki <xref:System.Windows.Forms.Button> denetimlerinin boyutunun değişmediğini unutmayın.

5. İki sütun arasında dikey boyutlandırma tutamacını alın ve sağa taşıyın. İlk sütundaki <xref:System.Windows.Forms.Button> denetimlerinin özgün boyutlarına dönüşdiğine ve ikinci sütundaki <xref:System.Windows.Forms.Button> denetimlerinin sağa taşındığını unutmayın.

6. Paneldeki denetimlerde etkiyi görmek için yatay boyutlandırma tutamacını yukarı ve aşağı taşıyın.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Yerleştirme ve sabitleme kullanarak hücrelerde denetimleri konumlandırma

Bir <xref:System.Windows.Forms.TableLayoutPanel> alt denetimlerin sabitleme davranışı, diğer kapsayıcı denetimlerindeki davranıştan farklıdır. Alt denetimlerin yerleştirme davranışı, diğer kapsayıcı denetimleriyle aynıdır.

#### <a name="positioning-controls-within-cells"></a>Hücrelerin içindeki denetimleri konumlandırma

1. İlk <xref:System.Windows.Forms.Button> denetimini seçin. <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak değiştirin. <xref:System.Windows.Forms.Button> denetiminin hücresini dolduracak şekilde genişletildiğine unutmayın.

2. Diğer <xref:System.Windows.Forms.Button> denetimlerinden birini seçin. <xref:System.Windows.Forms.Control.Anchor%2A> özelliğinin değerini <xref:System.Windows.Forms.AnchorStyles.Right>olarak değiştirin. Sağ kenarlığının hücrenin sağ kenarlığının yakınında olması için taşındığını unutmayın. Kenarlıklar arasındaki mesafe, <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin ve bölmenin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin toplamıdır.

3. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğinin değerini <xref:System.Windows.Forms.AnchorStyles.Right> ve <xref:System.Windows.Forms.AnchorStyles.Left>olarak değiştirin. Denetim, <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> değerleri hesaba götürülüyse hücrenin genişliğine göre boyutlandırıldığını unutmayın.

4. <xref:System.Windows.Forms.AnchorStyles.Top> ve <xref:System.Windows.Forms.AnchorStyles.Bottom> stilleriyle birlikte 2 ve 3. adımları yineleyin.

## <a name="setting-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlama

<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonlarını kullanarak satırların ve sütunların ayrı özelliklerini ayarlayabilirsiniz.

#### <a name="to-set-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlamak için

1. **Windows Form Tasarımcısı**<xref:System.Windows.Forms.TableLayoutPanel> denetimini seçin.

2. **Özellikler** penceresinde, **sütunlar** girişinin yanındaki üç![nokta düğmesini (Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png)) düğmesine tıklayarak <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonunu açın.

3. İlk sütunu seçin ve <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğinin değerini <xref:System.Windows.Forms.SizeType.AutoSize>olarak değiştirin. Değişikliği kabul etmek için **Tamam** ' ı tıklatın. İlk sütunun genişliğinin <xref:System.Windows.Forms.Button> denetimine sığacak şekilde azaltıldığına unutmayın. Ayrıca, sütunun genişliğinin yeniden boyutlandırılabilir olduğunu unutmayın.

4. **Özellikler** penceresinde <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonunu açın ve ilk sütunu seçin. <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğinin değerini <xref:System.Windows.Forms.SizeType.Percent>olarak değiştirin. Değişikliği kabul etmek için **Tamam** ' ı tıklatın. <xref:System.Windows.Forms.TableLayoutPanel> denetimini daha büyük bir genişliğe göre yeniden boyutlandırın ve ilk sütunun genişliğinin genişlediğine unutmayın. <xref:System.Windows.Forms.TableLayoutPanel> denetimini daha küçük bir genişliğe göre yeniden boyutlandırın ve ilk sütundaki düğmelerin hücreye sığacak şekilde boyutlandırıldığını unutmayın. Ayrıca, sütunun genişliğinin yeniden boyutlandırılabilir olduğunu unutmayın.

5. **Özellikler** penceresinde <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonunu açın ve listelenen tüm sütunları seçin. Her <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğinin değerini <xref:System.Windows.Forms.SizeType.Percent>olarak ayarlayın. Değişikliği kabul etmek için **Tamam** ' ı tıklatın. <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> koleksiyonuyla tekrarlayın.

6. Köşe yeniden boyutlandırma tutamaçlarından birini alın ve <xref:System.Windows.Forms.TableLayoutPanel> denetiminin genişliğini ve yüksekliğini yeniden boyutlandırın. Satırların ve sütunların <xref:System.Windows.Forms.TableLayoutPanel> denetimin boyut değişiklikleri olarak yeniden boyutlandırıldığını unutmayın. Ayrıca, satır ve sütunların yatay ve dikey boyutlandırma tutamaçlarıyla yeniden boyutlandırılabilir olduğunu unutmayın.

## <a name="spanning-rows-and-columns-with-a-control"></a>Satırları ve sütunları bir denetimle yayma

<xref:System.Windows.Forms.TableLayoutPanel> denetimi, tasarım zamanında denetimlere birkaç yeni özellik ekler. Bu özelliklerden ikisi `RowSpan` ve `ColumnSpan`. Bu özellikleri, bir denetimi birden fazla satır veya sütuna yaymak için kullanabilirsiniz.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Satırları ve sütunları bir denetimle yayma

1. İlk satırda ve ilk sütunda <xref:System.Windows.Forms.Button> denetimini seçin.

2. **Özellikler** penceresinde, `ColumnSpan` özelliğinin değerini **2**olarak değiştirin. <xref:System.Windows.Forms.Button> denetiminin ilk sütunu ve ikinci sütunu doldurduğunu unutmayın. Ayrıca, bu değişikliğe uyum sağlamak için ek bir satır eklendiğini de göz önünde bulabilirsiniz.

3. `RowSpan` özelliği için 2. adımı tekrarlayın.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetim ekleme

**Araç kutusundaki**denetimleri çift tıklayarak <xref:System.Windows.Forms.TableLayoutPanel> denetiminizi doldurabilirsiniz.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusuna çift tıklayarak denetim eklemek için

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.

2. **Araç kutusundaki**<xref:System.Windows.Forms.Button> denetim simgesine çift tıklayın. <xref:System.Windows.Forms.TableLayoutPanel> denetiminin ilk hücresinde yeni bir düğme denetimi göründüğünü unutmayın.

3. **Araç kutusunda**birden fazla denetim ' e çift tıklayın. Yeni denetimlerin <xref:System.Windows.Forms.TableLayoutPanel> denetimin açılmamış hücrelerinde çok büyük bir şekilde göründüğünü unutmayın. Ayrıca, açık hücre yoksa <xref:System.Windows.Forms.TableLayoutPanel> denetiminin yeni denetimlere uyum sağlayacak şekilde genişlediğine de unutmayın.

## <a name="automatic-handling-of-overflows"></a>Taşmaları otomatik Işleme

<xref:System.Windows.Forms.TableLayoutPanel> denetimine denetim eklerken, yeni Denetimleriniz için boş hücreler tükenmeyebilir. <xref:System.Windows.Forms.TableLayoutPanel> denetim, hücre sayısını artırarak bu durumu otomatik olarak işler.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Taşın otomatik işlemesini gözlemlemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> denetiminde hala boş hücreler varsa, <xref:System.Windows.Forms.TableLayoutPanel> denetimi dolana kadar yeni <xref:System.Windows.Forms.Button> denetimleri eklemeye devam edin.

2. <xref:System.Windows.Forms.TableLayoutPanel> denetimi dolduğunda, başka bir <xref:System.Windows.Forms.Button> denetimi eklemek için **araç kutusundaki** <xref:System.Windows.Forms.Button> simgesine çift tıklayın. <xref:System.Windows.Forms.TableLayoutPanel> denetiminin yeni denetime uyum sağlamak için yeni hücreler oluşturduğunu unutmayın. Birkaç denetim ekleyin ve yeniden boyutlandırma davranışını gözlemleyin.

3. <xref:System.Windows.Forms.TableLayoutPanel> denetiminin <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özelliğinin değerini <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>olarak değiştirin. <xref:System.Windows.Forms.TableLayoutPanel> denetimi dolana kadar <xref:System.Windows.Forms.Button> denetimleri eklemek için **araç kutusundaki** <xref:System.Windows.Forms.Button> simgesine çift tıklayın. **Araç kutusundaki** <xref:System.Windows.Forms.Button> simgesine tekrar çift tıklayın. Ek satır ve sütun oluşturulamadığını bildiren **Windows Form Tasarımcısı** bir hata mesajı almayacağınızı unutmayın.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim ekleme

<xref:System.Windows.Forms.TableLayoutPanel> denetimine bir denetim ekleyebilir ve kendi anahattını bir hücreye çizerek boyutunu belirtebilirsiniz.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim eklemek için

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.

2. **Araç kutusunda**<xref:System.Windows.Forms.Button> denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

3. Fare işaretçisini <xref:System.Windows.Forms.TableLayoutPanel> denetiminin üzerine taşıyın. İşaretçinin, <xref:System.Windows.Forms.Button> denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın.

4. Fare düğmesine tıklayın ve basılı tutun.

5. <xref:System.Windows.Forms.Button> denetiminin anahattını çizmek için fare işaretçisini sürükleyin. Boyutla memnun olduğunuzda fare düğmesini bırakın. <xref:System.Windows.Forms.Button> denetiminin, denetimin anahattını çizdiğiniz hücrede oluşturulduğunu unutmayın.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Hücreler Içindeki birden çok denetime Izin verilmiyor

<xref:System.Windows.Forms.TableLayoutPanel> denetim, her hücre için yalnızca bir alt denetim içerebilir.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Hücreler içinde birden çok denetime izin verilmediğini göstermek için

- **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.TableLayoutPanel> denetimine sürükleyin ve bulunan hücrelerden birine bırakın. <xref:System.Windows.Forms.TableLayoutPanel> denetiminin, <xref:System.Windows.Forms.Button> denetimini bulunan hücreye bırakmaya izin vermediğini unutmayın.

## <a name="swapping-controls"></a>Denetimleri değiştirme

<xref:System.Windows.Forms.TableLayoutPanel> denetimi, iki farklı hücreyi kaplayan denetimleri takas etmenizi sağlar.

#### <a name="to-swap-controls"></a>Denetimleri değiştirmek için

- <xref:System.Windows.Forms.Button> denetimlerinden birini, bulunan bir hücreden sürükleyin ve başka bir dolu hücreden üzerine bırakın. İki denetimin bir hücreden diğerine taşındığını unutmayın.

## <a name="next-steps"></a>Sonraki Adımlar

Düzen panellerinin ve denetimlerin birleşimini kullanarak karmaşık bir düzen elde edebilirsiniz. Daha fazla araştırma için öneriler şunlardır:

- <xref:System.Windows.Forms.Button> denetimlerinden birini daha büyük bir boyuta yeniden boyutlandırmayı deneyin ve düzen üzerindeki etkiyi aklınızda yapın.

- <xref:System.Windows.Forms.TableLayoutPanel> denetimine birden fazla denetimin seçimini yapıştırın ve denetimlerin nasıl eklendiğini notın.

- Düzen panelleri, diğer düzen panellerini içerebilir. Mevcut denetime <xref:System.Windows.Forms.TableLayoutPanel> denetimi bırakmayı deneyin.

- <xref:System.Windows.Forms.TableLayoutPanel> denetimini üst forma yerleştirin. Formu yeniden boyutlandırın ve düzen üzerindeki etkiyi aklınızda yapın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [İzlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [İzlenecek yol: yerelleştirilebilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel Denetimi için En İyi Yöntemler](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms’da Denetimleri Bağlama](how-to-anchor-controls-on-windows-forms.md)
- [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](windows-forms-controls-padding-autosize.md)
