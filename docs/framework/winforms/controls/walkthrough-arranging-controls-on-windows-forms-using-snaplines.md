---
title: "İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 8ac1ba6b8121aabea3c992ca5b943f231fc19ce2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950066"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme
Denetimlerin formunuza kesin olarak yerleştirilmesi birçok uygulama için yüksek önceliktir. Windows Form Tasarımcısı bunu gerçekleştirmek için size çok sayıda düzen aracı sağlar. En önemlileri <xref:System.Windows.Forms.Design.Behavior.SnapLine> bu özellikten biridir.

 Anlık görüntü çizgileri, denetimleri diğer denetimlerle nerede hizalamak gerektiğini tam olarak gösterir. Ayrıca, Windows Kullanıcı arabirimi yönergeleri tarafından belirtildiği gibi denetimler arasındaki kenar boşlukları için önerilen uzaklıkları gösterir. Ayrıntılar için bkz. [Kullanıcı arabirimi tasarımı ve geliştirme](https://go.microsoft.com/FWLink/?LinkId=83878).

 Anlık görüntü çizgileri denetimlerinizi, profesyonel görünüm ve davranış için (göz atın) kolayca hizalamanızı kolaylaştırır.

 Bu izlenecek yolda gösterilen görevler şunlardır:

- Windows Forms projesi oluşturma

- Anlık görüntü çizgileri kullanarak denetimleri değiştirme ve hizalama

- Form ve kapsayıcı kenar boşluklarına hizalama

- Gruplanmış denetimlere hizalama

- Boyutunu belirleyerek bir denetimi yerleştirmek için Snaplines kullanma

- Araç kutusundan denetim sürüklerken Snaplines kullanma

- Anlık görüntü çizgilerini kullanarak denetimleri yeniden boyutlandırma

- Bir etiketi denetimin metnine hizalama

- Klavye gezintisi ile Snaplines kullanma

- Anlık görüntü çizgileri ve düzen bölmeleri

- Anlık görüntü satırlarını devre dışı bırakma

 İşiniz bittiğinde, yama satırları özelliğinin oynadığı düzen rolünü kavramış olursunuz.

## <a name="creating-the-project"></a>Projeyi Oluşturma
 İlk adım projeyi oluşturmak ve formu kurmak olur.

### <a name="to-create-the-project"></a>Proje oluşturmak için

1. "SnaplineExample" adlı Windows tabanlı bir uygulama projesi oluşturun (**Dosya** > **Yeni** > **Proje** >  **C# görseli** veya **Visual Basic** > **Klasik** Masaüstü > **Windows Forms uygulaması**).

2. Form tasarımcısında formu seçin.

## <a name="spacing-and-aligning-controls-using-snaplines"></a>Anlık görüntü çizgileri kullanarak denetimleri değiştirme ve hizalama
 Anlık görüntü çizgileri, formunuzdaki denetimleri hizalamak için size doğru ve sezgisel bir yol sağlar. Seçili bir denetim veya denetimleri başka bir denetimle veya denetim kümesiyle hizalaacak bir konuma yakın taşırken görünürler. Seçiminiz, diğer denetimlerin ötesinde hareket etmesinden önce önerilen konuma "yasla" eklenir.

### <a name="to-arrange-controls-using-snaplines"></a>Anlık görüntü çizgilerini kullanarak denetimleri düzenlemek için

1. <xref:System.Windows.Forms.Button> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. <xref:System.Windows.Forms.Button> Denetimi formun sağ alt köşesine taşıyın. <xref:System.Windows.Forms.Button> Denetim olarak görünen anlık görüntü çizgileri formun alt ve sağ kenarlıklarına yaklaşır. Bu anlık çizgiler, denetimin kenarlıkları ve form arasındaki önerilen mesafeyi görüntüler.

3. <xref:System.Windows.Forms.Button> Denetimi, form kenarlıklarının etrafında taşıyın ve anlık görüntü çizgilerinin nerede göründüğünü aklınızda yapın. İşiniz bittiğinde <xref:System.Windows.Forms.Button> denetimi formun merkezine yaklaştırın.

4. <xref:System.Windows.Forms.Button> **Araç kutusundan** başka bir denetimi formunuza sürükleyin.

5. İkinci <xref:System.Windows.Forms.Button> denetimi ilk ile neredeyse düzeyi olana kadar taşıyın. Her iki düğmenin de metin taban çizgisinde görüntülenen ve taşıdığınız denetimin diğer denetimle tam düzeyde bir konuma yaslandığına göz önünde bulunduğunu unutmayın.

6. İkinci <xref:System.Windows.Forms.Button> denetimi, önce doğrudan üzerine konumlandırılana kadar taşıyın. Her iki düğmenin sol ve sağ kenarlarındaki anlık görüntü çizgilerini ve taşıdığınız denetimin diğer denetimle tam olarak hizalanmış bir konuma yaslandığını unutmayın.

7. <xref:System.Windows.Forms.Button> Denetimlerden birini seçin ve neredeyse dokununcaya kadar, diğerine yakın hareket ettirin. Aralarında görüntülenen anlık görüntü çizgisini unutmayın. Bu uzaklık, denetimlerin kenarlıkları arasında önerilen uzaklıktan oluşur. Ayrıca, taşıdığınız denetimin bu konuma yaslandığına de unutmayın.

8. <xref:System.Windows.Forms.Panel> **Araç kutusundan** iki denetimi formunuza sürükleyin.

9. İlk ile neredeyse düzeyi <xref:System.Windows.Forms.Panel> olana kadar denetimlerden birini taşıyın. Her iki denetimin üst ve alt kenarları üzerinde görünen anlık görüntü çizgilerini ve taşıdığınız denetimin diğer denetimle tam düzeyde bir konuma yaslanmadığını unutmayın.

## <a name="aligning-to-form-and-container-margins"></a>Form ve kapsayıcı kenar boşluklarına hizalama
 Anlık görüntü çizgileri, denetimlerinizi, düzenli bir şekilde form ve kapsayıcı kenar boşluklarına hizalamanıza yardımcı olur.

### <a name="to-align-controls-to-form-and-container-margins"></a>Denetimleri form ve kapsayıcı kenar boşluklarına hizalamak için

1. <xref:System.Windows.Forms.Button> Denetimlerden birini seçin ve bir anlık görüntü satırı görünene kadar formun sağ kenarlığına yakın taşıyın. Anlık görüntü çizgisinin sağ kenarından uzaklığı denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin ve <xref:System.Windows.Forms.Control.Padding%2A> formun özellik değerlerinin toplamıdır.

> [!NOTE]
> Formun <xref:System.Windows.Forms.Control.Padding%2A> özelliği 0, 0, 0, 0 olarak ayarlandıysa Windows Form Tasarımcısı, forma 9, 9, 9, 9 ' un <xref:System.Windows.Forms.Control.Padding%2A> gölgeli bir değer verir. Bu davranışı geçersiz kılmak için 0, 0, 0, 0 dışında bir değer atayın.

1. <xref:System.Windows.Forms.Button> **Özellikler** penceresinde girişigenişleterek<xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> özelliğini0olarakayarlayarakdenetiminözelliğinindeğerinideğiştirin.<xref:System.Windows.Forms.Padding.All%2A> Ayrıntılar için bkz [. İzlenecek yol: Doldurma, kenar boşlukları ve AutoSize özelliği](windows-forms-controls-padding-autosize.md)ile Windows Forms denetimleri yerleştirme.

2. Anlık görüntü satırı görünene kadar denetimiformunsağkenarlığınataşıyın.<xref:System.Windows.Forms.Button> Bu uzaklık artık formun <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değeri tarafından verilir.

3. <xref:System.Windows.Forms.GroupBox> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

4. <xref:System.Windows.Forms.GroupBox> **Özellikler** penceresinde girişigenişleterek<xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> özelliğini10olarakayarlayarakdenetiminözelliğinindeğerinideğiştirin.<xref:System.Windows.Forms.Padding.All%2A>

5. Bir <xref:System.Windows.Forms.Button> denetimi **araç kutusundan denetime sürükleyin** <xref:System.Windows.Forms.GroupBox> .

6. Bir anlık görüntü satırı görünene kadar <xref:System.Windows.Forms.GroupBox> denetimisağkenarlığıylataşıyın.<xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> Denetim içindekidenetimitaşıyınveanlıkgörüntüçizgilerininnerede<xref:System.Windows.Forms.GroupBox> göründüğünü aklınızda yapın.

## <a name="aligning-to-grouped-controls"></a>Gruplanmış denetimlere hizalama
 Gruplanmış denetimleri ve <xref:System.Windows.Forms.GroupBox> denetim içindeki denetimleri hizalamak için Snapın çizgilerini kullanabilirsiniz.

### <a name="to-align-to-grouped-controls"></a>Gruplanmış denetimlere hizalamak için

1. Formunuzdaki iki denetimden birini seçin. Seçimi taşıyın ve seçiminiz ve diğer denetimler arasında görünen anlık görüntü çizgilerini unutmayın.

2. <xref:System.Windows.Forms.GroupBox> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

3. Bir <xref:System.Windows.Forms.Button> denetimi **araç kutusundan denetime sürükleyin** <xref:System.Windows.Forms.GroupBox> .

4. <xref:System.Windows.Forms.Button> Denetimlerden birini seçin ve <xref:System.Windows.Forms.GroupBox> denetimin çevresinde taşıyın. <xref:System.Windows.Forms.GroupBox> Denetimin kenarlarındaki görünen ek çizgi çizgilerini unutmayın. Ayrıca, denetimin içindeki <xref:System.Windows.Forms.Button> denetimin kenarları üzerinde görünen <xref:System.Windows.Forms.GroupBox> ek çizgi çizgilerini de unutmayın. Bir kapsayıcı denetiminin alt öğeleri olan denetimler de yama çizgilerini destekler.

## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Boyutunu belirleyerek bir denetimi yerleştirmek için Snaplines kullanma
 Anlık görüntü çizgileri, bir forma ilk kez yerleştirirken denetimleri hizalamaya yardımcı olur.

### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Bir denetimi, boyutunun anahatlarını belirleyerek yerleştirmek için yama çizgileri kullanma

1. **Araç kutusunda** <xref:System.Windows.Forms.Button> denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

2. Fare işaretçisini formun Tasarım yüzeyi üzerine taşıyın. İşaretçinin, <xref:System.Windows.Forms.Button> denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın. Ayrıca, <xref:System.Windows.Forms.Button> denetim için hizalanmış konumlar önermek için görüntülenen anlık görüntü çizgilerini de unutmayın.

3. Fare düğmesine tıklayın ve basılı tutun.

4. Fare işaretçisini formun etrafında sürükleyin. Denetimin konumunu ve boyutunu belirten bir ana hat çizildiğini unutmayın.

5. Formdaki başka bir denetimle hizalanana kadar işaretçiyi sürükleyin. Hizalama belirten bir anlık görüntü satırı göründüğünü unutmayın.

6. Fare düğmesini bırakın. Denetim, ana hat tarafından belirtilen konumda ve boyutta oluşturulur.

## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Araç kutusundan denetim sürüklerken Snaplines kullanma
 Anlık görüntü çizgileri, **araç kutusu** ' ndan formunuza sürüklediğinizde denetimleri hizalamaya yardımcı olur.

### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Araç kutusundan denetim sürüklerken dayama çizgileri kullanmak için

1. <xref:System.Windows.Forms.Button> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin, ancak fare düğmesini serbest bırakın.

2. Fare işaretçisini formun Tasarım yüzeyi üzerine taşıyın. İşaretçinin, yeni <xref:System.Windows.Forms.Button> denetimin oluşturulacağı konumu belirtecek şekilde değişdiğine unutmayın.

3. Fare işaretçisini formun etrafında sürükleyin. <xref:System.Windows.Forms.Button> Denetim için hizalanmış konumlar önermek için görüntülenen anlık görüntü çizgilerini unutmayın. Diğer denetimlerle hizalanmış bir konum bulun.

4. Fare düğmesini bırakın. Denetim, snaplines belirtilen konumda oluşturulur.

## <a name="resizing-controls-using-snaplines"></a>Anlık görüntü çizgilerini kullanarak denetimleri yeniden boyutlandırma
 Anlık görüntü çizgileri, yeniden boyutlandırdıkça denetimleri hizalamanıza yardımcı olur.

### <a name="to-resize-a-control-using-snaplines"></a>Anlık görüntü çizgilerini kullanarak bir denetimi yeniden boyutlandırmak için

1. <xref:System.Windows.Forms.Button> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. Yakalayıp, <xref:System.Windows.Forms.Button> köşe boyutlandırma tutamaçlarından birini ve sürüklemeyi seçerek denetimi yeniden boyutlandırın. Ayrıntılar için bkz [. nasıl yapılır: Windows Forms](how-to-resize-controls-on-windows-forms.md)denetimleri yeniden boyutlandırın.

3. <xref:System.Windows.Forms.Button> Denetimin kenarlıklarıyla bir başka denetimle hizalanana kadar boyutlandırma tutamacını sürükleyin. Bir ek yük çizgisi göründüğünü unutmayın. Ayrıca, boyutlandırma tutamacının, snapline tarafından belirtilen konuma yaslandığına de unutmayın.

4. <xref:System.Windows.Forms.Button> Denetimi farklı yönlere göre yeniden boyutlandırın ve boyutlandırma tutamacını farklı denetimlere hizalayın. Hizalı göstermek için, ek çizgi çizgilerinin çeşitli yönlere nasıl göründüğünü aklınızda yapın.

## <a name="aligning-a-label-to-a-controls-text"></a>Bir etiketi denetimin metnine hizalama
 Bazı denetimler, diğer denetimleri görüntülenecek metin ile hizalamak için bir ek yük çizgisi sunar.

### <a name="to-align-a-label-to-a-controls-text"></a>Bir etiketi denetimin metnine hizalamak için

1. <xref:System.Windows.Forms.TextBox> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin. <xref:System.Windows.Forms.TextBox> Denetimi forma bıraktığınızda, akıllı etiket glifi ' na tıklayın ve **metni textBox1 olarak ayarla** seçeneğini belirleyin. Ayrıntılar için bkz [. İzlenecek yol: Windows Forms denetimlerinde](performing-common-tasks-using-smart-tags-on-wf-controls.md)Akıllı etiketleri kullanarak ortak görevleri gerçekleştirme.

2. <xref:System.Windows.Forms.Label> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

3. <xref:System.Windows.Forms.Label> Denetimin özelliğinin değerini olarak`true`değiştirin. <xref:System.Windows.Forms.Control.AutoSize%2A> Denetimin kenarlıklarının, görüntüleme metnine uyacak şekilde ayarlandığını unutmayın.

4. Denetimi denetimin soluna <xref:System.Windows.Forms.TextBox> taşıyın, bu nedenle <xref:System.Windows.Forms.TextBox> denetimin alt kenarıyla hizalanır. <xref:System.Windows.Forms.Label> İki denetimin alt kenarları üzerinde görünen Snapın çizgisini unutmayın.

5. <xref:System.Windows.Forms.Label> Metin ve <xref:System.Windows.Forms.Label> metinhizalananakadardenetimibiraz<xref:System.Windows.Forms.TextBox> daha yukarıya taşıyın. Her iki denetimin metin alanlarının ne zaman hizalandığını belirten, görüntülenen farklı stillendirilmiş ek çizgi olduğunu unutmayın.

## <a name="using-snaplines-with-keyboard-navigation"></a>Klavye gezintisi ile Snaplines kullanma
 Anlık görüntü çizgileri, klavye oku tuşlarını kullanarak bunları düzenleyerek denetimleri hizalamaya yardımcı olur.

### <a name="to-use-snaplines-with-keyboard-navigation"></a>Klavye gezintisi ile Snapın çizgilerini kullanmak için

1. <xref:System.Windows.Forms.Button> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin. Formun sol üst köşesine yerleştirin.

2. CTRL + aşağı ok tuşlarına basın. Denetimin formu, kullanılabilir ilk yatay hizalama konumuna taşıdığına unutmayın.

3. CTRL + aşağı ok tuşlarına basarak denetim formun altına ulaşana kadar basın. Formun aşağı doğru olduğu konumları göz önünde kalın.

4. CTRL + sağ ok tuşlarına basın. Denetimin form genelinde ilk kullanılabilir dikey hizalama konumuna taşındığını unutmayın.

5. Denetim formun kenarına ulaşıncaya kadar CTRL + sağ ok tuşlarına basın. Form boyunca taşıdıkça kapladığı konumları göz önünde edin.

6. Denetimi, ok tuşlarının birleşimiyle birlikte form etrafında taşıyın. Denetimin kapladığı konumları ve bunlara eşlik eden anlık görüntü satırlarını unutmayın.

7. <xref:System.Windows.Forms.Button> Denetimi bir pikselin artışlarla yeniden boyutlandırmak için SHIFT + any ok tuşuna basın.

8. CTRL + SHIFT + herhangi bir ok tuşuna basarak <xref:System.Windows.Forms.Button> denetimin anlık çizgi artışlarını yeniden boyutlandırın.

## <a name="snaplines-and-layout-panels"></a>Anlık görüntü çizgileri ve düzen bölmeleri
 Yerleştirme çizgileri, düzen bölmeleri içinde devre dışı bırakıldı.

### <a name="to-selectively-disable-snaplines"></a>Anlık görüntü çizgilerini seçmeli olarak devre dışı bırakmak için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. <xref:System.Windows.Forms.Button> **Araç kutusundaki**denetim simgesine çift tıklayın. <xref:System.Windows.Forms.TableLayoutPanel> Denetimin ilk hücresinde yeni bir düğme denetimi göründüğünü unutmayın.

3. <xref:System.Windows.Forms.Button> **Araç kutusundaki** denetim simgesine iki kez çift tıklayın. Bu, <xref:System.Windows.Forms.TableLayoutPanel> denetimde boş bir hücre bırakır.

4. <xref:System.Windows.Forms.Button> **Araç kutusundan** bir denetimi <xref:System.Windows.Forms.TableLayoutPanel> denetimin boş hücresine sürükleyin. Hiçbir yama çizgisi görünmediğini unutmayın.

5. Denetimi denetimin dışına<xref:System.Windows.Forms.TableLayoutPanel> sürükleyin ve denetimin çevresinde taşıyın. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.TableLayoutPanel> Anlık görüntü çizgilerinin yeniden göründüğünü unutmayın.

## <a name="disabling-snaplines"></a>Anlık görüntü satırlarını devre dışı bırakma
 Snaplines varsayılan olarak açıktır. Anlık görüntü satırlarını seçmeli olarak devre dışı bırakabilir veya tasarım ortamında devre dışı bırakabilirsiniz.

### <a name="to-selectively-disable-snaplines"></a>Anlık görüntü çizgilerini seçmeli olarak devre dışı bırakmak için

- Bir denetimi form etrafında taşırken ALT tuşuna basın.

     Hiçbir yama çizgisi görünmediğini ve denetimin olası hizalama konumlarına uydurmadığını unutmayın.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Tasarım ortamında ek gitme çizgilerini devre dışı bırakmak için

1. **Araçlar** menüsünde **Seçenekler** iletişim kutusunu açın. Windows Form Tasarımcısı iletişim kutusunu açın. Ayrıntılar için bkz. [Genel, Windows Form Tasarımcısı, Seçenekler Iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).

2. **Genel** düğümünü seçin. **Düzen modu** bölümünde seçimi **snaplines** iken **SnapToGrid**olarak değiştirin.

3. Ayarı uygulamak için Tamam ' ı tıklatın.

4. Formunuzda bir denetim seçin ve diğer denetimlerin çevresinde taşıyın. Anlık görüntü çizgilerinin görünmediğini unutmayın.

## <a name="next-steps"></a>Sonraki Adımlar
 Anlık görüntü çizgileri, formunuzdaki denetimleri hizalamak için sezgisel bir yöntem sunar. Daha fazla araştırma için öneriler şunlardır:

- Bir <xref:System.Windows.Forms.GroupBox> denetimi başka <xref:System.Windows.Forms.GroupBox> bir denetim içinde iç içe geçirmeyi deneyin. Alt <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Button> Denetimiçine<xref:System.Windows.Forms.GroupBox> ve diğeri de üst denetim içine bir denetim koyun. Anlık görüntü, kapsayıcı sınırlarının çapraz çizgilerinin nasıl çapraz olduğunu görmek için denetimlerietrafındataşıyın.<xref:System.Windows.Forms.Button>

- <xref:System.Windows.Forms.TextBox> Denetimlerin bir sütununu ve ilgili <xref:System.Windows.Forms.Label> denetimlerin bir sütununu oluşturun. <xref:System.Windows.Forms.Label> Denetimlerin `true`' <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğinin değerini olarak ayarlayın. <xref:System.Windows.Forms.Label> Denetimleri, görüntülenmekte olan metinlerin <xref:System.Windows.Forms.TextBox> denetimlerde metinle hizalanmasını sağlayacak şekilde taşımak için dayama çizgileri kullanın.

 Windows Kullanıcı arabirimi tasarımı hakkında daha fazla bilgi için, bkz. *Microsoft Windows Kullanıcı deneyimi, Kullanıcı arabirimi geliştiricileri ve tasarımcılar Için resmi kılavuz* bilgileri, Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
