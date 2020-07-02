---
title: FlowLayoutPanel kullanarak denetimleri düzenleme
description: Windows Forms projenizdeki denetimleri düzenlemek için sezgisel yollar sağlamak üzere FlowLayoutPanel denetimini ve TableLayoutPanel denetimini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: efcb38275be7b0cf94afb6b68aa139876f7cf5fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619292"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme

Bazı uygulamalar, form yeniden boyutlandırıldığı veya içeriklerin boyutu değiştikçe kendisini uygun şekilde değiştiren düzen içeren bir form gerektirir. Dinamik bir düzene ihtiyacınız olduğunda ve <xref:System.Windows.Forms.Control.Layout> kodunuzda açıkça olayları işlemek istemiyorsanız, bir Düzen paneli kullanmayı düşünün.

<xref:System.Windows.Forms.FlowLayoutPanel>Denetim ve denetim, <xref:System.Windows.Forms.TableLayoutPanel> formunuzdaki denetimleri düzenlemek için sezgisel yollar sağlar. Her ikisi de içindeki alt denetimlerin göreli konumlarını denetlemek için otomatik, yapılandırılabilir bir özellik sağlar ve her ikisi de çalışma zamanında dinamik düzen özellikleri sağlar, bu sayede üst form değişikliğinin boyutları olarak alt denetimleri yeniden boyutlandırabilir ve yeniden konumlandırabilirsiniz. Düzen bölmeleri, gelişmiş kullanıcı arabirimlerinin yerine geçme özelliğini etkinleştirmek için Düzen panelleri içinde iç içe olabilir.

, <xref:System.Windows.Forms.TableLayoutPanel> HTML öğesine benzer işlevler sağlayan bir kılavuzda içeriğini düzenler \<table> . Hücreleri satırlar ve sütunlar halinde düzenlenir ve bunlar farklı boyutlarda olabilir. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

, <xref:System.Windows.Forms.FlowLayoutPanel> İçeriğini belirli bir akış yönünde düzenler: yatay veya dikey. İçeriği bir satırdan sonrakine veya bir sütundan sonrakine kaydırılmış olabilir. Alternatif olarak, içeriği sarmalanabilir yerine kırpılabilir. Bu izlenecek yolda gösterilen görevler şunlardır:

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

## <a name="create-the-project"></a>Proje oluşturma

1. Visual Studio 'da, "flowlayoutpanelexzel" adlı Windows tabanlı bir uygulama projesi oluşturun (**Dosya**  >  **Yeni**  >  **Proje**  >  **Visual C#** veya **Visual Basic**  >  **Klasik Masaüstü**  >  **Windows Forms uygulaması**).

2. Form **tasarımcısında**formu seçin.

## <a name="arranging-controls-horizontally-and-vertically"></a>Denetimleri yatayda ve dikeyde düzenleme
 <xref:System.Windows.Forms.FlowLayoutPanel>Denetim, her bir denetimin konumunu tam olarak belirtmenize gerek kalmadan, denetimleri satır veya sütunlara yerleştirmenize olanak sağlar.

 <xref:System.Windows.Forms.FlowLayoutPanel>Denetim, üst form değişikliğinin boyutları olarak alt denetimlerini yeniden boyutlandırabilir veya yeniden düzenleyebilir.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>FlowLayoutPanel kullanarak denetimleri yatayda ve dikeyde düzenleme

1. <xref:System.Windows.Forms.FlowLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. <xref:System.Windows.Forms.Button> **Araç kutusundan** bir denetimi öğesine sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> . Otomatik olarak denetimin sol üst köşesine taşındığını unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> .

3. <xref:System.Windows.Forms.Button> **Araç kutusundan** başka bir denetimi öğesine sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.Button>Denetimin otomatik olarak ilk denetimin yanındaki bir konuma taşındığını unutmayın <xref:System.Windows.Forms.Button> . <xref:System.Windows.Forms.FlowLayoutPanel>Aynı satırdaki iki denetimi sığdırmak için çok dar ise, yeni <xref:System.Windows.Forms.Button> Denetim otomatik olarak sonraki satıra taşınır.

4. <xref:System.Windows.Forms.Button> **Araç kutusundan** birkaç denetimi daha sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.Button>Bir sonraki satıra kaydırılana kadar denetimleri yerleştirmeye devam edin.

5. <xref:System.Windows.Forms.FlowLayoutPanel>Denetimin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğinin değerini olarak değiştirin `false` . Alt denetimlerin artık sonraki satıra akmadığını unutmayın. Bunun yerine, ilk satıra taşınır ve kırpılır.

6. <xref:System.Windows.Forms.FlowLayoutPanel>Denetimin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğinin değerini olarak değiştirin `true` . Alt denetimlerin bir sonraki satıra sarılacağını unutmayın.

7. <xref:System.Windows.Forms.FlowLayoutPanel>Tüm <xref:System.Windows.Forms.Button> denetimler ilk sütuna taşınana kadar denetimin genişliğini azaltın.

8. <xref:System.Windows.Forms.FlowLayoutPanel>Tüm <xref:System.Windows.Forms.Button> denetimler ilk satıra taşınana kadar denetimin genişliğini artırın. Formunuzu daha büyük genişliğe uyacak şekilde yeniden boyutlandırmanız gerekebilir.

## <a name="changing-flow-direction"></a>Akış yönünü değiştirme
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Özelliği, denetimlerin düzenlendiği yönü değiştirmenize izin verir. Alt denetimleri soldan sağa, sağdan sola, yukarıdan aşağıya veya alttan üste kadar düzenleyebilirsiniz.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>FlowLayoutPanel 'teki akış yönünü değiştirmek için

1. <xref:System.Windows.Forms.FlowLayoutPanel>Denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.FlowDirection.TopDown> . Alt denetimlerin, denetimin yüksekliğine bağlı olarak bir veya daha fazla sütuna yeniden düzenlendiğini unutmayın.

2. <xref:System.Windows.Forms.FlowLayoutPanel>Yüksekliğini denetimin sütunuyla daha kısa olacak şekilde yeniden boyutlandırın <xref:System.Windows.Forms.Button> . Bir <xref:System.Windows.Forms.FlowLayoutPanel> sonraki sütuna akan alt denetimleri yeniden düzenler. Yüksekliği azaltmasına devam edin ve alt denetimlerin ardışık sütunlara akmasını unutmayın. <xref:System.Windows.Forms.FlowLayoutPanel>Denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.FlowDirection.RightToLeft> . Alt denetimlerin konumlarının tersine çevrilip çevrildiğine unutmayın. Özelliğin değerini olarak değiştirdiğinizde düzeni gözlemleyin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.BottomUp> .

## <a name="inserting-flow-breaks"></a>Akış sonları ekleniyor
 <xref:System.Windows.Forms.FlowLayoutPanel>Denetim, alt denetimlerine FlowBreak özelliği sağlar. FlowBreak özelliğinin değerini, `true` <xref:System.Windows.Forms.FlowLayoutPanel> denetimin geçerli akış yönünde denetimleri yerleştirme ve sonraki satıra veya sütuna kaymasına neden olacak şekilde ayarlama.

### <a name="to-insert-flow-breaks"></a>Akış sonları eklemek için

1. <xref:System.Windows.Forms.FlowLayoutPanel>Denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.FlowDirection.TopDown> .

2. <xref:System.Windows.Forms.Button>En soldaki sütunun ortasında bulunan denetimlerden birini seçin.

3. <xref:System.Windows.Forms.Button>Denetimin FlowBreak özelliğinin değerini olarak ayarlayın `true` . Sütunun bozuk olduğuna ve Seçili denetimi izleyen denetimlerin <xref:System.Windows.Forms.Button> sonraki sütuna akmasını unutmayın. <xref:System.Windows.Forms.Button>Asıl davranışa dönmek için denetimin FlowBreak özelliğinin değerini olarak ayarlayın `false` .

## <a name="positioning-controls-using-docking-and-anchoring"></a>Yerleştirme ve sabitleme kullanarak denetimleri konumlandırma
 Alt denetimlerin sabitleme ve sabitleme davranışları, diğer kapsayıcı denetimlerindeki davranışlardan farklıdır. Hem yerleştirme hem de sabitleme, akış yönündeki en büyük denetime göredir.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Yerleştirme ve sabitleme kullanarak denetimleri konumlandırmak için

1. <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Button> Denetimlerin tümü bir sütunda düzenlenene kadar boyutunu artırın.

2. Üstteki denetimi seçin <xref:System.Windows.Forms.Button> . Diğer denetimlerin genişliğinde iki kat daha olması için genişliğini artırın <xref:System.Windows.Forms.Button> .

3. İkinci denetimi seçin <xref:System.Windows.Forms.Button> . <xref:System.Windows.Forms.Control.Anchor%2A>Özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.AnchorStyles.Right> . Sağ kenarlığının ilk <xref:System.Windows.Forms.Button> denetimin sağ kenarlığıyla hizalanması için taşındığını unutmayın.

4. <xref:System.Windows.Forms.Control.Anchor%2A>Özelliğinin değerini ve olarak değiştirin <xref:System.Windows.Forms.AnchorStyles.Right> <xref:System.Windows.Forms.AnchorStyles.Left> . İlk denetimle aynı genişliğe göre boyutlandırıldığını unutmayın <xref:System.Windows.Forms.Button> .

5. Üçüncü denetimi seçin <xref:System.Windows.Forms.Button> . <xref:System.Windows.Forms.Control.Dock%2A>Özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.DockStyle.Fill> . İlk denetimle aynı genişliğe göre boyutlandırıldığını unutmayın <xref:System.Windows.Forms.Button> .

## <a name="arranging-controls-using-padding-and-margins"></a>Doldurma ve kenar boşlukları kullanarak denetimleri düzenleme
 Ayrıca <xref:System.Windows.Forms.FlowLayoutPanel> , ve özelliklerini değiştirerek denetiminizdeki denetimleri de düzenleyebilirsiniz <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Margin%2A> .

 <xref:System.Windows.Forms.Control.Padding%2A>Özelliği, denetimin hücresinin içindeki denetimlerin yerleşimini denetlemenize olanak tanır <xref:System.Windows.Forms.FlowLayoutPanel> . Alt denetimler ve denetimin kenarlığı arasındaki boşluğu belirtir <xref:System.Windows.Forms.FlowLayoutPanel> .

 <xref:System.Windows.Forms.Control.Margin%2A>Özelliği, denetimler arasındaki boşluğu denetlemenize olanak tanır.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Doldurma ve kenar boşluğu özelliklerini kullanarak denetimleri düzenlemek için

1. <xref:System.Windows.Forms.FlowLayoutPanel>Denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini olarak değiştirin <xref:System.Windows.Forms.DockStyle.Fill> . Formunuz yeterince büyükse, <xref:System.Windows.Forms.Button> denetimler denetimin ilk sütununa taşınır <xref:System.Windows.Forms.FlowLayoutPanel> .

2. <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A> **Özellikler** penceresinde girişi genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **20**olarak ayarlayarak denetimin özelliğinin değerini değiştirin. Daha fazla bilgi için bkz. [Izlenecek yol: doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md). Alt denetimlerin, denetimin ortasına doğru taşındığını unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> . Özelliğin artan değeri, <xref:System.Windows.Forms.Control.Padding%2A> alt denetimleri <xref:System.Windows.Forms.FlowLayoutPanel> denetimin kenarlıklarından uzağa gönderir.

3. İçindeki tüm denetimleri seçin <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin değerini **20**olarak ayarlayın. Denetimler arasındaki Aralık <xref:System.Windows.Forms.Button> arttıkça, daha fazla taşınırlar. <xref:System.Windows.Forms.FlowLayoutPanel>Tüm alt denetimleri görmek için denetimi daha büyük olacak şekilde yeniden boyutlandırmanız gerekebilir.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetim ekleme
 <xref:System.Windows.Forms.FlowLayoutPanel> **Araç kutusundaki**denetimleri çift tıklatarak denetiminizi doldurabilirsiniz.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusuna çift tıklayarak denetim eklemek için

1. <xref:System.Windows.Forms.Button> **Araç kutusundaki**denetim simgesine çift tıklayın. Denetimde yeni bir <xref:System.Windows.Forms.Button> denetimin göründüğünü unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> .

2. **Araç kutusunda**birden fazla denetim ' e çift tıklayın. Yeni denetimlerin denetimde çok büyük bir şekilde göründüğünü unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="inserting-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim ekleme
 Bir denetime denetim ekleyebilir <xref:System.Windows.Forms.FlowLayoutPanel> ve kendi anahattını bir hücreye çizerek boyutunu belirtebilirsiniz.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Ana hattını çizerek bir denetim eklemek için

1. **Araç kutusunda** <xref:System.Windows.Forms.Button> Denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

2. Fare işaretçisini denetimin üzerine taşıyın <xref:System.Windows.Forms.FlowLayoutPanel> . İşaretçinin, denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın <xref:System.Windows.Forms.Button> .

3. Fare düğmesine tıklayın ve basılı tutun.

4. Denetimin anahattını çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.Button> . Boyutla memnun olduğunuzda fare düğmesini bırakın. Denetimin <xref:System.Windows.Forms.Button> bir sonraki açık konumunda denetimin oluşturulduğunu unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="inserting-controls-using-the-insertion-bar"></a>Ekleme çubuğunu kullanarak denetim ekleme
 Denetimdeki belirli bir konuma denetimler ekleyebilirsiniz <xref:System.Windows.Forms.FlowLayoutPanel> . Denetimin istemci alanına bir denetimi sürüklediğinizde <xref:System.Windows.Forms.FlowLayoutPanel> , denetimin nereye ekleneceğini gösteren bir ekleme çubuğu görünür.

### <a name="to-insert-a-control-using-the-caret"></a>Giriş işaretini kullanarak bir denetim eklemek için

1. <xref:System.Windows.Forms.Button> **Araç kutusundan** denetim içine bir denetim sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> ve iki denetim arasındaki boşluğu işaret edin <xref:System.Windows.Forms.Button> . Bir ekleme çubuğunun çizildiğine ve denetimin denetime bırakıldığında nereye yerleştirileceğini aklınızda olduğunu unutmayın <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.FlowLayoutPanel> . Denetime yeni denetimi bırakmadan önce <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.FlowLayoutPanel> , ekleme çubuğunun nasıl hareket edeceğini gözlemlemek için fare işaretçisini etrafında taşıyın.

2. <xref:System.Windows.Forms.Button>Denetime yeni denetimi bırakın <xref:System.Windows.Forms.FlowLayoutPanel> . Yeni <xref:System.Windows.Forms.Button> denetimin, <xref:System.Windows.Forms.Control.Margin%2A> özelliği farklı bir değere sahip olduğu için diğerleri ile Hizalanmadığını unutmayın.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Varolan denetimleri farklı bir üst öğeye yeniden atama
 Formunuzda bulunan denetimleri yeni bir <xref:System.Windows.Forms.FlowLayoutPanel> denetime atayabilirsiniz.

### <a name="to-reparent-existing-controls"></a>Varolan denetimleri yeniden üst üste eklemek için

1. <xref:System.Windows.Forms.Button> **Araç kutusundan** üç denetimi form üzerine sürükleyin. Bunları birbirlerine yakın bir konuma konumlandırın, ancak hizalanmamış olarak bırakın.

2. **Araç kutusunda** <xref:System.Windows.Forms.FlowLayoutPanel> Denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

3. Fare işaretçisini üç denetime yakın bir şekilde taşıyın <xref:System.Windows.Forms.Button> . İşaretçinin, denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> .

4. Fare düğmesine tıklayın ve basılı tutun.

5. Denetimin anahattını çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> . Ana hattı üç denetimin çevresine çizin <xref:System.Windows.Forms.Button> .

6. Fare düğmesini bırakın. Üç denetimin <xref:System.Windows.Forms.Button> denetime eklendiğini unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="next-steps"></a>Sonraki Adımlar
 Düzen panellerinin ve denetimlerin birleşimini kullanarak karmaşık bir düzen elde edebilirsiniz. Daha fazla araştırma için öneriler şunlardır:

- <xref:System.Windows.Forms.Button>Denetimlerden birini daha büyük bir boyuta göre yeniden boyutlandırın ve düzen üzerindeki etkiyi aklınızda yapın.

- Düzen panelleri, diğer düzen panellerini içerebilir. <xref:System.Windows.Forms.TableLayoutPanel>Varolan denetime bir denetim bırakmayı deneyin.

- <xref:System.Windows.Forms.FlowLayoutPanel>Denetimi üst forma yerleştirin. Formu yeniden boyutlandırın ve düzen üzerindeki etkiyi aklınızda yapın.

- <xref:System.Windows.Forms.Control.Visible%2A>Denetimlerden birinin özelliğini olarak ayarlayın `false` ve yeniden akıtıldığında nasıl yanıt olduğunu aklınızda yapın <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'ta Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Formlarına Denetimleri Yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Formlarında Denetimleri Sabitleme](how-to-anchor-controls-on-windows-forms.md)
- [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Formları Denetimlerini Düzenleme](windows-forms-controls-padding-autosize.md)
