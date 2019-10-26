---
title: Özelleştirilebilir Görünümü olan Denetim Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: c98035ef0b4ea1add22b09fb9927bcd49c00cd9b
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920037"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Özelleştirilebilir Görünümü olan Denetim Oluşturma

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], görünümü özelleştirilebilen bir denetim oluşturma olanağı sağlar. Örneğin, yeni bir <xref:System.Windows.Controls.ControlTemplate>oluşturarak, özelliği ayarların ne yapacakından daha fazla <xref:System.Windows.Controls.CheckBox> görünümünü değiştirebilirsiniz. Aşağıdaki çizimde, varsayılan <xref:System.Windows.Controls.ControlTemplate> ve özel bir <xref:System.Windows.Controls.ControlTemplate>kullanan bir <xref:System.Windows.Controls.CheckBox> kullanan bir <xref:System.Windows.Controls.CheckBox> gösterilmektedir.

![Varsayılan denetim şablonuyla bir onay kutusu.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Varsayılan denetim şablonunu kullanan bir onay kutusu

![Özel denetim şablonuyla bir onay kutusu.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Özel denetim şablonu kullanan bir onay kutusu

Bir denetim oluştururken parçalar ve durumlar modelini izlerseniz, denetiminizin görünümü özelleştirilebilir olur. Visual Studio için Blend gibi tasarımcı araçları parçalar ve durumlar modelini destekler, bu nedenle bu modeli izlediğinizde denetiminiz bu tür uygulamalarda özelleştirilebilir.  Bu konuda parçalar ve durumlar modeli ve kendi denetiminizi oluştururken nasıl takip edilecek anlatılmaktadır. Bu konu, bu modelin felsefesini göstermek için `NumericUpDown`özel bir denetim örneğini kullanır.  `NumericUpDown` denetim, kullanıcının denetim düğmelerine tıklayarak artırabileceği veya azaltırabileceği sayısal bir değer görüntüler.  Aşağıdaki çizimde, bu konuda ele alınan `NumericUpDown` denetimi gösterilmektedir.

![NumericUpDown özel denetimi.](./media/ndp-numericupdown.png "NDP_NumericUPDown")
Özel NumericUpDown denetimi

Bu konu aşağıdaki bölümleri içermektedir:

- [Önkoşullar](#prerequisites)

- [Parçalar ve durumlar modeli](#parts_and_states_model)

- [Bir ControlTemplate içindeki bir denetimin görsel yapısını ve görsel davranışını tanımlama](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)

- [Kodda ControlTemplate 'in parçalarını kullanma](#using_parts_of_the_controltemplate_in_code)

- [Denetim sözleşmesini sağlama](#providing_the_control_contract)

- [Örnek Tamam](#complete_example)

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prerequisites

Bu konu başlığı altında, var olan bir denetim için yeni bir <xref:System.Windows.Controls.ControlTemplate> oluşturmayı bildiğiniz, bir denetim sözleşmesindeki öğelerin ne olduğu hakkında bilgi sahibi olduğunuz ve [var olan bir denetimin görünümünü özelleştirme bölümünde açıklanan kavramları anladığınızı varsayılmaktadır ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

> [!NOTE]
> Görünümü özelleştirilmiş bir denetim oluşturmak için, <xref:System.Windows.Controls.Control> sınıfından devralan bir denetim veya <xref:System.Windows.Controls.UserControl>dışındaki alt sınıflarından birini oluşturmanız gerekir.  <xref:System.Windows.Controls.UserControl> devralan bir denetim, hızlı bir şekilde oluşturulabilecek bir denetimdir, ancak bir <xref:System.Windows.Controls.ControlTemplate> kullanmaz ve görünümünü özelleştiremezsiniz.

<a name="parts_and_states_model"></a>

## <a name="parts-and-states-model"></a>Parçalar ve durumlar modeli

Parçalar ve durumlar modeli, bir denetimin görsel yapısının ve görsel davranışının nasıl tanımlanacağını belirtir. Parçalar ve durumlar modelini izlemek için aşağıdakileri yapmanız gerekir:

- Bir denetimin <xref:System.Windows.Controls.ControlTemplate> görsel yapısını ve görsel davranışını tanımlayın.

- Denetiminizin mantığı denetim şablonunun bölümleriyle etkileşime geçtiğinde belirli en iyi uygulamaları izleyin.

- <xref:System.Windows.Controls.ControlTemplate>nelerin ekleneceğini belirtmek için bir denetim sözleşmesi sağlayın.

Bir denetimin <xref:System.Windows.Controls.ControlTemplate> görsel yapısını ve görsel davranışı tanımladığınızda, uygulama yazarları, kod yazmak yerine yeni bir <xref:System.Windows.Controls.ControlTemplate> oluşturarak denetiminizin görsel yapısını ve görsel davranışını değiştirebilir.   Uygulama yazarlarına <xref:System.Windows.FrameworkElement> nesne ve durum <xref:System.Windows.Controls.ControlTemplate>tanımlanması gerektiğini söyleyen bir denetim sözleşmesi sağlamalısınız. Denetiminizin tamamlanmamış bir <xref:System.Windows.Controls.ControlTemplate>doğru bir şekilde işlemesini sağlamak için <xref:System.Windows.Controls.ControlTemplate> bölümlerle etkileşim kurarken bazı en iyi yöntemleri izlemeniz gerekir.  Bu üç ilkeden birini izlerseniz, uygulama yazarları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ile birlikte gelen denetimlerde kolayca denetim için bir <xref:System.Windows.Controls.ControlTemplate> oluşturabilir.  Aşağıdaki bölümde Bu önerilerin her biri ayrıntılı olarak açıklanmaktadır.

<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>

## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Bir ControlTemplate içindeki bir denetimin görsel yapısını ve görsel davranışını tanımlama

Özel denetiminizi parçalar ve durumlar modelini kullanarak oluşturduğunuzda, denetimin görsel yapısını ve görsel davranışını kendi mantığı yerine <xref:System.Windows.Controls.ControlTemplate> tanımlarsınız.  Bir denetimin görsel yapısı, denetimi oluşturan <xref:System.Windows.FrameworkElement> nesnelerinin bir bileşiminin oluşur.  Görsel davranış, denetimin belirli bir durumda olduğunda görünme yöntemidir.   Bir denetimin görsel yapısını ve görsel davranışını belirten <xref:System.Windows.Controls.ControlTemplate> oluşturma hakkında daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).

`NumericUpDown` denetimi örneğinde, görsel yapı iki <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi ve bir <xref:System.Windows.Controls.TextBlock>içerir.  Bu denetimleri `NumericUpDown` denetimin koduna eklerseniz--------------bu denetimlerin konumları geri alınamaz.  Denetimin görsel yapısını ve kendi kodunda görsel davranışını tanımlamak yerine <xref:System.Windows.Controls.ControlTemplate>tanımlamanız gerekir.  Ardından, düğmelerin ve <xref:System.Windows.Controls.TextBlock> konumunu özelleştirmek için bir uygulama geliştiricisi ve <xref:System.Windows.Controls.ControlTemplate> değiştirilebilmesi için `Value` negatifse hangi davranışın gerçekleşeceğini belirtin.

Aşağıdaki örnek, `Value`arttırmak için bir <xref:System.Windows.Controls.Primitives.RepeatButton>, `Value`azaltmak için bir <xref:System.Windows.Controls.Primitives.RepeatButton> ve <xref:System.Windows.Controls.TextBlock> görüntülenmesini sağlayan bir `Value`içeren `NumericUpDown` denetiminin görsel yapısını gösterir.

[!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]

`NumericUpDown` denetiminin görsel bir davranışı, negatifse değerin kırmızı bir yazı tipinde olması olur.  `Value` negatifse, koddaki <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Foreground%2A> değiştirirseniz `NumericUpDown` her zaman kırmızı negatif bir değer gösterilir. <xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.VisualState> nesneleri ekleyerek <xref:System.Windows.Controls.ControlTemplate> denetimin görsel davranışını belirlersiniz.  Aşağıdaki örnek, `Positive` ve `Negative` durumları için <xref:System.Windows.VisualState> nesneleri gösterir.  `Positive` ve `Negative` birbirini dışlamalı (denetim her zaman iki ' de olur), bu nedenle örnek <xref:System.Windows.VisualState> nesnelerini tek bir <xref:System.Windows.VisualStateGroup>koyar.  Denetim `Negative` duruma geçtiğinde, <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Foreground%2A> kırmızıya döner.  Denetim `Positive` durumundaysa, <xref:System.Windows.Controls.TextBlock.Foreground%2A> özgün değerine geri döner.  Bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.VisualState> nesneleri tanımlama, bir [ControlTemplate oluşturarak var olan bir denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md)konusunda daha fazla ele alınmıştır.

> [!NOTE]
> <xref:System.Windows.Controls.ControlTemplate>kök <xref:System.Windows.FrameworkElement> <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> ekli özelliği ayarladığınızdan emin olun.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

<a name="using_parts_of_the_controltemplate_in_code"></a>

## <a name="using-parts-of-the-controltemplate-in-code"></a>Kodda ControlTemplate 'in parçalarını kullanma

<xref:System.Windows.Controls.ControlTemplate> yazarı <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.VisualState> nesneleri ya da herhangi bir durum ya da yanlışlıkla atlayabilir, ancak denetiminizin mantığı bu bölümlerin düzgün şekilde çalışmasını gerektirebilir. Parçalar ve durumlar modeli, denetiminizin <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.VisualState> nesneleri eksik bir <xref:System.Windows.Controls.ControlTemplate> dayanıklı olması gerektiğini belirtir.  <xref:System.Windows.Controls.ControlTemplate>bir <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>veya <xref:System.Windows.VisualStateGroup> eksikse denetiminiz bir özel durum oluşturmaz veya hata bildirmemelidir. Bu bölümde <xref:System.Windows.FrameworkElement> nesneleriyle etkileşim kurmak ve durumları yönetmek için önerilen uygulamalar açıklanmaktadır.

### <a name="anticipate-missing-frameworkelement-objects"></a>Eksik FrameworkElement nesnelerini tahmin edin

<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.FrameworkElement> nesneleri tanımladığınızda, denetiminizin mantığının bazıları bunlardan Bazılarınızla etkileşim kurması gerekebilir.  Örneğin, `NumericUpDown` denetimi `Value` artırmak veya azaltmak için düğmelere ' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayına abone olur ve <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Text%2A> özelliğini `Value`olarak ayarlar. Özel bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TextBlock> veya düğmeleri atladığında, denetimin bazı işlevlerini kaybetmesi kabul edilebilir, ancak denetiminizin bir hataya neden olmadığından emin olmalısınız. Örneğin, bir <xref:System.Windows.Controls.ControlTemplate> `Value`değiştirecek düğmeleri içermiyorsa `NumericUpDown` bu işlevselliği kaybeder, ancak <xref:System.Windows.Controls.ControlTemplate> kullanan bir uygulama çalışmaya devam eder.

Aşağıdaki uygulamalar, denetiminizin eksik <xref:System.Windows.FrameworkElement> nesneleri için düzgün şekilde yanıt vermesini sağlar:

1. Kodda başvuru yapmanız gereken her bir <xref:System.Windows.FrameworkElement> için `x:Name` özniteliğini ayarlayın.

2. Etkileşimde bulunmak için ihtiyacınız olan her bir <xref:System.Windows.FrameworkElement> için özel özellikler tanımlayın.

3. <xref:System.Windows.FrameworkElement> özelliğinin set erişimcisinde denetim tanıtıcılarınızın işleyeceği olaylara abone olun ve aboneliği kaldırın.

4. <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> yönteminde adım 2 ' de tanımladığınız <xref:System.Windows.FrameworkElement> özelliklerini ayarlayın. Bu, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.FrameworkElement> denetimde kullanılabilir olan en erken zamandır. <xref:System.Windows.Controls.ControlTemplate>almak için <xref:System.Windows.FrameworkElement> `x:Name` kullanın.

5. <xref:System.Windows.FrameworkElement> üyelerine erişmeden önce `null` olmadığından emin olun.  `null`bir hata bildirmeyin.

Aşağıdaki örneklerde, `NumericUpDown` denetiminin önceki listedeki önerilere göre <xref:System.Windows.FrameworkElement> nesnelerle nasıl etkileşim kurduğu gösterilmektedir.

<xref:System.Windows.Controls.ControlTemplate>`NumericUpDown` denetiminin görsel yapısını tanımlayan örnekte, `Value` artıran <xref:System.Windows.Controls.Primitives.RepeatButton> `x:Name` özniteliği `UpButton`olarak ayarlanmıştır.  Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate>bildirildiği <xref:System.Windows.Controls.Primitives.RepeatButton> temsil eden `UpButtonElement` adlı bir özellik bildirir. `set` erişimci önce `UpDownElement` `null`yoksa düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayına abone olur, sonra özelliği ayarlar ve ardından <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayına abone olur. Ayrıca, `DownButtonElement`olarak adlandırılan diğer <xref:System.Windows.Controls.Primitives.RepeatButton>için de tanımlı bir özellik vardır ancak burada gösterilmez.

[!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
[!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]

Aşağıdaki örnek, `NumericUpDown` denetiminin <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> gösterir.  Örnek, <xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.FrameworkElement> nesneleri almak için <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> yöntemini kullanır.  Örneğin, <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> beklenen türde olmayan, belirtilen ada sahip bir <xref:System.Windows.FrameworkElement> bulduğu durumlarda örneğe karşı koruduğuna dikkat edin. Ayrıca, belirtilen `x:Name` sahip olan ancak yanlış türde olan öğeleri yoksaymak için de en iyi uygulamadır.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Önceki örneklerde gösterilen uygulamaları izleyerek, <xref:System.Windows.Controls.ControlTemplate> bir <xref:System.Windows.FrameworkElement>eksik olduğunda denetiminizin çalışmaya devam etmesini sağlayabilirsiniz.

### <a name="use-the-visualstatemanager-to-manage-states"></a>VisualStateManager 'ı kullanarak durumları yönetme

<xref:System.Windows.VisualStateManager>, bir denetimin durumlarını izler ve durumlar arasında geçiş yapmak için gereken mantığı gerçekleştirir. <xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.VisualState> nesneleri eklediğinizde, bunları bir <xref:System.Windows.VisualStateGroup> ekler ve <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> iliştirilmiş özelliğine <xref:System.Windows.VisualStateGroup> ekleyerek <xref:System.Windows.VisualStateManager> bunlara erişimi vardır.

Aşağıdaki örnek, denetimin `Positive` ve `Negative` durumlarına karşılık gelen <xref:System.Windows.VisualState> nesneleri gösteren önceki örneği yineler. `Negative`<xref:System.Windows.VisualState> <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.TextBlock> kırmızı <xref:System.Windows.Controls.TextBlock.Foreground%2A> döndürür.   `NumericUpDown` denetimi `Negative` durumundayken, `Negative` durumundaki film şeridi başlar.  Sonra, `Negative` durumundaki <xref:System.Windows.Media.Animation.Storyboard> denetim `Positive` durumuna dönzaman duraklar.  `Positive`<xref:System.Windows.VisualState> <xref:System.Windows.Media.Animation.Storyboard> içermesi gerekmez, çünkü `Negative` <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Controls.TextBlock.Foreground%2A> özgün rengine geri döner.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

<xref:System.Windows.Controls.TextBlock> bir ad verildiğini, ancak denetimin mantığı <xref:System.Windows.Controls.TextBlock>hiçbir şekilde başvurmadığından, <xref:System.Windows.Controls.TextBlock> `NumericUpDown` için denetim sözleşmesinde değil.  <xref:System.Windows.Controls.ControlTemplate> başvurulan öğelerin adları vardır, ancak denetim için yeni bir <xref:System.Windows.Controls.ControlTemplate> bu öğeye başvurması gerekmiyorsa denetim sözleşmesinin bir parçası olmak zorunda değildir.  Örneğin, `NumericUpDown` için yeni bir <xref:System.Windows.Controls.ControlTemplate> oluşturan birisi, <xref:System.Windows.Controls.Control.Foreground%2A>değiştirilerek `Value` negatif olduğunu Belirtmemeye karar verebilir.  Bu durumda, ne kod ne de <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TextBlock> adına göre başvurmaz.

Denetimin mantığı, denetimin durumunu değiştirmekten sorumludur. Aşağıdaki örnek, `NumericUpDown` denetiminin `Value` 0 veya daha büyükse `Positive` durumuna geçmek için <xref:System.Windows.VisualStateManager.GoToState%2A> yöntemini ve `Negative` 0 ' dan küçük olduğunda `Value` durumunu çağırıyorsa gösterir.

[!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
[!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]

<xref:System.Windows.VisualStateManager.GoToState%2A> yöntemi, görsel taslakları uygun şekilde başlatmak ve durdurmak için gereken mantığı gerçekleştirir. Bir denetim, durumunu değiştirmek için <xref:System.Windows.VisualStateManager.GoToState%2A> çağırdığında, <xref:System.Windows.VisualStateManager> şunları yapar:

- Denetimin <xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.VisualState>, film şeridi başlar. Sonra, denetimin geldiği <xref:System.Windows.VisualState> bir <xref:System.Windows.Media.Animation.Storyboard>varsa, film şeridi sonlanır.

- Denetim zaten belirtilen durumundaysa, <xref:System.Windows.VisualStateManager.GoToState%2A> hiçbir eylemde bulunmaz ve `true`döndürmez.

- Belirtilen durum `control`<xref:System.Windows.Controls.ControlTemplate> yoksa, <xref:System.Windows.VisualStateManager.GoToState%2A> hiçbir işlem yapmaz ve `false`döndürmez.

#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>VisualStateManager ile çalışmaya yönelik en iyi uygulamalar

Denetiminizin durumlarını korumak için aşağıdakileri yapmanız önerilir:

- Durumunu izlemek için özellikleri kullanın.

- Durumlar arasında geçiş yapmak için bir yardımcı yöntem oluşturun.

`NumericUpDown` denetimi, `Positive` veya `Negative` durumunda olup olmadığını izlemek için `Value` özelliğini kullanır.  `NumericUpDown` denetimi Ayrıca, <xref:System.Windows.UIElement.IsFocused%2A> özelliğini izleyen `Focused` ve `UnFocused` durumlarını tanımlar. Doğal olarak denetimin bir özelliğine karşılık gelen durumlar kullanırsanız, durumu izlemek için özel bir özellik tanımlayabilirsiniz.

Tüm durumları güncelleştiren tek bir yöntem, <xref:System.Windows.VisualStateManager> çağrıları merkezileştirir ve kodunuzu yönetilebilir halde tutar. Aşağıdaki örnekte, `UpdateStates``NumericUpDown` denetimin yardımcı yöntemi gösterilmektedir. `Value` 0 ' dan büyük veya buna eşitse, <xref:System.Windows.Controls.Control> `Positive` durumundadır.  `Value` 0 ' dan küçükse, denetim `Negative` durumundadır.  <xref:System.Windows.UIElement.IsFocused%2A> `true`, denetim `Focused` durumundadır; Aksi takdirde, `Unfocused` durumundadır.  Denetim, durumu ne olursa olsun, durumunu değiştirmek gerektiğinde `UpdateStates` çağırabilir.

[!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
[!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]

Denetim zaten bu durumda olduğunda <xref:System.Windows.VisualStateManager.GoToState%2A> bir durum adı geçirirseniz <xref:System.Windows.VisualStateManager.GoToState%2A> hiçbir şey yapmaz, bu nedenle denetimin geçerli durumunu denetlemeniz gerekmez.  Örneğin, `Value` bir negatif sayıdan başka negatif bir sayıya değişirse, `Negative` durumunun film şeridi kesintiye uğramaz ve Kullanıcı denetimde bir değişiklik görmez.

<xref:System.Windows.VisualStateManager>, <xref:System.Windows.VisualStateManager.GoToState%2A>çağırdığınızda hangi durumun çıkaceğini belirleyen <xref:System.Windows.VisualStateGroup> nesneleri kullanır. Denetim her zaman <xref:System.Windows.Controls.ControlTemplate> tanımlanan her <xref:System.Windows.VisualStateGroup> için tek bir durumdur ve yalnızca aynı <xref:System.Windows.VisualStateGroup>başka bir duruma geçtiğinde bir durumu bırakır. Örneğin, `NumericUpDown` denetiminin <xref:System.Windows.Controls.ControlTemplate>, `Positive` ve `Negative`<xref:System.Windows.VisualState> nesnelerini bir <xref:System.Windows.VisualStateGroup> ve `Focused` `Unfocused`nesneleri başka bir<xref:System.Windows.VisualState> tanımlar. (Denetim `Positive` durumdan `Negative` duruma geçtiğinde veya bunun tersi durumda, denetim `Focused` veya `Unfocused` içinde kalırsa, bu konunun [tam örnek](#complete_example) bölümünde tanımlanan `Focused` ve `Unfocused`<xref:System.Windows.VisualState> bakabilirsiniz. durumunda.

Bir denetimin durumunun değiştirebildiği üç tipik konum vardır:

- <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Control>uygulandığında.

- Bir özellik değiştiğinde.

- Bir olay gerçekleştiğinde.

Aşağıdaki örneklerde, bu durumlarda `NumericUpDown` denetiminin durumunu güncelleştirme gösterilmektedir.

<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> yönteminde denetimin durumunu güncelleştirmeniz gerekir, böylece <xref:System.Windows.Controls.ControlTemplate> uygulandığında denetimin doğru durumda görünmesini sağlayabilirsiniz. Aşağıdaki örnek, denetimin uygun durumlarda olduğundan emin olmak için <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> `UpdateStates` çağırır.  Örneğin, bir `NumericUpDown` denetimi oluşturduğunuzu ve <xref:System.Windows.Controls.Control.Foreground%2A> yeşil ve `Value`-5 olarak ayarladığınızı varsayalım.  <xref:System.Windows.Controls.ControlTemplate> `NumericUpDown` denetimine uygulandığında `UpdateStates` çağırmayın, denetim `Negative` durumunda değildir ve değeri kırmızı yerine yeşil olur.  Denetimi `Negative` duruma koymak için `UpdateStates` çağırmanız gerekir.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Genellikle bir özellik değiştiğinde bir denetimin durumlarını güncelleştirmeniz gerekir. Aşağıdaki örnekte `ValueChangedCallback` yönteminin tamamı gösterilmektedir. `ValueChangedCallback` `Value` değiştiğinde, yöntem `Value` pozitif iken negatif ya da tam tersi yönde `UpdateStates` çağrılır. `Value` değiştiğinde `UpdateStates` çağırmak kabul edilebilir, ancak pozitif veya negatif kalır, bu durumda denetim durumları değiştirmez.

[!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
[!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]

Ayrıca bir olay gerçekleştiğinde durumları güncelleştirmeniz gerekebilir. Aşağıdaki örnek, `NumericUpDown` <xref:System.Windows.UIElement.GotFocus> olayını işlemek için <xref:System.Windows.Controls.Control> `UpdateStates` çağırın gösterir.

[!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
[!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]

<xref:System.Windows.VisualStateManager>, Denetiminizin durumlarını yönetmenize yardımcı olur. <xref:System.Windows.VisualStateManager>kullanarak, denetiminizin durumlar arasında doğru şekilde geçiş yapıldığından emin olursunuz.  <xref:System.Windows.VisualStateManager>çalışmak için bu bölümde açıklanan önerileri izlerseniz, denetiminizin kodu okunabilir ve sürdürülebilir olarak kalır.

<a name="providing_the_control_contract"></a>

## <a name="providing-the-control-contract"></a>Denetim sözleşmesini sağlama

<xref:System.Windows.Controls.ControlTemplate> yazarların şablona ne yerleştirileceğini bilmesi için bir denetim sözleşmesi sağlarsınız. Bir denetim sözleşmesinin üç öğesi vardır:

- Denetimin mantığının kullandığı görsel öğeler.

- Denetimin durumları ve her durumun ait olduğu grup.

- Denetimi görsel olarak etkileyen ortak özellikler.

Yeni bir <xref:System.Windows.Controls.ControlTemplate> oluşturan birisinin, denetimin mantığının hangi <xref:System.Windows.FrameworkElement> nesnelerini kullandığını, her bir nesnenin ne tür olduğunu ve adının ne olduğunu bililmesi gerekir. Ayrıca, bir <xref:System.Windows.Controls.ControlTemplate> yazarın, denetimin içinde yer aldığı ve durumun <xref:System.Windows.VisualStateGroup> hangi olası bir durumun adını bilmeleri gerekir.

`NumericUpDown` örneğe dönerek, denetim <xref:System.Windows.Controls.ControlTemplate> aşağıdaki <xref:System.Windows.FrameworkElement> nesnelerine sahip olmasını bekler:

- `UpButton`adlı bir <xref:System.Windows.Controls.Primitives.RepeatButton>.

- `DownButton.` adlı bir <xref:System.Windows.Controls.Primitives.RepeatButton>

 Denetim aşağıdaki durumlarda olabilir:

- `ValueStates`<xref:System.Windows.VisualStateGroup>

  - `Positive`

  - `Negative`

- `FocusStates`<xref:System.Windows.VisualStateGroup>

  - `Focused`

  - `Unfocused`

Denetimin beklediği <xref:System.Windows.FrameworkElement> nesneleri belirtmek için, beklenen öğelerin adını ve türünü belirten <xref:System.Windows.TemplatePartAttribute>kullanırsınız.  Bir denetimin olası durumlarını belirtmek için, durumun adını ve hangi <xref:System.Windows.VisualStateGroup> ait olduğunu belirten <xref:System.Windows.TemplateVisualStateAttribute>kullanırsınız.  <xref:System.Windows.TemplatePartAttribute> ve <xref:System.Windows.TemplateVisualStateAttribute> denetimin sınıf tanımına koyun.

Denetiminizin görünümünü etkileyen tüm ortak özellikler ayrıca denetim sözleşmesinin bir parçasıdır.

Aşağıdaki örnek, `NumericUpDown` denetiminin <xref:System.Windows.FrameworkElement> nesnesini ve durumlarını belirtir.

[!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
[!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]

<a name="complete_example"></a>

## <a name="complete-example"></a>Tam Örnek

Aşağıdaki örnek, `NumericUpDown` denetiminin tüm <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]

Aşağıdaki örnekte `NumericUpDown`mantığı gösterilmektedir.

[!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
[!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]

## <a name="see-also"></a>Ayrıca bkz.

- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
- [Denetim Özelleştirme](control-customization.md)
