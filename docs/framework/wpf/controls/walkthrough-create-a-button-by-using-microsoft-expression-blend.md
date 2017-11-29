---
title: "İzlenecek yol: Microsoft Expression Blend Kullanarak Düğme Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1371fdc3582e2ebe052442b15ecb2d5cf0b2865a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>İzlenecek yol: Microsoft Expression Blend Kullanarak Düğme Oluşturma
Bu kılavuzda oluşturma işleminde size adımlar bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Microsoft Expression Blend kullanarak özelleştirilmiş düğmesi.  
  
> [!IMPORTANT]
>  Microsoft Expression Blend çalışır oluşturarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , sonra derlenmiş bir yürütülebilir programı yapma. Bunun yerine ile çalışır, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] doğrudan bu kullanarak bir tane olarak aynı uygulamayı oluşturan başka bir gözden geçirme yok [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ile [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] karışım yerine. Bkz: [bir düğme kullanarak XAML tarafından oluşturmak](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md) daha fazla bilgi için.  
  
 Aşağıdaki çizimde, oluşturacağınız özelleştirilmiş düğmesini gösterir.  
  
 ![Oluşturacağınız özelleştirilmiş düğme](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Bir şekli bir düğmeye Dönüştür  
 Bu kılavuzun ilk bölümünde özel düğme özel görünümünü oluşturun. Bunu yapmak için öncelikle bir düğmeye dikdörtgen dönüştürmeniz gerekir. Ardından ek şekiller düğmesi şablonu için daha karmaşık bir görünümlü düğmesi oluşturma ekleyin. Neden normal düğmesi ile başlayıp özelleştirin mi? Bir düğme ihtiyacınız olmayan yerleşik bir işleve sahiptir çünkü; özel düğmeler için bir dikdörtgen başlatmak daha kolay olur.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Expression Blend yeni bir proje oluşturmak için  
  
1.  Expression Blend başlatın. (Tıklatın **Başlat**, işaret **tüm programlar**, işaret **Microsoft Expression**ve ardından **Microsoft Expression Blend**.)  
  
2.  Uygulama gerekirse ekranı kaplamasını sağlayın.  
  
3.  Üzerinde **dosya** menüsünde tıklatın **yeni proje**.  
  
4.  Seçin **standart uygulama (.exe)**.  
  
5.  Proje adı `CustomButton` ve basın **Tamam**.  
  
 Bu noktada boş sahip [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projesi. Uygulamayı çalıştırmak için F5 tuşuna basabilirsiniz. Beklediğiniz gibi uygulama yalnızca boş bir pencere oluşur. Ardından, yuvarlak dikdörtgen oluşturmak ve bir düğme dönüştürün.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Dikdörtgen bir düğmeye dönüştürmek için  
  
1.  **Siyah penceresi arka plan özelliğini ayarlayın:** penceresi seçin, **özellikler sekmesi**ve <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Black`.  
  
     ![Siyah bir düğmenin arka planını ayarlama](../../../../docs/framework/wpf/controls/media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2.  **Penceresinde yaklaşık bir düğme boyutunu dikdörtgen çizmek:** sol aracı panelindeki Dikdörtgen aracını seçin ve dikdörtgen penceresi sürükleyin.  
  
     ![Dikdörtgen çizmek nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3.  **Yuvarlak dikdörtgen köşelerinde çıkışı:** dikdörtgenin kontrol noktalarını sürükleyin ya da doğrudan ayarlayın <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri. Değerlerini ayarlamak <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 20.  
  
     ![Dikdörtgene köşelerinde yuvarlak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4.  **Dikdörtgen bir düğmesinde değiştirme:** dikdörtgen seçin. Üzerinde **Araçları** menüsünde tıklatın **olun düğmesi**.  
  
     ![Bir şekli bir düğme nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5.  **Stil/şablonu kapsamını belirtin:** aşağıdaki belirir gibi bir iletişim kutusu.  
  
     !["Stil kaynağı oluştur" iletişim kutusu](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     İçin **kaynak adı (anahtar)**seçin **tümüne uygula**.  Bu, sonuçta elde edilen stil ve düğmeler tüm nesnelere Uygula düğmesini şablon hale getirir. İçin **tanımlayın**seçin **uygulama**. Bu, sonuçta elde edilen stil ve tüm uygulama kapsama sahip düğmesi şablon hale getirir. Bu iki kutularında değerleri ayarlayın, tüm uygulama içindeki tüm düğmeleri düğme stili ve şablonu uygulamak ve uygulamada oluşturduğunuz her düğme, varsayılan olarak, bu şablonu kullanın.  
  
## <a name="edit-the-button-template"></a>Düğme şablonunu düzenleyin.  
 Artık bir düğmeye değiştirilmiş bir dikdörtgen var. Bu bölümde, şablonu düğmesinin değiştirmek ve nasıl göründüğünü özelleştirin.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Düğme görünümünü değiştirmek için düğme şablonu düzenlemek için  
  
1.  **Düzen şablonu gelsin gidin:** daha fazla bizim düğmesi görünümünü özelleştirmek için düğme şablonu düzenlemek ihtiyacımız. Bu şablon, biz dikdörtgen bir düğmesinde dönüştürüldüğünde oluşturuldu. Düğme şablonunun düzenlemek için düğmeyi sağ tıklatın ve seçin **Düzenle denetim bölümleri (şablonu)** ve ardından **Şablonu Düzenle**.  
  
     ![Bir şablonu düzenlemek nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     Düğme içine şimdi ayrılır Şablon Düzenleyicisi'nde fark bir <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Controls.ContentPresenter>. <xref:System.Windows.Controls.ContentPresenter> İçeriği (örneğin, "Button" dizesi) düğmesini içinde sunmak üzere kullanılır. Her iki dikdörtgen ve <xref:System.Windows.Controls.ContentPresenter> içine düzenlenmiştir bir <xref:System.Windows.Controls.Grid>.  
  
     ![Dikdörtgene sunumu bileşenlerinde](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2.  **Şablon bileşenleri adlarını değiştirmek:** şablonu stok, değişiklik dikdörtgende sağ <xref:System.Windows.Shapes.Rectangle> adı "[dikdörtgen]" "outerRectangle" ve "myContentPresenter" "[ContentPresenter]" değiştirin.  
  
     ![Şablonun bileşenini yeniden adlandırmak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3.  **Böylece (halka gibi) boş içinde dikdörtgen alter:** seçin **outerRectangle** ve <xref:System.Windows.Shapes.Shape.Fill%2A> "Saydam" ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 5.  
  
     ![Dikdörtgene boş nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Ardından <xref:System.Windows.Shapes.Shape.Stroke%2A> ne olursa olsun şablon olacaktır rengini için. Bunu yapmak için küçük beyaz kutunun yanındaki tıklatın **vuruş**seçin **CustomExpression**ve "{TemplateBinding arka plan}" iletişim kutusuna yazın.  
  
     ![Kullanım şablon rengini ayarlamak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4.  **Bir iç dikdörtgen oluşturun:** şimdi, başka bir dikdörtgen oluşturun ("innerRectangle" adı) ve simetrik iç Yerleştir **outerRectangle** . Bu iş türü için muhtemelen düğmesi düzenleme alanında büyütmek için yakınlaştırma istersiniz.  
  
    > [!NOTE]
    >  Dikdörtgen farklı bir şekilde görünebilir (örneğin, bunu Köşeleri Yuvarlanmış).  
  
     ![Başka bir dikdörtgen dikdörtgende oluşturma](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5.  **ContentPresenter en üstüne taşıyın:** bu noktada, "Button" metin artık görünür olmayacağını mümkündür. Bu durumda, bunun nedeni, **innerRectangle** üstünde olduğu **myContentPresenter**. Bu sorunu gidermek için sürükleyin **myContentPresenter** aşağıda **innerRectangle**. Dikdörtgenler yeniden konumlandırma ve **myContentPresenter** aşağıda benzer.  
  
    > [!NOTE]
    >  Alternatif olarak, aynı zamanda yerleştirebilir **myContentPresenter** sağ ve tuşlarına basarak üstte **İleri Gönder**.  
  
     ![Başka bir düğme en üstünde bir düğme taşıma](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6.  **İnnerRectangle görünümünü değiştirme:** ayarlamak <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 20 değerleri. İn addition, ayarlamak <xref:System.Windows.Shapes.Shape.Fill%2A> "{TemplateBinding arka plan}" Özel ifade kullanılarak şablon arka planı için) ve <xref:System.Windows.Shapes.Shape.Stroke%2A> "saydam". Dikkat ayarlarını <xref:System.Windows.Shapes.Shape.Fill%2A> ve <xref:System.Windows.Shapes.Shape.Stroke%2A> , **innerRectangle** için olanlar karşıtı olan **outerRectangle**.  
  
     ![Dikdörtgene görünümünü değiştirmek nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7.  **En üstte bir cam katman ekleyin:** düğmenin görünümünü özelleştirme son parçası üstte cam katman eklemektir. Bu cam katman üçüncü bir dikdörtgen oluşur. Cam tüm düğmenin ele alınacaktır çünkü Cam Dikdörtgen boyutları için de benzer **outerRectangle**. Bu nedenle, yalnızca bir kopyasını oluşturarak dikdörtgen oluşturmak **outerRectangle**. Vurgula **outerRectangle** ve bir kopya yapmak için CTRL + C ve CTRL + V kullanın. Bu yeni dikdörtgen "glassCube" olarak adlandırın.  
  
8.  **Gerekirse glassCube yeniden konumlandırmak:** varsa **glassCube** olan tüm düğmenin kapsayan şekilde henüz yerleştirilmiş, yerine sürükleyin.  
  
9. **GlassCube outerRectangle değerinden biraz daha farklı bir şekli verin:** özelliklerini değiştirme **glassCube**. Başlangıçta değiştirerek <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 10 özellikleri ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 2.  
  
     ![GlassCube için Görünüm ayarları](../../../../docs/framework/wpf/controls/media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Cam gibi ara glassCube olun:** ayarlamak <xref:System.Windows.Shapes.Shape.Fill%2A> % 75 opak ve rengi beyaz arasında saydam 6 yaklaşık eşit diğerleri doğrusal gradyan kullanarak glassy bir görünüm için aralıkları aralarına aralık. Bu gradyan durakları ayarlamak için Yenilikler:  
  
    -   Gradyan durağının 1: Beyaz %75 alfa değeri ile  
  
    -   Gradyan durdurun 2: saydam  
  
    -   Gradyan durağının 3: Beyaz %75 alfa değeri ile  
  
    -   Gradyan Durdur 4: saydam  
  
    -   Gradyan durağının 5: Beyaz %75 alfa değeri ile  
  
    -   Gradyan Durdur 6: saydam  
  
     Bu, bir "dalgalı" cam görünüm oluşturur.  
  
     ![Cam gibi görünen bir dikdörtgen](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Cam katmanı gizleyin:** glassy katman nasıl göründüğünü görmek, yerleştirilmesini **Görünüm bölmesi** , **özellikleri paneli** ve opaklık % saklamak için 0 olarak ayarlayın. Bölümlerde şimdi, özellik tetikleyiciler ve olayları Göster ve cam katman işlemek için kullanacağız.  
  
     ![Cam dikdörtgeni gizleme](../../../../docs/framework/wpf/controls/media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Düğme davranışını özelleştirme  
 Bu noktada, kendi şablonu düzenleyerek düğmesi sunumu özelleştirdikten ancak düğmesi tipik düğmeleri yapın (örneğin, fare üzerinden bağlı görünümünü değiştirme, odak alması ve tıklayarak) kullanıcı eylemlerine tepki vermez Sonraki iki yordamlar bunları özel düğme gibi davranışlar nasıl oluşturulacağını gösterir. Biz olan basit özellik tetikleyici başlatmak ve olay tetikleyicileri ve animasyonları ekleyin.  
  
#### <a name="to-set-property-triggers"></a>Özellik tetikleyicileri ayarlamak için  
  
1.  **Yeni bir özellik tetikleyici oluşturma:** ile **glassCube** seçili tıklatın **+ özelliği** içinde **Tetikleyicileri** paneli (sonraki adım aşağıdaki şekle bakın). Bu özellik tetikleyici ile varsayılan özellik tetikleyici oluşturur.  
  
2.  **Tetik tarafından kullanılan özellik IsMouseOver olun:** özelliğini değiştirmek <xref:System.Windows.UIElement.IsMouseOver%2A>. Bu özellik tetikleyici etkinleştirin yapar <xref:System.Windows.UIElement.IsMouseOver%2A> özelliği `true` (zaman kullanıcı noktaları fareyle düğmesine).  
  
     ![Bir tetikleyici bir özellik kümesi nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3.  **IsMouseOver tetikler glassCube için % 100 geçirgenliğini:** dikkat **tetikleyici kaydını açıktır** (önceki şekil bakın). Bu özellik değerleri yaptığınız tüm değişiklikler anlamına **glassCube** kaydı açıkken zaman gerçekleşir, bir eylem olacak <xref:System.Windows.UIElement.IsMouseOver%2A> olan `true`. Kayıt sırasında değiştirme <xref:System.Windows.UIElement.Opacity%2A> , **glassCube** % 100.  
  
     ![Düğmenin geçirgenliğini ayarlama](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     İlk özellik tetikleyici oluşturdunuz. Dikkat **Tetikleyicileri paneli** Düzenleyicisi kaydettiği <xref:System.Windows.UIElement.Opacity%2A> % 100 olarak değiştiriliyor.  
  
     !["Tetikleyiciler" paneli](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Uygulamayı çalıştırın ve fare işaretçisini üzerinden ve kapama düğmesi taşımak için F5 tuşuna basın. Ne zaman görünür cam katman görmeniz gerekir, fare üzerinde düğmesi ve de işaretçi ayrıldığında kaybolur.  
  
4.  **IsMouseOver Tetikleyicileri vuruş değeri değişikliği:** şirketinizdeki başka bazı eylemler ilişkilendirmek <xref:System.Windows.UIElement.IsMouseOver%2A> tetikleyici. Seçiminizden kaydı devam ederken, geçiş **glassCube** için **outerRectangle**. Ardından <xref:System.Windows.Shapes.Shape.Stroke%2A> , **outerRectangle** "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}" özel bir ifade için. Bu ayarlar <xref:System.Windows.Shapes.Shape.Stroke%2A> tipik için düğmeler tarafından kullanılan rengi vurgulayın. Düğmenin üzerinde fare zaman etkisini görmek için F5 tuşuna basın.  
  
     ![Vurgulama renk vuruşun ayarlamak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5.  **IsMouseOver tetikler bulanık metin:** şimdi ilişkilendirmek için daha fazla eylem <xref:System.Windows.UIElement.IsMouseOver%2A> özellik tetikleyici. Düğmenin içeriğini cam üzerinde göründüğünde biraz bulanık olun. Bunu yapmak için biz Bulanıklaştırma uygulayabilirsiniz <xref:System.Windows.Media.Effects.BitmapEffect> için <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Düğme içeriğini ölçeklendirilmelidir nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Döndürülecek **özellikleri paneli** BT'nin geri araması için yaptığınız önce oldu <xref:System.Windows.Media.Effects.BitmapEffect>, metinden temizleyin **arama kutusu**.  
  
     Bu noktada, biz özellik tetikleyici birkaç ilişkili eylem fare işaretçisini girer ve düğme alanının çıktığında vurgulama davranışını oluşturmak için kullanılan. Başka bir tipik bir düğme odağa sahip olduğunda vurgulamak için davranıştır (gibi tıklatıldığında sonra). Bu tür davranış için başka bir özellik tetikleyici ekleyerek ekleyebiliriz <xref:System.Windows.UIElement.IsFocused%2A> özelliği.  
  
6.  **Özellik tetikleyici için IsFocused oluşturun:** olarak için aynı yordamı kullanarak <xref:System.Windows.UIElement.IsMouseOver%2A> (ilk adım, bu bölümün bakın) oluşturmak için başka bir özellik tetikleyici <xref:System.Windows.UIElement.IsFocused%2A> özelliği. Sırada **tetikleyici kaydını açıktır**, aşağıdaki eylemleri tetikleyiciye ekleyin:  
  
    -   **glassCube** alır bir <xref:System.Windows.UIElement.Opacity%2A> % 100.  
  
    -   **outerRectangle** alır bir <xref:System.Windows.Shapes.Shape.Stroke%2A> "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}" Özel ifade değeri.  
  
 Bu kılavuzda son adım olarak, düğme animasyonları ekleyeceğiz. Animasyonlarına olaylar tarafından tetiklenen — özellikle <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaylar.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Olay tetikleyicileri ve animasyonları kullanarak etkileşim eklemek için  
  
1.  **MouseEnter olayı tetikleyici oluşturmak:** yeni bir olay tetikleyicisi ekleyin ve seçin <xref:System.Windows.UIElement.MouseEnter> tetikleyici kullanılacak olayı olarak.  
  
     ![MouseEnter olayı Tetikleyici oluşturma](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2.  **Animasyon zaman çizelgesi oluşturma:** ardından, bir animasyon çizelgesine ilişkilendirmek <xref:System.Windows.UIElement.MouseEnter> olay.  
  
     ![Bir olaya animasyon zaman çizelgesi ekleme](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Tuşuna bastıktan sonra **Tamam** yeni bir zaman çizelgesi oluşturmak için bir **Zaman Çizelgesi panelini** görünür ve "kayıt olduğu zaman çizelgesi" tasarım Masası'nda görünür. Bu, biz özellik değişiklikleri (animasyon olarak oluşturmak özellik değişikliklerini) zaman çizelgesinde kaydı başlatmak anlamına gelir.  
  
    > [!NOTE]
    >  Pencere ve/veya paneller görüntü görmek için yeniden boyutlandır gerekebilir.  
  
     ![Zaman Çizelgesi panelini](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3.  **Bir ana kare oluşturun:** bir animasyon oluşturmak için animasyon, iki veya daha fazla ana kare zaman çizelgesi ve bu anahtar için oluşturma, animasyonun arasında kesinti istediğiniz özellik değerlerini ayarlamak istediğiniz nesne seçin. Aşağıdaki şekilde, bir ana kare oluşturulmasını size yol gösterir.  
  
     ![Bir ana kare oluşturmak nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4.  **Bu ana kare adresindeki glassCube Küçült:** ikinci kareyi seçili boyutunu küçültmek **glassCube** kendi tam boyutlu kullanımının % 90 **boyutu dönüştürme**.  
  
     ![Bir düğme boyutunu küçültmek nasıl](../../../../docs/framework/wpf/controls/media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Uygulamayı çalıştırmak için F5 tuşuna basın. Fare işaretçisini düğmenin üzerine taşıyın. Cam katman üstünde düğmesi küçültür dikkat edin.  
  
5.  **Başka bir olay tetikleyicisi oluşturmak ve farklı bir animasyon ile ilişkilendirin:** bir daha fazla animasyon ekleyelim. Önceki olay tetikleyici animasyon oluşturmak için kullandığınız için benzer bir yordamı kullanın:  
  
    1.  Kullanarak yeni bir olay tetikleyicisi oluşturmak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
    2.  Yeni bir zaman çizelgesi ile ilişkilendirmek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
     ![Yeni bir zaman çizelgesi oluşturma](../../../../docs/framework/wpf/controls/media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1.  Bu zaman çizelgesi için iki ana kare, 0.0 saniye teker ve ikincisi 0,3 saniye konumunda oluşturun.  
  
    2.  Ana kareyi 0,3 vurgulanmış saniye sırasında ayarlamak **dönüştürme açı döndürme** -360 derece.  
  
     ![Döndürme dönüşümü oluşturma](../../../../docs/framework/wpf/controls/media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1.  Uygulamayı çalıştırmak için F5 tuşuna basın. Düğmesini tıklatın. Cam katman çevrede döner dikkat edin.  
  
## <a name="conclusion"></a>Sonuç  
 Özelleştirilmiş bir düğme tamamladınız. Bu uygulamadaki tüm düğmeleri uygulandığı bir düğme şablonu kullanarak yaptığınız. Şablon düzenleme modunda bırakırsanız (Aşağıdaki şekle bakın) ve daha fazla düğme oluşturmak, konum ve özel düğmesi gibi yerine varsayılan düğme gibi davranır görürsünüz.  
  
 ![Özel düğme şablonu](../../../../docs/framework/wpf/controls/media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Aynı şablonu kullanan birden çok düğmeleri](../../../../docs/framework/wpf/controls/media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Uygulamayı çalıştırmak için F5 tuşuna basın. Düğmeler'i tıklatın ve bunların tümü aynı nasıl davranacağını dikkat edin.  
  
 Şablonu özelleştirme sırada ayarladığınız unutmayın <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği **innerRectangle** ve <xref:System.Windows.Shapes.Shape.Stroke%2A> özelliği **outerRectangle** ({şablon arka plan TemplateBinding arka plan}). Tek tek düğmelerinin arka plan rengi ayarladığınızda, bu nedenle, bu ilgili özellikler için ayarladığınız arka plan kullanılır. Arka plan şimdi değiştirmeyi deneyin. Aşağıdaki şekilde, farklı gradyanlar kullanılır. Bu nedenle, bir şablon genel özelleştirmesi düğmesi gibi denetimleri için yararlı olsa da, şablonları denetimleriyle hala birbirinden farklı aramak için değiştirilebilir.  
  
 ![Farklı Ara aynı şablonu düğmeleriyle](../../../../docs/framework/wpf/controls/media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Conclusion, düğme şablonunun özelleştirme sürecinde Microsoft Expression Blend aşağıdakileri yapmak nasıl öğrendiniz:  
  
-   Bir denetimin görünümünü özelleştirin.  
  
-   Özellik tetikleyicileri ayarlayın. Özellik tetikleyicileri çünkü çoğu nesneleri, yalnızca denetimleri kullanılabilir oldukça faydalıdır.  
  
-   Olay tetikleyicileri ayarlayın. Olay tetikleyicileri çünkü çoğu nesneleri, yalnızca denetimleri kullanılabilir oldukça faydalıdır.  
  
-   Animasyon oluşturun.  
  
-   Gradyan, çeşitli: oluşturmak BitmapEffects ekleyin, Dönüşümlerin kullanın ve nesnelerin temel özelliklerini ayarlayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML kullanarak bir düğme oluşturma](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Boyama düz renklerle ve gradyan genel bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Bit eşlem efektleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
