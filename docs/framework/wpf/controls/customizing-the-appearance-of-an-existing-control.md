---
title: ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: 435789e0d1bc601a9eb51488254407fefd334e05
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47058480"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme
<a name="introduction"></a> A <xref:System.Windows.Controls.ControlTemplate> görsel yapı ve denetim görsel davranışını belirtir. Yeni bir BT vererek denetiminin görünümünü özelleştirebilirsiniz <xref:System.Windows.Controls.ControlTemplate>. Oluştururken bir <xref:System.Windows.Controls.ControlTemplate>, işlevselliği değiştirmeden mevcut bir denetimin görünümünü değiştirin. Örneğin, düğmeler, uygulamanızda yerine varsayılan kare şekil yuvarlak yapabileceğiniz ancak düğme hala oluşturacağı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
 Bu konu çeşitli bölümlerini açıklamaktadır bir <xref:System.Windows.Controls.ControlTemplate>, basit bir oluşturma işlemi <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button>ve görünümünü özelleştirebileceğiniz bir denetimin denetim sözleşmesi öğrenmek açıklanmaktadır. Oluşturduğunuz çünkü bir <xref:System.Windows.Controls.ControlTemplate> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], herhangi bir kod yazmadan bir denetimin görünümünü değiştirebilirsiniz. Microsoft Expression Blend gibi bir tasarımcıdan özel denetim şablonları oluşturmak için de kullanabilirsiniz. Bu konuda örnekler gösterilmektedir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] görünüşünü özelleştirme bir <xref:System.Windows.Controls.Button> ve konunun sonunda tam bir örnek listeler. Expression Blend kullanma hakkında daha fazla bilgi için bkz. [Şablonları destekleyen bir denetime stil uygulama](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Aşağıdaki resimlerde gösterildiği bir <xref:System.Windows.Controls.Button> kullanan <xref:System.Windows.Controls.ControlTemplate> bu konudaki oluşturulur.  
  
 ![Bir özel denetim şablonu bir düğme. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Bir özel denetim şablonunu kullanan bir düğme  
  
 ![Kırmızı bir kenarlık bir düğme. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Bir özel denetim şablonu kullanır ve üzerine fare işaretçisini bir düğme  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, oluşturma ve açıklandığı gibi denetimleri ve stilleri kullanmak anladığınızı varsayar [denetimleri](../../../../docs/framework/wpf/controls/index.md). Bu konuda açıklanan kavramları devralacak öğelere uygula <xref:System.Windows.Controls.Control> sınıfı dışında <xref:System.Windows.Controls.UserControl>. Uygulayamazsınız bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>ControlTemplate oluştururken  
 Denetimler içeren özellikleri gibi <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, ve <xref:System.Windows.Controls.Control.FontFamily%2A>, denetimin görünümünü farklı yönlerini belirtmek üzere ayarlayabilirsiniz, ancak bu özellikleri ayarlayarak yaptığınız değişiklikler sınırlıdır. Örneğin, ayarlayabilirsiniz <xref:System.Windows.Controls.Control.Foreground%2A> mavi özelliği ve <xref:System.Windows.Controls.Control.FontStyle%2A> üzerinde çok italik bir <xref:System.Windows.Controls.CheckBox>.  
  
 Yeni bir oluşturma olanağı olmadan <xref:System.Windows.Controls.ControlTemplate> denetimler için tüm denetimleri içinde her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama bir özel görünüm ile uygulama oluşturma becerisini sınırlandırır aynı genel görünüme sahip. Varsayılan olarak, her <xref:System.Windows.Controls.CheckBox> benzer özelliklere sahiptir. Örneğin, içeriği <xref:System.Windows.Controls.CheckBox> seçimi göstergesi sağında her zaman olduğu ve onay işaretine her zaman göstermek için kullanılan <xref:System.Windows.Controls.CheckBox> seçilir.  
  
 Oluşturduğunuz bir <xref:System.Windows.Controls.ControlTemplate> hangi diğer özellikleri üzerinde denetimi ayarlama yapmak ötesinde denetimin görünümünü özelleştirme istediğinizde. Örneğinde <xref:System.Windows.Controls.CheckBox>göstermek için bir X istediğiniz ve içeriğin seçimi göstergesi olması için bu onay kutusu istediğinizi varsayın <xref:System.Windows.Controls.CheckBox> seçilir. Bu değişiklikleri belirttiğiniz <xref:System.Windows.Controls.ControlTemplate> , <xref:System.Windows.Controls.CheckBox>.  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.CheckBox> varsayılan <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Varsayılan denetim şablonunu içeren bir onay kutusu. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Varsayılan denetim şablonunu kullanan bir onay kutusu  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.CheckBox> özel kullanan <xref:System.Windows.Controls.ControlTemplate> içeriğini yerleştirmek için <xref:System.Windows.Controls.CheckBox> seçimi göstergesi ve görüntüler X yukarıda olduğunda <xref:System.Windows.Controls.CheckBox> seçilir.  
  
 ![Bir özel denetim şablonu ile bir onay kutusu. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Bir özel denetim şablonunu kullanan bir onay kutusu  
  
 <xref:System.Windows.Controls.ControlTemplate> İçin <xref:System.Windows.Controls.CheckBox> bu konuda oluşturmanın basit bir örneği kullanması için bu örnekte nispeten karmaşık olan bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Bir denetimin görsel yapı değiştirme  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], genellikle bir bileşik denetimdir <xref:System.Windows.FrameworkElement> nesneleri. Oluştururken bir <xref:System.Windows.Controls.ControlTemplate>, birleştirerek <xref:System.Windows.FrameworkElement> tek bir denetim oluşturmak için nesne. A <xref:System.Windows.Controls.ControlTemplate> yalnızca bir <xref:System.Windows.FrameworkElement> , kök öğesi olarak. Kök öğe genellikle diğer içeren <xref:System.Windows.FrameworkElement> nesneleri. Denetimin görsel yapısına nesnelerinin birleşimini sağlar.  
  
 Aşağıdaki örnek bir özel oluşturur <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> Görsel yapısını oluşturur <xref:System.Windows.Controls.Button>. Bu örnek, fareyi üzerine taşıdığınızda veya tıklatın düğmenin görünümünü değiştirmez. Farklı bir durumda olduğunda düğmenin görünümünü değiştirme, bu konunun ilerleyen bölümlerinde ele alınmıştır.  
  
 Bu örnekte, görsel yapı aşağıdaki bölümden oluşur:  
  
-   A <xref:System.Windows.Controls.Border> adlı `RootElement` şablonun kök olarak hizmet veren <xref:System.Windows.FrameworkElement>.  
  
-   A <xref:System.Windows.Controls.Grid> diğer bir deyişle bir alt öğesi `RootElement`.  
  
-   A <xref:System.Windows.Controls.ContentPresenter> , düğmenin içeriğini görüntüler. <xref:System.Windows.Controls.ContentPresenter> Herhangi görüntülenecek nesne türünü sağlar.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Bir denetimin özelliklerini işlevselliğini TemplateBinding kullanarak koruma  
 Yeni bir oluşturduğunuzda <xref:System.Windows.Controls.ControlTemplate>, denetimin görünümünü değiştirmek için ortak özellikleri kullanmak yine de isteyebilirsiniz. [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) işaretleme uzantısı bağlayan bir özelliği olan bir öğenin <xref:System.Windows.Controls.ControlTemplate> denetim tarafından tanımlanan ortak bir özellik için. Kullanırken [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), şablon parametreleri olarak davranmak üzere denetimi özellikleri sağlar. Denetim üzerinde bir özelliği ayarlandığında bu değere sahip öğe için diğer bir deyişle, geçirildiğinde [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) üzerindeki.  
  
 Aşağıdaki örnek kullanan yukarıdaki örnekte parçası yineler [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) bulunan öğelerin özelliklerini bağlamak için işaretleme uzantısı <xref:System.Windows.Controls.ControlTemplate> düğme tarafından tanımlanan ortak özellikleri.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Bu örnekte, <xref:System.Windows.Controls.Grid> sahip kendi <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> özelliği şablon bağlı <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Çünkü <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> olan bağlı şablon aynı kullanan birden çok düğmeleri oluşturabilirsiniz <xref:System.Windows.Controls.ControlTemplate> ve <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> düğmelerin üzerindeki farklı değerler. Varsa <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> değil şablonu içindeki bir öğenin bir özelliğe bağlı değildi <xref:System.Windows.Controls.ControlTemplate>ayarını <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> bir düğmeye düğmenin görünümünü üzerinde hiçbir etkisi yoktur.  
  
 Not, iki özellik adları aynı olması gerekmez. Önceki örnekte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Controls.Button> şablon bağlı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Controls.ContentPresenter>. Bu düğmenin yatay olarak konumlandırılan içeriğini sağlar. <xref:System.Windows.Controls.ContentPresenter> adlı bir özellik yok `HorizontalContentAlignment`, ancak <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> bağlanabilir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Bir özellik, şablon bağladığınızda, hedef ve kaynak özelliklerini aynı türde olduğundan emin olun.  
  
 <xref:System.Windows.Controls.Control> Sınıfı ayarlanırken bir etkisi denetimi için denetim şablonu tarafından kullanılması gereken çeşitli özellikleri tanımlar. Nasıl <xref:System.Windows.Controls.ControlTemplate> özelliği bağlıdır özelliği kullanır. <xref:System.Windows.Controls.ControlTemplate> Özelliği aşağıdaki yollardan birini kullanmanız gerekir:  
  
-   Bir öğedeki <xref:System.Windows.Controls.ControlTemplate> şablon özelliğe bağlar.  
  
-   Bir öğedeki <xref:System.Windows.Controls.ControlTemplate> özelliği bir üst öğeden devralır <xref:System.Windows.FrameworkElement>.  
  
 Aşağıdaki tabloda bir denetimden devralan görsel özellikleri listeler <xref:System.Windows.Controls.Control> sınıfı. Ayrıca, bir denetimin varsayılan denetim şablonunu devralınan özellik değerini kullanıp kullanmadığını veya şablon bağlı olması gerekir, gösterir.  
  
|Özellik|Kullanım yöntemi|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|Şablon Bağlama|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Şablon Bağlama|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Şablon Bağlama|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Şablon Bağlama|  
|<xref:System.Windows.Controls.Control.Padding%2A>|Şablon Bağlama|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Şablon Bağlama|  
  
 Bir tabloda yalnızca devralınan görsel özellikleri <xref:System.Windows.Controls.Control> sınıfı. Tabloda listelenen özellikleri dışında bir denetim de devralabilir <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, ve <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> üst çerçeve öğesinin özellikleri.  
  
 Ayrıca, varsa <xref:System.Windows.Controls.ContentPresenter> bulunduğu <xref:System.Windows.Controls.ControlTemplate> , bir <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> otomatik olarak bağlayacaksınız <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A> özellikleri. Benzer şekilde, bir <xref:System.Windows.Controls.ItemsPresenter> alanında <xref:System.Windows.Controls.ControlTemplate> , bir <xref:System.Windows.Controls.ItemsControl> otomatik olarak bağlayacaksınız <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.ItemsPresenter> özellikleri.  
  
 Aşağıdaki örnek, kullanan iki düğme oluşturur <xref:System.Windows.Controls.ControlTemplate> önceki örnekte tanımlanan. Örnek <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, ve <xref:System.Windows.Controls.Control.FontSize%2A> her düğmesine özellikleri. Ayarı <xref:System.Windows.Controls.Control.Background%2A> özelliği, şablonu içinde bağlı olduğundan bir etkiye sahiptir <xref:System.Windows.Controls.ControlTemplate>. Olsa da <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.FontSize%2A> ayarı bir etkisi değerlerine devraldığından, Özellikler şablon bağlı değildir.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 Önceki örnekte aşağıdaki çizime benzer bir çıktı oluşturulur.  
  
 ![İki düğme, bir mavi ve mor bir. ](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
İki düğme farklı bir arka plan renkleri  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Durumuna bağlı olarak bir denetimin görünümünü değiştirme  
 Varsayılan görünümünü bir düğme ve düğmeyi arasındaki fark önceki örnekte, farklı durumlarda olduğunda varsayılan düğme farenizin değiştiğini ' dir. Örneğin, bir düğmeye basıldığında veya fare işaretçisi düğmenin üzerine geldiğinde varsayılan düğmenin görünümünü değiştirir. Ancak <xref:System.Windows.Controls.ControlTemplate> işlevsellik değişmez bir denetimin, denetimin görsel davranışı değişmez. Belirli bir durumda olduğunda görsel bir davranış, denetimin görünümünü açıklar. İşlevi bir denetimin görsel davranış arasındaki farkı anlamak için düğme örneği göz önünde bulundurun. Düğmenin işlevselliği başlatılmasıdır <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay tıklatıldığında, ancak düğmenin görsel işaret veya basılı görünümünü değiştirmek için bir davranıştır.  
  
 Kullandığınız <xref:System.Windows.VisualState> nesneleri belirli bir durumda olduğunda, bir denetimin görünümünü belirtmek için. A <xref:System.Windows.VisualState> içeren bir <xref:System.Windows.Media.Animation.Storyboard> bulunan öğelerin görünümünü değiştirir <xref:System.Windows.Controls.ControlTemplate>. Bu denetimin mantığı kullanarak durumu değiştiğinden ortaya yapmak için kod yazmanız gerekmez <xref:System.Windows.VisualStateManager>. Denetim tarafından belirtilen durumuna girdiğinde <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Media.Animation.Storyboard> başlar. Denetim durumu çıktığında <xref:System.Windows.Media.Animation.Storyboard> durdurur.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.VisualState> görünümünü değiştiren bir <xref:System.Windows.Controls.Button> fare işaretçisi olduğunda üzerine. <xref:System.Windows.Media.Animation.Storyboard> Rengini değiştirerek düğmenin kenarlık rengini değiştirir `BorderBrush`. Başvurursanız <xref:System.Windows.Controls.ControlTemplate> örnek bu konunun başında, Hatırlayacağınız `BorderBrush` adıdır <xref:System.Windows.Media.SolidColorBrush> için atanan <xref:System.Windows.Controls.Border.Background%2A> , <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Denetim durumlarını ayrıntılı olarak ele denetim sözleşmesinin bir parçası olarak tanımlamaktan sorumludur [denetim sözleşmesi anlama tarafından diğer denetimleri özelleştirme](#customizing_other_controls_by_understanding_the_control_contract) bu konuda. Aşağıdaki tablo için belirtilen durumları listeler <xref:System.Windows.Controls.Button>.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Basılan|CommonStates|Denetime basıldığında.|  
|Devre dışı|CommonStates|Denetim devre dışıdır.|  
|Odaklanmış|FocusStates|Denetim odağa sahip.|  
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|  
  
 <xref:System.Windows.Controls.Button> İki durum grubu tanımlar: `CommonStates` grubunu içeren `Normal`, `MouseOver`, `Pressed`, ve `Disabled` durumları. `FocusStates` Grubunu içeren `Focused` ve `Unfocused` durumları. Durumlar aynı durum grubu içinde birlikte kullanılamaz. Denetim grubu başına tam olarak bir durumda her zaman alır. Örneğin, bir <xref:System.Windows.Controls.Button> bile fare işaretçisi üzerinde bu nedenle olmadığında odak olabilir bir <xref:System.Windows.Controls.Button> içinde `Focused` durumu olabilir `MouseOver`, `Pressed`, veya `Normal` durumu.  
  
 Eklediğiniz <xref:System.Windows.VisualState> nesneleri için <xref:System.Windows.VisualStateGroup> nesneleri. Eklediğiniz <xref:System.Windows.VisualStateGroup> nesneleri için <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> ekli özellik. Aşağıdaki örnek tanımlar <xref:System.Windows.VisualState> için nesneleri `Normal`, `MouseOver`, ve `Pressed` hepsini olan durumları `CommonStates` grubu. <xref:System.Windows.VisualState.Name%2A> Her <xref:System.Windows.VisualState> önceki tabloda adıyla aynıdır. `Disabled` Durumu ve durumlarda `FocusStates` grubu örneği kısa tutmak için atlanmış, ancak bu konunun sonunda Örneğin tamamını dahil edilir.  
  
> [!NOTE]
>  Ayarladığınızdan emin olun <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> ekli özellik kök <xref:System.Windows.FrameworkElement> , <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 Yukarıdaki örnekte, aşağıdaki çizimler için benzer bir çıktı üretir.  
  
 ![Bir özel denetim şablonu bir düğme. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Normal durumunda bir özel denetim şablonunu kullanan bir düğme  
  
 ![Kırmızı bir kenarlık bir düğme. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Bir özel denetim şablonu durum önizlemesini kullanan bir düğme  
  
 ![Basılan düğmenin kenarlığı saydamdır. ](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Basılan durumda bir özel denetim şablonunu kullanan bir düğme  
  
 Görsel durumları ile birlikte denetimler bulmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Durum arasında geçiş yaptığında, denetimin davranışını belirtme  
 Önceki örnekte, bir düğmenin görünümünü kullanıcı buna tıkladığında, ancak kullanıcı düğmeyi için tam bir saniye basılmadığı sürece etkisi görmez değiştirir. Varsayılan olarak, bir saniye içinde gerçekleşmesi animasyon alır. Kullanıcılar'a tıklayın ve çok daha kısa sürede bir düğme yayın olası olduğundan, görsel geri bildirim bırakırsanız etkili olmayacak <xref:System.Windows.Controls.ControlTemplate> varsayılan durumunda.  
  
 Animasyon ekleyerek bir denetimi bir durumdan diğerine sorunsuz geçiş yapmak için gerçekleşmesi için geçen süreyi belirleyebilirsiniz <xref:System.Windows.VisualTransition> nesneleri için <xref:System.Windows.Controls.ControlTemplate>. Oluştururken bir <xref:System.Windows.VisualTransition>, aşağıdakilerden birini veya birkaçını belirtin:  
  
-   Oluştuğu durumlar arasında geçiş için geçen süre.  
  
-   Geçiş yapıldığı sırada gerçekleşen ek değişiklikleri denetimin görünümü.  
  
-   Hangi durumları <xref:System.Windows.VisualTransition> uygulanır.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Geçiş süresini belirleme  
 Ne kadar bir geçişin ayarlayarak alacağını belirtebilirsiniz <xref:System.Windows.VisualTransition.GeneratedDuration%2A> özelliği. Yukarıdaki örnekte sahip bir <xref:System.Windows.VisualState> düğmenin kenarlık düğmeye basıldığında, ancak animasyon düğme hızla basılı serbest ve belirgin olması için fazla uzun sürdüğü saydam olacağını belirtir. Kullanabileceğiniz bir <xref:System.Windows.VisualTransition> süreyi belirtmek için bu denetim basılı durumu geçiş alır. Aşağıdaki örnek, denetim bir yüzde birine basılı duruma geçmesine aldığını belirtir.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Geçiş sırasında denetimin görünümünü değişiklikleri belirtme  
 <xref:System.Windows.VisualTransition> İçeren bir <xref:System.Windows.Media.Animation.Storyboard> denetim durum arasında geçiş yaptığında başlar. Örneğin, belirli bir animasyonu gelen denetim geçiş yaptığında oluşur belirtebilirsiniz `MouseOver` durumunu `Normal` durumu. Aşağıdaki örnek, oluşturur bir <xref:System.Windows.VisualTransition> kullanıcı düğmenin fare işaretçisini hareket ettirdiğinde düğmenin kenarlık mavi, ardından sarı ardından siyah 1.5 saniye cinsinden değiştiğini belirtir.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Bir VisualTransition uygulandığında belirtme  
 A <xref:System.Windows.VisualTransition> yalnızca belirli durumlar uygulamak için kısıtlı olabilir ya da uygulanabilir denetim geçişlerinden durumlar arasında istediğiniz zaman. Önceki örnekte, <xref:System.Windows.VisualTransition> denetim geçerse uygulanan `MouseOver` durumunu `Normal` durum; örnekte, önce <xref:System.Windows.VisualTransition> denetim uygulamasına gittiğinde uygulanan `Pressed` durumu. Ne zaman kısıtlama bir <xref:System.Windows.VisualTransition> ayarlayarak uygulanan <xref:System.Windows.VisualTransition.To%2A> ve <xref:System.Windows.VisualTransition.From%2A> özellikleri. Aşağıdaki tabloda, en kısıtlayıcı kısıtlaması için en az kısıtlayıcı düzeyleri açıklanmaktadır.  
  
|Kısıtlama türü|Gelen değeri|İçin değeri|  
|-------------------------|-------------------|-----------------|  
|Belirtilen bir durumdan başka bir belirtilen duruma|Adı bir <xref:System.Windows.VisualState>|Adı bir <xref:System.Windows.VisualState>|  
|Belirli bir duruma herhangi durumundan|Ayarlı değil|Adı bir <xref:System.Windows.VisualState>|  
|Herhangi bir durumu için belirtilen bir durum|Adı bir <xref:System.Windows.VisualState>|Ayarlı değil|  
|Bir durumdan diğer bir duruma|Ayarlı değil|Ayarlı değil|  
  
 Birden çok olabilir <xref:System.Windows.VisualTransition> nesneler bir <xref:System.Windows.VisualStateGroup> aynı durumuna bakın, ancak önceki tabloda belirten sırayla kullanılır. Aşağıdaki örnekte, var olan iki <xref:System.Windows.VisualTransition> nesneleri. Denetimin ne zaman değişir `Pressed` durumunu `MouseOver` durumu <xref:System.Windows.VisualTransition> hem de olan <xref:System.Windows.VisualTransition.From%2A> ve <xref:System.Windows.VisualTransition.To%2A> kümesi kullanılır. Denetim olmayan bir durumu ne zaman geçiş `Pressed` için `MouseOver` durumuna başka bir duruma kullanılır.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> Sahip bir <xref:System.Windows.VisualStateGroup.Transitions%2A> içeren özellik <xref:System.Windows.VisualTransition> uygulamak nesneleri <xref:System.Windows.VisualState> nesneler <xref:System.Windows.VisualStateGroup>. Olarak <xref:System.Windows.Controls.ControlTemplate> yazar, herhangi bir dosyayı eklemek ücretsiz <xref:System.Windows.VisualTransition> istediğiniz. Ancak, varsa <xref:System.Windows.VisualTransition.To%2A> ve <xref:System.Windows.VisualTransition.From%2A> özellikleri olmayan durum adlarını ayarlanır <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> göz ardı edilir.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.VisualStateGroup> için `CommonStates`. Örnek tanımlayan bir <xref:System.Windows.VisualTransition> düğmenin aşağıdakilerin her geçiş için.  
  
-   İçin `Pressed` durumu.  
  
-   İçin `MouseOver` durumu.  
  
-   Gelen `Pressed` durumunu `MouseOver` durumu.  
  
-   Gelen `MouseOver` durumunu `Normal` durumu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Denetim sözleşmesi anlayarak diğer denetimleri özelleştirme  
 Kullanan bir denetim bir <xref:System.Windows.Controls.ControlTemplate> visual yapısını belirtmek için (kullanarak <xref:System.Windows.FrameworkElement> nesneleri) ve görsel davranışını (kullanarak <xref:System.Windows.VisualState> nesneleri) bölümleri denetimi modeli kullanır. Dahil olan denetimlerin birçok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 Bu modeli kullanın. Bölümleri, bir <xref:System.Windows.Controls.ControlTemplate> Yazar farkında olması gerekiyor denetim sözleşmesi iletilir. Denetim sözleşmesi bölümlerini anladığınızda, bölümleri denetimi modeli kullanır. herhangi bir denetimin görünümünü özelleştirebilirsiniz.  
  
 Denetim sözleşmesi üç öğe vardır:  
  
-   Görsel öğeler denetimin mantığı kullanır.  
  
-   Denetim ve her durumun ait olduğu Grup durumları.  
  
-   Denetimin görsel olarak etkileyen genel özellikler.  
  
### <a name="visual-elements-in-the-control-contract"></a>Denetim sözleşmesi görsel öğe  
 Bazen bir denetimin mantığı ile etkileşime giren bir <xref:System.Windows.FrameworkElement> alanında <xref:System.Windows.Controls.ControlTemplate>. Örneğin, Denetim öğelerinden biri olay işleyebilir. Ne zaman bir denetim bekliyor belirli bir bulmak <xref:System.Windows.FrameworkElement> içinde <xref:System.Windows.Controls.ControlTemplate>, bu bilgileri iletmek gerekir <xref:System.Windows.Controls.ControlTemplate> yazar. Denetimi kullanan <xref:System.Windows.TemplatePartAttribute> türü beklenen öğe ve neler öğe adı olması gerektiğini belirtmek için. <xref:System.Windows.Controls.Button> Olmayan <xref:System.Windows.FrameworkElement> denetim sözleşmesi, ancak diğer denetimler gibi bölümleri <xref:System.Windows.Controls.ComboBox>, yapın.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.TemplatePartAttribute> üzerinde belirtilen nesneleri <xref:System.Windows.Controls.ComboBox> sınıfı. Mantığını <xref:System.Windows.Controls.ComboBox> bulmayı beklediği bir <xref:System.Windows.Controls.TextBox> adlı `PART_EditableTextBox` ve <xref:System.Windows.Controls.Primitives.Popup> adlı `PART_Popup` içinde kendi <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 Aşağıdaki örnek bir Basitleştirilmiş gösterir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ComboBox> tarafından belirtilen öğeleri içeren <xref:System.Windows.TemplatePartAttribute> üzerindeki nesneleri <xref:System.Windows.Controls.ComboBox> sınıfı.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Denetim sözleşmesi durumları  
 Bir denetim durumlarını da Denetim sözleşmesi parçasıdır. Örnek oluşturma bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button> gösterilmektedir görünümünü belirtmek bir <xref:System.Windows.Controls.Button> kendi durumlarını bağlı olarak. Oluşturduğunuz bir <xref:System.Windows.VisualState> her durum belirttiniz ve tüm <xref:System.Windows.VisualState> nesneleri paylaşan bir <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> içinde bir <xref:System.Windows.VisualStateGroup>anlatılan şekilde [denetim bağlı olarak kendi durumu görünümünü değiştirme](#changing_the_appearance_of_a_control_depending_on_its_state) bu önceki konu. Üçüncü taraf denetimleri kullanarak durumları belirtmelidir <xref:System.Windows.TemplateVisualStateAttribute>, denetim şablonları yazma denetimin durumları göstermek için Expression Blend gibi tasarımcı araçları sağlar.  
  
 Denetim sözleşmesi bulunan denetimleri bulmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Denetim sözleşmesi özellikleri  
 Denetimin görsel olarak etkileyen genel özelliklerini de denetimi sözleşmede dahil edilir. Yeni bir oluşturmadan denetiminin görünümünü değiştirmek için bu özellikleri ayarlayabilirsiniz <xref:System.Windows.Controls.ControlTemplate>. Ayrıca [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) bulunan öğelerin özelliklerini bağlamak için işaretleme uzantısı <xref:System.Windows.Controls.ControlTemplate> tarafından tanımlanan ortak özelliklere <xref:System.Windows.Controls.Button>.  
  
 Aşağıdaki örnek, düğme için Denetim sözleşmesi gösterir.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate>, genellikle varolan ile başlamak kolay <xref:System.Windows.Controls.ControlTemplate> ve ona değişiklikler. Varolan değiştirmek için aşağıdakilerden birini yapabilirsiniz <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Denetim şablonları oluşturmak için bir grafik kullanıcı arabirimi sağlayan Expression Blend gibi bir tasarımcı kullanır. Daha fazla bilgi için [Şablonları destekleyen bir denetime stil uygulama](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Varsayılan <xref:System.Windows.Controls.ControlTemplate> ve düzenleyin. Varsayılan, dahil olan denetim şablonları bulmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [varsayılan WPF temaları](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, tam gösterir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> bu konuda ele alınmıştır.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
