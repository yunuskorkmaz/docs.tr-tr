---
title: "İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 8cfcdf8595733434cc56c621428c31238dd166dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211165"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme

Bazı uygulamalar, kendisini formu yeniden boyutlandırıldığından veya içeriği boyutu değiştikçe uygun şekilde düzenler bir düzene sahip bir form gerektirir. Ne zaman dinamik bir düzen gerekir ve işlemek istemediğiniz <xref:System.Windows.Forms.Control.Layout> açıkça kodunuzda olayları, Düzen panelini kullanma göz önünde bulundurun.

<xref:System.Windows.Forms.FlowLayoutPanel> Denetimi ve <xref:System.Windows.Forms.TableLayoutPanel> denetimi, form üzerinde denetimleri düzenlemek için sezgisel yolu sağlayın. Her ikisini birden içerdiği alt denetimler göreli konumlarını denetlemek için otomatik, yapılandırılabilir bir yeteneği sağlar ve yeniden boyutlandırma ve alt denetimler üst formun boyutları yeniden konumlandırmak için hem de çalışma zamanında dinamik düzen özelliklerini size değiştirin. Düzen bölmeleri, gelişmiş kullanıcı arabirimleri gerçekleştirme etkinleştirmek için Düzen panelleri içinde yuvalanabilir.

<xref:System.Windows.Forms.TableLayoutPanel> İçeriğinin HTML benzer işlevsellik sağlayan bir kılavuzda düzenler \<Tablo > öğesi. Satırları ve sütunları hücrelerinden düzenlenir ve bu farklı boyutlarda olabilir. Daha fazla bilgi için [izlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

<xref:System.Windows.Forms.FlowLayoutPanel> İçeriğini belirli bir akış yönünü ayarlar: yatay veya dikey. İçeriği sonraki bir satır veya sonraki bir sütun sarmalanabilir. Alternatif olarak, içeriğinin yerine kırpılmış DC'de sona erdi. Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

- Bir Windows Forms projesi oluşturma

- Denetimleri yatay ve dikey olarak düzenleme

- Akış yönü değiştirme

- Ekleme akış sonu

- Doldurma ve kenar boşluklarını kullanarak denetimleri düzenleme

- Araç kutusunda çift tıklayarak denetimler ekleme

- Anahattı çizerek bir denetim ekleme

- Şapka karakterini kullanarak denetimleri ekleme

- Mevcut denetimleri farklı bir üst öğeye yeniden atama

İşiniz bittiğinde, bu önemli bir düzen özellikleri tarafından oynadığı rol bir anlayışa sahip olacaksınız.

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio'da "FlowLayoutPanelExample" adlı bir Windows tabanlı uygulama projesi oluşturun (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).

2. Formda seçin **Form Tasarımcısı**.

## <a name="arranging-controls-horizontally-and-vertically"></a>Denetimleri yatay ve dikey olarak düzenleme
 <xref:System.Windows.Forms.FlowLayoutPanel> Denetimi satır veya sütun boyunca denetimleri tam olarak her denetim konumunu belirtmek gerek kalmadan yerleştirmenize olanak sağlar.

 <xref:System.Windows.Forms.FlowLayoutPanel> Denetimi yeniden boyutlandırma veya üst formu değişiklik boyutları, alt denetimlerini yeniden akışı.

#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Denetimleri yatay ve dikey olarak FlowLayoutPanel kullanarak düzenlemek için

1. Sürükleme bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimi **araç kutusu** formunuza.

2. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.FlowLayoutPanel>. İçin sol üst köşesindeki otomatik olarak taşınır Not <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.

3. Başka bir sürükleyin <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.FlowLayoutPanel>. Unutmayın <xref:System.Windows.Forms.Button> denetimi ilk yanında bir konuma otomatik olarak taşınır <xref:System.Windows.Forms.Button> denetimi. Varsa, <xref:System.Windows.Forms.FlowLayoutPanel> iki denetimi aynı satırdaki sığdırmak için çok dar yeni <xref:System.Windows.Forms.Button> denetimi otomatik olarak sonraki satıra taşınır.

4. Daha fazlasını sürükleyin <xref:System.Windows.Forms.Button> denetimler **araç kutusu** içine <xref:System.Windows.Forms.FlowLayoutPanel>. Yerleştirmeye devam <xref:System.Windows.Forms.Button> bir sonraki satıra kaydırılacağını kadar denetler.

5. Değiştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğini `false`. Alt artık sonraki satırda akışına denetimleri unutmayın. Bunun yerine, bunlar ilk satırın taşınır ve kırpılır.

6. Değiştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğini `true`. Alt yeniden sonraki satırda kaydırılır denetimleri unutmayın.

7. Genişliğini azaltma <xref:System.Windows.Forms.FlowLayoutPanel> kadar tüm denetim <xref:System.Windows.Forms.Button> denetimleri ilk sütuna taşınır.

8. Genişliğini artırın <xref:System.Windows.Forms.FlowLayoutPanel> kadar tüm denetim <xref:System.Windows.Forms.Button> denetimleri, ilk satırın taşınır. Formunuza büyük genişliğini uyum sağlayacak şekilde yeniden boyutlandırmak gerekebilir.

## <a name="changing-flow-direction"></a>Akış yönü değiştirme
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Özelliği denetimleri düzenlenir yönünü değiştirmenize izin verir. Alt denetimler soldan sağa, sağdan sola, yukarıdan aşağıya veya aşağıdan yukarıya gelen düzenleyebilirsiniz.

#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>FlowLayoutPanel akış yönünü değiştirmek için

1. Değiştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğini <xref:System.Windows.Forms.FlowDirection.TopDown>. Alt denetimler denetimin yüksekliği bağlı olarak, bir veya daha fazla sütunlara düzenlenir unutmayın.

2. Yeniden boyutlandırma <xref:System.Windows.Forms.FlowLayoutPanel> yükseklik sütunu kısa olacak şekilde <xref:System.Windows.Forms.Button> kontrol eder. Unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> sonraki sütuna akışı alt denetimleri yeniden düzenler. Devam yüksekliğini azaltmak ve alt akış ardışık sütunlara denetimleri dikkat edin. Değiştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğini <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Alt denetimler konumlarını ters gerektiğini unutmayın. Değerini değiştirdiğinizde düzenini gözlemleyin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğini <xref:System.Windows.Forms.FlowDirection.BottomUp>.

## <a name="inserting-flow-breaks"></a>Ekleme akış sonu
 <xref:System.Windows.Forms.FlowLayoutPanel> Denetim, alt denetimlerini FlowBreak özellik sağlar. FlowBreak özelliğin değerini ayarlamak `true` neden <xref:System.Windows.Forms.FlowLayoutPanel> sonraki satır veya sütun kaydırılır ve geçerli akış yönü denetimlerinde düzenlemeyi durdurmak için denetimi.

#### <a name="to-insert-flow-breaks"></a>Akış sonu eklemek için

1. Değiştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğini <xref:System.Windows.Forms.FlowDirection.TopDown>.

2. Birini <xref:System.Windows.Forms.Button> en soldaki sütuna ortasında denetimleri.

3. Değerini <xref:System.Windows.Forms.Button> denetimin FlowBreak özelliğini `true`. Sütun bozuk olduğunu unutmayın ve seçili aşağıdaki denetimleri <xref:System.Windows.Forms.Button> denetim akışı bir sonraki sütuna. Değerini <xref:System.Windows.Forms.Button> denetimin FlowBreak özelliğini `false` başlangıçtaki davranışı için döndürülecek.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Sabitleme ve yerleştirme kullanarak denetimleri konumlandırma
 Davranışlar alt denetimleri sabitleme ve yerleştirme diğer kapsayıcı denetimleri davranışları farklıdır. Hem yerleşik hem de bağlama göre akış yönü en büyük denetiminde olan.

#### <a name="to-position-controls-using-docking-and-anchoring"></a>Denetimleri sabitleme ve yerleştirme kullanarak konumlandırmak için

1. Boyutu arttırmak <xref:System.Windows.Forms.FlowLayoutPanel> kadar <xref:System.Windows.Forms.Button> denetimleri tüm düzenlenir bir sütun.

2. Üst <xref:System.Windows.Forms.Button> denetimi. Böylece ilgili olduğunu genişliğini artırmak iki katı kadar geniş diğer <xref:System.Windows.Forms.Button> denetimleri.

3. İkinci seçin <xref:System.Windows.Forms.Button> denetimi. Değerini değiştirebilir, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.Right>. Böylece doğru kenarlığını hizalanmış, taşınır unutmayın ilk <xref:System.Windows.Forms.Button> denetimin sağ kenarlık.

4. Değerini değiştirebilir, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.Right> ve <xref:System.Windows.Forms.AnchorStyles.Left>. İlk olarak aynı genişliğe boyutlandırılır unutmayın <xref:System.Windows.Forms.Button> denetimi.

5. Üçüncü seçin <xref:System.Windows.Forms.Button> denetimi. Değerini değiştirebilir, <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>. İlk olarak aynı genişliğe boyutlandırılır unutmayın <xref:System.Windows.Forms.Button> denetimi.

## <a name="arranging-controls-using-padding-and-margins"></a>Doldurma ve kenar boşluklarını kullanarak denetimleri düzenleme
 Denetimleri de düzenleyebilirsiniz, <xref:System.Windows.Forms.FlowLayoutPanel> değiştirerek denetimi <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> özellikleri.

 <xref:System.Windows.Forms.Control.Padding%2A> Özelliği sayesinde içindeki denetimleri yerleşimini denetlemek bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimin hücre. Alt denetimler arasındaki boşluğu belirtir ve <xref:System.Windows.Forms.FlowLayoutPanel> Denetimin kenarlık.

 <xref:System.Windows.Forms.Control.Margin%2A> Özellik denetimler arasındaki aralığı denetlemenize olanak tanır.

#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Doldurma ve kenar boşluğu özelliklerini kullanarak denetimleri düzenlemek için

1. Değiştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>. Formunuza yeteri kadar büyük olursa <xref:System.Windows.Forms.Button> denetimleri ilk sütuna taşınacak <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.

2. Değiştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliği genişleterek <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> özelliğini **20**. Daha fazla bilgi için [izlenecek yol: Yerleştirme Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile](windows-forms-controls-padding-autosize.md). Alt denetimler merkezine taşınır Not <xref:System.Windows.Forms.FlowLayoutPanel> denetimi. Daha fazla değer için <xref:System.Windows.Forms.Control.Padding%2A> özelliği liste kutusundan alt denetimler gönderim <xref:System.Windows.Forms.FlowLayoutPanel> Denetimin kenarlık.

3. Tümünü seçmek <xref:System.Windows.Forms.Button> denetimlerini <xref:System.Windows.Forms.FlowLayoutPanel> ve değerini ayarlama <xref:System.Windows.Forms.Control.Margin%2A> özelliğini **20**. Unutmayın aralığını <xref:System.Windows.Forms.Button> arttıkça daha sonraya taşındıktan şekilde denetler. Yeniden boyutlandırma gerekebilir <xref:System.Windows.Forms.FlowLayoutPanel> denetimi tüm alt denetimleri görmek için daha büyük olabilir.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetimler ekleme
 Doldurabilirsiniz, <xref:System.Windows.Forms.FlowLayoutPanel> denetimlerinde çift tıklayarak denetim **araç kutusu**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusunda çift tıklayarak denetim eklemek için

1. Çift <xref:System.Windows.Forms.Button> denetim simgesini **araç kutusu**. Unutmayın yeni <xref:System.Windows.Forms.Button> denetimi görünür <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.

2. Daha fazla denetimlerinde çift **araç kutusu**. Yeni denetimler sırayla da göründüğünü fark <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim ekleme
 Bir denetime eklemek bir <xref:System.Windows.Forms.FlowLayoutPanel> denetlemek ve bir hücrede anahattı çizerek boyutunu belirtin.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim eklemek için

1. İçinde **araç kutusu**, tıklayın <xref:System.Windows.Forms.Button> denetim simgesi. Form üzerine sürükleyin değil.

2. Fare işaretçisi taşıyabiliyor <xref:System.Windows.Forms.FlowLayoutPanel> denetimi. Bir artı işareti ile işaretçi Not <xref:System.Windows.Forms.Button> bağlı denetim simgesi.

3. ' A tıklayın ve fare düğmesini basılı tutun.

4. Fare işaretçisi ana hat çizmek için sürükleyin <xref:System.Windows.Forms.Button> denetimi. Boyutu ile memnun kaldığınızda, fare düğmesini bırakın. Unutmayın <xref:System.Windows.Forms.Button> denetim sonraki açık konumunda oluşturulur <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.

## <a name="inserting-controls-using-the-insertion-bar"></a>Ekleme çubuğunu kullanarak denetimleri ekleme
 Belirli bir konumda denetimler ekleyebileceğiniz bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimi. Bir denetime sürüklediğinizde <xref:System.Windows.Forms.FlowLayoutPanel> denetimin istemci alanı, bir ekleme çubuğu görünür denetim ekleneceği belirtmek için.

#### <a name="to-insert-a-control-using-the-caret"></a>Şapka karakterini kullanarak bir denetim eklemek için

1. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.FlowLayoutPanel> denetlemek ve iki arasındaki boşluk noktasına <xref:System.Windows.Forms.Button> denetimleri. Not ekleme çubuğu, yeri belirten çizileceğini <xref:System.Windows.Forms.Button> içine bırakıldığında yerleştirilecek <xref:System.Windows.Forms.FlowLayoutPanel> denetimi. Yeni atmadan önce <xref:System.Windows.Forms.Button> içine denetim <xref:System.Windows.Forms.FlowLayoutPanel> yaklaşık nasıl ekleme çubuğu taşır gözlemlemek için fare işaretçisini denetim.

2. Yeni açılan <xref:System.Windows.Forms.Button> içine denetim <xref:System.Windows.Forms.FlowLayoutPanel> denetimi. Unutmayın yeni <xref:System.Windows.Forms.Button> denetim hizalı değil başkalarıyla, çünkü kendi <xref:System.Windows.Forms.Control.Margin%2A> özelliği, farklı bir değere sahip.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Mevcut denetimleri farklı bir üst öğeye yeniden atama
 Yeni bir formunuzdaki mevcut denetimleri atayabilirsiniz <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.

#### <a name="to-reparent-existing-controls"></a>Mevcut denetimleri yeniden üst öğe yap için

1. Üç sürükleyin <xref:System.Windows.Forms.Button> denetimler **araç kutusu** forma. Birbirine yakın yerleştirin, ancak bunları hizalanmamış bırakın.

2. İçinde **araç kutusu**, tıklayın <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesi. Form üzerine sürükleyin değil.

3. Fare işaretçisini üç yakın <xref:System.Windows.Forms.Button> kontrol eder. Bir artı işareti ile işaretçi Not <xref:System.Windows.Forms.FlowLayoutPanel> bağlı denetim simgesi.

4. ' A tıklayın ve fare düğmesini basılı tutun.

5. Fare işaretçisi ana hat çizmek için sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> denetimi. Üç çevresinde anahat çizmek <xref:System.Windows.Forms.Button> kontrol eder.

6. Fare düğmesini bırakın. Unutmayın üç <xref:System.Windows.Forms.Button> denetimleri içine yerleştirildiğinde <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.

## <a name="next-steps"></a>Sonraki Adımlar
 Düzen bölmeleri ve denetimleri kullanarak karmaşık Düzen elde edebilirsiniz. Daha fazla araştırma için öneriler şunlardır:

- Aşağıdakilerden birini yeniden boyutlandırın <xref:System.Windows.Forms.Button> büyük boyut ve düzenini üzerindeki etkisini Not denetimleri.

- Düzen bölmelerini diğer düzen bölmeleri içerebilir. Bırakma ile deneme bir <xref:System.Windows.Forms.TableLayoutPanel> denetime varolan bir denetimi.

- Dock <xref:System.Windows.Forms.FlowLayoutPanel> üst form denetimi. Formu yeniden boyutlandırmak ve düzeni üzerindeki etkisini dikkat edin.

- Ayarlama <xref:System.Windows.Forms.Control.Visible%2A> özelliği denetimlere birinin `false` ve Not nasıl <xref:System.Windows.Forms.FlowLayoutPanel> yanıt olarak yeniden akış.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricileri ve tasarımcıları için resmi yönergeleri. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms'da denetimleri yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms'da denetimleri](how-to-anchor-controls-on-windows-forms.md)
- [İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme](windows-forms-controls-padding-autosize.md)
