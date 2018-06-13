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
ms.openlocfilehash: bbdc79fabf8dbe344baae66d718d79ac6375db7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558063"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme
<a name="introduction"></a> A <xref:System.Windows.Controls.ControlTemplate> görsel yapı ve bir denetim görsel davranışını belirtir. Yeni bir BT vererek, denetimin görünümünü özelleştirebilirsiniz <xref:System.Windows.Controls.ControlTemplate>. Oluştururken bir <xref:System.Windows.Controls.ControlTemplate>, işlevselliğini değiştirmeden varolan bir denetim görünümünü değiştirin. Örneğin, düğmeleri uygulamanızda yerine varsayılan kare şekli yuvarlak yapabileceğiniz ancak düğmesi hala oluşturacağı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
 Bu konu çeşitli bölümlerini açıklamaktadır bir <xref:System.Windows.Controls.ControlTemplate>, basit bir oluşturmayı gösterir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button>ve böylece görünümünü özelleştirebilirsiniz denetimi denetim sözleşme anlamak açıklanmaktadır. Oluşturduğunuz çünkü bir <xref:System.Windows.Controls.ControlTemplate> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], herhangi bir kod yazmak zorunda kalmadan bir denetimin görünümünü değiştirebilirsiniz. Özel denetim şablonları oluşturmak için Microsoft Expression Blend gibi bir tasarımcı de kullanabilirsiniz. Bu konuda örnekler gösterilmektedir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] görünümünü özelleştirme bir <xref:System.Windows.Controls.Button> ve tam bir örnek konunun sonunda listeler. Expression Blend kullanma hakkında daha fazla bilgi için bkz: [bir denetime stil şablonlarını destekler](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Aşağıdaki çizimler gösterisini bir <xref:System.Windows.Controls.Button> kullanan <xref:System.Windows.Controls.ControlTemplate> Bu konu başlığı altında oluşturulur.  
  
 ![Özel denetim şablonu bir düğme. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Bir özel denetim şablonu kullanan bir düğme  
  
 ![Kırmızı bir sınır bir düğme. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Bir özel denetim şablonunu kullanır ve fare işaretçisini üzerine olan bir düğme  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda oluşturma ve denetimleri ve stiller anlatıldığı gibi kullanan anladığınızı varsayar [denetimleri](../../../../docs/framework/wpf/controls/index.md). Bu konuda açıklanan kavramları devralınmalıdır öğelerine uygulamak <xref:System.Windows.Controls.Control> sınıfı dışında <xref:System.Windows.Controls.UserControl>. Uygulayamazsınız bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>ControlTemplate oluşturduğunuzda  
 Denetimleri sahip birçok özelliği gibi <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, ve <xref:System.Windows.Controls.Control.FontFamily%2A>, denetimin görünümünü farklı yönlerini belirtmek için ayarlayabileceğiniz, ancak bu özellikleri ayarlayarak yaptığınız değişiklikler sınırlıdır. Örneğin, ayarlayabileceğiniz <xref:System.Windows.Controls.Control.Foreground%2A> mavi özelliği ve <xref:System.Windows.Controls.Control.FontStyle%2A> üzerinde çok italik bir <xref:System.Windows.Controls.CheckBox>.  
  
 Yeni bir oluşturma yeteneği olmadan <xref:System.Windows.Controls.ControlTemplate> denetimleri için tüm denetimleri içinde her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulama bir özel görünüm ile uygulama oluşturma becerisini sınırlandırır aynı genel görünüm sahip olabilir. Varsayılan olarak, her <xref:System.Windows.Controls.CheckBox> benzer özelliklere sahip. Örneğin, içeriği <xref:System.Windows.Controls.CheckBox> her zaman seçim göstergesini sağında olan ve onay işaretini her zaman belirtmek için kullanılan <xref:System.Windows.Controls.CheckBox> seçilir.  
  
 Oluşturduğunuz bir <xref:System.Windows.Controls.ControlTemplate> hangi diğer özellikler denetimde ayarlama ne yapacağını ötesinde denetimin görünümünü özelleştirmek istediğinizde. Örneğinde <xref:System.Windows.Controls.CheckBox>olduğunu belirten bir X istediğiniz ve seçim göstergesi olması için bu onay kutusunu içeriğini istediğinizi varsayalım <xref:System.Windows.Controls.CheckBox> seçilir. Bu değişiklikler ile belirttiğiniz <xref:System.Windows.Controls.ControlTemplate> , <xref:System.Windows.Controls.CheckBox>.  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.CheckBox> varsayılan kullanan <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Bir onay kutusu varsayılan denetim şablonu ile. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Varsayılan denetim şablonunu kullanan bir onay kutusu  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.CheckBox> özel kullanan <xref:System.Windows.Controls.ControlTemplate> içeriğini yerleştirmek için <xref:System.Windows.Controls.CheckBox> görüntüler bir X ve seçim göstergesini yukarıda zaman <xref:System.Windows.Controls.CheckBox> seçilir.  
  
 ![Bir özel denetim şablonuyla bir onay kutusu. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Bir özel denetim şablonu kullanan bir onay kutusu  
  
 <xref:System.Windows.Controls.ControlTemplate> İçin <xref:System.Windows.Controls.CheckBox> bu konuda oluşturma daha basit bir örnek kullanan bu örnekte oldukça karmaşık olan bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Bir denetim görsel yapısını değiştirme  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bileşik bir denetim görülür <xref:System.Windows.FrameworkElement> nesneleri. Oluştururken bir <xref:System.Windows.Controls.ControlTemplate>, birleştirme <xref:System.Windows.FrameworkElement> tek bir denetim oluşturmak için nesneleri. A <xref:System.Windows.Controls.ControlTemplate> yalnızca bir olmalıdır <xref:System.Windows.FrameworkElement> , kök öğesi olarak. Kök öğe genellikle diğer içeriyor <xref:System.Windows.FrameworkElement> nesneleri. Nesnelerinin birleşimini denetimin görsel yapısı sağlar.  
  
 Aşağıdaki örnek, bir özel oluşturur <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> Görsel yapısı oluşturur <xref:System.Windows.Controls.Button>. Bu örnek, fare işaretçisini üzerine taşıdığınızda veya tıklatın düğmenin görünümünü değiştirmez. Farklı bir durumda olduğunda düğmenin görünümünü değiştirme, bu konunun ilerleyen bölümlerinde ele alınmıştır.  
  
 Bu örnekte, görsel yapısı aşağıdaki bölümlerden oluşur:  
  
-   A <xref:System.Windows.Controls.Border> adlı `RootElement` şablonun kök olarak hizmet veren <xref:System.Windows.FrameworkElement>.  
  
-   A <xref:System.Windows.Controls.Grid> olan bir alt `RootElement`.  
  
-   A <xref:System.Windows.Controls.ContentPresenter> düğmenin içeriği görüntüler. <xref:System.Windows.Controls.ContentPresenter> Herhangi görüntülenecek nesne türünü sağlar.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Bir denetimin özelliklerini işlevselliğini TemplateBinding kullanarak koruma  
 Yeni bir oluşturduğunuzda <xref:System.Windows.Controls.ControlTemplate>, yine de denetimin görünümünü değiştirmek için ortak özellikleri kullanmak isteyebilirsiniz. [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) biçimlendirme uzantısı olan bir öğesi özelliği bağlar <xref:System.Windows.Controls.ControlTemplate> denetim tarafından tanımlanan bir genel özelliğe. Kullandığınızda [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), şablonu parametreleri olarak davranmak üzere denetim özelliklerini etkinleştirin. Bir denetim bir özellik ayarladığınızda, bu değeri olan öğeyi diğer bir deyişle, geçirildiğinde [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) üzerindeki.  
  
 Aşağıdaki örnek kullanan önceki örnekte parçası yineler [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) olan öğelerin özellikleri bağlamak için işaretleme uzantısı <xref:System.Windows.Controls.ControlTemplate> düğmesi tarafından tanımlanan genel özelliklerine.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Bu örnekte, <xref:System.Windows.Controls.Grid> sahip kendi <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> özelliği şablon bağlı <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Çünkü <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> olan bağlı şablon aynı birden çok düğmeleri oluşturabilirsiniz <xref:System.Windows.Controls.ControlTemplate> ve ayarlayın <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> her düğmesine farklı değerlere. Varsa <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> şablonunu değil, bir öğenin bir özelliğe bağlı değildi <xref:System.Windows.Controls.ControlTemplate>, ayar <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> bir düğmesine düğmenin görünümünü hiçbir etkisi yoktur.  
  
 Not iki özellik adlarını aynı olması gerekmez. Önceki örnekte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Controls.Button> şablonu bağlı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Controls.ContentPresenter>. Bu, yatay olarak konumlandırılmış için düğmesini içeriği sağlar. <xref:System.Windows.Controls.ContentPresenter> adlı bir özellik yok `HorizontalContentAlignment`, ancak <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> bağlanabilir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Bir özellik, şablon bağladığınızda, hedef ve kaynak özellikleri aynı türde olduğundan emin olun.  
  
 <xref:System.Windows.Controls.Control> Sınıfı tarafından denetim şablonu ayarlanırken denetimi üzerinde bir etkisi yoktur için kullanılması gereken çeşitli özellikleri tanımlar. Nasıl <xref:System.Windows.Controls.ControlTemplate> özelliği bağlıdır özelliği kullanır. <xref:System.Windows.Controls.ControlTemplate> Özelliği aşağıdaki yollardan birini kullanmanız gerekir:  
  
-   Bir öğedeki <xref:System.Windows.Controls.ControlTemplate> şablonu özelliğe bağlar.  
  
-   Bir öğedeki <xref:System.Windows.Controls.ControlTemplate> özelliği bir üst öğeden devralır <xref:System.Windows.FrameworkElement>.  
  
 Aşağıdaki tabloda denetimden tarafından devralınan visual özellikleri listeler <xref:System.Windows.Controls.Control> sınıfı. Ayrıca bir denetimin varsayılan denetim şablonu devralınan özellik değeri kullanıp kullanmadığını ya da şablon bağlı olması gerekir, gösterir.  
  
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
  
 Tabloda yalnızca devralınan görsel özelliklerini <xref:System.Windows.Controls.Control> sınıfı. Tabloda listelenen özellikleri dışında bir denetim ayrıca devralır <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, ve <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> üst framework öğenin özelliklerinden.  
  
 Ayrıca, varsa <xref:System.Windows.Controls.ContentPresenter> yer <xref:System.Windows.Controls.ControlTemplate> , bir <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> otomatik olarak bağlanacağı <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A> özellikleri. Benzer şekilde, bir <xref:System.Windows.Controls.ItemsPresenter> alanında <xref:System.Windows.Controls.ControlTemplate> , bir <xref:System.Windows.Controls.ItemsControl> otomatik olarak bağlanacağı <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.ItemsPresenter> özellikleri.  
  
 Aşağıdaki örnek, kullanma iki düğme oluşturur <xref:System.Windows.Controls.ControlTemplate> önceki örnekte tanımlı. Örnek <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, ve <xref:System.Windows.Controls.Control.FontSize%2A> her düğme özellikleri. Ayarı <xref:System.Windows.Controls.Control.Background%2A> özelliği bir etkisi bağlanan şablonu olduğundan <xref:System.Windows.Controls.ControlTemplate>. Olsa bile <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.FontSize%2A> özellikleri şablonu bağlı değil, bunları ayarlama bir etkisi değerlerine devraldığından.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 Önceki örnekte aşağıdaki çizime benzer bir çıktı üretir.  
  
 ![İki düğmesi, bir mavi ve diğeri mor. ] (../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
İki düğmeleriyle farklı arka plan renkleri  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Durumuna bağlı olarak denetiminin görünümünü değiştirme  
 Bir düğme varsayılan görünümünü ve düğmesi arasında önceki örnekte farklı durumlarda olduğunda varsayılan düğme dilden çok az değiştiğini farktır. Örneğin, varsayılan düğme görünümünü düğmesine basıldığında veya fare işaretçisini düğmenin üzerinde olduğunda değiştirir. Ancak <xref:System.Windows.Controls.ControlTemplate> işlev değişikliği değil bir denetimin denetimin görsel davranışını değiştirin. Belirli bir durumda olduğunda görsel bir davranış denetimin görünümünü açıklar. Bir denetim görsel davranışını ve işlevlerinin arasındaki farkı anlamak için düğmesini örneği göz önünde bulundurun. Düğmenin yükseltmek için bir işlevdir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay tıklatıldığında, ancak düğmenin görsel işaret veya basılı görünümünü değiştirmek için bir davranıştır.  
  
 Kullandığınız <xref:System.Windows.VisualState> nesneleri belirli bir durumda olduğunda bir denetimin görünümünü belirtin. A <xref:System.Windows.VisualState> içeren bir <xref:System.Windows.Media.Animation.Storyboard> olan öğelerin görünümünü değiştirir <xref:System.Windows.Controls.ControlTemplate>. Bu denetimin mantığı kullanarak durumu değiştiğinden ortaya yapmak için herhangi bir kod yazmak zorunda değilsiniz <xref:System.Windows.VisualStateManager>. Denetim tarafından belirtilen durumuna girdiğinde <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Media.Animation.Storyboard> başlar. Denetim durumu çıktığında <xref:System.Windows.Media.Animation.Storyboard> durdurur.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.VisualState> görünümünü değiştiren bir <xref:System.Windows.Controls.Button> fare işaretçisini olduğunda üzerinde. <xref:System.Windows.Media.Animation.Storyboard> Rengi değiştirerek düğmenin kenarlık rengi değişir `BorderBrush`. Başvurursanız <xref:System.Windows.Controls.ControlTemplate> örnek bu konunun başında, sözcüğünün `BorderBrush` adı <xref:System.Windows.Media.SolidColorBrush> için atanan <xref:System.Windows.Controls.Border.Background%2A> , <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Denetim içinde ayrıntılı olarak ele alınmıştır denetim sözleşmesinin bir parçası olarak durumları tanımlamaktan sorumludur [denetim sözleşme anlama tarafından diğer denetimleri özelleştirme](#customizing_other_controls_by_understanding_the_control_contract) bu konuda daha sonra. Aşağıdaki tablo için belirtilen durumlarını listeler <xref:System.Windows.Controls.Button>.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerinde denetim konumlandırıldı.|  
|Basılı|CommonStates|Denetim basıldığında.|  
|Devre dışı|CommonStates|Denetim devre dışı bırakıldı.|  
|Odaklanmış|FocusStates|Denetimi odağa sahip.|  
|Odaksız|FocusStates|Denetim odağı yok.|  
  
 <xref:System.Windows.Controls.Button> İki durumu grupları tanımlar: `CommonStates` içeren grubu `Normal`, `MouseOver`, `Pressed`, ve `Disabled` durumları. `FocusStates` İçeren grubu `Focused` ve `Unfocused` durumları. Aynı durum grubu Devletleri'nde karşılıklı olarak birbirini dışlar. Denetimi her zaman grubu başına tam olarak bir durumda değil. Örneğin, bir <xref:System.Windows.Controls.Button> bile fare işaretçisini üzerinde bu nedenle olmadığında odak olabilir bir <xref:System.Windows.Controls.Button> içinde `Focused` durumu içinde olabileceği `MouseOver`, `Pressed`, veya `Normal` durumu.  
  
 Eklediğiniz <xref:System.Windows.VisualState> nesneleri <xref:System.Windows.VisualStateGroup> nesneleri. Eklediğiniz <xref:System.Windows.VisualStateGroup> nesneleri <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> özelliği eklenmiş. Aşağıdaki örnek tanımlar <xref:System.Windows.VisualState> için nesneleri `Normal`, `MouseOver`, ve `Pressed` tüm olan durumları `CommonStates` grubu. <xref:System.Windows.VisualState.Name%2A> Her <xref:System.Windows.VisualState> önceki tabloda adıyla aynıdır. `Disabled` Durumu ve Devletleri'nde `FocusStates` Grup atlanmış kısa örnek tutmak için ancak bu konunun sonunda tüm örnek dahil edilir.  
  
> [!NOTE]
>  Ayarladığınızdan emin olun <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> özelliği eklenmiş kök üzerinde <xref:System.Windows.FrameworkElement> , <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 Önceki örnekte aşağıdaki çizimler için benzer bir çıktı üretir.  
  
 ![Özel denetim şablonu bir düğme. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Normal durumunda bir özel denetim şablonu kullanan bir düğme  
  
 ![Kırmızı bir sınır bir düğme. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Fare durumu bir özel denetim şablonu kullanan bir düğme  
  
 ![Kenarlığın Basılan düğmenin saydamdır. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Bir özel denetim şablonu basılı durumda kullanan bir düğme  
  
 Dahil edilen denetimleri için görsel durumlarını bulmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Durumları arasında geçiş yaptığında davranışını belirtme  
 Önceki örnekte, düğmenin görünümünü kullanıcı bağlantıya tıkladığında, ancak düğmesi için tam bir saniye basılı sürece, kullanıcı etkisi görmez değiştirir. Varsayılan olarak, animasyon gerçekleşmesi için bir saniye sürer. Kullanıcılar'ı tıklatın ve çok daha kısa sürede bir düğme yayın olası olduğundan, görsel geribildirim bırakır etkili olmayacaktır <xref:System.Windows.Controls.ControlTemplate> varsayılan durumu.  
  
 Animasyonun ekleyerek bir denetim bir durumdan diğerine sorunsuz geçiş için gerçekleşmesi için geçen süreyi belirleyebilirsiniz <xref:System.Windows.VisualTransition> nesneleri <xref:System.Windows.Controls.ControlTemplate>. Oluştururken bir <xref:System.Windows.VisualTransition>, bir veya daha fazlasını belirtin:  
  
-   Oluşmasına durumları arasında geçiş için geçen süre.  
  
-   Geçiş aynı anda gerçekleşen ek değişiklikler denetimin görünümünü.  
  
-   Hangi durumları <xref:System.Windows.VisualTransition> uygulanır.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Bir geçiş süresini belirtme  
 Bir geçiş ayarlayarak gereken süreyi belirtin <xref:System.Windows.VisualTransition.GeneratedDuration%2A> özelliği. Önceki örnekte sahip bir <xref:System.Windows.VisualState> belirtir düğmenin kenarlık düğmesine basıldığında ancak animasyon düğmesi hızla basılı serbest bırakılmış ve belirgin olması için çok uzun sürdüğü saydam haline gelir. Kullanabileceğiniz bir <xref:System.Windows.VisualTransition> süreyi belirtmek için denetimi basılı duruma geçiş sürer. Aşağıdaki örnek, denetim bir yüzde bir saniye basılı durumuna geçer aldığını belirtir.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Geçiş sırasında denetimin görünümünü değişiklikleri belirtme  
 <xref:System.Windows.VisualTransition> İçeren bir <xref:System.Windows.Media.Animation.Storyboard> denetimi durumları arasında geçiş yaptığında başlar. Örneğin, belirli bir animasyon denetimi gelen geçiş yaptığında oluşur belirtebilirsiniz `MouseOver` durumunu `Normal` durumu. Aşağıdaki örnekte bir <xref:System.Windows.VisualTransition> kullanıcı düğmesi fare işaretçisini getirdiğinde düğmenin kenarlık mavi, ardından sarı sonra siyah 1.5 saniye cinsinden değiştiğine belirtir.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Bir VisualTransition ne zaman uygulanacağını belirleme  
 A <xref:System.Windows.VisualTransition> yalnızca belirli durumlar uygulamak için kısıtlanmış olabilir veya bu uygulanabilir herhangi durumları arasında denetim geçişler saat. Önceki örnekte <xref:System.Windows.VisualTransition> denetimi geçerse uygulanan `MouseOver` durumunu `Normal` durum; örnekte, önce <xref:System.Windows.VisualTransition> denetimi uygulamasına gittiğinde uygulanan `Pressed` durumu. Ne zaman kısıtlamak bir <xref:System.Windows.VisualTransition> ayarlayarak uygulanan <xref:System.Windows.VisualTransition.To%2A> ve <xref:System.Windows.VisualTransition.From%2A> özellikleri. Aşağıdaki tabloda en az kısıtlayıcı için sınırlama listesinden en kısıtlayıcı düzeylerini açıklar.  
  
|Kısıtlama türü|Gelen değeri|İçin değeri|  
|-------------------------|-------------------|-----------------|  
|Belirtilen bir durumdan başka bir belirtilen durumuna|Adı bir <xref:System.Windows.VisualState>|Adı bir <xref:System.Windows.VisualState>|  
|Belirli bir duruma herhangi durumundan|Ayarlı değil|Adı bir <xref:System.Windows.VisualState>|  
|Belirtilen bir durumdan herhangi bir durum için|Adı bir <xref:System.Windows.VisualState>|Ayarlı değil|  
|Başka bir duruma herhangi durumundan|Ayarlı değil|Ayarlı değil|  
  
 Birden çok olabilir <xref:System.Windows.VisualTransition> nesnelerini bir <xref:System.Windows.VisualStateGroup> aynı duruma bakın, ancak önceki tabloda sırayla kullanılacak. Aşağıdaki örnekte, var olan iki <xref:System.Windows.VisualTransition> nesneleri. Denetim zaman geçiş `Pressed` durumunu `MouseOver` durumu, <xref:System.Windows.VisualTransition> her ikisi de sahip <xref:System.Windows.VisualTransition.From%2A> ve <xref:System.Windows.VisualTransition.To%2A> kümesi kullanılır. Ne zaman denetim geçişleri olmayan bir durumdan `Pressed` için `MouseOver` durumunda, başka bir duruma kullanılır.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> Sahip bir <xref:System.Windows.VisualStateGroup.Transitions%2A> içeren özelliği <xref:System.Windows.VisualTransition> uygulamak nesneleri <xref:System.Windows.VisualState> nesnelerini <xref:System.Windows.VisualStateGroup>. Olarak <xref:System.Windows.Controls.ControlTemplate> yazar, size herhangi dahil etmek ücretsiz <xref:System.Windows.VisualTransition> istiyor. Ancak, varsa <xref:System.Windows.VisualTransition.To%2A> ve <xref:System.Windows.VisualTransition.From%2A> özelliklerini bulunmayan durumu adlarını ayarlamak <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> göz ardı edilir.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.VisualStateGroup> için `CommonStates`. Örnek tanımlayan bir <xref:System.Windows.VisualTransition> her düğmenin aşağıdaki geçişleri için.  
  
-   İçin `Pressed` durumu.  
  
-   İçin `MouseOver` durumu.  
  
-   Gelen `Pressed` durumunu `MouseOver` durumu.  
  
-   Gelen `MouseOver` durumunu `Normal` durumu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Denetim anlaşması anlayarak diğer denetimleri özelleştirme  
 Kullanan bir denetim bir <xref:System.Windows.Controls.ControlTemplate> visual yapısını belirtmek için (kullanarak <xref:System.Windows.FrameworkElement> nesneler) ve görsel davranışını (kullanarak <xref:System.Windows.VisualState> nesneler) bölümleri denetimi modeli kullanır. Dahil edilen denetimlerinin birçok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 Bu modeli kullanın. Bölümleri, bir <xref:System.Windows.Controls.ControlTemplate> Yazar farkında olması gerekiyor denetim anlaşması iletilen. Denetim anlaşması bölümlerini anladığınızda, bölümleri denetimi modelini kullanan herhangi bir denetimi görünümünü özelleştirebilirsiniz.  
  
 Denetim anlaşması üç öğeye sahiptir:  
  
-   Denetimin mantığı kullanır görsel öğeler.  
  
-   Denetim ve Grup durumları her durum ait.  
  
-   Denetim görsel olarak etkileyen ortak özellikler.  
  
### <a name="visual-elements-in-the-control-contract"></a>Denetim anlaşması görsel öğeleri  
 Bazen bir denetimin mantığı ile etkileşime giren bir <xref:System.Windows.FrameworkElement> alanında <xref:System.Windows.Controls.ControlTemplate>. Örneğin, Denetim öğelerinden biri olay işleyebilirsiniz. Ne zaman bir denetim bekliyor belirli bir bulmak <xref:System.Windows.FrameworkElement> içinde <xref:System.Windows.Controls.ControlTemplate>, bu bilgileri iletmek gerekir <xref:System.Windows.Controls.ControlTemplate> yazar. Denetim kullanan <xref:System.Windows.TemplatePartAttribute> türüne ve beklenen öğe, ne öğesinin adı olmalıdır iletmek için. <xref:System.Windows.Controls.Button> Sahip olmayan <xref:System.Windows.FrameworkElement> denetim sözleşmesi, ancak diğer denetimleri gibi bölümleri <xref:System.Windows.Controls.ComboBox>, yapın.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.TemplatePartAttribute> üzerinde belirtilen nesneleri <xref:System.Windows.Controls.ComboBox> sınıfı. Mantığını <xref:System.Windows.Controls.ComboBox> bulmak beklediği bir <xref:System.Windows.Controls.TextBox> adlı `PART_EditableTextBox` ve <xref:System.Windows.Controls.Primitives.Popup> adlı `PART_Popup` içinde kendi <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 Aşağıdaki örnek, Basitleştirilmiş bir gösterir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ComboBox> tarafından belirtilen öğeleri içerir <xref:System.Windows.TemplatePartAttribute> üzerinde nesneleri <xref:System.Windows.Controls.ComboBox> sınıfı.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Denetim sözleşmesindeki durumları  
 Denetimin durumlarını ayrıca Denetim sözleşme parçasıdır. Örnek oluşturma bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button> görünümünü belirtmek gösterilmektedir bir <xref:System.Windows.Controls.Button> kendi durumlarını bağlı olarak. Oluşturduğunuz bir <xref:System.Windows.VisualState> her durumu belirtilen ve tüm put <xref:System.Windows.VisualState> nesneleri paylaşan bir <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> içinde bir <xref:System.Windows.VisualStateGroup>açıklandığı gibi [denetim bağlı olarak ITS durumuna görünümünü değiştirme](#changing_the_appearance_of_a_control_depending_on_its_state) bu önceki konu. Üçüncü taraf denetimleri kullanarak durumları belirtmelidir <xref:System.Windows.TemplateVisualStateAttribute>, denetim şablonları yazma denetimin durumları kullanıma sunmak için Expression Blend gibi tasarımcı araçları sağlar.  
  
 Dahil edilen denetimleri için denetim anlaşması bulmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Denetim sözleşmesindeki özellikleri  
 Denetim görsel olarak etkileyen ortak özellikler de denetim sözleşmede dahil edilir. Yeni bir oluşturmadan denetiminin görünümünü değiştirmek için bu özellikleri ayarlayabilirsiniz <xref:System.Windows.Controls.ControlTemplate>. Aynı zamanda [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) olan öğelerin özellikleri bağlamak için işaretleme uzantısı <xref:System.Windows.Controls.ControlTemplate> tarafından tanımlanan genel özelliklerine <xref:System.Windows.Controls.Button>.  
  
 Aşağıdaki örnek, düğme denetim sözleşme gösterir.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate>, genellikle bir var olan başlamak kolay <xref:System.Windows.Controls.ControlTemplate> ve değişiklikleri yapın. Var olan değiştirmek için aşağıdakilerden birini yapabilirsiniz <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Denetim şablonları oluşturmak için bir grafik kullanıcı arabirimi sağlar Expression Blend gibi bir designer'ı kullanın. Daha fazla bilgi için bkz: [bir denetime stil şablonlarını destekler](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Varsayılan alma <xref:System.Windows.Controls.ControlTemplate> ve düzenleyin. Dahil edilen denetim şablonları varsayılan bulmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [varsayılan WPF temaları](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki örnek eksiksiz gösterir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> bu konuda ele alınmıştır.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
