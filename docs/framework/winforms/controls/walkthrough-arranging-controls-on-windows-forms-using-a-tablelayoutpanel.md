---
title: TableLayoutPanel kullanarak denetimleri düzenleme
description: FlowLayoutPanel denetimi ve TableLayoutPanel denetimini kullanarak Windows Forms denetimleri düzenlemeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 6dfc6dbdef38d635dc94877f79a8e3659295bd98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622802"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme

Bazı uygulamalar, form yeniden boyutlandırıldığı veya içeriklerin boyutu değiştikçe kendisini uygun şekilde değiştiren düzen içeren bir form gerektirir. Dinamik bir düzene ihtiyacınız olduğunda ve <xref:System.Windows.Forms.Control.Layout> kodunuzda açıkça olayları işlemek istemiyorsanız, bir Düzen paneli kullanmayı düşünün.

<xref:System.Windows.Forms.FlowLayoutPanel>Denetim ve denetim, <xref:System.Windows.Forms.TableLayoutPanel> formunuzdaki denetimleri düzenlemek için sezgisel yollar sağlar. Her ikisi de içindeki alt denetimlerin göreli konumlarını denetlemek için otomatik, yapılandırılabilir bir özellik sağlar ve her ikisi de çalışma zamanında dinamik düzen özellikleri sağlar, bu sayede üst form değişikliğinin boyutları olarak alt denetimleri yeniden boyutlandırabilir ve yeniden konumlandırabilirsiniz. Düzen bölmeleri, gelişmiş kullanıcı arabirimlerinin yerine geçme özelliğini etkinleştirmek için Düzen panelleri içinde iç içe olabilir.

, <xref:System.Windows.Forms.FlowLayoutPanel> İçeriğini belirli bir akış yönünde düzenler: yatay veya dikey. İçeriği bir satırdan sonrakine veya bir sütundan sonrakine kaydırılmış olabilir. Alternatif olarak, içeriği sarmalanabilir yerine kırpılabilir. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir FlowLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

, <xref:System.Windows.Forms.TableLayoutPanel> HTML öğesine benzer işlevler sağlayan bir kılavuzda içeriğini düzenler \<table> . <xref:System.Windows.Forms.TableLayoutPanel>Denetim, denetimleri her bir denetimin konumunu tam olarak belirtmenize gerek kalmadan kılavuz düzenine yerleştirmenize olanak sağlar. Hücreleri satırlar ve sütunlar halinde düzenlenir ve bunlar farklı boyutlarda olabilir. Hücreler, satırlar ve sütunlar arasında birleştirilebilir. Hücreler, bir form içerebilen ve kapsayıcı olarak birçok yönden davranan her şeyi içerebilir.

<xref:System.Windows.Forms.TableLayoutPanel>Denetim, çalışma zamanında orantılı bir yeniden boyutlandırma özelliği de sağlar, böylece formunuz yeniden boyutlandırıldığından düzen sorunsuzca değişebilir. Bu, <xref:System.Windows.Forms.TableLayoutPanel> denetimi veri girişi formları ve yerelleştirilmiş uygulamalar gibi amaçlar için uygun hale getirir. Daha fazla bilgi için bkz. [Izlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) ve [izlenecek yol: bir yerelleştirilebilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

Genel olarak, <xref:System.Windows.Forms.TableLayoutPanel> tüm düzen için kapsayıcı olarak bir denetim kullanmamalısınız. <xref:System.Windows.Forms.TableLayoutPanel>Düzenin bölümlerine orantılı yeniden boyutlandırma özellikleri sağlamak için denetimleri kullanın.

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

<xref:System.Windows.Forms.TableLayoutPanel>Denetim, denetimleri satırlar ve sütunlar halinde kolayca düzenlemenizi sağlar.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>TableLayoutPanel kullanarak satırlarda ve sütunlarda denetimleri düzenlemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin. Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> denetimin dört hücresi olduğunu unutmayın.

2. <xref:System.Windows.Forms.Button> **Araç kutusundan** denetimin içine bir denetim sürükleyin <xref:System.Windows.Forms.TableLayoutPanel> ve hücrelerden birine bırakın. <xref:System.Windows.Forms.Button>Denetimin seçtiğiniz hücre içinde oluşturulduğunu unutmayın.

3. <xref:System.Windows.Forms.Button> **Araç kutusundan** üç denetimi daha sürükleyin <xref:System.Windows.Forms.TableLayoutPanel> , böylece her hücrede bir düğme bulunur.

4. İki sütun arasında dikey boyutlandırma tutamacını alın ve sola taşıyın. <xref:System.Windows.Forms.Button>İlk sütundaki denetimlerin daha küçük bir genişliğe yeniden boyutlandırıldığını, <xref:System.Windows.Forms.Button> ikinci sütundaki denetimlerin boyutunun değişmeden olduğunu unutmayın.

5. İki sütun arasında dikey boyutlandırma tutamacını alın ve sağa taşıyın. <xref:System.Windows.Forms.Button>İlk sütundaki denetimlerin özgün boyutlarına dönüşdiğine, <xref:System.Windows.Forms.Button> ikinci sütundaki denetimlerin sağa taşınacağını unutmayın.

6. Paneldeki denetimlerde etkiyi görmek için yatay boyutlandırma tutamacını yukarı ve aşağı taşıyın.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Yerleştirme ve sabitleme kullanarak hücrelerde denetimleri konumlandırma

İçindeki alt denetimlerin sabitleme davranışı, <xref:System.Windows.Forms.TableLayoutPanel> diğer kapsayıcı denetimlerindeki davranıştan farklıdır. Alt denetimlerin yerleştirme davranışı, diğer kapsayıcı denetimleriyle aynıdır.

#### <a name="positioning-controls-within-cells"></a>Hücrelerin içindeki denetimleri konumlandırma

1. İlk denetimi seçin <xref:System.Windows.Forms.Button> . <xref:System.Windows.Forms.Control.Dock%2A>Özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.DockStyle.Fill> . <xref:System.Windows.Forms.Button>Denetimin hücresini dolduracak şekilde genişlediğine unutmayın.

2. Diğer denetimlerden birini seçin <xref:System.Windows.Forms.Button> . <xref:System.Windows.Forms.Control.Anchor%2A>Özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.AnchorStyles.Right> . Sağ kenarlığının hücrenin sağ kenarlığının yakınında olması için taşındığını unutmayın. Kenarlıklar arasındaki mesafe, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin ve panelin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin toplamıdır.

3. <xref:System.Windows.Forms.Button>Denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğinin değerini ve olarak değiştirin <xref:System.Windows.Forms.AnchorStyles.Right> <xref:System.Windows.Forms.AnchorStyles.Left> . Denetim, <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> değerlerini hesaba götürülüyse, hücrenin genişliğine göre boyutlandırıldığını unutmayın.

4. 2 ve 3 <xref:System.Windows.Forms.AnchorStyles.Top> . adımları ve stilleriyle tekrarlayın <xref:System.Windows.Forms.AnchorStyles.Bottom> .

## <a name="setting-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlama

Ve koleksiyonlarını kullanarak satırların ve sütunların ayrı özelliklerini ayarlayabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> .

#### <a name="to-set-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlamak için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Windows Form Tasarımcısı**denetimi seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> ![ ](./media/visual-studio-ellipsis-button.png) **sütunlar** girişinin yanındaki üç nokta (Visual Studio Özellikler penceresi) düğmesine tıklayarak koleksiyonu açın (...).

3. İlk sütunu seçin ve <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.SizeType.AutoSize> . Değişikliği kabul etmek için **Tamam** ' ı tıklatın. İlk sütunun genişliğinin denetime sığacak şekilde azaltıldığına unutmayın <xref:System.Windows.Forms.Button> . Ayrıca, sütunun genişliğinin yeniden boyutlandırılabilir olduğunu unutmayın.

4. **Özellikler** penceresinde, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonu açın ve ilk sütunu seçin. <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>Özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.SizeType.Percent> . Değişikliği kabul etmek için **Tamam** ' ı tıklatın. <xref:System.Windows.Forms.TableLayoutPanel>Denetimi daha büyük bir genişliğe göre yeniden boyutlandırın ve ilk sütunun genişliğinin genişlediğine unutmayın. <xref:System.Windows.Forms.TableLayoutPanel>Denetimi daha küçük bir genişliğe göre yeniden boyutlandırın ve ilk sütundaki düğmelerin hücreye sığacak şekilde boyutlandırıldığını unutmayın. Ayrıca, sütunun genişliğinin yeniden boyutlandırılabilir olduğunu unutmayın.

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonu açın ve listelenen tüm sütunları seçin. Her özelliğinin değerini olarak ayarlayın <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> <xref:System.Windows.Forms.SizeType.Percent> . Değişikliği kabul etmek için **Tamam** ' ı tıklatın. <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>Koleksiyonla tekrarlayın.

6. Köşe yeniden boyutlandırma tutamaçlarından birini alın ve denetimin genişliğini ve yüksekliğini yeniden boyutlandırın <xref:System.Windows.Forms.TableLayoutPanel> . Denetim boyutu değiştiğinde satırların ve sütunların yeniden boyutlandırıldığını unutmayın <xref:System.Windows.Forms.TableLayoutPanel> . Ayrıca, satır ve sütunların yatay ve dikey boyutlandırma tutamaçlarıyla yeniden boyutlandırılabilir olduğunu unutmayın.

## <a name="spanning-rows-and-columns-with-a-control"></a>Satırları ve sütunları bir denetimle yayma

<xref:System.Windows.Forms.TableLayoutPanel>Denetim, tasarım zamanında denetimlere birkaç yeni özellik ekler. Bu özelliklerden ikisi de `RowSpan` ve ' dir `ColumnSpan` . Bu özellikleri, bir denetimi birden fazla satır veya sütuna yaymak için kullanabilirsiniz.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Satırları ve sütunları bir denetimle yayma

1. <xref:System.Windows.Forms.Button>İlk satırdaki ve ilk sütundaki denetimi seçin.

2. **Özellikler** penceresinde, `ColumnSpan` özelliğinin değerini **2**olarak değiştirin. <xref:System.Windows.Forms.Button>Denetimin ilk sütunu ve ikinci sütunu doldurduğunu unutmayın. Ayrıca, bu değişikliğe uyum sağlamak için ek bir satır eklendiğini de göz önünde bulabilirsiniz.

3. Özelliği için 2. adımı tekrarlayın `RowSpan` .

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetim ekleme

<xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusundaki**denetimleri çift tıklatarak denetiminizi doldurabilirsiniz.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusuna çift tıklayarak denetim eklemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. <xref:System.Windows.Forms.Button> **Araç kutusundaki**denetim simgesine çift tıklayın. Denetimin ilk hücresinde yeni bir düğme denetimi göründüğünü unutmayın <xref:System.Windows.Forms.TableLayoutPanel> .

3. **Araç kutusunda**birden fazla denetim ' e çift tıklayın. Yeni denetimlerin, denetimin kullanılmayan hücrelerinde çok büyük bir şekilde göründüğünü unutmayın <xref:System.Windows.Forms.TableLayoutPanel> . Ayrıca, <xref:System.Windows.Forms.TableLayoutPanel> kullanılabilir açık hücre yoksa denetimin yeni denetimlere uyum sağlayacak şekilde genişlediğine de unutmayın.

## <a name="automatic-handling-of-overflows"></a>Taşmaları otomatik Işleme

<xref:System.Windows.Forms.TableLayoutPanel>Denetime denetim eklerken, yeni Denetimleriniz için boş hücreler tükenmeyebilir. <xref:System.Windows.Forms.TableLayoutPanel>Denetim, hücre sayısını artırarak bu durumu otomatik olarak işler.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Taşın otomatik işlemesini gözlemlemek için

1. Denetimde hala boş hücreler varsa <xref:System.Windows.Forms.TableLayoutPanel> , <xref:System.Windows.Forms.Button> Denetim tamamlanana kadar yeni denetimler eklemeye devam edin <xref:System.Windows.Forms.TableLayoutPanel> .

2. <xref:System.Windows.Forms.TableLayoutPanel>Denetim dolduğunda, <xref:System.Windows.Forms.Button> başka bir denetim eklemek Için **araç kutusundaki** simgeye çift tıklayın <xref:System.Windows.Forms.Button> . <xref:System.Windows.Forms.TableLayoutPanel>Denetimin yeni denetim için yeni hücreler oluşturduğunu unutmayın. Birkaç denetim ekleyin ve yeniden boyutlandırma davranışını gözlemleyin.

3. <xref:System.Windows.Forms.TableLayoutPanel>Denetimin <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize> . <xref:System.Windows.Forms.Button>Denetim tam olana kadar denetimler eklemek Için **araç kutusundaki** simgeye çift tıklayın <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.TableLayoutPanel> . <xref:System.Windows.Forms.Button> **Araç kutusundaki** simgeye tekrar çift tıklayın. Ek satır ve sütun oluşturulamadığını bildiren **Windows Form Tasarımcısı** bir hata mesajı almayacağınızı unutmayın.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim ekleme

Bir denetime denetim ekleyebilir <xref:System.Windows.Forms.TableLayoutPanel> ve kendi anahattını bir hücreye çizerek boyutunu belirtebilirsiniz.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim eklemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. **Araç kutusunda** <xref:System.Windows.Forms.Button> Denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

3. Fare işaretçisini denetimin üzerine taşıyın <xref:System.Windows.Forms.TableLayoutPanel> . İşaretçinin, denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın <xref:System.Windows.Forms.Button> .

4. Fare düğmesine tıklayın ve basılı tutun.

5. Denetimin anahattını çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.Button> . Boyutla memnun olduğunuzda fare düğmesini bırakın. <xref:System.Windows.Forms.Button>Denetimin, denetimin anahattını çizdiğiniz hücrede oluşturulduğunu unutmayın.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Hücreler Içindeki birden çok denetime Izin verilmiyor

<xref:System.Windows.Forms.TableLayoutPanel>Denetim, her hücre için yalnızca bir alt denetim içerebilir.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Hücreler içinde birden çok denetime izin verilmediğini göstermek için

- <xref:System.Windows.Forms.Button> **Araç kutusundan** denetimin içine bir denetim sürükleyin <xref:System.Windows.Forms.TableLayoutPanel> ve bulunan hücrelerden birine bırakın. <xref:System.Windows.Forms.TableLayoutPanel>Denetimin, denetimi, bulunan hücreye bırakmayı izin vermediğini unutmayın <xref:System.Windows.Forms.Button> .

## <a name="swapping-controls"></a>Denetimleri değiştirme

<xref:System.Windows.Forms.TableLayoutPanel>Denetim, iki farklı hücreyi kaplayan denetimleri takas etmenizi sağlar.

#### <a name="to-swap-controls"></a>Denetimleri değiştirmek için

- Denetimlerin bulunan bir hücreden birini sürükleyin <xref:System.Windows.Forms.Button> ve başka bir dolu hücreye bırakın. İki denetimin bir hücreden diğerine taşındığını unutmayın.

## <a name="next-steps"></a>Sonraki Adımlar

Düzen panellerinin ve denetimlerin birleşimini kullanarak karmaşık bir düzen elde edebilirsiniz. Daha fazla araştırma için öneriler şunlardır:

- <xref:System.Windows.Forms.Button>Denetimlerden birini daha büyük bir boyuta yeniden boyutlandırmayı deneyin ve düzen üzerindeki etkiyi aklınızda yapın.

- Denetime birden fazla denetim seçimi yapıştırın <xref:System.Windows.Forms.TableLayoutPanel> ve denetimlerin nasıl eklendiğini notın.

- Düzen panelleri, diğer düzen panellerini içerebilir. <xref:System.Windows.Forms.TableLayoutPanel>Varolan denetime bir denetim bırakmayı deneyin.

- <xref:System.Windows.Forms.TableLayoutPanel>Denetimi üst forma yerleştirin. Formu yeniden boyutlandırın ve düzen üzerindeki etkiyi aklınızda yapın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'ta Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [İzlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [İzlenecek yol: yerelleştirilebilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel Denetimi için En İyi Yöntemler](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Formlarına Denetimleri Yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Formlarında Denetimleri Sabitleme](how-to-anchor-controls-on-windows-forms.md)
- [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Formları Denetimlerini Düzenleme](windows-forms-controls-padding-autosize.md)
