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
ms.openlocfilehash: 0c79ba3dd42f2e65eb241409946e921577ced5f1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920060"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme
<a name="introduction"></a><xref:System.Windows.Controls.ControlTemplate> bir denetimin görsel yapısını ve görsel davranışını belirtir. Bir denetimin görünümünü yeni bir <xref:System.Windows.Controls.ControlTemplate>vererek özelleştirebilirsiniz. Bir <xref:System.Windows.Controls.ControlTemplate>oluşturduğunuzda, mevcut bir denetimin görünüşünü, işlevselliğini değiştirmeden değiştirirsiniz. Örneğin, uygulamadaki düğmeleri varsayılan kare şekli yerine yuvarlayabilmeniz, ancak düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayını yine de yükseltecektir.

 Bu konu, bir <xref:System.Windows.Controls.ControlTemplate>çeşitli parçalarını açıklar, bir <xref:System.Windows.Controls.Button>için basit bir <xref:System.Windows.Controls.ControlTemplate> oluşturmayı gösterir ve görünümünü özelleştirebilmeniz için bir denetimin denetim sözleşmesinin nasıl anlaşılmasını açıklar. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<xref:System.Windows.Controls.ControlTemplate> oluşturduğunuz için, bir denetimin görünümünü herhangi bir kod yazmadan değiştirebilirsiniz. Özel denetim şablonları oluşturmak için Visual Studio için Blend gibi bir tasarımcı de kullanabilirsiniz. Bu konuda, bir <xref:System.Windows.Controls.Button> görünümünü özelleştiren [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnekler gösterilmektedir ve konunun sonundaki tüm örnek listelenir. Visual Studio için Blend kullanma hakkında daha fazla bilgi için, bkz. [şablonları destekleyen bir denetimin stillendirme](https://go.microsoft.com/fwlink/?LinkId=161153).

 Aşağıdaki çizimlerde, bu konuda oluşturulan <xref:System.Windows.Controls.ControlTemplate> kullanan bir <xref:System.Windows.Controls.Button> gösterilmektedir.

 ![Özel denetim şablonuyla bir düğme.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Özel denetim şablonu kullanan bir düğme

 ![Kırmızı kenarlıklı bir düğme.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Özel denetim şablonu kullanan ve üzerinde fare işaretçisi bulunan bir düğme

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Prerequisites
 Bu konu başlığında [açıklanan denetimleri ve](index.md)stilleri oluşturma ve kullanma hakkında bilgi sahibi olduğunuz varsayılır. Bu konu başlığı altında açıklanan kavramlar, <xref:System.Windows.Controls.UserControl>hariç <xref:System.Windows.Controls.Control> sınıfından kalıtımla alan öğeler için geçerlidir. Bir <xref:System.Windows.Controls.UserControl><xref:System.Windows.Controls.ControlTemplate> uygulayamazsınız.

<a name="when_you_should_create_a_controltemplate"></a>
## <a name="when-you-should-create-a-controltemplate"></a>Bir ControlTemplate oluşturmanız gerektiğinde
 Denetimlerin, <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>ve <xref:System.Windows.Controls.Control.FontFamily%2A>gibi birçok özelliği vardır, bu da denetimin görünümünün farklı yönlerini belirtmek için ayarlayabilirsiniz, ancak bu özellikleri ayarlayarak yapabileceğiniz değişiklikler sınırlıdır. Örneğin, <xref:System.Windows.Controls.Control.Foreground%2A> özelliğini mavi ve <xref:System.Windows.Controls.CheckBox><xref:System.Windows.Controls.Control.FontStyle%2A> italik olarak ayarlayabilirsiniz.

 Denetimler için yeni bir <xref:System.Windows.Controls.ControlTemplate> oluşturma özelliği olmadan, her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamadaki tüm denetimler aynı genel görünüme sahip olur ve bu da özel bir görünüm ile uygulama oluşturma özelliğini sınırlayabilir. Varsayılan olarak, her <xref:System.Windows.Controls.CheckBox> benzer özelliklere sahiptir. Örneğin, <xref:System.Windows.Controls.CheckBox> içeriği her zaman seçim göstergesinin sağında bulunur ve onay işareti her zaman <xref:System.Windows.Controls.CheckBox> seçili olduğunu göstermek için kullanılır.

 Denetimin diğer özelliklerinin ne yapacakından sonra denetimin görünümünü özelleştirmek istediğinizde bir <xref:System.Windows.Controls.ControlTemplate> oluşturursunuz. <xref:System.Windows.Controls.CheckBox>örneğinde, onay kutusunun içeriğinin seçim göstergesinin üzerinde olmasını istediğinizi ve bir X öğesinin <xref:System.Windows.Controls.CheckBox> seçili olduğunu belirtmek istediğinizi varsayalım. Bu değişiklikleri <xref:System.Windows.Controls.CheckBox><xref:System.Windows.Controls.ControlTemplate> belirlersiniz.

 Aşağıdaki çizimde, varsayılan <xref:System.Windows.Controls.ControlTemplate>kullanan bir <xref:System.Windows.Controls.CheckBox> gösterilmektedir.

 ![Varsayılan denetim şablonuyla bir onay kutusu.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Varsayılan denetim şablonunu kullanan bir onay kutusu

 Aşağıdaki çizim, <xref:System.Windows.Controls.CheckBox> içeriğini seçim göstergesinin üzerine yerleştirmek için özel bir <xref:System.Windows.Controls.ControlTemplate> kullanan <xref:System.Windows.Controls.CheckBox> gösterir ve <xref:System.Windows.Controls.CheckBox> seçildiğinde bir X görüntüler.

 ![Özel denetim şablonuyla bir onay kutusu.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Özel denetim şablonu kullanan bir onay kutusu

 Bu örnekteki <xref:System.Windows.Controls.CheckBox> için <xref:System.Windows.Controls.ControlTemplate> nispeten karmaşıktır, bu nedenle bu konu, <xref:System.Windows.Controls.Button>için <xref:System.Windows.Controls.ControlTemplate> oluşturmanın daha basit bir örneğini kullanır.

<a name="changing_the_visual_structure_of_a_control"></a>
## <a name="changing-the-visual-structure-of-a-control"></a>Bir denetimin görsel yapısını değiştirme
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir denetim genellikle bileşik <xref:System.Windows.FrameworkElement> nesneleridir. Bir <xref:System.Windows.Controls.ControlTemplate>oluşturduğunuzda, tek bir denetim oluşturmak için <xref:System.Windows.FrameworkElement> nesneleri birleştirmelisiniz. <xref:System.Windows.Controls.ControlTemplate>, kök öğesi olarak yalnızca bir <xref:System.Windows.FrameworkElement> içermelidir. Kök öğe genellikle diğer <xref:System.Windows.FrameworkElement> nesneleri içerir. Nesnelerin birleşimi denetimin görsel yapısını oluşturur.

 Aşağıdaki örnek, <xref:System.Windows.Controls.Button>için özel bir <xref:System.Windows.Controls.ControlTemplate> oluşturur. <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Button>görsel yapısını oluşturur. Bu örnek, fare işaretçisini üzerine getirdiğinizde düğmenin görünümünü değiştirmez. Düğmenin görünümü farklı bir durumda olduğunda, bu konunun ilerleyen kısımlarında ele alınmıştır.

 Bu örnekte, görsel yapı aşağıdaki bölümlerden oluşur:

- Şablonun kök <xref:System.Windows.FrameworkElement>olarak hizmet veren `RootElement` adlı bir <xref:System.Windows.Controls.Border>.

- `RootElement`alt öğesi olan bir <xref:System.Windows.Controls.Grid>.

- Düğmenin içeriğini görüntüleyen bir <xref:System.Windows.Controls.ContentPresenter>. <xref:System.Windows.Controls.ContentPresenter>, her tür nesnenin görüntülenmesini sağlar.

 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]

### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>TemplateBinding kullanarak bir denetimin özelliklerinin Işlevselliğini koruma
 Yeni bir <xref:System.Windows.Controls.ControlTemplate>oluşturduğunuzda, denetimin görünümünü değiştirmek için yine de ortak özellikleri kullanmak isteyebilirsiniz. [TemplateBinding](../advanced/templatebinding-markup-extension.md) biçimlendirme uzantısı, <xref:System.Windows.Controls.ControlTemplate> olan bir öğenin özelliğini Denetim tarafından tanımlanan ortak bir özelliğe bağlar. [TemplateBinding](../advanced/templatebinding-markup-extension.md)kullandığınızda, denetimdeki özellikleri şablona parametre olarak davranacak şekilde etkinleştirin. Diğer bir deyişle, bir denetimdeki özellik ayarlandığında, bu değer üzerinde [TemplateBinding](../advanced/templatebinding-markup-extension.md) 'e sahip olan öğeye geçirilir.

 Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> olan öğelerin özelliklerini düğme tarafından tanımlanan ortak özelliklerle bağlamak için [TemplateBinding](../advanced/templatebinding-markup-extension.md) biçimlendirme uzantısını kullanan önceki örneğin bölümünü yineler.

 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]

 Bu örnekte, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> Özellik şablonu <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>'e bağımlıdır. <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> şablon bağlı olduğundan, aynı <xref:System.Windows.Controls.ControlTemplate> kullanan birden çok düğme oluşturabilir ve <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> her düğme üzerinde farklı değerlere ayarlayabilirsiniz. <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.ControlTemplate>bir öğenin bir özelliğine bağlı değilse, bir düğmenin <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> ayarlamanın düğmenin görünümü üzerinde hiçbir etkisi olmaz.

 İki özellik adının aynı olması gerekmediğini unutmayın. Yukarıdaki örnekte, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> özelliğine bağımlıdır. Bu düğme içeriğinin yatay olarak konumlandırılmasını sağlar. <xref:System.Windows.Controls.ContentPresenter>, `HorizontalContentAlignment`adında bir özelliğe sahip değildir ancak <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>bağlanabilir. Şablon bir özelliği bağladığınızda, hedef ve kaynak özelliklerinin aynı türde olduğundan emin olun.

 <xref:System.Windows.Controls.Control> sınıfı, denetim şablonu tarafından ayarlandıklarında bir etkiye sahip olmak için kullanılması gereken birkaç özelliği tanımlar. <xref:System.Windows.Controls.ControlTemplate> özelliğini kullanma özelliği, özelliğine bağlıdır. <xref:System.Windows.Controls.ControlTemplate>, özelliği aşağıdaki yollarla kullanmalıdır:

- <xref:System.Windows.Controls.ControlTemplate> şablonundaki bir öğe özelliğe bağlanır.

- <xref:System.Windows.Controls.ControlTemplate> bir öğe, bir üst <xref:System.Windows.FrameworkElement>özelliğini devralır.

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

 Tablo yalnızca <xref:System.Windows.Controls.Control> sınıfından devralınan görsel özellikleri listeler. Tabloda listelenen özelliklerden ayrı olarak, bir denetim üst Framework öğesinden <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>ve <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> özelliklerini de alabilir.

 Ayrıca, <xref:System.Windows.Controls.ContentPresenter> bir <xref:System.Windows.Controls.ContentControl><xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.ContentPresenter> otomatik olarak <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliklerine bağlanır. Benzer şekilde, bir <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ControlTemplate> bir <xref:System.Windows.Controls.ItemsPresenter> otomatik olarak <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.ItemsPresenter> özelliklerine bağlanır.

 Aşağıdaki örnek, önceki örnekte tanımlanan <xref:System.Windows.Controls.ControlTemplate> kullanan iki düğme oluşturur. Örnek, her düğme üzerinde <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>ve <xref:System.Windows.Controls.Control.FontSize%2A> özelliklerini ayarlar. <xref:System.Windows.Controls.Control.Background%2A> özelliğinin ayarlanması bir etkiye sahiptir çünkü bu, <xref:System.Windows.Controls.ControlTemplate>şablon bağlantılı. <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.FontSize%2A> özellikleri şablon bağlanmamış olsa da, bunların değerleri devralındığından, bunların ayarlanması bir etkiye sahip olur.

 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]

 Yukarıdaki örnek aşağıdaki çizime benzer bir çıktı üretir.

 ![İki düğme, bir mavi ve bir mor.](./media/ndp-buttontwo.png "NDP_ButtonTwo")
Farklı arka plan renkleriyle iki düğme

<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Bir denetimin görünüşünü durumuna göre değiştirme
 Varsayılan görünümü ile bir düğme arasındaki fark, önceki örnekteki düğme, farklı durumlardadır. Örneğin, düğme basıldığında varsayılan düğme görünümü değişir veya fare işaretçisi düğmenin üzerindeyken değişir. <xref:System.Windows.Controls.ControlTemplate> bir denetimin işlevselliğini değiştirmese de, denetimin görsel davranışını değiştirir. Görsel bir davranış, belirli bir durumda olduğu zaman denetim görünümünü açıklar. Bir denetimin işlevselliği ve görsel davranışı arasındaki farkı anlamak için, düğme örneğini göz önünde bulundurun. Düğmenin işlevselliği, tıklandığı zaman <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı tetiklemedir, ancak düğmenin görsel davranışı, işaret edildiğinde veya basıldığında görünümünü değiştirmesidir.

 Belirli bir durumda olduğunda bir denetimin görünümünü belirtmek için <xref:System.Windows.VisualState> nesneleri kullanırsınız. <xref:System.Windows.VisualState>, <xref:System.Windows.Controls.ControlTemplate>olan öğelerin görünümünü değiştiren bir <xref:System.Windows.Media.Animation.Storyboard> içerir. Denetimin mantığı <xref:System.Windows.VisualStateManager>kullanarak durumu değiştiğinden, bunu yapmak için herhangi bir kod yazmanız gerekmez. Denetim, <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> özelliği tarafından belirtilen duruma girdiğinde <xref:System.Windows.Media.Animation.Storyboard> başlar. Denetim durumdan çıktığında <xref:System.Windows.Media.Animation.Storyboard> durduruluyor.

 Aşağıdaki örnekte, fare işaretçisi üzerindeyken bir <xref:System.Windows.Controls.Button> görünümünü değiştiren <xref:System.Windows.VisualState> gösterilmektedir. <xref:System.Windows.Media.Animation.Storyboard>, `BorderBrush`rengini değiştirerek düğmenin kenarlık rengini değiştirir. Bu konunun başındaki <xref:System.Windows.Controls.ControlTemplate> örneğe başvurursanız, bu `BorderBrush`, <xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Border.Background%2A> atanan <xref:System.Windows.Media.SolidColorBrush> adı olduğunu hatırlayacaksınız.

 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]

 Denetim, bu konunun ilerleyen kısımlarında yer aldığı denetim [sözleşmesini Inceleyerek diğer denetimleri özelleştirme](#customizing_other_controls_by_understanding_the_control_contract) bölümünde ayrıntılı olarak bahsedilen denetim sözleşmesinin bir parçası olarak durumları tanımlamaktan sorumludur. Aşağıdaki tabloda <xref:System.Windows.Controls.Button>için belirtilen durumlar listelenmektedir.

|VisualState adı|VisualStateGroup adı|Açıklama|
|----------------------|---------------------------|-----------------|
|Olağan|Ortak durumlar|Varsayılan durum.|
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|
|Basılması|Ortak durumlar|Denetime basıldığında.|
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|
|Diğinize|Odaklardaki durumlar|Denetim odağa sahiptir.|
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|

 <xref:System.Windows.Controls.Button> iki durum grubunu tanımlar: `CommonStates` grubu `Normal`, `MouseOver`, `Pressed`ve `Disabled` durumlarını içerir. `FocusStates` grubu `Focused` ve `Unfocused` durumlarını içerir. Aynı durum grubundaki durumlar birbirini dışlıyor. Denetim her zaman grup başına tam olarak bir durumdur. Örneğin, fare işaretçisi üzerine olmasa bile bir <xref:System.Windows.Controls.Button> odağa sahip olabilir, bu nedenle `Focused` durumundaki bir <xref:System.Windows.Controls.Button> `MouseOver`, `Pressed`veya `Normal` durumunda olabilir.

 <xref:System.Windows.VisualStateGroup> nesnelerine <xref:System.Windows.VisualState> nesneleri eklersiniz. <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> iliştirilmiş özelliğine <xref:System.Windows.VisualStateGroup> nesneleri eklersiniz. Aşağıdaki örnek, `CommonStates` grubunda bulunan `Normal`, `MouseOver`ve `Pressed` durumları için <xref:System.Windows.VisualState> nesnelerini tanımlar. Her bir <xref:System.Windows.VisualState> <xref:System.Windows.VisualState.Name%2A>, önceki tablodaki adla eşleşir. Örnek kısa tutmak için `Disabled` durumu ve `FocusStates` grubundaki durumlar atlanır, ancak bu konunun sonundaki tüm örneğe dahil edilmiştir.

> [!NOTE]
> <xref:System.Windows.Controls.ControlTemplate>kök <xref:System.Windows.FrameworkElement> <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> ekli özelliği ayarladığınızdan emin olun.

 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]

 Yukarıdaki örnek, aşağıdaki çizimlerle benzer bir çıktı üretir.

 ![Özel denetim şablonuyla bir düğme.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Normal durumda özel denetim şablonu kullanan bir düğme

 ![Kırmızı kenarlıklı bir düğme.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Üzerinde fare durumunda özel denetim şablonu kullanan bir düğme

 ![Kenarlık, basılan düğmede saydamdır.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")
Basılan durumda özel denetim şablonu kullanan bir düğme

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]eklenen denetimlerin görsel durumlarını bulmak için bkz. [denetim stilleri ve şablonları](control-styles-and-templates.md).

<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Durumlar arasında geçiş yaparken bir denetimin davranışını belirtme
 Yukarıdaki örnekte, düğme görünümü Kullanıcı tıkladığı zaman de değişir, ancak düğmeye tam bir saniye boyunca basıldığında kullanıcı etkisini görmez. Varsayılan olarak, animasyonun gerçekleşmesi bir saniye sürer. Kullanıcıların, bir düğmeyi çok daha az zamanda tıkladığı ve serbest bırakabildiğinden, <xref:System.Windows.Controls.ControlTemplate> varsayılan durumunda bırakırsanız görsel geri bildirim geçerli olmayacaktır.

 <xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.VisualTransition> nesneleri ekleyerek bir denetimin bir durumdan diğerine düzgün bir şekilde geçişini sağlamak için animasyonun ne kadar süre içinde gerçekleşmesini sağlayabilirsiniz. Bir <xref:System.Windows.VisualTransition>oluşturduğunuzda aşağıdakilerden birini veya birkaçını belirtirsiniz:

- Durumlar arasında geçiş için gereken süre.

- Geçişin sırasında oluşan denetimin görünümünde ek değişiklikler.

- <xref:System.Windows.VisualTransition> hangi durumlarda uygulanacağını belirtir.

### <a name="specifying-the-duration-of-a-transition"></a>Bir geçişin süresini belirtme
 <xref:System.Windows.VisualTransition.GeneratedDuration%2A> özelliğini ayarlayarak bir geçişin ne kadar sürdüğünü belirtebilirsiniz. Yukarıdaki örnekte, düğme basıldığında düğme kenarlığının saydam hale geldiğini belirten bir <xref:System.Windows.VisualState> vardır, ancak düğme hızlı basıldığında ve serbest bırakıldığında animasyonun fark edilebilir olması çok uzun sürer. Bir <xref:System.Windows.VisualTransition>, denetimin basılan duruma geçmesi için geçen süreyi belirtmek için kullanabilirsiniz. Aşağıdaki örnek, denetimin saniyenin bir yüz, basılan duruma gitmesini belirtir.

 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]

### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Geçiş sırasında denetimin görünümünde yapılan değişiklikleri belirtme
 <xref:System.Windows.VisualTransition>, denetim durumlar arasında geçiş yaptığında başlayan bir <xref:System.Windows.Media.Animation.Storyboard> içerir. Örneğin, denetim `MouseOver` durumundan `Normal` durumuna geçiş yaptığında belirli bir animasyonun meydana geldiğinden emin olabilirsiniz. Aşağıdaki örnek, Kullanıcı fare işaretçisini düğmeden uzağa taşısa, düğme kenarlığının mavi, sonra sarı ve ardından 1,5 saniye içinde siyah olarak değiştiği belirten bir <xref:System.Windows.VisualTransition> oluşturur.

 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]

### <a name="specifying-when-a-visualtransition-is-applied"></a>Bir VisualTransition uygulandığında belirtme
 Bir <xref:System.Windows.VisualTransition> yalnızca belirli durumlara uygulanabilir veya denetim durumları arasında geçiş yaptığında uygulanabilir. Yukarıdaki örnekte, denetim `MouseOver` durumundan `Normal` durumuna geçtiğinde <xref:System.Windows.VisualTransition> uygulanır; Bu örnekte, denetim `Pressed` durumuna geçtiğinde <xref:System.Windows.VisualTransition> uygulanır. <xref:System.Windows.VisualTransition.To%2A> ve <xref:System.Windows.VisualTransition.From%2A> özelliklerini ayarlayarak <xref:System.Windows.VisualTransition> ne zaman uygulanacağını kısıtlayabilirsiniz. Aşağıdaki tabloda, en kısıtlayıcı kısıtlama düzeyi en az kısıtlayıcı olan kısıtlama düzeyleri açıklanmaktadır.

|Kısıtlama türü|Değerin değeri|Öğesinin değeri|
|-------------------------|-------------------|-----------------|
|Belirtilen bir durumdan belirtilen başka bir duruma|<xref:System.Windows.VisualState> adı|<xref:System.Windows.VisualState> adı|
|Herhangi bir durumdan belirtilen duruma|Ayarlı değil|<xref:System.Windows.VisualState> adı|
|Belirtilen bir durumdan herhangi bir duruma|<xref:System.Windows.VisualState> adı|Ayarlı değil|
|Herhangi bir durumdan diğer bir duruma|Ayarlı değil|Ayarlı değil|

 Aynı duruma başvuran bir <xref:System.Windows.VisualStateGroup> birden çok <xref:System.Windows.VisualTransition> nesneniz olabilir, ancak bunlar önceki tablonun belirttiği sırada kullanılacaktır. Aşağıdaki örnekte, iki <xref:System.Windows.VisualTransition> nesnesi vardır. Denetim `Pressed` durumundan `MouseOver` durumuna geçerse, hem <xref:System.Windows.VisualTransition.From%2A> hem de <xref:System.Windows.VisualTransition.To%2A> kümesi olan <xref:System.Windows.VisualTransition> kullanılır. Denetim, `MouseOver` duruma `Pressed` olmayan bir durumdan geçerse, diğer durum kullanılır.

 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]

 <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualStateGroup><xref:System.Windows.VisualState> nesneler için uygulanan <xref:System.Windows.VisualTransition> nesnelerini içeren bir <xref:System.Windows.VisualStateGroup.Transitions%2A> özelliğine sahiptir. <xref:System.Windows.Controls.ControlTemplate> yazar olarak istediğiniz <xref:System.Windows.VisualTransition> ekleyebilirsiniz. Ancak, <xref:System.Windows.VisualTransition.To%2A> ve <xref:System.Windows.VisualTransition.From%2A> özellikleri <xref:System.Windows.VisualStateGroup>olmayan durum adlarına ayarlandıysa, <xref:System.Windows.VisualTransition> yok sayılır.

 Aşağıdaki örnek, `CommonStates`<xref:System.Windows.VisualStateGroup> gösterir. Örnek, düğmenin aşağıdaki geçişlerinin her biri için bir <xref:System.Windows.VisualTransition> tanımlar.

- `Pressed` durumuna.

- `MouseOver` durumuna.

- `Pressed` durumundan `MouseOver` durumuna.

- `MouseOver` durumundan `Normal` durumuna.

 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]

<a name="customizing_other_controls_by_understanding_the_control_contract"></a>
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Denetim sözleşmesini anlamak için diğer denetimleri özelleştirme
 Görsel yapısını (<xref:System.Windows.FrameworkElement> nesneleri kullanarak) ve görsel davranışı (<xref:System.Windows.VisualState> nesneleri kullanarak) belirtmek için <xref:System.Windows.Controls.ControlTemplate> kullanan bir denetim, parçalar Denetim modelini kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 ' te yer alan denetimlerin birçoğu bu modeli kullanır. <xref:System.Windows.Controls.ControlTemplate> yazarının farkında olması gereken bölümler denetim sözleşmesi aracılığıyla iletilerdir. Bir denetim sözleşmesinin parçalarını anladığınızda, bölümler denetim modelini kullanan herhangi bir denetimin görünümünü özelleştirebilirsiniz.

 Bir denetim sözleşmesinin üç öğesi vardır:

- Denetimin mantığının kullandığı görsel öğeler.

- Denetimin durumları ve her durumun ait olduğu grup.

- Denetimi görsel olarak etkileyen ortak özellikler.

### <a name="visual-elements-in-the-control-contract"></a>Denetim sözleşmesindeki görsel öğeler
 Bazen bir denetimin mantığı, <xref:System.Windows.Controls.ControlTemplate>bir <xref:System.Windows.FrameworkElement> ile etkileşime girer. Örneğin, denetim öğelerinden birinin bir olayını işleyebilir. Bir denetim <xref:System.Windows.Controls.ControlTemplate>belirli bir <xref:System.Windows.FrameworkElement> bulmayı bekliyorsa, bu bilgileri <xref:System.Windows.Controls.ControlTemplate> yazarına iletmelidir. Denetim, beklenen öğe türünü ve öğenin adının ne olması gerektiğini <xref:System.Windows.TemplatePartAttribute> kullanır. <xref:System.Windows.Controls.Button>, denetim sözleşmesinde <xref:System.Windows.FrameworkElement> parçaya sahip değil, ancak <xref:System.Windows.Controls.ComboBox>gibi diğer denetimler.

 Aşağıdaki örnek, <xref:System.Windows.Controls.ComboBox> sınıfında belirtilen <xref:System.Windows.TemplatePartAttribute> nesneleri gösterir. <xref:System.Windows.Controls.ComboBox> mantığı `PART_EditableTextBox` adlı bir <xref:System.Windows.Controls.TextBox> ve `PART_Popup` adında bir <xref:System.Windows.Controls.Primitives.Popup> bulmayı bekler.

 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]

 Aşağıdaki örnek, <xref:System.Windows.Controls.ComboBox> sınıfında <xref:System.Windows.TemplatePartAttribute> nesneleri tarafından belirtilen öğeleri içeren <xref:System.Windows.Controls.ComboBox> için basitleştirilmiş bir <xref:System.Windows.Controls.ControlTemplate> gösterir.

 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]

### <a name="states-in-the-control-contract"></a>Denetim sözleşmesindeki durumlar
 Bir denetimin durumları da denetim sözleşmesinin bir parçasıdır. Bir <xref:System.Windows.Controls.Button> için <xref:System.Windows.Controls.ControlTemplate> oluşturma örneği, durumlarına bağlı olarak bir <xref:System.Windows.Controls.Button> görünümünü belirtmeyi gösterir. Belirtilen her durum için bir <xref:System.Windows.VisualState> oluşturur ve bir <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> paylaşan tüm <xref:System.Windows.VisualState> nesnelerini, bu konunun önceki [durumuna bağlı olarak bir denetimin görünümünü değiştirme](#changing_the_appearance_of_a_control_depending_on_its_state) bölümünde açıklandığı gibi bir <xref:System.Windows.VisualStateGroup>. Üçüncü taraf denetimleri, Visual Studio 'daki [XAML Tasarımcısı](/visualstudio/xaml-tools/designing-xaml-in-visual-studio) gibi tasarımcı araçlarının ve Visual Studio için Blend denetim şablonlarının yazma durumlarını açığa çıkarmak için <xref:System.Windows.TemplateVisualStateAttribute>kullanarak durumları belirtmelidir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]eklenen denetimler için denetim sözleşmesini bulmak için bkz. [denetim stilleri ve şablonları](control-styles-and-templates.md).

### <a name="properties-in-the-control-contract"></a>Denetim sözleşmesindeki Özellikler
 Denetimi görsel olarak etkileyen ortak özellikler Denetim sözleşmesine de dahildir. Bu özellikleri, denetimin görünümünü yeni bir <xref:System.Windows.Controls.ControlTemplate>oluşturmadan değiştirecek şekilde ayarlayabilirsiniz. Ayrıca, <xref:System.Windows.Controls.ControlTemplate> olan öğelerin özelliklerini <xref:System.Windows.Controls.Button>tarafından tanımlanan ortak özelliklerle bağlamak için [TemplateBinding](../advanced/templatebinding-markup-extension.md) biçimlendirme uzantısını da kullanabilirsiniz.

 Aşağıdaki örnek, düğme için denetim sözleşmesini gösterir.

 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]

 <xref:System.Windows.Controls.ControlTemplate>oluştururken, var olan bir <xref:System.Windows.Controls.ControlTemplate> başlamak ve üzerinde değişiklik yapmak genellikle en kolay yoldur. Mevcut bir <xref:System.Windows.Controls.ControlTemplate>değiştirmek için aşağıdakilerden birini yapabilirsiniz:

- Denetim şablonları oluşturmak için grafik kullanıcı arabirimi sağlayan Visual Studio için Blend gibi bir tasarımcı kullanın. Daha fazla bilgi için bkz. [şablonları destekleyen bir denetimin stillendirme](https://go.microsoft.com/fwlink/?LinkId=161153).

- Varsayılan <xref:System.Windows.Controls.ControlTemplate> alın ve düzenleyin. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]eklenen varsayılan denetim şablonlarını bulmak için bkz. [varsayılan WPF temaları](https://go.microsoft.com/fwlink/?LinkID=158252).

<a name="complete_example"></a>
## <a name="complete-example"></a>Tam Örnek
 Aşağıdaki örnek, bu konuda ele alınan tüm <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate> gösterir.

 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](styling-and-templating.md)
