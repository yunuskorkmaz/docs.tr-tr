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
ms.openlocfilehash: 63a0b724b71c4a4901c2dedcf502045a75ec405c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933726"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme
<a name="introduction"></a>Bir <xref:System.Windows.Controls.ControlTemplate> denetimin görsel yapısını ve görsel davranışını belirtir. Bir denetimin görünüşünü yeni <xref:System.Windows.Controls.ControlTemplate>bir vererek özelleştirebilirsiniz. Bir <xref:System.Windows.Controls.ControlTemplate>oluşturduğunuzda, mevcut bir denetimin görünüşünü, işlevselliğini değiştirmeden değiştirirsiniz. Örneğin, uygulamadaki düğmeleri varsayılan kare şekli yerine yuvarlayabilmeniz, ancak düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı yine de oluşturacak.  
  
 Bu konu, bir öğesinin <xref:System.Windows.Controls.ControlTemplate>çeşitli parçalarını açıklar, bir <xref:System.Windows.Controls.Button>için basit <xref:System.Windows.Controls.ControlTemplate> oluşturmayı gösterir ve görünümünü özelleştirebilmeniz için bir denetimin denetim sözleşmesinin nasıl anlaşılmasını açıklar. <xref:System.Windows.Controls.ControlTemplate> İçinde[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir oluşturduğunuz için, herhangi bir kod yazmadan bir denetimin görünümünü değiştirebilirsiniz. Ayrıca, özel denetim şablonları oluşturmak için Microsoft Expression Blend gibi bir tasarımcı da kullanabilirsiniz. Bu konu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içindeki görünümünü <xref:System.Windows.Controls.Button> özelleştiren ve konusunun sonundaki bütün örneği listeleyen örnekleri gösterir. Ifade Blend kullanma hakkında daha fazla bilgi için, bkz. [şablonları destekleyen bir denetimin stillendirme](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Aşağıdaki çizimlerde, <xref:System.Windows.Controls.ControlTemplate> bu <xref:System.Windows.Controls.Button> konuda oluşturulan öğesini kullanan bir gösterilmektedir.  
  
 ![Özel denetim şablonuyla bir düğme.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Özel denetim şablonu kullanan bir düğme  
  
 ![Kırmızı kenarlıklı bir düğme.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Özel denetim şablonu kullanan ve üzerinde fare işaretçisi bulunan bir düğme  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu başlığında açıklanan denetimleri ve stilleri oluşturma ve kullanma hakkında bilgi sahibi olduğunuz varsayılır. [](index.md) Bu konu başlığı altında açıklanan kavramlar, <xref:System.Windows.Controls.Control> sınıfının dışında <xref:System.Windows.Controls.UserControl>sınıfından kalıtımla alan öğeler için geçerlidir. Öğesine bir <xref:System.Windows.Controls.ControlTemplate>uygulayamazsınız. <xref:System.Windows.Controls.UserControl>  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Bir ControlTemplate oluşturmanız gerektiğinde  
 Denetimlerin, ve <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>gibi birçok özelliği vardır, ancak bu, denetimin görünümünün farklı yönlerini belirtmek için ayarlayabilirsiniz, ancak bu özellikleri ayarlayarak yapabileceğiniz değişiklikler sınırlıdır. <xref:System.Windows.Controls.Control.FontFamily%2A> Örneğin, <xref:System.Windows.Controls.Control.Foreground%2A> özelliğini mavi ve <xref:System.Windows.Controls.Control.FontStyle%2A> italik olarak bir <xref:System.Windows.Controls.CheckBox>olarak ayarlayabilirsiniz.  
  
 Denetimler için yeni <xref:System.Windows.Controls.ControlTemplate> bir oluşturma özelliği olmadan, her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir tabanlı uygulamadaki tüm denetimler aynı genel görünüme sahip olur ve bu da özel bir görünüm ile uygulama oluşturma özelliğini sınırlandırır. Varsayılan olarak, her <xref:System.Windows.Controls.CheckBox> bir benzer özelliğe sahiptir. Örneğin, öğesinin <xref:System.Windows.Controls.CheckBox> içeriği her zaman seçim göstergesinin sağında bulunur ve onay işareti her zaman seçili <xref:System.Windows.Controls.CheckBox> olduğunu göstermek için kullanılır.  
  
 Denetim görünümünü özelleştirmek <xref:System.Windows.Controls.ControlTemplate> istediğinizde, denetimin diğer özelliklerinin ne yapacakınızın ötesinde bir oluşturmanız gerekir. Örneğinde <xref:System.Windows.Controls.CheckBox>, onay kutusunun içeriğinin seçim göstergesinin üzerinde olmasını istediğinizi ve bir X öğesinin seçili olduğunu belirtmek <xref:System.Windows.Controls.CheckBox> istediğinizi varsayalım. Bu değişiklikleri içinde <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox>belirtirsiniz.  
  
 Aşağıdaki çizimde, varsayılan <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.ControlTemplate>olarak kullanılan bir gösterilmektedir.  
  
 ![Varsayılan denetim şablonuyla bir onay kutusu.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Varsayılan denetim şablonunu kullanan bir onay kutusu  
  
 Aşağıdaki çizimde, bir, <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.CheckBox> Yukarıdaki <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox> seçim göstergesinin içeriğini yerleştirmek için özel bir kullanılan ve seçildiğinde bir X görüntüleyen bir, gösterilmektedir.  
  
 ![Özel denetim şablonuyla bir onay kutusu.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Özel denetim şablonu kullanan bir onay kutusu  
  
 Bu <xref:System.Windows.Controls.ControlTemplate> örnekteki <xref:System.Windows.Controls.ControlTemplate> için için <xref:System.Windows.Controls.Button>, görece karmaşıktır, bu konuda bir için oluşturmak için daha basit bir örnek kullanılmıştır. <xref:System.Windows.Controls.CheckBox>  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Bir denetimin görsel yapısını değiştirme  
 ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, bir denetim genellikle bileşik <xref:System.Windows.FrameworkElement> bir nesne olur. Oluşturduğunuzda <xref:System.Windows.Controls.ControlTemplate>, tek bir denetim oluşturmak için <xref:System.Windows.FrameworkElement> nesneleri birleştirmelisiniz. , Kök öğesi olarak yalnızca <xref:System.Windows.FrameworkElement> bir tane olmalıdır.<xref:System.Windows.Controls.ControlTemplate> Kök öğe genellikle diğer <xref:System.Windows.FrameworkElement> nesneleri içerir. Nesnelerin birleşimi denetimin görsel yapısını oluşturur.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Button>için bir özel <xref:System.Windows.Controls.ControlTemplate> oluşturur. , Öğesinin görsel yapısını <xref:System.Windows.Controls.ControlTemplate>oluşturur. <xref:System.Windows.Controls.Button> Bu örnek, fare işaretçisini üzerine getirdiğinizde düğmenin görünümünü değiştirmez. Düğmenin görünümü farklı bir durumda olduğunda, bu konunun ilerleyen kısımlarında ele alınmıştır.  
  
 Bu örnekte, görsel yapı aşağıdaki bölümlerden oluşur:  
  
- Şablon kökü `RootElement` <xref:System.Windows.Controls.Border> görevi<xref:System.Windows.FrameworkElement>gören adlandırılmış bir ad.  
  
- <xref:System.Windows.Controls.Grid> Öğesinin`RootElement`bir alt öğesidir.  
  
- Düğme <xref:System.Windows.Controls.ContentPresenter> içeriğini görüntüleyen bir. , <xref:System.Windows.Controls.ContentPresenter> Görüntülenecek herhangi bir nesne türünü sağlar.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>TemplateBinding kullanarak bir denetimin özelliklerinin Işlevselliğini koruma  
 Yeni <xref:System.Windows.Controls.ControlTemplate>bir oluşturduğunuzda, denetimin görünümünü değiştirmek için yine de ortak özellikleri kullanmak isteyebilirsiniz. [TemplateBinding](../advanced/templatebinding-markup-extension.md) biçimlendirme uzantısı, <xref:System.Windows.Controls.ControlTemplate> içindeki bir öğesinin özelliğini Denetim tarafından tanımlanan ortak bir özelliğe bağlar. [TemplateBinding](../advanced/templatebinding-markup-extension.md)kullandığınızda, denetimdeki özellikleri şablona parametre olarak davranacak şekilde etkinleştirin. Diğer bir deyişle, bir denetimdeki özellik ayarlandığında, bu değer üzerinde [TemplateBinding](../advanced/templatebinding-markup-extension.md) 'e sahip olan öğeye geçirilir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> düğme tarafından tanımlanan ortak özelliklerde bulunan öğelerin özelliklerini bağlamak için [TemplateBinding](../advanced/templatebinding-markup-extension.md) biçimlendirme uzantısını kullanan önceki örneğin bölümünü yineler.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Bu örnekte <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> , öğesinin özellik şablonu öğesine <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>bağımlıdır. Şablon <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> bağlı olduğundan, aynısını <xref:System.Windows.Controls.ControlTemplate> kullanan birden çok düğme oluşturabilir ve her düğme üzerinde farklı değerlere ayarlayabilirsiniz <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> . Şablon, <xref:System.Windows.Controls.ControlTemplate>içindeki bir öğesinin özelliğine bağlı değilse, bir düğmenin ayarlanması <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> düğmenin görünümü üzerinde hiçbir etkisi olmaz. <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>  
  
 İki özellik adının aynı olması gerekmediğini unutmayın. <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> Önceki örnekte <xref:System.Windows.Controls.Button> , öğesinin özelliği olan <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> özelliğine <xref:System.Windows.Controls.ContentPresenter>bağımlıdır. Bu düğme içeriğinin yatay olarak konumlandırılmasını sağlar. <xref:System.Windows.Controls.ContentPresenter>adında `HorizontalContentAlignment`bir özelliği yoktur, ancak <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> ile <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>bağlanabilir. Şablon bir özelliği bağladığınızda, hedef ve kaynak özelliklerinin aynı türde olduğundan emin olun.  
  
 <xref:System.Windows.Controls.Control> Sınıfı, denetim şablonu tarafından ayarlandıklarında bir etkiye sahip olmak için kullanılması gereken birkaç özelliği tanımlar. Özelliği, <xref:System.Windows.Controls.ControlTemplate> özelliğini kullanarak özelliğine bağlıdır. , <xref:System.Windows.Controls.ControlTemplate> Özelliğini aşağıdaki yollarla kullanmalıdır:  
  
- <xref:System.Windows.Controls.ControlTemplate> Şablondaki bir öğe özelliğe bağlanır.  
  
- İçindeki bir öğesi, <xref:System.Windows.Controls.ControlTemplate> bir üst <xref:System.Windows.FrameworkElement>öğeden özelliği devralır.  
  
 Aşağıdaki tabloda, <xref:System.Windows.Controls.Control> sınıfından bir denetim tarafından devralınan görsel özellikler listelenmiştir. Ayrıca, bir denetimin varsayılan denetim şablonunun devralınan özellik değerini kullanıp kullanmadığını veya şablon bağlanması gerekip gerekmediğini gösterir.  
  
|Özellik|Kullanım yöntemi|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|Şablon bağlama|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Şablon bağlama|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Şablon bağlama|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|Özellik devralma veya şablon bağlama|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Şablon bağlama|  
|<xref:System.Windows.Controls.Control.Padding%2A>|Şablon bağlama|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Şablon bağlama|  
  
 Tabloda yalnızca <xref:System.Windows.Controls.Control> sınıftan devralınan görsel özellikler listelenir. Tabloda listelenen özelliklerden ayrı olarak, bir denetim üst Framework öğesinden <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>ve <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> özelliklerini de alabilir.  
  
 <xref:System.Windows.Controls.ControlTemplate> Ayrıca,<xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> bir içinde<xref:System.Windows.Controls.ContentPresenter> ise, otomatik olarak ve<xref:System.Windows.Controls.ContentControl.Content%2A> özelliklerine bağlanır. <xref:System.Windows.Controls.ContentPresenter> Benzer şekilde, <xref:System.Windows.Controls.ItemsPresenter> <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl.Items%2A> içinde <xref:System.Windows.Controls.ItemsControl> olan bir, ve<xref:System.Windows.Controls.ItemsPresenter> özelliklerine otomatik olarak bağlanır.  
  
 Aşağıdaki örnek, önceki örnekte <xref:System.Windows.Controls.ControlTemplate> tanımlanan öğesini kullanan iki düğme oluşturur. Örnek, her bir <xref:System.Windows.Controls.Control.Background%2A>düğmedeki <xref:System.Windows.Controls.Control.Foreground%2A>,, <xref:System.Windows.Controls.Control.FontSize%2A> ve özelliklerini ayarlar. Özelliğinin ayarlanması bir etkiye sahiptir çünkü <xref:System.Windows.Controls.ControlTemplate>içinde şablon bağlanmıştır. <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A> Ve<xref:System.Windows.Controls.Control.FontSize%2A> özellikleri şablon bağlanmamış olsa da, değerleri devralındığından bu ayarların bir etkisi vardır.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 Yukarıdaki örnek aşağıdaki çizime benzer bir çıktı üretir.  
  
 ![İki düğme, bir mavi ve bir mor.](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
Farklı arka plan renkleriyle iki düğme  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Bir denetimin görünüşünü durumuna göre değiştirme  
 Varsayılan görünümü ile bir düğme arasındaki fark, önceki örnekteki düğme, farklı durumlardadır. Örneğin, düğme basıldığında varsayılan düğme görünümü değişir veya fare işaretçisi düğmenin üzerindeyken değişir. <xref:System.Windows.Controls.ControlTemplate> Bir denetimin işlevselliğini değiştirmese de, denetimin görsel davranışını değiştirir. Görsel bir davranış, belirli bir durumda olduğu zaman denetim görünümünü açıklar. Bir denetimin işlevselliği ve görsel davranışı arasındaki farkı anlamak için, düğme örneğini göz önünde bulundurun. Düğmenin işlevselliği tıklandığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı tetiklemedir, ancak düğmenin görsel davranışı, işaret edildiğinde veya basıldığında görünümünü değiştirmesidir.  
  
 Belirli bir <xref:System.Windows.VisualState> durumda olduğunda bir denetimin görünümünü belirtmek için nesneleri kullanırsınız. , <xref:System.Windows.VisualState> <xref:System.Windows.Media.Animation.Storyboard> İçinde olan öğelerin görünümünü değiştiren bir içerir. <xref:System.Windows.Controls.ControlTemplate> Bunu yapmak için herhangi bir kod yazmanız gerekmez, <xref:System.Windows.VisualStateManager>çünkü denetimin mantığı ' i kullanarak durumu değişir. Denetim, <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Media.Animation.Storyboard> tarafından belirtilen duruma girdiğinde başlar. Denetim durumdan <xref:System.Windows.Media.Animation.Storyboard> çıktığında, duraklar.  
  
 Aşağıdaki örnek, <xref:System.Windows.VisualState> fare işaretçisi üzerine <xref:System.Windows.Controls.Button> geldiğinde görünümünü değiştiren öğesini gösterir. , Düğmesinin rengini `BorderBrush`değiştirerek düğmenin kenarlık rengini değiştirir.<xref:System.Windows.Media.Animation.Storyboard> Bu konunun <xref:System.Windows.Controls.ControlTemplate> başındaki örneğe başvurursanız, ' <xref:System.Windows.Controls.Border.Background%2A> nin `BorderBrush` <xref:System.Windows.Media.SolidColorBrush> ' a atanan öğesinin adı olduğunu anımsayın. <xref:System.Windows.Controls.Border>  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Denetim, bu konunun ilerleyen kısımlarında yer aldığı denetim [sözleşmesini Inceleyerek diğer denetimleri özelleştirme](#customizing_other_controls_by_understanding_the_control_contract) bölümünde ayrıntılı olarak bahsedilen denetim sözleşmesinin bir parçası olarak durumları tanımlamaktan sorumludur. Aşağıdaki tabloda, <xref:System.Windows.Controls.Button>için belirtilen durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Basılan|Ortak durumlar|Denetime basıldığında.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|Diğinize|Odaklardaki durumlar|Denetim odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|  
  
 `CommonStates` `Normal` İkidurum`Pressed`grubunu `MouseOver`tanımlar: Grup,,, ve`Disabled` durumlarını içerir. <xref:System.Windows.Controls.Button> `FocusStates` Grup `Focused` ve durumlarını`Unfocused` içerir. Aynı durum grubundaki durumlar birbirini dışlıyor. Denetim her zaman grup başına tam olarak bir durumdur. Örneğin, fare işaretçisi <xref:System.Windows.Controls.Button> üzerine olmasa bile, bir, `MouseOver` `Focused` durumunda olan bir <xref:System.Windows.Controls.Button> , `Pressed`, veya `Normal` durumunda olabilir.  
  
 Nesneleri <xref:System.Windows.VisualStateGroup> nesnelere <xref:System.Windows.VisualState> eklersiniz. <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> Eklenmiş özelliğe <xref:System.Windows.VisualStateGroup> nesneler eklersiniz. Aşağıdaki örnek,, <xref:System.Windows.VisualState> `MouseOver` `Normal` ve`Pressed`durumları için, Grupiçindeki`CommonStates` tüm nesneleri tanımlar. Öğesinin <xref:System.Windows.VisualState.Name%2A> her<xref:System.Windows.VisualState> biri, önceki tablodaki adla eşleşir. Örnekteki durum ve durumlar `FocusStates` , örnek kısa tutulması için atlanır, ancak bu konunun sonundaki tüm örneğe dahil edilir. `Disabled`  
  
> [!NOTE]
> Öğesinin <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> kökünde<xref:System.Windows.FrameworkElement>iliştirilmiş özelliğini ayarladığınızdan emin olun. <xref:System.Windows.Controls.ControlTemplate>  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 Yukarıdaki örnek, aşağıdaki çizimlerle benzer bir çıktı üretir.  
  
 ![Özel denetim şablonuyla bir düğme.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Normal durumda özel denetim şablonu kullanan bir düğme  
  
 ![Kırmızı kenarlıklı bir düğme.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Üzerinde fare durumunda özel denetim şablonu kullanan bir düğme  
  
 ![Kenarlık, basılan düğmede saydamdır.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Basılan durumda özel denetim şablonu kullanan bir düğme  
  
 İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimlerin görsel durumlarını bulmak için bkz. [denetim stilleri ve şablonları](control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Durumlar arasında geçiş yaparken bir denetimin davranışını belirtme  
 Yukarıdaki örnekte, düğme görünümü Kullanıcı tıkladığı zaman de değişir, ancak düğmeye tam bir saniye boyunca basıldığında kullanıcı etkisini görmez. Varsayılan olarak, animasyonun gerçekleşmesi bir saniye sürer. Kullanıcıların bir düğmeyi çok daha az zaman içinde tıkladığından ve serbest bırakacağından, varsayılan durumunda bıraktığınızda <xref:System.Windows.Controls.ControlTemplate> görsel geri bildirim etkili olmayacaktır.  
  
 <xref:System.Windows.VisualTransition> '<xref:System.Windows.Controls.ControlTemplate>Ye nesneler ekleyerek bir denetimin bir durumdan diğerine düzgün bir şekilde geçişini sağlamak için animasyonun oluşma süresini belirtebilirsiniz. Bir <xref:System.Windows.VisualTransition>oluşturduğunuzda, aşağıdakilerden birini veya birkaçını belirtirsiniz:  
  
- Durumlar arasında geçiş için gereken süre.  
  
- Geçişin sırasında oluşan denetimin görünümünde ek değişiklikler.  
  
- Hangi durumları uygulanacağını <xref:System.Windows.VisualTransition> belirtir.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Bir geçişin süresini belirtme  
 <xref:System.Windows.VisualTransition.GeneratedDuration%2A> Özelliği ayarlayarak bir geçişin ne kadar sürdüğünü belirtebilirsiniz. Yukarıdaki örnekte düğmeye basıldığında düğme <xref:System.Windows.VisualState> kenarlığının saydam hale geldiğini belirten bir, ancak düğmeye hızlı basıldığında ve serbest bırakıldığında animasyonun fark edilebilir olması çok uzun sürer. ' I kullanarak <xref:System.Windows.VisualTransition> , denetimin basılan duruma geçmesi için geçen süreyi belirleyebilirsiniz. Aşağıdaki örnek, denetimin saniyenin bir yüz, basılan duruma gitmesini belirtir.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Geçiş sırasında denetimin görünümünde yapılan değişiklikleri belirtme  
 Denetim durumlar arasında <xref:System.Windows.Media.Animation.Storyboard> geçiş yaptığında başlayan bir içerir.<xref:System.Windows.VisualTransition> Örneğin, Denetim `MouseOver` durumdan `Normal` duruma geçiş yaptığında belirli bir animasyonun meydana geldiğinden emin olabilirsiniz. Aşağıdaki örnek, Kullanıcı fare <xref:System.Windows.VisualTransition> işaretçisini düğmeden uzağa taşısa, düğme kenarlığının mavi, sonra sarı ve sonra 1,5 saniye içinde siyah olarak değiştiği belirten bir oluşturur.  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Bir VisualTransition uygulandığında belirtme  
 <xref:System.Windows.VisualTransition> Yalnızca belirli durumlara uygulanabilir veya denetim durumları arasında geçiş yapıldığında uygulanabilir. <xref:System.Windows.VisualTransition> Yukarıdaki örnekte `Pressed` , Denetim `MouseOver` durumdan `Normal` duruma geçtiğinde uygulanır <xref:System.Windows.VisualTransition> ; önceki örnekte, denetim duruma geçtiğinde uygulanır.... Ve <xref:System.Windows.VisualTransition.To%2A> <xref:System.Windows.VisualTransition> özellikleriniayarlayarak,nezamanuygulanacağınıkısıtlayabilirsiniz<xref:System.Windows.VisualTransition.From%2A> . Aşağıdaki tabloda, en kısıtlayıcı kısıtlama düzeyi en az kısıtlayıcı olan kısıtlama düzeyleri açıklanmaktadır.  
  
|Kısıtlama türü|Değerin değeri|Öğesinin değeri|  
|-------------------------|-------------------|-----------------|  
|Belirtilen bir durumdan belirtilen başka bir duruma|Öğesinin adı<xref:System.Windows.VisualState>|Öğesinin adı<xref:System.Windows.VisualState>|  
|Herhangi bir durumdan belirtilen duruma|Ayarlı değil|Öğesinin adı<xref:System.Windows.VisualState>|  
|Belirtilen bir durumdan herhangi bir duruma|Öğesinin adı<xref:System.Windows.VisualState>|Ayarlı değil|  
|Herhangi bir durumdan diğer bir duruma|Ayarlı değil|Ayarlı değil|  
  
 Aynı duruma başvuran bir <xref:System.Windows.VisualTransition> <xref:System.Windows.VisualStateGroup> içinde birden fazla nesneniz olabilir, ancak bunlar önceki tablonun belirttiği sırada kullanılacaktır. Aşağıdaki örnekte iki <xref:System.Windows.VisualTransition> nesne vardır. Denetim `Pressed` durumdan `MouseOver` duruma geçerse, <xref:System.Windows.VisualTransition> hem hem <xref:System.Windows.VisualTransition.From%2A> de<xref:System.Windows.VisualTransition.To%2A> kümesi kullanılır. Denetim, `Pressed` `MouseOver` durum olmayan bir durumdan geçerse, diğer durum kullanılır.  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup.Transitions%2A> <xref:System.Windows.VisualTransition> , İçindeki nesneler<xref:System.Windows.VisualState> için uygulanan <xref:System.Windows.VisualStateGroup> nesneleriiçeren<xref:System.Windows.VisualStateGroup>bir özelliğine sahiptir. Yazar olarak, istediğiniz her türlü <xref:System.Windows.VisualTransition> dahil edebilirsiniz. <xref:System.Windows.Controls.ControlTemplate> Ancak, <xref:System.Windows.VisualTransition.From%2A> <xref:System.Windows.VisualStateGroup>veözellikleri içinde<xref:System.Windows.VisualTransition> olmayan durum adlarına ayarlanmışsa, yok sayılır. <xref:System.Windows.VisualTransition.To%2A>  
  
 Aşağıdaki örnek, <xref:System.Windows.VisualStateGroup> `CommonStates`için ' i gösterir. Örnek, her düğmenin <xref:System.Windows.VisualTransition> aşağıdaki geçişleri için bir tanımlar.  
  
- `Pressed` Durumuna göre.  
  
- `MouseOver` Durumuna göre.  
  
- `Pressed` Durumdan`MouseOver` durumuna.  
  
- `MouseOver` Durumdan`Normal` durumuna.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Denetim sözleşmesini anlamak için diğer denetimleri özelleştirme  
 Görsel yapısını (nesneleri kullanarak <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.FrameworkElement> ) ve görsel davranışı (nesneleri kullanarak <xref:System.Windows.VisualState> ) belirtmek için kullanan bir denetim, parçalar Denetim modelini kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 ' te yer alan denetimlerin birçoğu bu modeli kullanır. Bir <xref:System.Windows.Controls.ControlTemplate> yazarın farkında olması gereken bölümler denetim sözleşmesiyle iletilir. Bir denetim sözleşmesinin parçalarını anladığınızda, bölümler denetim modelini kullanan herhangi bir denetimin görünümünü özelleştirebilirsiniz.  
  
 Bir denetim sözleşmesinin üç öğesi vardır:  
  
- Denetimin mantığının kullandığı görsel öğeler.  
  
- Denetimin durumları ve her durumun ait olduğu grup.  
  
- Denetimi görsel olarak etkileyen ortak özellikler.  
  
### <a name="visual-elements-in-the-control-contract"></a>Denetim sözleşmesindeki görsel öğeler  
 Bazen bir denetimin mantığı, <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>içinde olan ile etkileşime girer. Örneğin, denetim öğelerinden birinin bir olayını işleyebilir. Bir denetim <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate> içinde belirli bir ' ibulmayıbekliyorsa,bubilgileriyazarailetmelidir.<xref:System.Windows.Controls.ControlTemplate> Denetim, <xref:System.Windows.TemplatePartAttribute> beklenen öğe türünü ve öğenin adının ne olması gerektiğini belirtmek için öğesini kullanır. , Denetim sözleşmesinde <xref:System.Windows.Controls.ComboBox>parçalar içermez, ancak gibi diğer denetimler. <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.Button>  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ComboBox> sınıfında belirtilen <xref:System.Windows.TemplatePartAttribute> nesneleri gösterir. Mantığı <xref:System.Windows.Controls.ComboBox> adında bir <xref:System.Windows.Controls.TextBox> adlandırılmış `PART_EditableTextBox` ve <xref:System.Windows.Controls.Primitives.Popup> adı bulmayı`PART_Popup`bekler .<xref:System.Windows.Controls.ControlTemplate>  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 Aşağıdaki <xref:System.Windows.Controls.ControlTemplate> örnek, <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.TemplatePartAttribute> sınıfındaki nesneler<xref:System.Windows.Controls.ComboBox> tarafından belirtilen öğeleri içeren için basitleşme gösterir.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Denetim sözleşmesindeki durumlar  
 Bir denetimin durumları da denetim sözleşmesinin bir parçasıdır. Bir <xref:System.Windows.Controls.ControlTemplate> içinoluşturma<xref:System.Windows.Controls.Button> örneği, durumlarına bağlı olarak görünümünü nasıl belirttiğinize gösterir.<xref:System.Windows.Controls.Button> Bir denetimin görünümünü <xref:System.Windows.VisualState> bu konunun önceki [durumuna göre değiştirme](#changing_the_appearance_of_a_control_depending_on_its_state) bölümünde açıklandığı gibi, belirtilen <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> her bir <xref:System.Windows.VisualStateGroup>durum için bir oluşturur ve ' a paylaşan tüm <xref:System.Windows.VisualState> nesneleri ' a yerleştirebilirsiniz. Üçüncü taraf denetimleri,, ifade Blend gibi tasarımcı araçlarının <xref:System.Windows.TemplateVisualStateAttribute>denetim şablonlarının yazma durumlarını açığa çıkarmak için kullanarak durumları belirtmelidir.  
  
 İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimlerin denetim sözleşmesini bulmak için bkz. [denetim stilleri ve şablonları](control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Denetim sözleşmesindeki Özellikler  
 Denetimi görsel olarak etkileyen ortak özellikler Denetim sözleşmesine de dahildir. Bu özellikleri, denetimin görünümünü yeni <xref:System.Windows.Controls.ControlTemplate>bir oluşturmadan değiştirecek şekilde ayarlayabilirsiniz. Tarafından [](../advanced/templatebinding-markup-extension.md) <xref:System.Windows.Controls.ControlTemplate> tanımlananortaközelliklerdeolanöğelerinözelliklerinibağlamakiçinTemplateBindingbiçimlendirmeuzantısınıda<xref:System.Windows.Controls.Button>kullanabilirsiniz.  
  
 Aşağıdaki örnek, düğme için denetim sözleşmesini gösterir.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Bir <xref:System.Windows.Controls.ControlTemplate>oluştururken, varolan <xref:System.Windows.Controls.ControlTemplate> bir ile başlamak ve üzerinde değişiklik yapmak genellikle en kolay yoldur. Varolan <xref:System.Windows.Controls.ControlTemplate>bir değişikliği değiştirmek için aşağıdakilerden birini yapabilirsiniz:  
  
- Denetim şablonları oluşturmak için grafik kullanıcı arabirimi sağlayan Ifade Blend gibi bir tasarımcı kullanın. Daha fazla bilgi için bkz. [şablonları destekleyen bir denetimin stillendirme](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
- Varsayılanı <xref:System.Windows.Controls.ControlTemplate> alın ve düzenleyin. İle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]birlikte gelen varsayılan denetim şablonlarını bulmak için bkz. [varsayılan WPF temaları](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu konuda ele <xref:System.Windows.Controls.Button> alınan tamamlanmış <xref:System.Windows.Controls.ControlTemplate> işlemi gösterir.  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](styling-and-templating.md)
