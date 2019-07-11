---
title: "İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: c91fecf9e786f4a8e35486e7b30e9efe36c972e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771648"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme
Formunuzdaki denetimleri kesin yerleşimini birçok uygulama için yüksek öncelik taşır. Windows Form Tasarımcısı, bunu gerçekleştirmek için çok sayıda düzen araçları sunar. En önemli biri <xref:System.Windows.Forms.Design.Behavior.SnapLine> özelliği.  
  
 Dayama çizgileri denetimleri başka denetimler ile hizalamak tam olarak nerede gösterir. Bunlar ayrıca, Windows kullanıcı arabirimi yönergelerine belirtildiği gibi denetimleri arasında kenar boşlukları için önerilen uzaklıkları gösterir. Ayrıntılar için bkz [kullanıcı arabirimi tasarımı ve geliştirme](https://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Dayama çizgileri kolaylaştırır, NET için denetimlerinizi hizalamak profesyonel görünümünü ve davranışını (Görünüm).  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
- Bir Windows Forms projesi oluşturma  
  
- Aralık ve dayama çizgileri kullanarak denetimleri hizalama  
  
- Form ve kapsayıcı kenar boşlukları hizalama  
  
- Gruplandırılmış denetimleri hizalama  
  
- Bir denetimi boyutuna anahat oluşturma tarafından yerleştirmek için dayama çizgileri kullanarak  
  
- Bir denetimi araç kutusundan sürüklendiğinde dayama çizgileri kullanarak  
  
- Dayama çizgileri kullanarak denetimleri yeniden boyutlandırma  
  
- Etiket denetimin metni hizalama  
  
- Klavye ile gezinti dayama çizgileri kullanarak  
  
- Dayama çizgileri ve Düzen bölmeleri  
  
- Dayama çizgileri devre dışı bırakma  
  
 İşlemi tamamladığınızda, Düzen rolünün dayama çizgileri özelliği tarafından yürütülen bir anlayışa sahip olacaksınız.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım projeyi oluşturmak ve formu ayarlamaktır.  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1. "SnaplineExample" adlı bir Windows tabanlı uygulama projesi oluşturun (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
2. Form, Form Tasarımcısı'nda seçin.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Aralık ve dayama çizgileri kullanarak denetimleri hizalama  
 Dayama çizgileri size Formunuza denetim hizalamak için doğru ve kullanımı kolay bir yol sağlar. Seçili denetimi veya denetimleri başka bir denetimi veya denetimleri hizalama bir konuma yakın taşıdığınız zaman görünürler. "Diğer denetimleri hareket ederken sizin seçiminiz için önerilen konum yaslanır".  
  
### <a name="to-arrange-controls-using-snaplines"></a>Dayama çizgileri kullanarak denetimleri düzenlemek için  
  
1. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza.  
  
2. Taşıma <xref:System.Windows.Forms.Button> sağ alt köşedeki form denetimi. Not olarak görünen dayama çizgileri <xref:System.Windows.Forms.Button> alt ve sağ kenarlık form denetimi yaklaşıyor. Bu dayama çizgileri Denetimin kenarlık ve formu arasındaki önerilen uzaklık görüntüler.  
  
3. Taşıma <xref:System.Windows.Forms.Button> çevresinde Kenarlıklar dayama çizgileri göründüğü Not ve form denetimi. İşlemi tamamladığınızda, taşıma <xref:System.Windows.Forms.Button> ortasında form denetimi.  
  
4. Başka bir sürükleyin <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza.  
  
5. İkinci taşıma <xref:System.Windows.Forms.Button> ilk neredeyse düzeyi olana kadar denetim. Görünen iki düğme metin taban çizgisini snapline unutmayın ve taşıdığınız denetim düzeyi diğer denetimi ile tam olarak bir konuma yaslanıp unutmayın.  
  
6. İkinci taşıma <xref:System.Windows.Forms.Button> denetiminin doğrudan ilk yerleştirilir. Her iki düğme sol ve sağ kenarları boyunca görünür ve denetim, tam olarak bir denetimi ile hizalanan bir konuma taşıma yapışır olduğuna dikkat edin dayama çizgileri unutmayın.  
  
7. Birini <xref:System.Windows.Forms.Button> denetler ve bunu diğer yakın temas neredeyse kadar. Bunlar arasında görünür snapline unutmayın. Bu uzaklık denetimleri Kenarlıklar arasında önerilen uzaklıktır. Ayrıca, taşıdığınız denetimi bu konuma yaslanıp unutmayın.  
  
8. İki <xref:System.Windows.Forms.Panel> denetimler **araç kutusu** formunuza.  
  
9. Birini Taşı <xref:System.Windows.Forms.Panel> ilk neredeyse düzeyi olana kadar denetler. Her iki denetim üst ve alt kenarları boyunca görünür ve taşıdığınız denetim düzeyi diğer denetimi ile tam olarak bir konuma yaslanıp Not dayama çizgileri unutmayın.  
  
## <a name="aligning-to-form-and-container-margins"></a>Form ve kapsayıcı kenar boşlukları hizalama  
 Dayama çizgileri form ve kapsayıcı kenar boşlukları, denetimleri tutarlı bir şekilde hizalayın yardımcı olur.  
  
### <a name="to-align-controls-to-form-and-container-margins"></a>Form ve kapsayıcı kenar boşlukları denetimleri hizalama  
  
1. Birini <xref:System.Windows.Forms.Button> denetler ve taşırsanız, formun sağ kenarının yakınında bir snapline görünene kadar. Sağ kenarlığın mesafe snapline'nın denetimin toplamıdır <xref:System.Windows.Forms.Control.Margin%2A> özelliği ve formun <xref:System.Windows.Forms.Control.Padding%2A> özellik değerleri.  
  
> [!NOTE]
>  Formun <xref:System.Windows.Forms.Control.Padding%2A> özelliği için 0,0,0,0 ayarlandığında, Windows Form Tasarımcısı gölgeli bir form sağlar <xref:System.Windows.Forms.Control.Padding%2A> 9,9,9,9 değeri. Bu davranışı geçersiz kılmak için 0,0,0,0 dışında bir değere atayın.  
  
1. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliği genişleterek <xref:System.Windows.Forms.Control.Margin%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> özelliğinin 0. Ayrıntılar için bkz [izlenecek yol: Yerleştirme Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile](windows-forms-controls-padding-autosize.md).  
  
2. Taşıma <xref:System.Windows.Forms.Button> bir snapline görünene kadar formun sağ kenarının yakınında denetimi. Bu uzaklık artık formun değeriyle verilir <xref:System.Windows.Forms.Control.Padding%2A> özelliği.  
  
3. Sürükleme bir <xref:System.Windows.Forms.GroupBox> denetimi **araç kutusu** formunuza.  
  
4. Değiştirin <xref:System.Windows.Forms.GroupBox> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliği genişleterek <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 10 özelliği.  
  
5. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.GroupBox> denetimi.  
  
6. Taşıma <xref:System.Windows.Forms.Button> denetimi sağ kenarının yakınında <xref:System.Windows.Forms.GroupBox> bir snapline görünene kadar denetim. Taşıma <xref:System.Windows.Forms.Button> denetimine <xref:System.Windows.Forms.GroupBox> denetimi ve dayama çizgileri nerede görüneceğini unutmayın.  
  
## <a name="aligning-to-grouped-controls"></a>Gruplandırılmış denetimleri hizalama  
 Dayama çizgileri gruplandırılmış denetimleri hizalama için kullanabileceğiniz de gibi denetimleri içinde bir <xref:System.Windows.Forms.GroupBox> denetimi.  
  
### <a name="to-align-to-grouped-controls"></a>Gruplandırılmış denetimleri hizalama  
  
1. İki, form üzerindeki denetimleri seçin. Seçimi yorumuyla kabarcıklar etrafta seçiminizi ve diğer denetimler arasında görünür dayama çizgileri unutmayın.  
  
2. Sürükleme bir <xref:System.Windows.Forms.GroupBox> denetimi **araç kutusu** formunuza.  
  
3. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içine <xref:System.Windows.Forms.GroupBox> denetimi.  
  
4. Birini <xref:System.Windows.Forms.Button> denetler ve dolaştırın <xref:System.Windows.Forms.GroupBox> denetimi. Not kenarlarını görünen dayama çizgileri <xref:System.Windows.Forms.GroupBox> denetimi. Ayrıca kenarlarını görünen dayama çizgileri unutmayın <xref:System.Windows.Forms.Button> tarafından bulunan denetim <xref:System.Windows.Forms.GroupBox> denetimi. Bir kapsayıcı denetimi alt denetimler dayama çizgileri da destekler.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Bir denetimi boyutuna anahat oluşturma tarafından yerleştirmek için dayama çizgileri kullanarak  
 Dayama çizgileri Yardım, hizalama, önce bunları bir form üzerinde yerleştirdiğinizde denetler.  
  
### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Bir denetimi boyutuna anahat oluşturma tarafından yerleştirmek için dayama çizgileri kullanmak için  
  
1. İçinde **araç kutusu**, tıklayın <xref:System.Windows.Forms.Button> denetim simgesi. Form üzerine sürükleyin değil.  
  
2. Fare işaretçisini form Tasarım yüzeyine taşıyın. Bir artı işareti ile işaretçi Not <xref:System.Windows.Forms.Button> bağlı denetim simgesi. Ayrıca hizalanmış konumları için önermek için görünen dayama çizgileri unutmayın <xref:System.Windows.Forms.Button> denetimi.  
  
3. ' A tıklayın ve fare düğmesini basılı tutun.  
  
4. Fare işaretçisi form etrafında sürükleyin. Anahat, konumu ve denetimin boyutunu gösteren çizileceğini unutmayın.  
  
5. Form üzerinde başka bir denetimi ile hizalar kadar işaretçiyi sürükleyin. Hizalama belirtmek için bir snapline göründüğüne dikkat edin.  
  
6. Fare düğmesini bırakın. Denetimin konumunu ve boyutunu anahat tarafından belirtilen oluşturulur.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Bir denetimi araç kutusundan sürüklendiğinde dayama çizgileri kullanarak  
 Dayama çizgileri Yardım, hizalama denetimleri bunları sürüklediğinizde **araç kutusu** formunuza.  
  
### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Bir denetimi araç kutusundan sürüklendiğinde dayama çizgileri kullanmak için  
  
1. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza, ancak fare düğmesini bırakın değil.  
  
2. Fare işaretçisini form Tasarım yüzeyine taşıyın. İşaretçi konumunda belirtmek için değiştiğine dikkat edin yeni <xref:System.Windows.Forms.Button> denetim oluşturulur.  
  
3. Fare işaretçisi form etrafında sürükleyin. Hizalanmış konumları için önermek için görünen dayama çizgileri Not <xref:System.Windows.Forms.Button> denetimi. Diğer denetimlerle hizalanmış bir konum bulun.  
  
4. Fare düğmesini bırakın. Denetim dayama çizgileri tarafından belirtilen konumda oluşturulur.  
  
## <a name="resizing-controls-using-snaplines"></a>Dayama çizgileri kullanarak denetimleri yeniden boyutlandırma  
 Dayama çizgileri yardımcı olarak bunları yeniden boyutlandırma denetimleri hizalama.  
  
### <a name="to-resize-a-control-using-snaplines"></a>Dayama çizgileri kullanarak bir denetimi yeniden boyutlandırmak için  
  
1. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza.  
  
2. Yeniden boyutlandırma <xref:System.Windows.Forms.Button> denetimi tarafından köşe tutamaçları ve sürükleyerek bir yazılımdır. Ayrıntılar için bkz [nasıl yapılır: Windows Forms'da denetimleri yeniden boyutlandırma](how-to-resize-controls-on-windows-forms.md).  
  
3. Biri kadar boyutlandırma tutamacı sürükleyin <xref:System.Windows.Forms.Button> Denetimin kenarlık, başka bir denetimi ile hizalanır. Bir snapline göründüğüne dikkat edin. Ayrıca, boyutlandırma tutamacı snapline tarafından belirtilen konumda yaslamaları olduğunu unutmayın.  
  
4. Yeniden boyutlandırma <xref:System.Windows.Forms.Button> farklı yönlere denetlemek ve farklı denetimler için boyutlandırma tutamacı Hizala. Dayama çizgileri hizalaması belirtmek için çeşitli yönleriyle içinde nasıl görüneceğini unutmayın.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Etiket denetimin metni hizalama  
 Diğer denetimleri için görüntülenen metin hizalama için bir snapline bazı denetimler sunar.  
  
### <a name="to-align-a-label-to-a-controls-text"></a>Etiket denetimin metni hizalama  
  
1. Sürükleme bir <xref:System.Windows.Forms.TextBox> denetimi **araç kutusu** formunuza. Bıraktığınız zaman <xref:System.Windows.Forms.TextBox> forma denetim, akıllı etiket karakterini tıklayıp seçin **metin ayarlamak için textBox1** seçeneği. Ayrıntılar için bkz [izlenecek yol: Denetimleri form üzerinde Windows akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2. Sürükleme bir <xref:System.Windows.Forms.Label> denetimi **araç kutusu** formunuza.  
  
3. Değiştirin <xref:System.Windows.Forms.Label> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`. Denetimin kenarlık görüntü metin sığdırmak için ayarlanacağını unutmayın.  
  
4. Taşıma <xref:System.Windows.Forms.Label> sol tarafındaki denetim <xref:System.Windows.Forms.TextBox> denetimi ile alt kenarı hizalanacağı şekilde <xref:System.Windows.Forms.TextBox> denetimi. İki denetimin alt kenarları görünen snapline unutmayın.  
  
5. Taşıma <xref:System.Windows.Forms.Label> denetim kadar biraz daha yukarı <xref:System.Windows.Forms.Label> metin ve <xref:System.Windows.Forms.TextBox> metin hizalanır. Görüntülenen her iki denetim metin alanlarını zaman hizalı olup olmadığını belirten farklı stil uygulanmış snapline unutmayın.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Klavye ile gezinti dayama çizgileri kullanarak  
 Dayama çizgileri Yardım, hizalama, ne zaman, klavye oklarını kullanarak bunları düzenleme denetler.  
  
### <a name="to-use-snaplines-with-keyboard-navigation"></a>Dayama çizgileri klavye gezintisi ile kullanmak için  
  
1. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** formunuza. Bunu, formun sol üst köşesinde bulunan yerleştirin.  
  
2. CTRL + AŞAĞI OK tuşlarına basın. Denetimin ilk kullanılabilir yatay hizalama konumu için formun taşır unutmayın.  
  
3. Formun alt kısmındaki denetim ulaşana kadar CTRL + AŞAĞI OK tuşuna basın. Formun hareket ettikçe kapladığı konumları unutmayın.  
  
4. CTRL + sağ ok tuşuna basın. Denetimin form üzerinde ilk kullanılabilir dikey hizalama konuma taşınır unutmayın.  
  
5. Denetimin form tarafında ulaşana kadar CTRL + sağ ok tuşuna basın. Form üzerinde hareket ederken kapladığı konumları unutmayın.  
  
6. Denetimin form etrafında bir ok tuşlarını birleşimiyle taşıyın. Denetimin kapladığı konumları ve bunlara eşlik eden dayama çizgileri unutmayın.  
  
7. Yeniden boyutlandırmak için SHIFT + ok herhangi bir tuşa basın <xref:System.Windows.Forms.Button> denetimi bir piksel artımlı tarafından.  
  
8. Yeniden boyutlandırmak için CTRL + SHIFT + ok herhangi bir tuşa basın <xref:System.Windows.Forms.Button> snapline denetimi.  
  
## <a name="snaplines-and-layout-panels"></a>Dayama çizgileri ve Düzen bölmeleri  
 Dayama çizgileri, Düzen bölmelerini içinde devre dışı bırakıldı.  
  
### <a name="to-selectively-disable-snaplines"></a>Seçmeli olarak dayama çizgileri devre dışı bırakmak için  
  
1. Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.  
  
2. Çift <xref:System.Windows.Forms.Button> denetim simgesini **araç kutusu**. Yeni bir düğme denetimi görünür Not <xref:System.Windows.Forms.TableLayoutPanel> denetimin ilk hücrenin.  
  
3. Çift <xref:System.Windows.Forms.Button> denetim simgesini **araç kutusu** iki kez. Bu boş bir hücreye bırakır <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
4. Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** boş hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetimi. Hiçbir dayama çizgileri görünür unutmayın.  
  
5. Sürükleme <xref:System.Windows.Forms.Button> dışı denetim <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve dolaştırın <xref:System.Windows.Forms.TableLayoutPanel> denetimi. Dayama çizgileri yeniden göründüğüne dikkat edin.  
  
## <a name="disabling-snaplines"></a>Dayama çizgileri devre dışı bırakma  
 Dayama çizgileri varsayılan olarak açık olabilir. Dayama çizgileri seçmeli olarak devre dışı ya da, bunları tasarım ortamında devre dışı bırakabilirsiniz.  
  
### <a name="to-selectively-disable-snaplines"></a>Seçmeli olarak dayama çizgileri devre dışı bırakmak için  
  
- ALT tuşuna basın ve bir denetimin form etrafında taşıma çalışırken.  
  
     Hiçbir dayama çizgileri görünür ve denetim, tüm olası hizalama konumlara Yasla değil unutmayın.  
  
### <a name="to-disable-snaplines-in-the-design-environment"></a>Tasarım ortamında dayama çizgileri devre dışı bırakmak için  
  
1. Gelen **Araçları** menüsünde, açık **seçenekleri** iletişim kutusu. Windows Form Tasarımcısı iletişim kutusunu açın. Ayrıntılar için bkz [genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).  
  
2. Seçin **genel** düğümü. İçinde **Düzen modu** bölümünde, seçimi değiştirme **dayama çizgileri** için **LayoutMode**.  
  
3. Ayarı uygulamak için Tamam'a tıklayın.  
  
4. Formunuzdaki bir denetim seçin ve diğer denetimlerin taşıyın. Dayama çizgileri görünmediğini unutmayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Dayama çizgileri, form üzerindeki denetimleri hizalama, sezgisel bir yol sunar. Daha fazla araştırma için öneriler şunlardır:  
  
- İç içe geçirmeyi deneyin bir <xref:System.Windows.Forms.GroupBox> başka denetimine <xref:System.Windows.Forms.GroupBox> denetimi. Bir yerde bir <xref:System.Windows.Forms.Button> alt denetimine <xref:System.Windows.Forms.GroupBox> denetimi ve üst içinde başka bir <xref:System.Windows.Forms.GroupBox> denetimi. Taşıma <xref:System.Windows.Forms.Button> yaklaşık nasıl dayama çizgileri kapsayıcı sınırlarının çapraz görmek için kontrol eder.  
  
- Bir sütun oluşturma <xref:System.Windows.Forms.TextBox> denetimleri ve karşılık gelen sütunun <xref:System.Windows.Forms.Label> denetimleri. Değerini <xref:System.Windows.Forms.Label> denetimleri <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`. Dayama çizgileri gidebilir <xref:System.Windows.Forms.Label> görüntülenen metin metinle hizalanacağı şekilde denetimleri <xref:System.Windows.Forms.TextBox> denetimleri.  
  
 Kitap Windows kullanıcı arabirimi tasarımı hakkında daha fazla bilgi için bkz. *Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricileri ve tasarımcıları için resmi yönergeleri* Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme](windows-forms-controls-padding-autosize.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
