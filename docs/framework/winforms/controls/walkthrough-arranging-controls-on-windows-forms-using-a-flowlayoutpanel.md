---
title: FlowLayoutPanel kullanarak denetimleri düzenleme
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 6df0a910ee346f319fbee835e5e632808630a99e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745406"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme

Bazı uygulamalar, form yeniden boyutlandırıldığı veya içeriklerin boyutu değiştikçe kendisini uygun şekilde değiştiren düzen içeren bir form gerektirir. Dinamik bir düzene ihtiyacınız olduğunda ve kodunuzda açıkça <xref:System.Windows.Forms.Control.Layout> olaylarını işlemek istemiyorsanız, bir Düzen paneli kullanmayı düşünün.

<xref:System.Windows.Forms.FlowLayoutPanel> denetimi ve <xref:System.Windows.Forms.TableLayoutPanel> denetimi, formunuzdaki denetimleri düzenlemek için sezgisel yollar sağlar. Her ikisi de içindeki alt denetimlerin göreli konumlarını denetlemek için otomatik, yapılandırılabilir bir özellik sağlar ve her ikisi de çalışma zamanında dinamik düzen özellikleri sunduklarında, ana formun boyutları olarak alt denetimleri yeniden boyutlandırabilir ve yeniden konumlandırabilirsiniz değişebilir. Düzen bölmeleri, gelişmiş kullanıcı arabirimlerinin yerine geçme özelliğini etkinleştirmek için Düzen panelleri içinde iç içe olabilir.

<xref:System.Windows.Forms.TableLayoutPanel>, HTML \<Tablo > öğesine benzer işlevler sağlayarak içeriğini bir kılavuza yerleştirir. Hücreleri satırlar ve sütunlar halinde düzenlenir ve bunlar farklı boyutlarda olabilir. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

<xref:System.Windows.Forms.FlowLayoutPanel>, içeriğini belirli bir akış yönünde düzenler: yatay veya dikey. İçeriği bir satırdan sonrakine veya bir sütundan sonrakine kaydırılmış olabilir. Alternatif olarak, içeriği sarmalanabilir yerine kırpılabilir. Bu izlenecek yolda gösterilen görevler şunlardır:

- Windows Forms projesi oluşturma

- Denetimleri yatayda ve dikeyde düzenleme

- Akış yönünü değiştirme

- Akış sonları ekleniyor

- Doldurma ve kenar boşlukları kullanarak denetimleri düzenleme

- Araç kutusunda çift tıklayarak denetim ekleme

- Ana hattını çizerek bir denetim ekleme

- Giriş Işaretini kullanarak denetim ekleme

- Varolan denetimleri farklı bir üst öğeye yeniden atama

İşiniz bittiğinde, bu önemli düzen özellikleri tarafından yürütülen rolü anlayacaksınız.

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio 'da, "flowlayoutpanelexbol" adlı bir Windows tabanlı **uygulama projesi oluşturun** ** > **  >  ** > (** **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması**).

2. Form **tasarımcısında**formu seçin.

## <a name="arranging-controls-horizontally-and-vertically"></a>Denetimleri yatayda ve dikeyde düzenleme
 <xref:System.Windows.Forms.FlowLayoutPanel> denetimi, her bir denetimin konumunu tam olarak belirtmenize gerek kalmadan, denetimleri satır veya sütunlara yerleştirmenize olanak sağlar.

 <xref:System.Windows.Forms.FlowLayoutPanel> denetimi, üst form değişikliğinin boyutları olarak alt denetimlerini yeniden boyutlandırabilir veya yeniden düzenleyebilir.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>FlowLayoutPanel kullanarak denetimleri yatayda ve dikeyde düzenleme

1. **Araç kutusundan** bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimini formunuza sürükleyin.

2. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.FlowLayoutPanel>sürükleyin. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin sol üst köşesine otomatik olarak taşınacağını unutmayın.

3. **Araç kutusundan** başka bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.FlowLayoutPanel>sürükleyin. <xref:System.Windows.Forms.Button> denetiminin otomatik olarak ilk <xref:System.Windows.Forms.Button> denetiminin yanındaki bir konuma taşındığını unutmayın. <xref:System.Windows.Forms.FlowLayoutPanel>, aynı satırdaki iki denetimi sığdırmak için çok dar ise, yeni <xref:System.Windows.Forms.Button> denetimi otomatik olarak sonraki satıra taşınır.

4. **Araç kutusundan** birkaç <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.FlowLayoutPanel>içine sürükleyin. Bir sonraki satıra kayana kadar <xref:System.Windows.Forms.Button> denetimleri yerleştirmeye devam edin.

5. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğinin değerini `false`olarak değiştirin. Alt denetimlerin artık sonraki satıra akmadığını unutmayın. Bunun yerine, ilk satıra taşınır ve kırpılır.

6. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğinin değerini `true`olarak değiştirin. Alt denetimlerin bir sonraki satıra sarılacağını unutmayın.

7. Tüm <xref:System.Windows.Forms.Button> denetimleri ilk sütuna taşınana kadar <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin genişliğini azaltın.

8. Tüm <xref:System.Windows.Forms.Button> denetimleri ilk satıra taşınana kadar <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin genişliğini artırın. Formunuzu daha büyük genişliğe uyacak şekilde yeniden boyutlandırmanız gerekebilir.

## <a name="changing-flow-direction"></a>Akış yönünü değiştirme
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliği, denetimlerin düzenlendiği yönü değiştirmenize izin verir. Alt denetimleri soldan sağa, sağdan sola, yukarıdan aşağıya veya alttan üste kadar düzenleyebilirsiniz.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>FlowLayoutPanel 'teki akış yönünü değiştirmek için

1. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğinin değerini <xref:System.Windows.Forms.FlowDirection.TopDown>olarak değiştirin. Alt denetimlerin, denetimin yüksekliğine bağlı olarak bir veya daha fazla sütuna yeniden düzenlendiğini unutmayın.

2. <xref:System.Windows.Forms.FlowLayoutPanel>, yüksekliğinin <xref:System.Windows.Forms.Button> denetimlerinin sütunundan daha kısa olacak şekilde yeniden boyutlandırın. <xref:System.Windows.Forms.FlowLayoutPanel> sonraki sütuna akan alt denetimleri yeniden düzenler. Yüksekliği azaltmasına devam edin ve alt denetimlerin ardışık sütunlara akmasını unutmayın. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğinin değerini <xref:System.Windows.Forms.FlowDirection.RightToLeft>olarak değiştirin. Alt denetimlerin konumlarının tersine çevrilip çevrildiğine unutmayın. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğinin değerini <xref:System.Windows.Forms.FlowDirection.BottomUp>olarak değiştirdiğinizde düzeni gözlemleyin.

## <a name="inserting-flow-breaks"></a>Akış sonları ekleniyor
 <xref:System.Windows.Forms.FlowLayoutPanel> denetimi, alt denetimlerine FlowBreak özelliği sağlar. FlowBreak özelliğinin değerini `true` olarak ayarlamak, <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin geçerli akış yönünde denetimleri yerleştirmeye ve sonraki satıra veya sütuna kaymasına neden olur.

### <a name="to-insert-flow-breaks"></a>Akış sonları eklemek için

1. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğinin değerini <xref:System.Windows.Forms.FlowDirection.TopDown>olarak değiştirin.

2. En soldaki sütunun ortasındaki <xref:System.Windows.Forms.Button> denetimlerinden birini seçin.

3. <xref:System.Windows.Forms.Button> denetiminin FlowBreak özelliğinin değerini `true`olarak ayarlayın. Sütunun bozuk olduğuna ve seçili <xref:System.Windows.Forms.Button> denetimini izleyen denetimlerin sonraki sütuna akmasını unutmayın. Özgün davranışa dönmek için <xref:System.Windows.Forms.Button> denetiminin FlowBreak özelliğinin değerini `false` olarak ayarlayın.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Yerleştirme ve sabitleme kullanarak denetimleri konumlandırma
 Alt denetimlerin sabitleme ve sabitleme davranışları, diğer kapsayıcı denetimlerindeki davranışlardan farklıdır. Hem yerleştirme hem de sabitleme, akış yönündeki en büyük denetime göredir.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Yerleştirme ve sabitleme kullanarak denetimleri konumlandırmak için

1. <xref:System.Windows.Forms.Button> denetimleri bir sütunda düzenlenene kadar <xref:System.Windows.Forms.FlowLayoutPanel> boyutunu artırın.

2. Üstteki <xref:System.Windows.Forms.Button> denetimini seçin. Genişliği, diğer <xref:System.Windows.Forms.Button> denetimlerinin iki katına daha fazla olacak şekilde arttırın.

3. İkinci <xref:System.Windows.Forms.Button> denetimini seçin. <xref:System.Windows.Forms.Control.Anchor%2A> özelliğinin değerini <xref:System.Windows.Forms.AnchorStyles.Right>olarak değiştirin. Sağ kenarlığının ilk <xref:System.Windows.Forms.Button> denetimin sağ kenarlığına hizalanmasını sağlayacak şekilde taşınacağını unutmayın.

4. <xref:System.Windows.Forms.Control.Anchor%2A> özelliğinin değerini <xref:System.Windows.Forms.AnchorStyles.Right> ve <xref:System.Windows.Forms.AnchorStyles.Left>olarak değiştirin. İlk <xref:System.Windows.Forms.Button> denetimiyle aynı genişliğe göre boyutlandırıldığını unutmayın.

5. Üçüncü <xref:System.Windows.Forms.Button> denetimini seçin. <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak değiştirin. İlk <xref:System.Windows.Forms.Button> denetimiyle aynı genişliğe göre boyutlandırıldığını unutmayın.

## <a name="arranging-controls-using-padding-and-margins"></a>Doldurma ve kenar boşlukları kullanarak denetimleri düzenleme
 Ayrıca, <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> özelliklerini değiştirerek <xref:System.Windows.Forms.FlowLayoutPanel> denetiinizdeki denetimleri düzenleyebilirsiniz.

 <xref:System.Windows.Forms.Control.Padding%2A> özelliği, denetimlerin bir <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin hücresinde yerleşimini denetlemenize olanak tanır. Alt denetimler ve <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin kenarlığı arasındaki boşluğu belirtir.

 <xref:System.Windows.Forms.Control.Margin%2A> özelliği, denetimler arasındaki aralığı denetlemenize olanak tanır.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Doldurma ve kenar boşluğu özelliklerini kullanarak denetimleri düzenlemek için

1. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak değiştirin. Formunuz yeterince büyükse, <xref:System.Windows.Forms.Button> denetimleri <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin ilk sütununa taşınır.

2. <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değerini, **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Padding%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **20**olarak ayarlayarak değiştirin. Daha fazla bilgi için bkz. [Izlenecek yol: doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md). Alt denetimlerin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin ortasına doğru taşındığını unutmayın. <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin artan değeri, alt denetimleri <xref:System.Windows.Forms.FlowLayoutPanel> denetimin kenarlıklarından uzağa gönderir.

3. <xref:System.Windows.Forms.FlowLayoutPanel> tüm <xref:System.Windows.Forms.Button> denetimlerini seçin ve <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin değerini **20**olarak ayarlayın. <xref:System.Windows.Forms.Button> denetimleri arasındaki boşluğun arttığı şekilde, daha fazla taşınabilmesini unutmayın. Tüm alt denetimleri görmek için <xref:System.Windows.Forms.FlowLayoutPanel> denetimini daha büyük olacak şekilde yeniden boyutlandırmanız gerekebilir.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetim ekleme
 **Araç kutusundaki**denetimleri çift tıklayarak <xref:System.Windows.Forms.FlowLayoutPanel> denetiminizi doldurabilirsiniz.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusuna çift tıklayarak denetim eklemek için

1. **Araç kutusundaki**<xref:System.Windows.Forms.Button> denetim simgesine çift tıklayın. Yeni bir <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel> denetiminde göründüğünü unutmayın.

2. **Araç kutusunda**birden fazla denetim ' e çift tıklayın. Yeni denetimlerin <xref:System.Windows.Forms.FlowLayoutPanel> denetiminde yoğun şekilde göründüğünü unutmayın.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim ekleme
 <xref:System.Windows.Forms.FlowLayoutPanel> denetimine bir denetim ekleyebilir ve kendi anahattını bir hücreye çizerek boyutunu belirtebilirsiniz.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim eklemek için

1. **Araç kutusunda**<xref:System.Windows.Forms.Button> denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

2. Fare işaretçisini <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin üzerine taşıyın. İşaretçinin, <xref:System.Windows.Forms.Button> denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın.

3. Fare düğmesine tıklayın ve basılı tutun.

4. <xref:System.Windows.Forms.Button> denetiminin anahattını çizmek için fare işaretçisini sürükleyin. Boyutla memnun olduğunuzda fare düğmesini bırakın. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin bir sonraki açık konumunda oluşturulduğunu unutmayın.

## <a name="inserting-controls-using-the-insertion-bar"></a>Ekleme çubuğunu kullanarak denetim ekleme
 <xref:System.Windows.Forms.FlowLayoutPanel> denetiminde belirli bir konuma denetim ekleyebilirsiniz. Bir denetimi <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin istemci alanına sürüklediğinizde, denetimin nereye ekleneceğini göstermek için bir ekleme çubuğu görünür.

### <a name="to-insert-a-control-using-the-caret"></a>Giriş işaretini kullanarak bir denetim eklemek için

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.FlowLayoutPanel> denetimine sürükleyin ve iki <xref:System.Windows.Forms.Button> denetimi arasındaki boşluğu işaret edin. <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.FlowLayoutPanel> denetimine bırakıldığında nereye yerleştirileceğini belirten bir ekleme çubuğunun çizildiğini unutmayın. Yeni <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.FlowLayoutPanel> denetimine bırakmadan önce, ekleme çubuğunun nasıl hareket edeceğini gözlemlemek için fare işaretçisini etrafında taşıyın.

2. Yeni <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.FlowLayoutPanel> denetimine bırakın. Yeni <xref:System.Windows.Forms.Button> denetiminin, <xref:System.Windows.Forms.Control.Margin%2A> özelliği farklı bir değere sahip olduğu için diğerleri ile Hizalanmadığını unutmayın.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Varolan denetimleri farklı bir üst öğeye yeniden atama
 Formunuzda bulunan denetimleri yeni bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimine atayabilirsiniz.

### <a name="to-reparent-existing-controls"></a>Varolan denetimleri yeniden üst üste eklemek için

1. **Araç kutusundan** üç <xref:System.Windows.Forms.Button> denetimini form üzerine sürükleyin. Bunları birbirlerine yakın bir konuma konumlandırın, ancak hizalanmamış olarak bırakın.

2. **Araç kutusunda**<xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

3. Fare işaretçisini üç <xref:System.Windows.Forms.Button> denetimine yakın bir şekilde taşıyın. İşaretçinin, <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın.

4. Fare düğmesine tıklayın ve basılı tutun.

5. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin anahattını çizmek için fare işaretçisini sürükleyin. Ana hattı üç <xref:System.Windows.Forms.Button> denetiminin çevresine çizin.

6. Fare düğmesini bırakın. Üç <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.FlowLayoutPanel> denetimine eklendiğini unutmayın.

## <a name="next-steps"></a>Sonraki Adımlar
 Düzen panellerinin ve denetimlerin birleşimini kullanarak karmaşık bir düzen elde edebilirsiniz. Daha fazla araştırma için öneriler şunlardır:

- <xref:System.Windows.Forms.Button> denetimlerinden birini daha büyük bir boyuta göre yeniden boyutlandırın ve düzen üzerindeki etkiyi aklınızda yapın.

- Düzen panelleri, diğer düzen panellerini içerebilir. Mevcut denetime <xref:System.Windows.Forms.TableLayoutPanel> denetimi bırakmayı deneyin.

- <xref:System.Windows.Forms.FlowLayoutPanel> denetimini üst forma yerleştirin. Formu yeniden boyutlandırın ve düzen üzerindeki etkiyi aklınızda yapın.

- Denetimlerden birinin <xref:System.Windows.Forms.Control.Visible%2A> özelliğini `false` olarak ayarlayın ve <xref:System.Windows.Forms.FlowLayoutPanel> yanıt olarak yeniden akıtıldığına göz önünde edin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms’da Denetimleri Bağlama](how-to-anchor-controls-on-windows-forms.md)
- [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](windows-forms-controls-padding-autosize.md)
