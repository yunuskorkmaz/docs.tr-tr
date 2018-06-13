---
title: "İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 573a0b8ee8e3fafea15b1fd111334da773beef11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541774"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme
Bazı uygulamalar kendisini formun boyutlandırıldığında veya içeriği boyutunu değiştirmek gibi uygun şekilde düzenler bir düzen formla gerektirir. Ne zaman dinamik düzen gerekir ve işlemek istemediğiniz <xref:System.Windows.Forms.Control.Layout> açıkça kodunuzda olayları, bir düzen panel kullanmayı düşünün.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Denetim ve <xref:System.Windows.Forms.TableLayoutPanel> denetimi, form üzerinde denetimleri düzenlemek için sezgisel yollar sağlar. Her ikisini birden içerdiği alt denetimleri göreli konumları denetlemek için otomatik, yapılandırılabilir bir beceri sağlar ve yeniden boyutlandırma ve alt denetimleri üst formu boyutları olarak yeniden konumlandırmak için her ikisi de, çalışma zamanında dinamik düzen özelliklerini verin değiştirin. Düzen panelleri gelişmiş kullanıcı arabirimleri gerçekleştirme etkinleştirmek için Düzen panelleri içinde iç içe.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> İçeriğini HTML benzer işlevsellik sağlayan bir kılavuz düzenler \<Tablo > öğesi. Satırları ve sütunları hücrelerinden düzenlenir ve bunlar farklı boyutlarda olabilir. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak bir TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> İçeriğini belirli akış yönü düzenler: yatay veya dikey. İçeriği, bir sonraki satıra veya sonraki bir sütuna sarmalamak. Alternatif olarak, içeriği yerine kırpılmış gibi sarılır. Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms projesi oluşturma  
  
-   Yatay ve dikey olarak denetimleri düzenleme  
  
-   Akış yönü değiştirme  
  
-   Akış sonları ekleme  
  
-   Doldurma ve kenar boşlukları kullanarak denetimleri düzenleme  
  
-   Araç kutusunda çift tıklatarak denetimler ekleme  
  
-   Anahattı çizerek bir denetim ekleme  
  
-   Şapka kullanarak denetimler ekleme  
  
-   Mevcut denetimleri farklı bir üst öğeye yeniden atama  
  
 İşiniz bittiğinde, bu önemli yerleşim özellikleri tarafından oynadığı rol anlaşılması gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  "FlowLayoutPanelExample" adlı bir Windows tabanlı bir uygulama projesi oluşturun. Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Formda seçin **Forms Tasarımcısı**.  
  
## <a name="arranging-controls-horizontally-and-vertically"></a>Yatay ve dikey olarak denetimleri düzenleme  
 <xref:System.Windows.Forms.FlowLayoutPanel> Denetim tam olarak her denetim konumunu belirtmek gerek kalmadan satır veya sütun boyunca denetimleri yerleştirin olanak tanır.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Denetim yeniden boyutlandırın veya onun alt denetimleri üst form değişiklik boyutları olarak yeniden akışı.  
  
#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Yatay ve dikey olarak FlowLayoutPanel kullanarak denetimlerini düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.FlowLayoutPanel> gelen denetim **araç** formunuza.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.FlowLayoutPanel>. İçin sol üst köşesindeki otomatik olarak taşınır Not <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
3.  Başka bir sürükleyin <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.FlowLayoutPanel>. Unutmayın <xref:System.Windows.Forms.Button> denetim ilk yanında bir konuma taşındı otomatik olarak <xref:System.Windows.Forms.Button> denetim. Varsa, <xref:System.Windows.Forms.FlowLayoutPanel> aynı satırda iki denetimleri sığması için çok dar yeni <xref:System.Windows.Forms.Button> denetim sonraki satıra otomatik olarak taşındı.  
  
4.  Birkaç daha sürükleyin <xref:System.Windows.Forms.Button> gelen denetimleri **araç** içine <xref:System.Windows.Forms.FlowLayoutPanel>. Yerleştirme devam <xref:System.Windows.Forms.Button> bir sonraki satıra sarmalar kadar denetler.  
  
5.  Değerini değiştirme <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğine `false`. Alt artık sonraki satıra akışına denetimleri unutmayın. Bunun yerine, bunlar ilk satırın taşınır ve kırpılır.  
  
6.  Değerini değiştirme <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliğine `true`. Alt yeniden sonraki satıra kaydırılır denetimleri unutmayın.  
  
7.  Genişliğini azaltma <xref:System.Windows.Forms.FlowLayoutPanel> tüm kadar denetim <xref:System.Windows.Forms.Button> denetimleri ilk sütuna taşınır.  
  
8.  Genişliğini artırmak <xref:System.Windows.Forms.FlowLayoutPanel> tüm kadar denetim <xref:System.Windows.Forms.Button> denetimleri, ilk satırın taşınır. Formunuz büyük genişliği uyum sağlayacak şekilde yeniden boyutlandırmak gerekebilir.  
  
## <a name="changing-flow-direction"></a>Akış yönü değiştirme  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Özelliği denetimleri düzenlenir yönünü değiştirmek olanak tanır. Alt denetimler soldan sağa sağdan sola, yukarıdan aşağıya veya aşağıdan yukarı gelen düzenleyebilirsiniz.  
  
#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>FlowLayoutPanel akış yönünü değiştirmek için  
  
1.  Değerini değiştirme <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğine <xref:System.Windows.Forms.FlowDirection.TopDown>. Alt denetimler denetimin yüksekliğini bağlı olarak, bir veya daha fazla sütunlara düzenlenir unutmayın.  
  
2.  Yeniden boyutlandırma <xref:System.Windows.Forms.FlowLayoutPanel> yüksekliğini sütunu kısa olacak şekilde <xref:System.Windows.Forms.Button> kontrol eder. Unutmayın <xref:System.Windows.Forms.FlowLayoutPanel> sonraki sütuna akış için alt denetimleri yeniden düzenler. Yükseklik azalan devam ve alt ardışık sütunlara akışını denetler not edin. Değerini değiştirme <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğine <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Alt denetimler konumlarını ters gerektiğini unutmayın. Değerini değiştirdiğinizde düzeni gözlemlemek <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğine <xref:System.Windows.Forms.FlowDirection.BottomUp>.  
  
## <a name="inserting-flow-breaks"></a>Akış sonları ekleme  
 <xref:System.Windows.Forms.FlowLayoutPanel> Denetim alt denetimlerinden FlowBreak özelliğine sağlar. FlowBreak özelliğinin değerini ayarlama `true` neden <xref:System.Windows.Forms.FlowLayoutPanel> denetim geçerli akış yönü ve bir sonraki satır veya sütun kaydırılır denetimlerinde düzenlemeyi durdur.  
  
#### <a name="to-insert-flow-breaks"></a>Akış sonları eklemek için  
  
1.  Değerini değiştirme <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliğine <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
2.  Aşağıdakilerden birini seçin <xref:System.Windows.Forms.Button> en soldaki sütunu ortasında kontrol eder.  
  
3.  Değerini <xref:System.Windows.Forms.Button> denetimin FlowBreak özelliğine `true`. Sütun bozuk olduğunu unutmayın ve seçili aşağıdaki denetimleri <xref:System.Windows.Forms.Button> sonraki sütununa akışı denetle. Değerini <xref:System.Windows.Forms.Button> denetimin FlowBreak özelliğine `false` özgün davranışa geri dönmek için.  
  
## <a name="positioning-controls-using-docking-and-anchoring"></a>Denetimleri sabitleme ve yerleştirme kullanarak konumlandırma  
 Yerleşen ve davranışları alt denetimleri sabitleme diğer kapsayıcı denetimleri davranışları farklıdır. Yerleştirme hem de bağlama en büyük denetim akış yönüne göre değişir.  
  
#### <a name="to-position-controls-using-docking-and-anchoring"></a>Denetimleri sabitleme ve yerleştirme kullanarak konumlandırmak için  
  
1.  Boyutunu artırın <xref:System.Windows.Forms.FlowLayoutPanel> kadar <xref:System.Windows.Forms.Button> denetimleri tüm düzenlenir bir sütun.  
  
2.  Üst seçin <xref:System.Windows.Forms.Button> denetim. İlgili olmasını sağlamak genişliğini artırmak iki katı kadar geniş halinde diğer <xref:System.Windows.Forms.Button> kontrol eder.  
  
3.  İkinci seçin <xref:System.Windows.Forms.Button> denetim. Değerini değiştirmek kendi <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine <xref:System.Windows.Forms.AnchorStyles.Right>. Sağ kenarlığın hizalanır böylece bu taşınır Not ilk ile <xref:System.Windows.Forms.Button> denetimin sağ kenarlık.  
  
4.  Değerini değiştirmek kendi <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine <xref:System.Windows.Forms.AnchorStyles.Right> ve <xref:System.Windows.Forms.AnchorStyles.Left>. Bu ilk aynı genişliğe boyutlandırılır Not <xref:System.Windows.Forms.Button> denetim.  
  
5.  Üçüncü seçin <xref:System.Windows.Forms.Button> denetim. Değerini değiştirmek kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>. Bu ilk aynı genişliğe boyutlandırılır Not <xref:System.Windows.Forms.Button> denetim.  
  
## <a name="arranging-controls-using-padding-and-margins"></a>Doldurma ve kenar boşlukları kullanarak denetimleri düzenleme  
 Denetimleri de düzenleyebilirsiniz, <xref:System.Windows.Forms.FlowLayoutPanel> değiştirerek denetim <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> özellikleri.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Özelliği sağlar, denetimleri içinde yerleşimini denetlemek bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimin hücre. Alt denetimler arasındaki boşluğu belirtir ve <xref:System.Windows.Forms.FlowLayoutPanel> denetimin kenarlığının.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Özellik denetimler arasındaki boşlukları denetlemenize olanak tanır.  
  
#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Doldurma ve kenar boşluğu özelliklerini kullanarak denetimlerini düzenlemek için  
  
1.  Değerini değiştirme <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>. Formunuz yeteri kadar büyük olursa <xref:System.Windows.Forms.Button> denetimleri ilk sütununa taşınmış <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
2.  Değerini değiştirme <xref:System.Windows.Forms.FlowLayoutPanel> denetimin <xref:System.Windows.Forms.Control.Padding%2A> genişleterek özelliği <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> özelliğine **20**. Daha fazla bilgi için bkz: [izlenecek yol: yerleştirmede çıkışı Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md). Alt denetimler merkezine taşınır Not <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Artan değeri <xref:System.Windows.Forms.Control.Padding%2A> özelliği iter merkezden alt denetimleri <xref:System.Windows.Forms.FlowLayoutPanel> denetimin kenarlıklar.  
  
3.  Tümünü seçmek <xref:System.Windows.Forms.Button> denetimlerini <xref:System.Windows.Forms.FlowLayoutPanel> ve değeri ayarlayın <xref:System.Windows.Forms.Control.Margin%2A> özelliğine **20**. Unutmayın arasındaki boşluğu <xref:System.Windows.Forms.Button> daha fazla bunlar parçalayın taşınır şekilde arttıkça denetler. Yeniden boyutlandırma gerekebilir <xref:System.Windows.Forms.FlowLayoutPanel> denetim tüm alt denetimleri görmek için daha büyük olmalıdır.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Araç kutusunda çift tıklatarak denetimler ekleme  
 Doldurmak, <xref:System.Windows.Forms.FlowLayoutPanel> denetimlerinde çift tıklatarak denetim **araç**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Araç kutusunda çift tıklatarak denetim eklemek için  
  
1.  Çift <xref:System.Windows.Forms.Button> denetim simgesinde **araç**. Unutmayın yeni <xref:System.Windows.Forms.Button> denetimi görünür <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
2.  Daha fazla denetimlerinde çift **araç**. Yeni denetimleri sırayla içinde göründüğüne dikkat edin <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim ekleme  
 Bir denetime ekleyebilirsiniz bir <xref:System.Windows.Forms.FlowLayoutPanel> denetlemek ve bir hücreye anahattı çizerek boyutunu belirtin.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Anahattı çizerek bir denetim eklemek için  
  
1.  İçinde **araç**, tıklatın <xref:System.Windows.Forms.Button> denetimi simgesi. Bu form üzerine sürükleyin değil.  
  
2.  Fare işaretçisini taşıyamazsınız <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Bir artı kıl ile işaretçi Not <xref:System.Windows.Forms.Button> bağlı denetimi simgesi.  
  
3.  ' A tıklayın ve fare düğmesini basılı tutun.  
  
4.  Özetini çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.Button> denetim. Boyutuyla memnun kaldığınızda, fare düğmesini bırakın. Unutmayın <xref:System.Windows.Forms.Button> denetimi sonraki açık konumunda oluşturulur <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
## <a name="inserting-controls-using-the-insertion-bar"></a>Ekleme çubuğunu kullanarak denetimler ekleme  
 Belirli bir konumda denetimler ekleme bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Bir denetime sürüklediğinizde <xref:System.Windows.Forms.FlowLayoutPanel> denetimin istemci alanı, bir ekleme çubuğunda görünür denetimi ekleneceği belirtmek için.  
  
#### <a name="to-insert-a-control-using-the-caret"></a>Şapka kullanarak denetim eklemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.FlowLayoutPanel> denetlemek ve iki arasındaki boşluğu noktasına <xref:System.Windows.Forms.Button> denetimleri. Bir ekleme çubuğu, where belirten çizileceğini Not <xref:System.Windows.Forms.Button> içine bırakıldığında yerleştirilecek <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Yeni bırakma önce <xref:System.Windows.Forms.Button> içine denetim <xref:System.Windows.Forms.FlowLayoutPanel> denetlemek, yaklaşık nasıl ekleme çubuğu taşır izlemek için fare işaretçisini.  
  
2.  Yeni bırakma <xref:System.Windows.Forms.Button> içine denetim <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Unutmayın yeni <xref:System.Windows.Forms.Button> denetim hizalı değil başkalarıyla, çünkü kendi <xref:System.Windows.Forms.Control.Margin%2A> özelliği farklı bir değere sahip.  
  
## <a name="reassigning-existing-controls-to-a-different-parent"></a>Mevcut denetimleri farklı bir üst öğeye yeniden atama  
 Yeni bir formunuzda mevcut denetimleri atayabilirsiniz <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
#### <a name="to-reparent-existing-controls"></a>Var olan denetimleri üst öğesini değiştirme için  
  
1.  Üç sürükleyin <xref:System.Windows.Forms.Button> gelen denetimleri **araç** forma. Diğer yakınında olmak getirin, ancak bunları hizalanmamış bırakın.  
  
2.  İçinde **araç**, tıklatın <xref:System.Windows.Forms.FlowLayoutPanel> denetimi simgesi. Bu form üzerine sürükleyin değil.  
  
3.  Fare işaretçisini üç yakın <xref:System.Windows.Forms.Button> kontrol eder. Bir artı kıl ile işaretçi Not <xref:System.Windows.Forms.FlowLayoutPanel> bağlı denetimi simgesi.  
  
4.  ' A tıklayın ve fare düğmesini basılı tutun.  
  
5.  Özetini çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Üç çevresinde anahat çizme <xref:System.Windows.Forms.Button> kontrol eder.  
  
6.  Fare düğmesini bırakın. Unutmayın üç <xref:System.Windows.Forms.Button> denetimleri içine yerleştirildiğinde <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Düzen panelleri ve denetimleri birleşimini kullanarak karmaşık bir düzen elde edebilirsiniz. Daha fazla araştırması için öneriler şunlardır:  
  
-   Aşağıdakilerden birini yeniden boyutlandırın <xref:System.Windows.Forms.Button> denetimleri büyük boyutuna ve Not yerleşim üzerinde etkisi.  
  
-   Düzen panelleri diğer düzen panelleri içerebilir. Deneme bırakma ile bir <xref:System.Windows.Forms.TableLayoutPanel> varolan denetimine denetim.  
  
-   Yerleştirme <xref:System.Windows.Forms.FlowLayoutPanel> üst form denetimi. Formu yeniden boyutlandırma ve yerleşim üzerinde etkisi not edin.  
  
-   Ayarlama <xref:System.Windows.Forms.Control.Visible%2A> denetimlere birinin özelliği `false` ve Not nasıl <xref:System.Windows.Forms.FlowLayoutPanel> yanıt olarak yeniden akış.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricilerin ve tasarımcıların resmi yönergeleri. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [AutoSize Özelliğine Genel Bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Nasıl yapılır: Windows Forms’da Denetimleri Bağlama](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
