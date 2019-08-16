---
title: "İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 7566f19282ffd5a3cac86693a64899f25ce37b9f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040286"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme

Bazı uygulamalar, form yeniden boyutlandırıldığı veya içeriklerin boyutu değiştikçe kendisini uygun şekilde değiştiren düzen içeren bir form gerektirir. Dinamik bir düzene ihtiyacınız olduğunda ve kodunuzda açıkça olayları işlemek <xref:System.Windows.Forms.Control.Layout> istemiyorsanız, bir Düzen paneli kullanmayı düşünün.

<xref:System.Windows.Forms.FlowLayoutPanel> Denetim<xref:System.Windows.Forms.TableLayoutPanel> ve denetim, formunuzdaki denetimleri düzenlemek için sezgisel yollar sağlar. Her ikisi de içindeki alt denetimlerin göreli konumlarını denetlemek için otomatik, yapılandırılabilir bir özellik sağlar ve her ikisi de çalışma zamanında dinamik düzen özellikleri sunduklarında, ana formun boyutları olarak alt denetimleri yeniden boyutlandırabilir ve yeniden konumlandırabilirsiniz değişebilir. Düzen bölmeleri, gelişmiş kullanıcı arabirimlerinin yerine geçme özelliğini etkinleştirmek için Düzen panelleri içinde iç içe olabilir.

, <xref:System.Windows.Forms.FlowLayoutPanel> İçeriğini belirli bir akış yönünde düzenler: yatay veya dikey. İçeriği bir satırdan sonrakine veya bir sütundan sonrakine kaydırılmış olabilir. Alternatif olarak, içeriği sarmalanabilir yerine kırpılabilir. Daha fazla bilgi için bkz [. İzlenecek yol: FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)kullanarak Windows Forms denetimlerini düzenleme.

, <xref:System.Windows.Forms.TableLayoutPanel> HTML\<Tablo > öğesine benzer işlevler sağlayan bir kılavuzda içeriğini düzenler. Denetim <xref:System.Windows.Forms.TableLayoutPanel> , denetimleri her bir denetimin konumunu tam olarak belirtmenize gerek kalmadan kılavuz düzenine yerleştirmenize olanak sağlar. Hücreleri satırlar ve sütunlar halinde düzenlenir ve bunlar farklı boyutlarda olabilir. Hücreler, satırlar ve sütunlar arasında birleştirilebilir. Hücreler, bir form içerebilen ve kapsayıcı olarak birçok yönden davranan her şeyi içerebilir.

Denetim <xref:System.Windows.Forms.TableLayoutPanel> , çalışma zamanında orantılı bir yeniden boyutlandırma özelliği de sağlar, böylece formunuz yeniden boyutlandırıldığından düzen sorunsuzca değişebilir. Bu, <xref:System.Windows.Forms.TableLayoutPanel> denetimi veri girişi formları ve yerelleştirilmiş uygulamalar gibi amaçlar için uygun hale getirir. Daha fazla bilgi için bkz [. İzlenecek yol: Veri girişi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) ve İzlenecek yol için yeniden [boyutlandırılabilir bir Windows formu oluşturma: Yerelleştirilebilir Windows formu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))oluşturma.

Genel olarak, tüm düzen için kapsayıcı olarak <xref:System.Windows.Forms.TableLayoutPanel> bir denetim kullanmamalısınız. Düzenin <xref:System.Windows.Forms.TableLayoutPanel> bölümlerine orantılı yeniden boyutlandırma özellikleri sağlamak için denetimleri kullanın.

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

1. "TableLayoutPanelExample" adlı bir Windows uygulaması projesi oluşturun. Daha fazla bilgi için [nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun.

2. **Windows** **form tasarımcısında**formu seçin.

## <a name="arranging-controls-in-rows-and-columns"></a>Satırlarda ve sütunlarda denetimleri düzenleme

Denetim <xref:System.Windows.Forms.TableLayoutPanel> , denetimleri satırlar ve sütunlar halinde kolayca düzenlemenizi sağlar.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>TableLayoutPanel kullanarak satırlarda ve sütunlarda denetimleri düzenlemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin. Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> denetimin dört hücresi olduğunu unutmayın.

2. **Araç kutusundan** denetimin içine <xref:System.Windows.Forms.Button> birdenetimsürükleyinvehücrelerdenbirinebırakın.<xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Button> Denetimin seçtiğiniz hücre içinde oluşturulduğunu unutmayın.

3. **Araç kutusundan** <xref:System.Windows.Forms.Button> üçdenetimidahasürükleyin,böyleceherhücredebirdüğmebulunur.<xref:System.Windows.Forms.TableLayoutPanel>

4. İki sütun arasında dikey boyutlandırma tutamacını alın ve sola taşıyın. İlk sütundaki <xref:System.Windows.Forms.Button> denetimlerin daha küçük bir genişliğe yeniden boyutlandırıldığını, ikinci sütundaki <xref:System.Windows.Forms.Button> denetimlerin boyutunun değişmeden olduğunu unutmayın.

5. İki sütun arasında dikey boyutlandırma tutamacını alın ve sağa taşıyın. İlk sütundaki <xref:System.Windows.Forms.Button> denetimlerin özgün boyutlarına dönüşdiğine, ikinci sütundaki denetimlerin sağa taşınacağını unutmayın. <xref:System.Windows.Forms.Button>

6. Paneldeki denetimlerde etkiyi görmek için yatay boyutlandırma tutamacını yukarı ve aşağı taşıyın.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Yerleştirme ve sabitleme kullanarak hücrelerde denetimleri konumlandırma

İçindeki alt denetimlerin sabitleme davranışı, diğer kapsayıcı denetimlerindeki <xref:System.Windows.Forms.TableLayoutPanel> davranıştan farklıdır. Alt denetimlerin yerleştirme davranışı, diğer kapsayıcı denetimleriyle aynıdır.

#### <a name="positioning-controls-within-cells"></a>Hücrelerin içindeki denetimleri konumlandırma

1. İlk <xref:System.Windows.Forms.Button> denetimi seçin. <xref:System.Windows.Forms.Control.Dock%2A> Özelliğinin değerini olarak <xref:System.Windows.Forms.DockStyle.Fill>değiştirin. <xref:System.Windows.Forms.Button> Denetimin hücresini dolduracak şekilde genişlediğine unutmayın.

2. Diğer <xref:System.Windows.Forms.Button> denetimlerden birini seçin. <xref:System.Windows.Forms.Control.Anchor%2A> Özelliğinin değerini olarak <xref:System.Windows.Forms.AnchorStyles.Right>değiştirin. Sağ kenarlığının hücrenin sağ kenarlığının yakınında olması için taşındığını unutmayın. Kenarlıklar arasındaki mesafe, <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin ve panelin özelliğinin toplamıdır.

3. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.AnchorStyles.Right> Denetimin özelliğinin değerini ve<xref:System.Windows.Forms.AnchorStyles.Left>olarak değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A> Denetim, <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> değerlerini hesaba götürülüyse, hücrenin genişliğine göre boyutlandırıldığını unutmayın.

4. 2 ve 3 <xref:System.Windows.Forms.AnchorStyles.Top> . adımları ve <xref:System.Windows.Forms.AnchorStyles.Bottom> stilleriyle tekrarlayın.

## <a name="setting-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlama

<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> Ve<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonlarını kullanarak satırların ve sütunların ayrı özelliklerini ayarlayabilirsiniz.

#### <a name="to-set-row-and-column-properties"></a>Satır ve sütun özelliklerini ayarlamak için

1. **Windows Form Tasarımcısı**denetimi seçin <xref:System.Windows.Forms.TableLayoutPanel> .

2. **Özellikler** penceresinde, **sütunlar** girişinin yanındaki üç <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> nokta (Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi)![düğmesine tıklayarak koleksiyonu açın (...).

3. İlk sütunu seçin ve <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğinin değerini olarak <xref:System.Windows.Forms.SizeType.AutoSize>değiştirin. Değişikliği kabul etmek için **Tamam** ' ı tıklatın. İlk sütunun genişliğinin <xref:System.Windows.Forms.Button> denetime sığacak şekilde azaltıldığına unutmayın. Ayrıca, sütunun genişliğinin yeniden boyutlandırılabilir olduğunu unutmayın.

4. **Özellikler** penceresinde, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonu açın ve ilk sütunu seçin. <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> Özelliğinin değerini olarak <xref:System.Windows.Forms.SizeType.Percent>değiştirin. Değişikliği kabul etmek için **Tamam** ' ı tıklatın. <xref:System.Windows.Forms.TableLayoutPanel> Denetimi daha büyük bir genişliğe göre yeniden boyutlandırın ve ilk sütunun genişliğinin genişlediğine unutmayın. <xref:System.Windows.Forms.TableLayoutPanel> Denetimi daha küçük bir genişliğe göre yeniden boyutlandırın ve ilk sütundaki düğmelerin hücreye sığacak şekilde boyutlandırıldığını unutmayın. Ayrıca, sütunun genişliğinin yeniden boyutlandırılabilir olduğunu unutmayın.

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> koleksiyonu açın ve listelenen tüm sütunları seçin. Her <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliğinin değerini olarak <xref:System.Windows.Forms.SizeType.Percent>ayarlayın. Değişikliği kabul etmek için **Tamam** ' ı tıklatın. <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> Koleksiyonla tekrarlayın.

6. Köşe yeniden boyutlandırma tutamaçlarından birini alın ve <xref:System.Windows.Forms.TableLayoutPanel> denetimin genişliğini ve yüksekliğini yeniden boyutlandırın. <xref:System.Windows.Forms.TableLayoutPanel> Denetim boyutu değiştiğinde satırların ve sütunların yeniden boyutlandırıldığını unutmayın. Ayrıca, satır ve sütunların yatay ve dikey boyutlandırma tutamaçlarıyla yeniden boyutlandırılabilir olduğunu unutmayın.

## <a name="spanning-rows-and-columns-with-a-control"></a>Satırları ve sütunları bir denetimle yayma

Denetim <xref:System.Windows.Forms.TableLayoutPanel> , tasarım zamanında denetimlere birkaç yeni özellik ekler. Bu özelliklerden ikisi de ve `RowSpan` ' `ColumnSpan`dir. Bu özellikleri, bir denetimi birden fazla satır veya sütuna yaymak için kullanabilirsiniz.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Satırları ve sütunları bir denetimle yayma

1. İlk satırdaki ve ilk sütundaki denetimiseçin.<xref:System.Windows.Forms.Button>

2. **Özellikler** penceresinde, `ColumnSpan` özelliğinin değerini **2**olarak değiştirin. <xref:System.Windows.Forms.Button> Denetimin ilk sütunu ve ikinci sütunu doldurduğunu unutmayın. Ayrıca, bu değişikliğe uyum sağlamak için ek bir satır eklendiğini de göz önünde bulabilirsiniz.

3. `RowSpan` Özelliği için 2. adımı tekrarlayın.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetim ekleme

**Araç kutusundaki**denetimleri çift <xref:System.Windows.Forms.TableLayoutPanel> tıklatarak denetiminizi doldurabilirsiniz.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusuna çift tıklayarak denetim eklemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. <xref:System.Windows.Forms.Button> **Araç kutusundaki**denetim simgesine çift tıklayın. <xref:System.Windows.Forms.TableLayoutPanel> Denetimin ilk hücresinde yeni bir düğme denetimi göründüğünü unutmayın.

3. **Araç kutusunda**birden fazla denetim ' e çift tıklayın. Yeni denetimlerin, <xref:System.Windows.Forms.TableLayoutPanel> denetimin kullanılmayan hücrelerinde çok büyük bir şekilde göründüğünü unutmayın. Ayrıca, <xref:System.Windows.Forms.TableLayoutPanel> kullanılabilir açık hücre yoksa denetimin yeni denetimlere uyum sağlayacak şekilde genişlediğine de unutmayın.

## <a name="automatic-handling-of-overflows"></a>Taşmaları otomatik Işleme

<xref:System.Windows.Forms.TableLayoutPanel> Denetime denetim eklerken, yeni Denetimleriniz için boş hücreler tükenmeyebilir. <xref:System.Windows.Forms.TableLayoutPanel> Denetim, hücre sayısını artırarak bu durumu otomatik olarak işler.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Taşın otomatik işlemesini gözlemlemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> Denetimde hala boş hücreler varsa, <xref:System.Windows.Forms.TableLayoutPanel> denetim tamamlanana kadar yeni <xref:System.Windows.Forms.Button> denetimler eklemeye devam edin.

2. Denetim dolduğunda <xref:System.Windows.Forms.Button> , başka bir <xref:System.Windows.Forms.Button> denetim eklemek için **araç kutusundaki** simgeye çift tıklayın. <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> Denetimin yeni denetim için yeni hücreler oluşturduğunu unutmayın. Birkaç denetim ekleyin ve yeniden boyutlandırma davranışını gözlemleyin.

3. <xref:System.Windows.Forms.TableLayoutPanel> Denetimin özelliğinin değerini olarak<xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>değiştirin. <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> Denetim tam olana kadar <xref:System.Windows.Forms.Button> denetimler <xref:System.Windows.Forms.Button> eklemek için araç kutusundaki simgeye çift tıklayın. <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Button> **Araç kutusundaki** simgeye tekrar çift tıklayın. Ek satır ve sütun oluşturulamadığını bildiren **Windows Form Tasarımcısı** bir hata mesajı almayacağınızı unutmayın.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim ekleme

Bir denetime denetim <xref:System.Windows.Forms.TableLayoutPanel> ekleyebilir ve kendi anahattını bir hücreye çizerek boyutunu belirtebilirsiniz.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim eklemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. **Araç kutusunda** <xref:System.Windows.Forms.Button> denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

3. Fare işaretçisini <xref:System.Windows.Forms.TableLayoutPanel> denetimin üzerine taşıyın. İşaretçinin, <xref:System.Windows.Forms.Button> denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın.

4. Fare düğmesine tıklayın ve basılı tutun.

5. <xref:System.Windows.Forms.Button> Denetimin anahattını çizmek için fare işaretçisini sürükleyin. Boyutla memnun olduğunuzda fare düğmesini bırakın. <xref:System.Windows.Forms.Button> Denetimin, denetimin anahattını çizdiğiniz hücrede oluşturulduğunu unutmayın.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Hücreler Içindeki birden çok denetime Izin verilmiyor

Denetim <xref:System.Windows.Forms.TableLayoutPanel> , her hücre için yalnızca bir alt denetim içerebilir.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Hücreler içinde birden çok denetime izin verilmediğini göstermek için

- **Araç kutusundan** denetimin içine <xref:System.Windows.Forms.Button> birdenetimsürükleyinvebulunanhücrelerdenbirinebırakın.<xref:System.Windows.Forms.TableLayoutPanel> Denetimin, denetimi, bulunan <xref:System.Windows.Forms.Button> hücreye bırakmayı izin vermediğini unutmayın. <xref:System.Windows.Forms.TableLayoutPanel>

## <a name="swapping-controls"></a>Denetimleri değiştirme

<xref:System.Windows.Forms.TableLayoutPanel> Denetim, iki farklı hücreyi kaplayan denetimleri takas etmenizi sağlar.

#### <a name="to-swap-controls"></a>Denetimleri değiştirmek için

- <xref:System.Windows.Forms.Button> Denetimlerin bulunan bir hücreden birini sürükleyin ve başka bir dolu hücreye bırakın. İki denetimin bir hücreden diğerine taşındığını unutmayın.

## <a name="next-steps"></a>Sonraki Adımlar

Düzen panellerinin ve denetimlerin birleşimini kullanarak karmaşık bir düzen elde edebilirsiniz. Daha fazla araştırma için öneriler şunlardır:

- <xref:System.Windows.Forms.Button> Denetimlerden birini daha büyük bir boyuta yeniden boyutlandırmayı deneyin ve düzen üzerindeki etkiyi aklınızda yapın.

- <xref:System.Windows.Forms.TableLayoutPanel> Denetime birden fazla denetim seçimi yapıştırın ve denetimlerin nasıl eklendiğini notın.

- Düzen panelleri, diğer düzen panellerini içerebilir. Varolan denetime bir <xref:System.Windows.Forms.TableLayoutPanel> denetim bırakmayı deneyin.

- <xref:System.Windows.Forms.TableLayoutPanel> Denetimi üst forma yerleştirin. Formu yeniden boyutlandırın ve düzen üzerindeki etkiyi aklınızda yapın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: Anlık görüntü çizgilerini kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows Kullanıcı deneyimi, Kullanıcı arabirimi geliştiricileri ve tasarımcıları için resmi yönergeler. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [İzlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [İzlenecek yol: Yerelleştirilebilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel Denetimi için En İyi Yöntemler](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms denetimleri yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms üzerinde geçiş denetimleri](how-to-anchor-controls-on-windows-forms.md)
- [İzlenecek yol: Doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md)
