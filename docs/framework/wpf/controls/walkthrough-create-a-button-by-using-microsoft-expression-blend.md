---
title: 'İzlenecek yol: Microsoft Expression Blend Kullanarak Düğme Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: bf6da0600335061e15560aabf668671a24d8911d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502254"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>İzlenecek yol: Microsoft Expression Blend Kullanarak Düğme Oluşturma
Bu izlenecek yol, oluşturma işleminde size yol gösterir bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Microsoft Expression Blend kullanarak özelleştirilmiş düğmesi.  
  
> [!IMPORTANT]
>  Microsoft Expression Blend çalışır oluşturarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , ardından derlenmiş yürütülebilir program yapma. Bunun yerine ile işe yarar, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] doğrudan bir kullanmakla aynı uygulamayı oluşturan başka bir gözden geçirme yok [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Blend yerine Visual Studio ile. Bkz: [tarafından XAML kullanarak bir düğme oluşturma](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md) daha fazla bilgi için.  
  
 Aşağıdaki çizimde özelleştirilmiş bir düğme, oluşturacağınız gösterilir.  
  
 ![Oluşturacağınız özelleştirilmiş bir düğme](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Bir düğmeye bir şekle Dönüştür  
 Bu kılavuzun ilk bölümünde özel düğme özel görünüşünü oluşturun. Bunu yapmak için önce bir düğmeye bir dikdörtgen dönüştürmeniz gerekir. Ardından ek şekiller düğmenin şablonuna daha karmaşık görünen bir düğme oluşturma eklersiniz. Neden normal bir düğme ile çalışmaya başlayabilir ve özelleştirilmelidir? Gereksinim duymadığınız yerleşik işlevleri bir düğme olduğu için; özel düğmeler için bir dikdörtgen ile başlamak kolaydır.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Expression Blend içinde yeni bir proje oluşturmak için  
  
1.  Expression Blend başlatın. (Tıklayın **Başlat**, işaret **tüm programlar**, işaret **Microsoft Expression**ve ardından **Microsoft Expression Blend**.)  
  
2.  Uygulama gerekirse en üst düzeye çıkarın.  
  
3.  Üzerinde **dosya** menüsünü tıklatın **yeni proje**.  
  
4.  Seçin **standart uygulaması (.exe)**.  
  
5.  Projeyi adlandırın `CustomButton` basın **Tamam**.  
  
 Bu noktada, boş bir sahip [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] proje. Uygulamayı çalıştırmak için F5 tuşuna basabilirsiniz. Bekleyebileceğiniz gibi uygulamayı yalnızca boş bir pencerenin oluşur. Ardından, bir Yuvarlatılmış Dikdörtgen oluşturur ve bir düğme Dönüştür.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Bir düğmeye bir dikdörtgen dönüştürmek için  
  
1.  **Pencere arkaplanı özelliği siyah olarak ayarlayın:** Pencerenin seçin, **Özellikleri sekmesi**, ayarlayıp <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Black`.  
  
     ![Bir düğmenin arka planı siyah olarak ayarlamak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2.  **Yaklaşık bir düğme boyutunu dikdörtgen penceresinde çizme:** Sol taraftaki araç panelde dikdörtgen Aracı'nı seçin ve dikdörtgen pencerenin sürükleyin.  
  
     ![Bir dikdörtgen çizmek nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3.  **Dikdörtgenin köşelerini yuvarlatmak:** Dikdörtgenin kontrol noktalarını sürükleyin ya da doğrudan ayarlayın <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri. Değerlerini ayarlayın <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 20.  
  
     ![Dikdörtgenin köşelerini yuvarlar hale getirme](../../../../docs/framework/wpf/controls/media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4.  **Bir düğme dikdörtgenin değiştirin:** Dikdörtgeni seçin. Üzerinde **Araçları** menüsünde tıklatın **olun düğmesi**.  
  
     ![Bir şekil bir düğme oluşturmak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5.  **Stil/şablonu kapsamını belirtin:** Aşağıdaki gibi bir iletişim kutusu görüntülenir.  
  
     !["Stil kaynağı oluştur" iletişim kutusu](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     İçin **kaynak adı (anahtar)** seçin **tümüne uygula**.  Bu, sonuçta elde edilen stil ve düğmeleri olan tüm nesneler için geçerli bir düğme şablonunun yapar. İçin **tanımlamak**seçin **uygulama**. Bu, elde edilen stil ve düğme şablonunu uygulamanın tamamı kapsama sahip olmanızı sağlar. Bu iki kutularında değerleri ayarlamak, tüm uygulama içindeki tüm düğmeler düğmeye stil ve şablon uygulamak ve uygulama içinde oluşturduğunuz her düğme, varsayılan olarak, bu şablonu kullanın.  
  
## <a name="edit-the-button-template"></a>Düğme şablonunu Düzenle  
 Artık bir düğme değiştirildi bir dikdörtgen var. Bu bölümde, düğmenin şablonun değiştirmek ve nasıl göründüğüne özelleştirin.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Düğme görünümünü değiştirmek için düğme şablonunu düzenlemek için  
  
1.  **Düzenleme şablonu görünüme gidin:** Daha fazla düğmemizin görünümünü özelleştirmek için düğme şablonunu düzenlemek ihtiyacımız var. Bu şablon, biz bir düğme dikdörtgenin dönüştürüldüğünde oluşturuldu. Düğme şablonunu düzenlemek için düğme sağ tıklayıp **denetim bölümlerini (şablon) Düzenle** ardından **şablonu Düzen**.  
  
     ![Şablon düzenleme](../../../../docs/framework/wpf/controls/media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     Şablonu Düzenleyicisi'nde düğmesi artık ayrılır, dikkat edin. bir <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Controls.ContentPresenter>. <xref:System.Windows.Controls.ContentPresenter> (Örneğin, "Button" dizesi) düğmesi içinde içerik sunmak için kullanılır. Her iki dikdörtgen ve <xref:System.Windows.Controls.ContentPresenter> içine yerleştirilir bir <xref:System.Windows.Controls.Grid>.  
  
     ![Belirli bir dikdörtgen bileşenlerde](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2.  **Şablonu bileşenleri adlarını değiştirin:** Değişiklik şablon stoktaki dikdörtgen sağ <xref:System.Windows.Shapes.Rectangle> "outerRectangle için" ad "[dikdörtgenden]" ve "myContentPresenter" için "[ContentPresenter]" değiştirin.  
  
     ![Bir bileşeni olan bir şablonu yeniden adlandırma](../../../../docs/framework/wpf/controls/media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3.  **Boş (halka gibi) içinde dikdörtgen değiştirin:** Seçin **outerRectangle** ayarlayıp <xref:System.Windows.Shapes.Shape.Fill%2A> "Saydam" ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 5.  
  
     ![Bir dikdörtgen boş hale getirme](../../../../docs/framework/wpf/controls/media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Ardından <xref:System.Windows.Shapes.Shape.Stroke%2A> ne olursa olsun şablonu olacaksa, renk. Bunu yapmak için küçük beyaz yanındaki kutusu **vuruş**seçin **CustomExpression**ve "{TemplateBinding arka plan}" iletişim kutusuna yazın.  
  
     ![Kullanımı şablon rengini ayarlama](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4.  **Bir iç dikdörtgen oluşturun:** Şimdi başka bir dikdörtgen oluşturun (bunu adı "innerRectangle") ve içi simetrik olarak konumlandırın **outerRectangle** . Bu iş türü için büyük olasılıkla düğmesi düzenleme alanı büyütmek için yakınlaştırma isteyeceksiniz.  
  
    > [!NOTE]
    >  Dikdörtgen, farklı şekilde görünebilir (örneğin, yuvarlak köşeler olacak).  
  
     ![İçinde başka bir dikdörtgen bir dikdörtgen oluşturma](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5.  **ContentPresenter en üste Taşı:** Bu noktada, "Button" metin artık görünür olmaz, mümkündür. Bu durumda, bunun nedeni, **innerRectangle** üstünde olan **myContentPresenter**. Bu sorunu gidermek için sürükleyin **myContentPresenter** aşağıda **innerRectangle**. Dikdörtgenler yeniden konumlandırma ve **myContentPresenter** aşağıdakine benzer şekilde.  
  
    > [!NOTE]
    >  Alternatif olarak, aynı zamanda yerleştirebilir **myContentPresenter** tıklayıp tuşuna basarak üstte **İleri Gönder**.  
  
     ![Başka bir düğme üzerine bir düğme nasıl taşırım](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6.  **İnnerRectangle görünümünü değiştirin:** Ayarlama <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 20 değerleri. İn addition, ayarlamak <xref:System.Windows.Shapes.Shape.Fill%2A> arka planını kullanarak özel ifade "{TemplateBinding arka plan}" şablonu için) ve <xref:System.Windows.Shapes.Shape.Stroke%2A> "saydam". Dikkat ayarlarını <xref:System.Windows.Shapes.Shape.Fill%2A> ve <xref:System.Windows.Shapes.Shape.Stroke%2A> , **innerRectangle** olanlar için karşıtı olduğu **outerRectangle**.  
  
     ![Bir dikdörtgen görünümünü değiştirmek nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7.  **Cam katman üstte ekleyin:** Düğmenin görünümünü özelleştirme son parçası, en üstte bir cam katmanı eklemektir. Bu cam katman üçüncü bir dikdörtgen oluşur. Cam tüm düğmenin ele alınacaktır, cam dikdörtgeni içinde boyutları benzer çünkü **outerRectangle**. Bu nedenle, bir kopyasını yaparak dikdörtgen oluşturma **outerRectangle**. Vurgulama **outerRectangle** bir kopyasını oluşturmak için CTRL + C ve CTRL + V kullanın. Bu yeni dikdörtgen "glassCube" olarak adlandırın.  
  
8.  **GlassCube gerekirse yeniden konumlandır:** Varsa **glassCube** olan tüm düğmesini kullanabilirsiniz, böylece henüz konumlandırılmış, istediğiniz konuma sürükleyin.  
  
9. **GlassCube outerRectangle değerinden biraz daha farklı bir şekil sağlar:** Özelliklerini değiştirmek **glassCube**. Değiştirerek başlayın <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 10 özellikleri ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 2.  
  
     ![Görünüm ayarlarını glassCube](../../../../docs/framework/wpf/controls/media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Cam gibi ara glassCube olun:** Ayarlama <xref:System.Windows.Shapes.Shape.Fill%2A> % 75 opak ve rengini beyaz ve saydam arasında 6 yaklaşık olarak eşit diğerleri doğrusal gradyan aralıklı aralıkları kullanarak glassy arama konumu. Gradyan duraklarının ayarlamak gerekenler budur:  
  
    -   Gradyan durağını 1: % 75'ini alfa değerine sahip beyaz  
  
    -   Gradyan durağını 2: Geçirgen  
  
    -   Gradyan durağını 3: % 75'ini alfa değerine sahip beyaz  
  
    -   Gradyan durağını 4: Geçirgen  
  
    -   Gradyan durağını 5: % 75'ini alfa değerine sahip beyaz  
  
    -   Gradyan durağını 6: Geçirgen  
  
     Bu, "dalgalı" Acil Durum görünümünü oluşturur.  
  
     ![Cam gibi görünen bir dikdörtgen](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Cam katmanı Gizle:** Glassy katman nasıl göründüğüne bakın, kısımlarda **görünümü bölmesinde** , **özellikler panelini** ve için %0 gizlemek için saydamlığı ayarlayın. Bölümlerde önceden, özellik Tetikleyicileri ve olayları göstermek ve cam katman işlemek için kullanacağız.  
  
     ![Cam dikdörtgeni gizleme](../../../../docs/framework/wpf/controls/media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Düğme davranışını özelleştirme  
 Bu noktada, düğmeyi sunumu şablonunu düzenleyerek özelleştirdiğiniz ancak düğme tipik düğmeleri yapın (örneğin, fare bekletme temel görünümünü değiştirme, odak alma ve tıklayarak.) kullanıcı eylemlerine tepki vermez Sonraki iki yordamlar nasıl oluşturacağınızı bu özel düğme gibi davranışları gösterir. Biz basit özellik tetikleyicileri ile başlatın ve ardından olay tetikleyicilerini ve animasyonlar ekleyebilirsiniz.  
  
#### <a name="to-set-property-triggers"></a>Özellik tetikleyicileri ayarlamak için  
  
1.  **Yeni bir özellik tetikleyicisi oluşturun:** İle **glassCube** seçili tıklayın **+ özelliği** içinde **Tetikleyicileri** paneli (sonraki adım aşağıdaki şekle bakın). Bu, varsayılan özellik tetikleyicisi ile bir özellik tetikleyicisi oluşturur.  
  
2.  **Tetik tarafından kullanılan özellik IsMouseOver olun:** Özelliğini değiştirmek <xref:System.Windows.UIElement.IsMouseOver%2A>. Bu özellik tetikleyicisi etkinleştirin sağlar <xref:System.Windows.UIElement.IsMouseOver%2A> özelliği `true` (ne zaman kullanıcı işaret fare düğmesi).  
  
     ![Bir tetikleyici bir özellik ayarlama](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3.  **Opaklık glassCube için % 100 IsMouseOver tetikleyen:** Dikkat **tetikleyici kayıt açıktır** (önceki şekilde bakın). Özellik değerleri, yaptığınız değişiklikleri buna **glassCube** olduğunda gerçekleşir, bir eylem kaydı açıkken olacak <xref:System.Windows.UIElement.IsMouseOver%2A> olduğu `true`. Kayıt sırasında değiştirme <xref:System.Windows.UIElement.Opacity%2A> , **glassCube** % 100.  
  
     ![Bir düğme opaklığını ayarlama](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     İlk özellik tetikleyicinize oluşturdunuz. Dikkat **Tetikleyicileri paneli** düzenleyiciyi kaydettiği <xref:System.Windows.UIElement.Opacity%2A> % 100 olarak değiştiriliyor.  
  
     !["Tetikleyici" paneli](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Uygulamayı çalıştırmak ve fareyi üzerine ve kapama düğmesi taşımak için F5 tuşuna basın. Görünür cam katman görmelisiniz, düğmenin fare bekletme ve de işaretçi çıktığında kaybolur.  
  
4.  **IsMouseOver Tetikleyicileri vuruş yapmak değeri değiştirin:** Şimdi başka bazı eylemler ilişkilendirmek <xref:System.Windows.UIElement.IsMouseOver%2A> tetikleyici. Kaydı devam ederken seçiminizden geçiş **glassCube** için **outerRectangle**. Ardından <xref:System.Windows.Shapes.Shape.Stroke%2A> , **outerRectangle** özel ifade, "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}". Bu ayarlar <xref:System.Windows.Shapes.Shape.Stroke%2A> tipik düğmeler tarafından kullanılan rengi vurgulayın. Düğmenin üzerine fare imlecinizle etkisini görmek için F5 tuşuna basın.  
  
     ![Vurgu renginin vuruş ayarlama](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5.  **IsMouseOver bulanık metin tetikleyen:** Şimdi bir daha fazla eyleme ilişkilendirmek <xref:System.Windows.UIElement.IsMouseOver%2A> özellik tetikleyicisi. Düğme içeriğini cam göründüğünde biraz bulanık olun. Bunu yapmak için biz Bulanıklaştırma uygulayabilirsiniz <xref:System.Windows.Media.Effects.BitmapEffect> için <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Bir düğme içeriğini Bulanıklaştırma](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Döndürülecek **özellikler panelini** BT'nin için geri arama yaptığınız önce olan <xref:System.Windows.Media.Effects.BitmapEffect>, metni temizleyin **arama kutusuna**.  
  
     Bu noktada, biz bir özellik tetikleyicisi birkaç ilişkili eylem fare işaretçisi girer ve düğme alanının bırakır vurgulama davranışı oluşturmak için kullanılan. Başka bir tipik bir düğmenin odağa sahip olduğunda vurgulamak için bir davranıştır (gibi tıklandığı sonra). Benzer bir davranış için başka bir özellik tetikleyicisi ekleyerek ekleyebiliriz <xref:System.Windows.UIElement.IsFocused%2A> özelliği.  
  
6.  **Özellik tetikleyicisi için IsFocused oluşturun:** Olarak için aynı yordamı kullanarak <xref:System.Windows.UIElement.IsMouseOver%2A> (Bu bölümün ilk adımı bakın), başka bir özellik tetikleyicisi için oluşturma <xref:System.Windows.UIElement.IsFocused%2A> özelliği. Sırada **tetikleyici kayıt açıktır**, aşağıdaki eylemleri tetikleyiciyi ekleyin:  
  
    -   **glassCube** alır bir <xref:System.Windows.UIElement.Opacity%2A> % 100.  
  
    -   **outerRectangle** alır bir <xref:System.Windows.Shapes.Shape.Stroke%2A> özel ifade değeri, "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}".  
  
 Bu kılavuzdaki son adım olarak düğmeye animasyon ekleyeceğiz. Animasyonlarına olaylar tarafından tetiklenen — özellikle <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Olay tetikleyicileri kullanma ve animasyon, etkileşim eklemek için  
  
1.  **MouseEnter olay tetikleyicisi oluşturun:** Yeni bir olay tetikleyicisi ekleyin ve seçin <xref:System.Windows.UIElement.MouseEnter> tetikleyiciyi kullanan etkinlik olarak.  
  
     ![MouseEnter olay tetikleyicisi oluşturmak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2.  **Bir animasyon zaman çizelgesini oluşturun:** Ardından, bir animasyon zaman çizelgesi için ilişkilendirme <xref:System.Windows.UIElement.MouseEnter> olay.  
  
     ![Bir olay için bir animasyon zaman çizelgesini ekleme](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Tuşuna bastıktan sonra **Tamam** yeni bir zaman çizelgesi oluşturmak için bir **zaman çizelgesi paneli** görünür ve "zaman çizelgesi kaydı açıktır" tasarım panelinde görünür. Başka bir deyişle, biz özellik değişiklikleri (Canlandır özellik değişiklikleri) zaman çizelgesinde kaydı başlatın.  
  
    > [!NOTE]
    >  Pencere ve/veya görüntüyü görmek için paneller yeniden boyutlandırmak gerekebilir.  
  
     ![Zaman Çizelgesi paneli](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3.  **Bir ana kare oluşturun:** Bir animasyon oluşturmak için animasyon, iki veya daha fazla ana kareleri zaman çizelgesi üzerinde bu ana kareleri oluşturun, ayarlanan özellik değerleri arasında enterpolasyon için animasyon istediğiniz nesneyi seçin. Aşağıdaki şekilde, bir ana kare oluşturulmasını size yol gösterir.  
  
     ![Bir ana kare oluşturma](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4.  **Bu ana kare, glassCube Daralt:** Seçilen ikinci ana kare ile boyutunu küçültmek **glassCube** tam boyutlu kullanarak % 90 **boyutu dönüştürme**.  
  
     ![Düğmenin boyutunu küçültme](../../../../docs/framework/wpf/controls/media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Uygulamayı çalıştırmak için F5'e basın. Fare işaretçisi düğmenin üzerine taşıyın. Cam katman düğmenin üzerine küçüldüğünü dikkat edin.  
  
5.  **Başka bir olay tetikleyicisi oluşturmak ve farklı bir animasyon ilişkilendirin:** Daha fazla bir animasyon ekleyelim. İçin önceki olay tetikleyicisi animasyon oluşturmak için kullanılan benzer bir yordamı kullanın:  
  
    1.  Kullanarak yeni bir olay tetikleyicisi oluşturmak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
    2.  Yeni bir zaman çizelgesi ile ilişkilendirmek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
     ![Yeni bir zaman çizelgesi oluşturma](../../../../docs/framework/wpf/controls/media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1.  Bu zaman çizelgesi için iki ana kare, 0.0 saniye, diğeri ikinci 0,3 saniye oluşturun.  
  
    2.  İle vurgulanmış 0,3 saniye, ayarlanan **dönüştürme açı döndürme** 360 derece için.  
  
     ![Döndürme dönüşümü oluşturmak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1.  Uygulamayı çalıştırmak için F5'e basın. Düğmesine tıklayın. Cam katman etrafında dönerek dikkat edin.  
  
## <a name="conclusion"></a>Sonuç  
 Özelleştirilmiş bir düğme tamamladınız. Bu uygulamadaki tüm düğmelerin uygulandığı bir düğme şablonunu kullanarak yaptığınız. Şablon düzenleme modunda bırakırsanız (Aşağıdaki şekle bakın) ve daha fazla düğme oluşturmak, arayın ve özel düğmenizin gibi yerine varsayılan düğme gibi davranan görürsünüz.  
  
 ![Özel düğme şablonunun](../../../../docs/framework/wpf/controls/media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Aynı şablonu kullanan birden çok düğmeleri](../../../../docs/framework/wpf/controls/media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Uygulamayı çalıştırmak için F5'e basın. Bu düğmeleri tıklatabilir ve bunların tümü aynı nasıl davranacağını dikkat edin.  
  
 Şablonu özelleştirme, ancak ayarladığınız unutmayın <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği **innerRectangle** ve <xref:System.Windows.Shapes.Shape.Stroke%2A> özelliği **outerRectangle** ({şablon arka plan TemplateBinding arka}). Düğmelerin, arka plan rengini ayarladığınızda, bu nedenle, bu ilgili özellikler için ayarladığınız arka plan kullanılır. Arka planları artık değiştirmeyi deneyin. Aşağıdaki resimde, farklı gradyanlar kullanılır. Bu nedenle, bir şablon genel özelleştirme düğmesi gibi denetimleri için kullanışlı olsa da, denetim şablonları ile hala birbirinden farklı aramak için değiştirilebilir.  
  
 ![Aynı şablonun farklı konum düğmeleriyle](../../../../docs/framework/wpf/controls/media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Conclusion, bir düğme şablonunu özelleştirme sürecinde, Microsoft Expression Blend içinde aşağıdakileri gerçekleştirmeyi öğrendiniz:  
  
-   Bir denetimin görünümünü özelleştirebilirsiniz.  
  
-   Özellik tetikleyicileri ayarlayın. Özellik tetikleyicileri, çoğu nesneler üzerinde tam denetim kullanılabildiğinden çok yararlı olur.  
  
-   Olay tetikleyicileri ayarlayın. Çoğu nesneler üzerinde tam denetim kullanılabildiğinden olay tetikleyicilerini çok yararlı olur.  
  
-   Animasyonlar oluşturun.  
  
-   Çeşitli: gradyan, oluşturun, BitmapEffects ekleyin, dönüşümler kullanma ve nesnelerin temel özelliklerini ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML Kullanarak bir Düğme Oluşturma](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Bit Eşlem Etkilerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
