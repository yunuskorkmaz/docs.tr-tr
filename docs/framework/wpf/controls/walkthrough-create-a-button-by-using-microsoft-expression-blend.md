---
title: 'İzlenecek yol: Microsoft Expression Blend Kullanarak Düğme Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 10d049288cf560dadedf7bc5e624deb7c42aae81
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636180"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>İzlenecek yol: Microsoft Expression Blend Kullanarak Düğme Oluşturma

Bu izlenecek yol, Microsoft Expression Blend kullanarak WPF özelleştirilmiş bir düğme oluşturma sürecinde size kılavuzluk eden bir adım adım.

> [!IMPORTANT]
> Microsoft Expression Blend, yürütülebilir programı oluşturmak için derlenen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturarak işe yarar. Doğrudan XAML ile çalışmayı tercih ediyorsanız, Blend yerine Visual Studio ile aynı uygulamayı oluşturan başka bir anlatım de vardır. Daha fazla bilgi için bkz. [XAML kullanarak düğme oluşturma](walkthrough-create-a-button-by-using-xaml.md) .

Aşağıdaki çizimde, oluşturacağınız özelleştirilmiş düğme gösterilmektedir.

![Oluşturacağınız özelleştirilmiş düğme](./media/custom-button-blend-intro.jpg)

## <a name="convert-a-shape-to-a-button"></a>Bir şekli düğmeye Dönüştür

Bu izlenecek yolun ilk bölümünde özel düğmesine özel bir görünüm oluşturursunuz. Bunu yapmak için, önce bir dikdörtgeni bir düğmeye dönüştürmeniz gerekir. Daha sonra düğme şablonuna daha karmaşık bir görünümlü düğme oluşturarak ek şekiller eklersiniz. Neden düzenli bir düğmeyle başlamasın ve özelleştirilemiyor? Bir düğme, ihtiyacınız olmayan yerleşik işlevlere sahip olduğundan, Özel düğmeler için bir dikdörtgenle başlamak daha kolaydır.

### <a name="to-create-a-new-project-in-expression-blend"></a>Ifade Blend 'de yeni bir proje oluşturmak için

1. Ifade Blend 'i Başlat. ( **Başlat**' a tıklayın, **tüm programlar**' ın, **Microsoft Expression**' ın üzerine gelin ve ardından **Microsoft Expression Blend**' e tıklayın.

2. Gerekirse uygulamayı en üst düzeye çıkarın.

3. **Dosya** menüsünde **Yeni proje**' ye tıklayın.

4. **Standart uygulama (. exe)** seçeneğini belirleyin.

5. Projeyi `CustomButton` adlandırın ve **Tamam**' a basın.

Bu noktada, boş bir WPF projeniz vardır. F5 tuşuna basarak uygulamayı çalıştırabilirsiniz. Tahmin edebileceğiniz gibi, uygulama yalnızca boş bir pencereden oluşur. Ardından, yuvarlatılmış bir dikdörtgen oluşturur ve bunu bir düğmeye dönüştürürsünüz.

### <a name="to-convert-a-rectangle-to-a-button"></a>Bir dikdörtgeni düğmeye dönüştürmek için

1. **Pencere arka plan özelliğini siyah olarak ayarlayın:** Pencereyi seçin, **Özellikler sekmesine**tıklayın ve <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Black`olarak ayarlayın.

    ![Bir düğmenin arka planını siyaha ayarlama](./media/custom-button-blend-changebackground.png)

2. **Penceredeki bir düğmenin boyutunu yaklaşık bir dikdörtgen çizin:** Sol taraftaki araç panelinde Dikdörtgen aracını seçin ve dikdörtgeni pencereye sürükleyin.

    ![Dikdörtgen çizme](./media/custom-button-blend-drawrect.png)

3. **Dikdörtgenin köşelerini yuvarlama:** Dikdörtgenin denetim noktalarını sürükleyin ya da <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özelliklerini doğrudan ayarlayın. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> değerlerini 20 olarak ayarlayın.

    ![Dikdörtgenin köşelerini bir yuvarlak yapma](./media/custom-button-blend-roundcorners.png)

4. **Dikdörtgeni bir düğme olarak değiştirin:** Dikdörtgeni seçin. **Araçlar** menüsünde, **Oluştur düğmesine**tıklayın.

    ![Bir düğmeye şekil oluşturma](./media/custom-button-blend-makebutton.png)

5. **Stilin/şablonun kapsamını belirtin:** Aşağıdakine benzer bir iletişim kutusu görünür.

    !["Stil kaynağı oluştur" iletişim kutusu](./media/custom-button-blend-makebutton2.gif)

    **Kaynak adı (anahtar)** Için **Tümüne Uygula**' yı seçin.  Bu, ortaya çıkan stilin ve düğme şablonunun düğme olan tüm nesnelere uygulanmasını sağlar. **Içinde tanımlama**için **uygulama**' yı seçin. Bu, ortaya çıkan stilin ve düğme şablonunun tüm uygulama üzerinde kapsama sahip olmasını sağlayacaktır. Bu iki kutu içindeki değerleri ayarladığınızda, düğme stili ve şablonu tüm uygulamanın içindeki tüm düğmelere ve uygulamada oluşturduğunuz düğmeye uygulanır, varsayılan olarak bu şablonu kullanır.

## <a name="edit-the-button-template"></a>Düğme şablonunu düzenleme

Artık bir düğmeye değiştirilmiş bir dikdörtgenine sahipsiniz. Bu bölümde, düğmenin şablonunu değiştirecek ve görünüşünü daha fazla özelleştireceksiniz.

### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Düğme görünümünü değiştirmek için düğme şablonunu düzenlemek için

1. **Şablonu Düzenle görünümüne git:** Düğimizin görünümünü daha da özelleştirmek için düğme şablonunu düzenlememiz gerekir. Bu şablon, dikdörtgeni bir düğmeye dönüştürtiğimiz zaman oluşturulmuştur. Düğme şablonunu düzenlemek için, düğmeye sağ tıklayın ve **Denetim bölümlerini Düzenle (şablon)** seçeneğini belirleyin ve ardından **Şablonu düzenleyin**.

    ![Bir şablonu düzenleme](./media/custom-button-blend-edittemplate.jpg)

    Şablon düzenleyicisinde, düğmenin artık <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Controls.ContentPresenter>ayrıldığına dikkat edin. <xref:System.Windows.Controls.ContentPresenter>, düğme içinde içerik sunmak için kullanılır (örneğin, "düğme" dizesi). Dikdörtgen ve <xref:System.Windows.Controls.ContentPresenter> her ikisi de bir <xref:System.Windows.Controls.Grid>içinde düzenlenir.

    ![Dikdörtgen sunumundaki bileşenler](./media/custom-button-blend-templatepanel.png)

2. **Şablon bileşenlerinin adlarını değiştirin:** Şablon envanterinde dikdörtgeni sağ tıklatın, <xref:System.Windows.Shapes.Rectangle> adı "[Rectangle]" iken "outerRectangle" olarak değiştirin ve "[ContentPresenter]" öğesini "myContentPresenter" olarak değiştirin.

    ![Bir şablonun bileşenini yeniden adlandırma](./media/custom-button-blend-renamecomponents.png)

3. **Dikdörtgeni, içinde boş olacak şekilde değiştirin (halka gibi):** **OuterRectangle** ' ı seçin ve <xref:System.Windows.Shapes.Shape.Fill%2A> "saydam" olarak ayarlayın ve 5 ' e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.

    ![Bir dikdörtgeni boş yapma](./media/custom-button-blend-changerectproperties.png)

    Ardından <xref:System.Windows.Shapes.Shape.Stroke%2A> şablonun hangi renge olacağını belirleyin. Bunu yapmak için, **vuruş**' ın yanındaki küçük beyaz kutusuna tıklayın, **CustomExpression**' ı seçin ve Iletişim kutusuna "{TemplateBinding background}" yazın.

    ![Şablonun rengini kullanımı nasıl ayarlanır](./media/custom-button-blend-templatestroke.png)

4. **İç dikdörtgen oluşturun:** Şimdi başka bir dikdörtgen oluşturun ("ınnerrectangle" olarak adlandırın) ve **outerRectangle** 'in içine simetrik olarak konumlandırın. Bu tür bir çalışma için büyük olasılıkla, bir düğmeyi daha büyük bir şekilde, düzen alanında büyütmek isteyeceksiniz.

    > [!NOTE]
    > Dikdörtgende, şekilden farklı görünebilir (örneğin, yuvarlatılmış köşeler olabilir).

    ![Başka bir dikdörtgenin içinde dikdörtgen oluşturma](./media/custom-button-blend-innerrectangleproperties.png)

5. **ContentPresenter 'ı en üste taşı:** Bu noktada, "Button" metni artık görünür olmayacaktır. Bu durumda, **ınnerrectangle** **myContentPresenter**üzerinde yer alır. Bunu yapmak için **myContentPresenter** ' nu **innerRectangle**' ın altına sürükleyin. Dikdörtgenleri ve **myContentPresenter** ' a benzer şekilde yeniden konumlandırın.

    > [!NOTE]
    > Alternatif olarak, **myContentPresenter** ' ı sağ tıklayıp, **İleri gönder**' i seçerek üst üste yerleştirebilirsiniz.

    ![Bir düğmeyi başka bir düğmenin üstüne taşıma](./media/custom-button-blend-innerrectangle2.png)

6. **Innerrectangle 'ın görünümünü değiştirme:** <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> değerlerini 20 olarak ayarlayın. Ayrıca, "{TemplateBinding background}" özel ifadesini kullanarak şablonun arka planına <xref:System.Windows.Shapes.Shape.Fill%2A> ayarlayın ve <xref:System.Windows.Shapes.Shape.Stroke%2A> "transparent" olarak ayarlayın. **Innerrectangle** 'ın <xref:System.Windows.Shapes.Shape.Fill%2A> ve <xref:System.Windows.Shapes.Shape.Stroke%2A> ayarlarının, **outerRectangle**için olanların tersi olduğuna dikkat edin.

    ![Dikdörtgenin görünümünü değiştirme](./media/custom-button-blend-glassrectangleproperties1.png)

7. **En üste bir cam katman ekleyin:** Düğme görünümünü özelleştirmenin son parçası, en üste bir cam katman eklemektir. Bu cam katman üçüncü bir dikdörtgenden oluşur. Cam düğmenin tamamını kapladığı için cam dikdörtgen **outerRectangle**boyutlarındaki boyutlara benzer. Bu nedenle, yalnızca **outerRectangle**kopyasını yaparak dikdörtgeni oluşturun. **OuterRectangle** vurgulayın ve bir kopya oluşturmak için CTRL + C ve CTRL + V kullanın. Bu yeni dikdörtgeni "glassCube" olarak adlandırın.

8. **Gerekirse Yeniden Konumlandır glassCube:** **GlassCube** , tüm düğmeyi kaplamasını sağlayacak şekilde zaten yerleştirilmediğinden konuma sürükleyin.

9. **GlassCube kıyasla biraz farklı bir şekil verin:** **GlassCube**özelliklerini değiştirin. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özelliklerini 10 ' a ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 2 ' ye değiştirerek baştan başlayın.

    ![GlassCube için görünüm ayarları](./media/custom-button-blend-glasscubeappearance.gif)

10. **Cam gibi glassCube görünmesini sağlama:** <xref:System.Windows.Shapes.Shape.Fill%2A> %75 opak olan doğrusal bir gradyan kullanarak bir glassy olarak ayarlayın, beyaz renkli ve yaklaşık 6 ' dan fazla aralıklı aralıklarla saydam bir şekilde görünür. Gradyan duraklarının şu şekilde ayarlanması için:

    - Gradyan durağı 1: alfa değeri %75 olan beyaz

    - Gradyan durağı 2: saydam

    - Gradyan durağı 3: alfa değeri %75 olan beyaz

    - Gradyan durdurma 4: saydam

    - Gradyan durdur 5: alfa değeri %75 olan beyaz

    - Gradyan durdur 6: saydam

    Bu, "dalgalı" cam görünümü oluşturur.

    ![Cam gibi görünen bir dikdörtgen](./media/custom-button-blend-glassrectangleproperties2.png)

11. **Cam katmanını gizleyin:** Glassy katmanının nasıl göründüğünü görmediğiniz için, **Özellikler panelinin** **Görünüm bölmesine** gidin ve opaklığı gizlemek için %0 olarak ayarlayın. Bölümlerde, cam katmanını göstermek ve işlemek için özellik Tetikleyicileri ve olayları kullanacağız.

    ![Cam dikdörtgeni gizleme](./media/custom-button-glassrectangleproperties3.gif)

## <a name="customize-the-button-behavior"></a>Düğme davranışını özelleştirme

Bu noktada, kendi şablonunu düzenleyerek düğmenin sunumunu özelleştirdiniz, ancak düğme, tipik düğmeler gibi kullanıcı eylemlerine yanıt vermez (örneğin, fare üzerindeyken, odak alırken ve ' a tıklayarak). Sonraki iki yordam, özel düğmeye benzer davranışlar oluşturmayı gösterir. Basit özellik Tetikleyicileri ile başlayacağız ve Olay Tetikleyicileri ve animasyonları ekleyeceğiz.

### <a name="to-set-property-triggers"></a>Özellik tetikleyicilerini ayarlamak için

1. **Yeni bir özellik tetikleyicisi oluşturun:** **GlassCube** seçiliyken, **Tetikleyiciler** panelinde **+ özelliği** ' ne tıklayın (sonraki adımdan sonra gelen şekle bakın). Bu, varsayılan özellik tetikleyicisine sahip bir özellik tetikleyicisi oluşturur.

2. **Tetikleyici tarafından kullanılan özelliğin üzerinde ısmouseyapın:** Özelliği <xref:System.Windows.UIElement.IsMouseOver%2A>olarak değiştirin. Bu, <xref:System.Windows.UIElement.IsMouseOver%2A> özelliği `true` olduğunda (Kullanıcı fareyle düğmesine işaret ediyorsa) özellik tetikleyicisinin etkinleştirmesini sağlar.

    ![Bir özellik üzerinde tetikleyici ayarlama](./media/custom-button-blend-ismousedoverpropertytrigger.png)

3. **IsMouseOver, glassCube için %100 oranında opaklık tetikler:** **Tetikleyici kaydının açık** olduğuna dikkat edin (önceki şekle bakın). Bu, **glassCube** öğesinin özellik değerlerinde yaptığınız tüm değişikliklerin, <xref:System.Windows.UIElement.IsMouseOver%2A> `true`olduğunda meydana gelen bir eylem olacağı anlamına gelir. Kayıt sırasında **glassCube** <xref:System.Windows.UIElement.Opacity%2A> %100 olarak değiştirin.

    ![Bir düğmenin opaklığını ayarlama](./media/custom-button-blend-ismousedoverpropertytrigger2.gif)

    Şimdi ilk özellik tetikleyicinizi oluşturdunuz. Düzenleyicinin **Tetikleyiciler panelinin** <xref:System.Windows.UIElement.Opacity%2A> %100 olarak değiştirildiğini kaydettiğine dikkat edin.

    !["Tetikleyiciler" paneli](./media/custom-button-blend-propertytriggerinfo.png)

    F5 tuşuna basarak uygulamayı çalıştırın ve fare işaretçisini düğmenin üzerine getirin ve düğme dışına taşıyın. Düğme üzerindeyken cam katmanın göründüğünü görmeniz gerekir ve işaretçi ayrıldığında kaybolur.

4. **Imouseover Tetikleyicileri vuruş değeri değişikliği:** <xref:System.Windows.UIElement.IsMouseOver%2A> tetikleyicisiyle bazı diğer eylemleri ilişkilendirelim. Kayıt devam ederken, seçiminizi **glassCube** 'den **outerRectangle**'e geçirin. Sonra **outerRectangle** 'in <xref:System.Windows.Shapes.Shape.Stroke%2A> "{DynamicResource {X:static SystemColors. Highlightbrühkey}}" özel ifadesi olarak ayarlayın. Bu, <xref:System.Windows.Shapes.Shape.Stroke%2A> düğmeler tarafından kullanılan tipik vurgu rengine ayarlar. Düğmenin üzerine fare uyguladığınızda etkisini görmek için F5 tuşuna basın.

    ![Vurgu rengine vuruş ayarlama](./media/custom-button-blend-ismousedoverpropertytrigger3.png)

5. **Imouseover, bulanık metin tetikler:** <xref:System.Windows.UIElement.IsMouseOver%2A> Özellik tetikleyicisiyle bir daha fazla eylem ilişkilendirelim. Cam üzerinde göründüğünde düğme içeriğinin biraz bulanık görünmesini sağlayın. Bunu yapmak için, <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**) <xref:System.Windows.Media.Effects.BitmapEffect> bir bulanıklaştırma uygulayabiliriz.

    ![Bir düğmenin içeriğini bulanıklaştırma](./media/custom-button-blend-propertytriggerwithbitmapeffect.png)

    > [!NOTE]
    > <xref:System.Windows.Media.Effects.BitmapEffect>arama yapmadan önce **Özellikler panelini** geri döndürmek Için, **arama kutusundan**metni temizleyin.

    Bu noktada, fare işaretçisinin düğme alanına girdiğinde ve ayrıldığında vurgulama davranışı oluşturmak için birkaç ilişkili eylem içeren bir özellik tetikleyicisi kullandık. Bir düğme için başka bir normal davranış, odağa sahip olduğunda (tıklandıktan sonra olduğu gibi) vurgulanmalıdır. <xref:System.Windows.UIElement.IsFocused%2A> özelliği için başka bir özellik tetikleyicisi ekleyerek bu davranışı ekleyebiliriz.

6. **Isodaklanmış için özellik tetikleyicisi oluştur:** <xref:System.Windows.UIElement.IsMouseOver%2A> için aynı yordamı kullanma (Bu bölümün ilk adımına bakın), <xref:System.Windows.UIElement.IsFocused%2A> özelliği için başka bir özellik tetikleyicisi oluşturun. **Kayıt tetikleme**sırasında, tetikleyicisine aşağıdaki eylemleri ekleyin:

    - **glassCube** %100 <xref:System.Windows.UIElement.Opacity%2A> alır.

    - **outerRectangle** , "{DynamicResource {X:static SystemColors. Highlightbrühkey}}" öğesinin <xref:System.Windows.Shapes.Shape.Stroke%2A> özel ifade değerini alır.

Bu izlenecek yolun son adımında, düğmeye animasyon ekleyeceğiz. Bu animasyonlar, Olaylar (özellikle <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları tarafından tetiklenir.

### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Etkileşimli eklenecek olay tetikleyicilerini ve animasyonlarını kullanmak için

1. **Bir MouseEnter olay tetikleyicisi oluşturun:** Yeni bir olay tetikleyicisi ekleyin ve tetikleyicide kullanılacak olay olarak <xref:System.Windows.UIElement.MouseEnter> seçin.

     ![MouseEnter olay tetikleyicisi oluşturma](./media/custom-button-blend-mouseovereventtrigger.png)

2. **Animasyon zaman çizelgesi oluşturma:** Sonra, bir animasyon zaman çizelgesini <xref:System.Windows.UIElement.MouseEnter> olayla ilişkilendirin.

    ![Bir olaya animasyon zaman çizelgesi ekleme](./media/custom-button-blend-mouseovereventtrigger2.png)

    Yeni bir zaman çizelgesi oluşturmak için **Tamam** 'a bastıktan sonra, bir **zaman çizelgesi paneli** görünür ve "zaman çizelgesi kaydı açık" tasarım panelinde görünür. Bu, zaman çizelgesinde özellik değişikliklerinin kaydına başlayabileceği anlamına gelir (özellik değişikliklerine animasyon ekleme).

    > [!NOTE]
    > Ekranı görmek için pencerenizi ve/veya panellerinizi yeniden boyutlandırmanız gerekebilir.

    ![Zaman çizelgesi bölmesi](./media/custom-button-blend-mouseovereventtrigger3.png)

3. **Bir ana kare oluşturun:** Bir animasyon oluşturmak için animasyon eklemek istediğiniz nesneyi seçin, zaman çizelgesinde iki veya daha fazla ana kare oluşturun ve bu ana kareler için, animasyonun arasında enterpolalanmayı istediğiniz özellik değerlerini ayarlayın. Aşağıdaki şekil, bir ana kare oluşturma sürecinde size rehberlik eder.

    ![Ana kare oluşturma](./media/custom-button-blend-mouseovereventtrigger4.png)

4. **Bu ana karede glassCube Küçült:** İkinci ana kare seçili olarak, **glassCube** boyutunu **Boyut dönüşümünü**kullanarak tam boyutunun %90 ' una küçültün.

    ![Bir düğmenin boyutunu küçültme](./media/custom-button-blend-sizetransform.png)

    Uygulamayı çalıştırmak için F5'e basın. Fare işaretçisini düğmenin üzerine taşıyın. Cam katmanın düğmenin üstünde küçültüdiğine dikkat edin.

5. **Başka bir olay tetikleyicisi oluşturun ve onunla farklı bir animasyon ilişkilendirin:** Daha sonra bir animasyon ekleyelim. Önceki olay tetikleyicisi animasyonunu oluşturmak için kullandığınız işlemin benzer bir yordamını kullanın:

    1. <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayını kullanarak yeni bir olay tetikleyicisi oluşturun.

    2. Yeni bir zaman çizelgesini <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayla ilişkilendirin.

        ![Yeni bir zaman çizelgesi oluşturma](./media/custom-button-blend-clickeventtrigger1.png)

    3. Bu zaman çizelgesinde bir tane olmak üzere iki ana kare oluşturun, biri 0,0 saniye, ikinci ise 0,3 saniye.

    4. Ana kare 0,3 saniye vurgulanmış olarak, **dönüşümü Döndür açısını** 360 derece olarak ayarlayın.

        ![Döndürme dönüşümü oluşturma](./media/custom-button-blend-rotatetransform.gif)

    5. Uygulamayı çalıştırmak için F5'e basın. Düğmesine tıklayın. Cam katmanın etrafında dönerek göründüğünü unutmayın.

## <a name="conclusion"></a>Sonuç

Özelleştirilmiş bir düğmeyi tamamladınız. Bu, uygulamadaki tüm düğmelere uygulanan bir düğme şablonu kullanıyorsunuz. Şablon düzenlemesi modundan ayrıldıysanız (aşağıdaki şekle bakın) ve daha fazla düğme oluşturursanız, varsayılan düğme gibi özel düğmeleriniz gibi göründüğünü ve davrandığını görürsünüz.

![Özel düğme şablonu](./media/custom-button-blend-scopeup.gif)

![Aynı şablonu kullanan birden çok düğme](./media/custom-button-blend-createmultiplebuttons.png)

Uygulamayı çalıştırmak için F5'e basın. Düğmelere tıklayın ve bunların tümünün aynı davranış şeklini görürsünüz.

Şablonu özelleştirirken, **ınnerrectangle** 'ın **<xref:System.Windows.Shapes.Shape.Fill%2A> özelliğini ve <xref:System.Windows.Shapes.Shape.Stroke%2A> özelliği şablon** arka planına ({TemplateBinding background}) ayarlandığını unutmayın. Bu nedenle, ayrı düğmelerin arka plan rengini ayarladığınızda, bu ilgili özellikler için ayarladığınız arka plan kullanılacaktır. Arka planları şimdi değiştirmeyi deneyin. Aşağıdaki şekilde farklı degradeler kullanılır. Bu nedenle, bir şablon düğme gibi denetimlerin genel özelleştirmesi için yararlı olsa da, şablonlara sahip denetimler, birbirleriyle farklı görünecek şekilde değiştirilebilir.

![Aynı şablona sahip düğmeler](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")

Sonuç olarak, bir düğme şablonunu özelleştirme sürecinde, Microsoft Expression Blend 'de aşağıdakilerin nasıl yapılacağını öğrendiniz:

- Bir denetimin görünümünü özelleştirin.

- Özellik tetikleyicilerini ayarlayın. Özellik Tetikleyicileri çok faydalı olduğundan, yalnızca denetimler değil birçok nesne üzerinde kullanılabilirler.

- Olay Tetikleyicilerini ayarlayın. Olay Tetikleyicileri çok yararlı olur, çünkü yalnızca denetimler değil birçok nesne üzerinde kullanılabilirler.

- Animasyonlar oluşturun.

- Çeşitli: degradeler oluşturun, BitmapEffects ekleyin, dönüşümler kullanın ve nesnelerin temel özelliklerini ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kullanarak bir Düğme Oluşturma](walkthrough-create-a-button-by-using-xaml.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Bit Eşlem Etkilerine Genel Bakış](../graphics-multimedia/bitmap-effects-overview.md)
