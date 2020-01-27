---
title: Anlık görüntü çizgilerini kullanarak denetimleri düzenleme
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3b88f64fca8d3f11308f1cbfde97de2e6c2f22cc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740212"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>İzlenecek yol: Windows Forms denetimleri, yama çizgileri kullanarak düzenleme

Denetimlerin formunuza kesin olarak yerleştirilmesi birçok uygulama için yüksek önceliktir. Windows Form Tasarımcısı bunu gerçekleştirmek için size çok sayıda düzen aracı sağlar. En önemlilerinden biri <xref:System.Windows.Forms.Design.Behavior.SnapLine> özelliğidir.

Anlık görüntü çizgileri, denetimleri diğer denetimlerle nerede hizalamak gerektiğini tam olarak gösterir. Ayrıca, [Windows Kullanıcı arabirimi yönergeleri](/windows/win32/uxguide/guidelines)tarafından belirtildiği gibi denetimler arasındaki kenar boşlukları için önerilen uzaklıkları gösterir.

Anlık görüntü çizgileri denetimlerinizi, profesyonel görünüm ve davranış için (göz atın) kolayca hizalamanızı kolaylaştırır.

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio 'da, "SnaplineExample" adlı bir Windows tabanlı uygulama projesi oluşturun.

2. Form tasarımcısında formu seçin.

## <a name="space-and-align-controls"></a>Boşluk ve hizalama denetimleri

Anlık görüntü çizgileri, formunuzdaki denetimleri hizalamak için size doğru ve sezgisel bir yol sağlar. Seçili bir denetim veya denetimleri başka bir denetimle veya denetim kümesiyle hizalaacak bir konuma yakın taşırken görünürler. Seçiminiz, diğer denetimlerin ötesinde hareket etmesinden önce önerilen konuma "yasla" eklenir.

### <a name="to-arrange-controls-using-snaplines"></a>Anlık görüntü çizgilerini kullanarak denetimleri düzenlemek için

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.Button> denetimini formun sağ alt köşesine taşıyın. <xref:System.Windows.Forms.Button> denetimi olarak görünen anlık görüntü çizgileri formun alt ve sağ kenarlıklarına yaklaşır. Bu anlık çizgiler, denetimin kenarlıkları ve form arasındaki önerilen mesafeyi görüntüler.

3. <xref:System.Windows.Forms.Button> denetimini form kenarlıklarının etrafında taşıyın ve anlık görüntü çizgilerinin nerede göründüğünü aklınızda yapın. İşiniz bittiğinde, form merkezinin yakınında <xref:System.Windows.Forms.Button> denetimini taşıyın.

4. **Araç kutusundan** başka bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin.

5. İkinci <xref:System.Windows.Forms.Button> denetimini, ilk ile neredeyse düzeyi olana kadar taşıyın. Her iki düğmenin de metin taban çizgisinde görüntülenen ve taşıdığınız denetimin diğer denetimle tam düzeyde bir konuma yaslandığına göz önünde bulunduğunu unutmayın.

6. İkinci <xref:System.Windows.Forms.Button> denetimini, önce doğrudan üzerine konumlandırılana kadar taşıyın. Her iki düğmenin sol ve sağ kenarlarındaki anlık görüntü çizgilerini ve taşıdığınız denetimin diğer denetimle tam olarak hizalanmış bir konuma yaslandığını unutmayın.

7. <xref:System.Windows.Forms.Button> denetimlerinden birini seçin ve neredeyse dokunana kadar bir sonrakine geçin. Aralarında görüntülenen anlık görüntü çizgisini unutmayın. Bu uzaklık, denetimlerin kenarlıkları arasında önerilen uzaklıktan oluşur. Ayrıca, taşıdığınız denetimin bu konuma yaslandığına de unutmayın.

8. **Araç kutusundan** iki <xref:System.Windows.Forms.Panel> denetimini formunuza sürükleyin.

9. <xref:System.Windows.Forms.Panel> denetimlerinden birini, ilk ile neredeyse düzeyi olana kadar taşıyın. Her iki denetimin üst ve alt kenarları üzerinde görünen anlık görüntü çizgilerini ve taşıdığınız denetimin diğer denetimle tam düzeyde bir konuma yaslanmadığını unutmayın.

## <a name="align-to-form-and-container-margins"></a>Form ve kapsayıcı kenar boşluklarına Hizala

Anlık görüntü çizgileri, denetimlerinizi, düzenli bir şekilde form ve kapsayıcı kenar boşluklarına hizalamanıza yardımcı olur.

1. <xref:System.Windows.Forms.Button> denetimlerinden birini seçin ve bir ek yük çizgisi görünene kadar formun sağ kenarlığına yakın taşıyın. Anlık görüntü çizgisinin sağ kenarından uzaklığı, denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin ve formun <xref:System.Windows.Forms.Control.Padding%2A> özellik değerlerinin toplamıdır.

   > [!NOTE]
   > Formun <xref:System.Windows.Forms.Control.Padding%2A> özelliği 0, 0, 0, 0 olarak ayarlandıysa, Windows Form Tasarımcısı forma 9, 9, 9, 9 ' un gölgeli bir <xref:System.Windows.Forms.Control.Padding%2A> değeri verir. Bu davranışı geçersiz kılmak için 0, 0, 0, 0 dışında bir değer atayın.

2. <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin değerini, **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Margin%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini 0 olarak ayarlayarak değiştirin. Ayrıntılar için bkz. [Izlenecek yol: doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md).

3. Bir Snapın çizgisi görünene kadar <xref:System.Windows.Forms.Button> denetimini formun sağ kenarlığına taşıyın. Bu uzaklık artık formun <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değeri tarafından verilir.

4. **Araç kutusundan** bir <xref:System.Windows.Forms.GroupBox> denetimini formunuza sürükleyin.

5. <xref:System.Windows.Forms.GroupBox> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değerini, **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Padding%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini 10 olarak ayarlayarak değiştirin.

6. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.GroupBox> denetimine sürükleyin.

7. Bir Snapın çizgisi görünene kadar <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.GroupBox> denetiminin sağ kenarlığına taşıyın. <xref:System.Windows.Forms.GroupBox> denetim içindeki <xref:System.Windows.Forms.Button> denetimini taşıyın ve anlık görüntü çizgilerinin nerede göründüğünü aklınızda yapın.

## <a name="align-to-grouped-controls"></a>Gruplanmış denetimlere Hizala

Gruplanmış denetimleri ve bir <xref:System.Windows.Forms.GroupBox> denetimindeki denetimleri hizalamak için dayama çizgileri ' i kullanabilirsiniz.

1. Formunuzdaki iki denetimden birini seçin. Seçimi taşıyın ve seçiminiz ve diğer denetimler arasında görünen anlık görüntü çizgilerini unutmayın.

2. **Araç kutusundan** bir <xref:System.Windows.Forms.GroupBox> denetimini formunuza sürükleyin.

3. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.GroupBox> denetimine sürükleyin.

4. <xref:System.Windows.Forms.Button> denetimlerinden birini seçin ve <xref:System.Windows.Forms.GroupBox> denetimi etrafında taşıyın. <xref:System.Windows.Forms.GroupBox> denetiminin kenarlarındaki görünen ek çizgi çizgilerini unutmayın. Ayrıca, <xref:System.Windows.Forms.GroupBox> denetiminin içerdiği <xref:System.Windows.Forms.Button> denetiminin kenarları üzerinde görünen anlık görüntü çizgilerini de unutmayın. Bir kapsayıcı denetiminin alt öğeleri olan denetimler de yama çizgilerini destekler.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Boyutunu belirleyerek bir denetim yerleştirmek için dayama çizgileri kullanın

1. **Araç kutusunda**<xref:System.Windows.Forms.Button> denetim simgesine tıklayın. Bunu form üzerine sürüklemeyin.

2. Fare işaretçisini formun Tasarım yüzeyi üzerine taşıyın. İşaretçinin, <xref:System.Windows.Forms.Button> denetim simgesinin eklendiği çapraz artı işaretine değişdiğine unutmayın. Ayrıca, <xref:System.Windows.Forms.Button> denetimi için hizalanmış konumlar önermek için görüntülenen anlık görüntü çizgilerini de unutmayın.

3. Fare düğmesine tıklayın ve basılı tutun.

4. Fare işaretçisini formun etrafında sürükleyin. Denetimin konumunu ve boyutunu belirten bir ana hat çizildiğini unutmayın.

5. Formdaki başka bir denetimle hizalanana kadar işaretçiyi sürükleyin. Hizalama belirten bir anlık görüntü satırı göründüğünü unutmayın.

6. Fare düğmesini bırakın. Denetim, ana hat tarafından belirtilen konumda ve boyutta oluşturulur.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Araç kutusundan denetim sürüklerken dayama çizgileri kullanın

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin, ancak fare düğmesini serbest bırakın.

2. Fare işaretçisini formun Tasarım yüzeyi üzerine taşıyın. İşaretçinin, yeni <xref:System.Windows.Forms.Button> denetiminin oluşturulacağı konumu belirtecek şekilde değişdiğine unutmayın.

3. Fare işaretçisini formun etrafında sürükleyin. <xref:System.Windows.Forms.Button> denetimi için hizalanmış konumlar önermek için görüntülenen anlık görüntü çizgilerini unutmayın. Diğer denetimlerle hizalanmış bir konum bulun.

4. Fare düğmesini bırakın. Denetim, snaplines belirtilen konumda oluşturulur.

## <a name="resize-a-control-using-snaplines"></a>Anlık görüntü çizgileri kullanarak bir denetimi yeniden boyutlandırma

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.Button> denetimini, köşe boyutlandırma tutamaçlarından birini ve sürüklemeyi yakalayıp göre yeniden boyutlandırın. Ayrıntılar için bkz. [nasıl yapılır: Windows Forms denetimleri yeniden boyutlandırma](how-to-resize-controls-on-windows-forms.md).

3. <xref:System.Windows.Forms.Button> denetiminin kenarlarından biri başka bir denetimle hizalanana kadar boyutlandırma tutamacını sürükleyin. Bir ek yük çizgisi göründüğünü unutmayın. Ayrıca, boyutlandırma tutamacının, snapline tarafından belirtilen konuma yaslandığına de unutmayın.

4. <xref:System.Windows.Forms.Button> denetimini farklı yönlere göre yeniden boyutlandırın ve boyutlandırma tutamacını farklı denetimlere hizalayın. Hizalı göstermek için, ek çizgi çizgilerinin çeşitli yönlere nasıl göründüğünü aklınızda yapın.

## <a name="align-a-label-to-a-controls-text"></a>Etiketi bir denetimin metnine hizalayın

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TextBox> denetimini formunuza sürükleyin. Form üzerine <xref:System.Windows.Forms.TextBox> denetimini bıraktığınızda, akıllı etiket simgesine tıklayın ve **metni textBox1 olarak ayarla** seçeneğini belirleyin. Ayrıntılar için bkz. [Izlenecek yol: Windows Forms Denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md).

2. **Araç kutusundan** bir <xref:System.Windows.Forms.Label> denetimini formunuza sürükleyin.

3. <xref:System.Windows.Forms.Label> denetiminin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğinin değerini `true`olarak değiştirin. Denetimin kenarlıklarının, görüntüleme metnine uyacak şekilde ayarlandığını unutmayın.

4. <xref:System.Windows.Forms.Label> denetimini <xref:System.Windows.Forms.TextBox> denetiminin soluna taşıyın, bu nedenle <xref:System.Windows.Forms.TextBox> denetiminin alt kenarıyla hizalanır. İki denetimin alt kenarları üzerinde görünen Snapın çizgisini unutmayın.

5. <xref:System.Windows.Forms.Label> metni ve <xref:System.Windows.Forms.TextBox> metni hizalanana kadar <xref:System.Windows.Forms.Label> denetimini biraz daha yukarı taşıyın. Her iki denetimin metin alanlarının ne zaman hizalandığını belirten, görüntülenen farklı stillendirilmiş ek çizgi olduğunu unutmayın.

## <a name="use-snaplines-with-keyboard-navigation"></a>Klavye gezintisi ile dayama çizgileri kullanma

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin. Formun sol üst köşesine yerleştirin.

2. **Ctrl**+**aşağı ok**tuşuna basın. Denetimin formu, kullanılabilir ilk yatay hizalama konumuna taşıdığına unutmayın.

3. Denetim formun altına ulaşana kadar **Ctrl**+**aşağı ok** tuşuna basın. Formun aşağı doğru olduğu konumları göz önünde kalın.

4. **Ctrl**+**sağ ok**tuşuna basın. Denetimin form genelinde ilk kullanılabilir dikey hizalama konumuna taşındığını unutmayın.

5. Denetim formun kenarına ulaşıncaya kadar **Ctrl**+**sağ ok** tuşuna basın. Form boyunca taşıdıkça kapladığı konumları göz önünde edin.

6. Denetimi, ok tuşlarının birleşimiyle birlikte form etrafında taşıyın. Denetimin kapladığı konumları ve bunlara eşlik eden anlık görüntü satırlarını unutmayın.

7. <xref:System.Windows.Forms.Button> denetimini bir pikselin artışlarla yeniden boyutlandırmak için **shıft**+**ok tuşlarına** basın.

8. <xref:System.Windows.Forms.Button> denetimini daha sonra yeniden boyutlandırmak için **Ctrl**+**SHIFT**+**ok** tuşlarına basın.

## <a name="selectively-disable-snaplines"></a>Ek yama çizgilerini seçmeli devre dışı bırak

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.

2. **Araç kutusundaki**<xref:System.Windows.Forms.Button> denetim simgesine çift tıklayın. <xref:System.Windows.Forms.TableLayoutPanel> denetiminin ilk hücresinde yeni bir düğme denetimi göründüğünü unutmayın.

3. **Araç kutusundaki** <xref:System.Windows.Forms.Button> denetim simgesine iki kez çift tıklayın. Bu, <xref:System.Windows.Forms.TableLayoutPanel> denetiminde boş bir hücre bırakır.

4. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.TableLayoutPanel> denetiminin boş hücresine sürükleyin. Hiçbir yama çizgisi görünmediğini unutmayın.

5. <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.TableLayoutPanel> denetiminden sürükleyin ve <xref:System.Windows.Forms.TableLayoutPanel> denetimi etrafında taşıyın. Anlık görüntü çizgilerinin yeniden göründüğünü unutmayın.

## <a name="disable-snaplines"></a>Anlık görüntü satırlarını devre dışı bırak

Bir denetimi form etrafında taşırken **alt** tuşuna basın.

Hiçbir yama satırı görünmez ve denetim olası hizalama konumlarına eklemez.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Tasarım ortamında ek gitme çizgilerini devre dışı bırakmak için

1. **Araçlar** menüsünde **Seçenekler** iletişim kutusunu açın. **Windows Form Tasarımcısı**seçin.

2. **Genel** düğümünü seçin. **Düzen modu** bölümünde seçimi **snaplines** iken **SnapToGrid**olarak değiştirin.

3. Ayarı uygulamak için **Tamam ' ı** seçin.

4. Formunuzda bir denetim seçin ve diğer denetimlerin çevresinde taşıyın. Anlık görüntü çizgilerinin görünmediğini unutmayın.

## <a name="next-steps"></a>Sonraki adımlar

Anlık görüntü çizgileri, formunuzdaki denetimleri hizalamak için sezgisel bir yöntem sunar. Daha fazla araştırma için öneriler şunlardır:

- Bir <xref:System.Windows.Forms.GroupBox> denetimini başka bir <xref:System.Windows.Forms.GroupBox> denetiminde iç içe geçirmeyi deneyin. Alt <xref:System.Windows.Forms.GroupBox> denetimine bir <xref:System.Windows.Forms.Button> denetimi ve üst <xref:System.Windows.Forms.GroupBox> denetiminin içinde başka bir denetim koyun. Anlık görüntü çizgilerinin çapraz kapsayıcı sınırlarının dışına bakmak için <xref:System.Windows.Forms.Button> denetimlerinin etrafında taşıyın.

- <xref:System.Windows.Forms.TextBox> denetimlerinin bir sütununu ve <xref:System.Windows.Forms.Label> denetimlerinin karşılık gelen sütununu oluşturun. <xref:System.Windows.Forms.Label> Controls ' <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğinin değerini `true`olarak ayarlayın. <xref:System.Windows.Forms.Label> denetimlerini, görüntülenecek metinlerin <xref:System.Windows.Forms.TextBox> denetimlerindeki metinle hizalandığı şekilde taşımak için dayama çizgileri kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](windows-forms-controls-padding-autosize.md)
