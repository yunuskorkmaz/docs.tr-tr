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
ms.openlocfilehash: 17b6fd604b5eca54d6323701dafdd38f9f6e7328
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131030"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Özelleştirilebilir Görünümü olan Denetim Oluşturma
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bir denetimin görünümünü özelleştirilebilir oluşturma olanağı sağlar. Örneğin, görünümünü değiştirebilirsiniz bir <xref:System.Windows.Controls.CheckBox> ötesinde hangi ayarı özellikleri yeni bir oluşturarak ne yapacağını <xref:System.Windows.Controls.ControlTemplate>. Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.CheckBox> varsayılan <xref:System.Windows.Controls.ControlTemplate> ve <xref:System.Windows.Controls.CheckBox> özel kullanan <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Varsayılan denetim şablonunu içeren bir onay kutusu. ](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Varsayılan denetim şablonunu kullanan bir onay kutusu  
  
 ![Bir özel denetim şablonu ile bir onay kutusu. ](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Bir özel denetim şablonunu kullanan bir onay kutusu  
  
 Bir denetimi oluşturduğunuzda, bölümler ve durumlar modeli izlerseniz, denetimin görünümünü özelleştirilebilir olacaktır. Bu modeli takip denetiminizin bu tür uygulamalarda özelleştirilebilir olacak Microsoft Expression Blend gibi tasarımcı araçları bölümler ve durumlar modeli destekler.  Bu konu, bölümler ve durumlar modeli ve kendi denetiminizi oluşturduğunuzda, onu izleyen nasıl açıklar. Bu konuda bir özel denetim örneği kullanan `NumericUpDown`, bu model felsefesini göstermek için.  `NumericUpDown` Denetimi, bir kullanıcı artırabilir veya azaltabilirsiniz denetimin düğmelerine tıklayarak bir sayısal bir değer görüntüler.  Aşağıdaki çizimde gösterildiği `NumericUpDown` bu konuda bahsedilen denetimi.  
  
 ![Özel NumericUpDown denetimi. ](./media/ndp-numericupdown.png "NDP_NumericUPDown")  
Özel bir NumericUpDown denetimi  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Önkoşullar](#prerequisites)  
  
-   [Bölümleri ve durumlar modeli](#parts_and_states_model)  
  
-   [ControlTemplate içinde görsel yapı ve denetim görsel davranışını tanımlama](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [ControlTemplate içinde kod parçalarını kullanma](#using_parts_of_the_controltemplate_in_code)  
  
-   [Denetim sözleşmesi sağlama](#providing_the_control_contract)  
  
-   [Tam Örnek](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, yeni bir oluşturulacağını bildiğinizi varsayar <xref:System.Windows.Controls.ControlTemplate> varolan bir denetim için bir denetim sözleşmesi öğelerde nelerdir ile ilgili bilgi sahibi olduğunuz ve içinde açıklanan kavramları öğrendikten [tarafından varolan denetimin görünümünü özelleştirme ControlTemplate oluşturarak](customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Özelleştirilmiş görünümünü olan bir denetim oluşturmak için devralınan bir denetim oluşturma <xref:System.Windows.Controls.Control> sınıf ya da daha fazla alt sınıflarından birini <xref:System.Windows.Controls.UserControl>.  Devralınan bir denetim <xref:System.Windows.Controls.UserControl> hızla oluşturulabilen denetimidir, ancak kullanmaz bir <xref:System.Windows.Controls.ControlTemplate> ve görünümünü özelleştirebilirsiniz.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Bölümleri ve durumlar modeli  
 Bölümleri ve durumları modelini görsel yapı ve denetim görsel davranışını nasıl tanımlanacağını belirtir. Bölümleri ve durumları modelini izlemek için şunları yapmalıdır:  
  
-   Görsel yapı ve visual davranışını tanımlayan <xref:System.Windows.Controls.ControlTemplate> denetimi.  
  
-   Denetim şablonunun bölümlerine ile denetim mantığının etkileşim kurduğunda bazı en iyi uygulamaları izleyin.  
  
-   Ne eklenmelidir belirtmek için bir denetim sözleşmesi sağlayan <xref:System.Windows.Controls.ControlTemplate>.  
  
 Görsel yapı ve visual davranışını tanımladığınızda <xref:System.Windows.Controls.ControlTemplate> bir denetimin uygulama yazarları görsel yapı ve visual davranışını yeni bir oluşturarak değiştirebilirsiniz <xref:System.Windows.Controls.ControlTemplate> kod yazmak yerine.   Uygulama belirten bir denetim sözleşmesi yazar, sağlamanız gereken <xref:System.Windows.FrameworkElement> nesneleri ve durumlar tanımlanmalıdır <xref:System.Windows.Controls.ControlTemplate>. Bölümleri ile etkileşim kurduğunuzda bazı en iyi uygulamaları izlemelisiniz <xref:System.Windows.Controls.ControlTemplate> denetiminiz düzgün tamamlanmamış işler, böylece <xref:System.Windows.Controls.ControlTemplate>.  Bu üç ilkeyi uygularsanız, uygulama oluşturmak yazarları bir <xref:System.Windows.Controls.ControlTemplate> denetiminiz için gibi kolayca denetimleri ile birlikte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Aşağıdaki bölümde her birini ayrıntılı bu önerileri açıklanmaktadır.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>ControlTemplate içinde görsel yapı ve denetim görsel davranışını tanımlama  
 Bölümleri ve durumları modeli kullanarak özel denetiminizi oluşturduğunuzda, denetimin görsel yapı ve visual davranışını tanımlayın, <xref:System.Windows.Controls.ControlTemplate> yerine mantığı.  Bir denetimin görsel yapı bileşimi olur <xref:System.Windows.FrameworkElement> denetimi oluşturan nesneleri.  Görsel davranış, belirli bir durumda olduğunda denetimi görünür yoludur.   Oluşturma hakkında daha fazla bilgi için bir <xref:System.Windows.Controls.ControlTemplate> görsel yapı ve denetim görsel davranışını belirleyen bkz [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
 Örneğinde `NumericUpDown` denetimi, görsel yapı içeren iki <xref:System.Windows.Controls.Primitives.RepeatButton> denetimleri ve <xref:System.Windows.Controls.TextBlock>.  Kodunda bu denetimleri eklerseniz `NumericUpDown` kendi oluşturucusuna, örneğin denetim bu denetimleri konumlarını değiştirilemez olur.  Denetimin görsel yapı ve görsel davranışını kendi kodunda tanımlamak yerine kaynakta tanımlamalıdır <xref:System.Windows.Controls.ControlTemplate>.  Düğmeleri konumunu özelleştirmek için daha sonra bir uygulama geliştiricisi ve <xref:System.Windows.Controls.TextBlock> ve hangi davranış belirtin, `Value` negatif olduğundan <xref:System.Windows.Controls.ControlTemplate> değiştirilebilir.  
  
 Aşağıdaki örnek visual yapısını gösterir `NumericUpDown` içeren denetim bir <xref:System.Windows.Controls.Primitives.RepeatButton> artırmak için `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> azaltmak için `Value`ve <xref:System.Windows.Controls.TextBlock> görüntülenecek `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Bir görsel davranışını `NumericUpDown` denetimidir negatif ise değer kırmızı bir yazı tipinde olduğunu.  Değiştirirseniz <xref:System.Windows.Controls.TextBlock.Foreground%2A> , <xref:System.Windows.Controls.TextBlock> içinde kod zaman `Value` negatif `NumericUpDown` kırmızı bir negatif değer her zaman gösterir. Denetimin görsel davranışını belirtin <xref:System.Windows.Controls.ControlTemplate> ekleyerek <xref:System.Windows.VisualState> nesneleri için <xref:System.Windows.Controls.ControlTemplate>.  Aşağıdaki örnekte gösterildiği <xref:System.Windows.VisualState> için nesneleri `Positive` ve `Negative` durumları.  `Positive` ve `Negative` (denetimidir her zaman tam olarak iki birinde) birbirini dışlayan olan, örnek koyar <xref:System.Windows.VisualState> nesnelerini tek <xref:System.Windows.VisualStateGroup>.  Denetimi geçildiğinde içine `Negative` durumu <xref:System.Windows.Controls.TextBlock.Foreground%2A> , <xref:System.Windows.Controls.TextBlock> kırmızıya döner.  Denetim olduğunda `Positive` durumu <xref:System.Windows.Controls.TextBlock.Foreground%2A> geri döndüğünde özgün değer.  Tanımlama <xref:System.Windows.VisualState> nesneler bir <xref:System.Windows.Controls.ControlTemplate> daha ayrıntılı olarak ele alınmıştır [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Ayarladığınızdan emin olun <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> ekli özellik kök <xref:System.Windows.FrameworkElement> , <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>ControlTemplate içinde kod parçalarını kullanma  
 A <xref:System.Windows.Controls.ControlTemplate> Yazar atlayabilir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.VisualState> nesneleri amaçlı veya yanlışlıkla, ancak denetim mantığının düzgün çalışması için bu bölümleri gerekebilir. Bölümleri ve durumları modelini denetiminiz için dayanıklı olması gerektiğini belirtir bir <xref:System.Windows.Controls.ControlTemplate> bulunmayan <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.VisualState> nesneleri.  Denetiminiz bir özel durum ya da rapor bir hata varsa oluşturmamalıdır bir <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, veya <xref:System.Windows.VisualStateGroup> eksik <xref:System.Windows.Controls.ControlTemplate>. Bu bölümde ile etkileşim kurmaya yönelik önerilen uygulamaları açıklanmaktadır <xref:System.Windows.FrameworkElement> nesneleri ve durumlarını yönetme.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>FrameworkElement nesneleri eksik tahmin  
 Tanımladığınızda <xref:System.Windows.FrameworkElement> nesneler <xref:System.Windows.Controls.ControlTemplate>, denetim mantığının bazıları ile etkileşim kurmak için gerekli.  Örneğin, `NumericUpDown` denetim düğmelere abone <xref:System.Windows.Controls.Primitives.ButtonBase.Click> artırmak veya azaltmak için olay `Value` ve ayarlar <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği <xref:System.Windows.Controls.TextBlock> için `Value`. Özel durumunda <xref:System.Windows.Controls.ControlTemplate> atlar <xref:System.Windows.Controls.TextBlock> veya düğme denetimi bazı işlevlerini kaybederse, ancak denetiminiz hataya neden olmadığından emin olmalısınız kabul edilebilir. Örneğin, bir <xref:System.Windows.Controls.ControlTemplate> değiştirmek için düğmelerini içermiyor `Value`, `NumericUpDown` işlevselliği, ancak kullanan bir uygulamayı kaybeder <xref:System.Windows.Controls.ControlTemplate> çalışmaya devam eder.  
  
 Eksik denetim düzgün yanıt aşağıdaki yöntemler sağlayacak <xref:System.Windows.FrameworkElement> nesneler:  
  
1.  Ayarlama `x:Name` her öznitelik <xref:System.Windows.FrameworkElement> kodda başvurmak gereken.  
  
2.  Her biri için özel özellikleri tanımlama <xref:System.Windows.FrameworkElement> ile etkileşim kurmak gereken.  
  
3.  Abone olma ve denetiminizin işlediği meydana gelen olayları abonelikten çıkma <xref:System.Windows.FrameworkElement> özelliği erişimcisi küme.  
  
4.  Ayarlama <xref:System.Windows.FrameworkElement> içinde tanımlanan özellikler adımı 2 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> yöntemi. Bu erken olduğundan, <xref:System.Windows.FrameworkElement> içinde <xref:System.Windows.Controls.ControlTemplate> denetimi için kullanılabilir. Kullanım `x:Name` , <xref:System.Windows.FrameworkElement> elde <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Bu maddeyi <xref:System.Windows.FrameworkElement> değil `null` üyelerine erişmeden önce.  Eğer öyleyse `null`, bir hata bildirmez.  
  
 Aşağıdaki örneklerde gösterildiği nasıl `NumericUpDown` denetim ile etkileşime <xref:System.Windows.FrameworkElement> yukarıdaki listede önerilerle nesneleri.  
  
 Görsel yapısını tanımlayan örnekte `NumericUpDown` denetim <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton> artıran `Value` sahip kendi `x:Name` özniteliğini `UpButton`.  Aşağıdaki örnekte adlı bir özelliği bildirir `UpButtonElement` temsil eden <xref:System.Windows.Controls.Primitives.RepeatButton> dosyasında bildirilen <xref:System.Windows.Controls.ControlTemplate>. `set` Erişimci ilk düğmenin abonelikten çıkma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay varsa `UpDownElement` değil `null`özelliğini ait olarak ayarlar ve sonra abone <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay. Ayrıca tanımlı, ancak burada diğer gösterilmeyen bir özelliği olan <xref:System.Windows.Controls.Primitives.RepeatButton>adlı `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> için `NumericUpDown` denetimi.  Örnekte <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> almak için yöntemi <xref:System.Windows.FrameworkElement> nesnelerin <xref:System.Windows.Controls.ControlTemplate>.  Örnek karşı koruduğu bildirimi durumlara <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> bulur bir <xref:System.Windows.FrameworkElement> beklenen türde değil. Belirtilen ada sahip. Ayrıca belirtilen sahip öğeyi yoksaymak için en iyi uygulama olan `x:Name` ancak yanlış türde.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Önceki örneklerde gösterilen yöntemleri izleyerek, denetimin çalışmaya devam edeceğinden emin <xref:System.Windows.Controls.ControlTemplate> eksik bir <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>VisualStateManager durumları yönetmek için kullanma  
 <xref:System.Windows.VisualStateManager> Denetim durumlarını izlemek ve durumlar arasında geçiş için gereken mantığı gerçekleştirir. Eklediğinizde <xref:System.Windows.VisualState> nesneleri için <xref:System.Windows.Controls.ControlTemplate>, bunları Ekle bir <xref:System.Windows.VisualStateGroup> ve ekleme <xref:System.Windows.VisualStateGroup> için <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> ekli özellik böylece <xref:System.Windows.VisualStateManager> bunlara erişebilir.  
  
 Aşağıdaki örnek gösteren önceki örnek yineler <xref:System.Windows.VisualState> karşılık gelen nesneleri `Positive` ve `Negative` durumları denetimi. <xref:System.Windows.Media.Animation.Storyboard> İçinde `Negative`<xref:System.Windows.VisualState> kapatır <xref:System.Windows.Controls.TextBlock.Foreground%2A> , <xref:System.Windows.Controls.TextBlock> kırmızı.   Zaman `NumericUpDown` denetimi `Negative` durumunda, film şeridi `Negative` durum başlar.  Ardından <xref:System.Windows.Media.Animation.Storyboard> içinde `Negative` denetim döndüğünde durakları durum `Positive` durumu.  `Positive`<xref:System.Windows.VisualState> İçermesi gerekmez bir <xref:System.Windows.Media.Animation.Storyboard> çünkü zaman <xref:System.Windows.Media.Animation.Storyboard> için `Negative` durdurur, <xref:System.Windows.Controls.TextBlock.Foreground%2A> özgün rengini döndürür.  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Unutmayın <xref:System.Windows.Controls.TextBlock> bir ad verilir ancak <xref:System.Windows.Controls.TextBlock> denetim sözleşmesi değil `NumericUpDown` denetimin mantığı asla başvurduğundan <xref:System.Windows.Controls.TextBlock>.  İçinde başvurulan öğeleri <xref:System.Windows.Controls.ControlTemplate> adlara sahip, ancak nedeni denetimi sözleşmesinin bir parçası olması gerekmez yeni <xref:System.Windows.Controls.ControlTemplate> için bu öğeye başvurmak denetim gerekmeyebilir.  Örneğin, birisi oluşturan yeni bir <xref:System.Windows.Controls.ControlTemplate> için `NumericUpDown` değil belirtmek isteyebilirsiniz `Value` değiştirerek negatiftir <xref:System.Windows.Controls.Control.Foreground%2A>.  Bu durumda, her iki kod ya da <xref:System.Windows.Controls.ControlTemplate> başvuruları <xref:System.Windows.Controls.TextBlock> ada göre.  
  
 Denetimin durumunu değiştirmek için denetim mantığının sorumludur. Aşağıdaki örnek, gösterir `NumericUpDown` denetim çağrıları <xref:System.Windows.VisualStateManager.GoToState%2A> yerleştirilmesini yöntemi `Positive` durumuna `Value` 0 veya daha büyük olduğu ve `Negative` durumuna `Value` 0'dan küçük.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> Yöntemi uygun şekilde film şeridini durdurmak ve başlatmak için gerekli mantığı gerçekleştirir. Bir denetim çağırdığında <xref:System.Windows.VisualStateManager.GoToState%2A> kendi durumunu değiştirmek için <xref:System.Windows.VisualStateManager> şunları yapar:  
  
-   Varsa <xref:System.Windows.VisualState> denetimin gittiği sahip bir <xref:System.Windows.Media.Animation.Storyboard>, film şeridi başlar. Ardından, eğer <xref:System.Windows.VisualState> denetim geldiği sahip bir <xref:System.Windows.Media.Animation.Storyboard>, film şeridi sonlandırılır.  
  
-   Denetim zaten belirtilen durumda ise <xref:System.Windows.VisualStateManager.GoToState%2A> hiç eylem almaması ve döndürür `true`.  
  
-   Belirtilen durum yoksa <xref:System.Windows.Controls.ControlTemplate> , `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> hiç eylem almaması ve döndürür `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>VisualStateManager ile çalışmak için en iyi yöntemler  
 Denetim durumlarını korumak için şunları yapmanız önerilir:  
  
-   Özelliklerini, durumunu izlemek için kullanın.  
  
-   Durumlar arasında geçiş için bir yardımcı yöntem oluşturun.  
  
 `NumericUpDown` Denetim kullanır, `Value` olup izlemek için özellik `Positive` veya `Negative` durumu.  `NumericUpDown` Denetimini de tanımlar `Focused` ve `UnFocused` durumlarını izleyen <xref:System.Windows.UIElement.IsFocused%2A> özelliği. Doğal olarak denetimin bir özelliğine karşılık gelmeyen bildiren kullanırsanız, durumunu izlemek için özel bir özellik tanımlayabilirsiniz.  
  
 Tüm durumları güncelleştirmeleri tek bir yöntem çağrıları merkezileştirir <xref:System.Windows.VisualStateManager> ve kodunuzun yönetilebilir korur. Aşağıdaki örnekte gösterildiği `NumericUpDown` denetimin yardımcı yöntem `UpdateStates`. Zaman `Value` değerinden büyükse veya eşitse 0 <xref:System.Windows.Controls.Control> bulunduğu `Positive` durumu.  Zaman `Value` olan 0'dan küçük denetimin bulunduğu `Negative` durumu.  Zaman <xref:System.Windows.UIElement.IsFocused%2A> olduğu `true`, Denetim `Focused` durum; Aksi durumda `Unfocused` durumu.  Denetim çağırabilirsiniz `UpdateStates` durum değişiklikleri bağımsız olarak kendi durumunu değiştirmek ihtiyaç duyduğunda.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 Bir durum adına geçirirseniz <xref:System.Windows.VisualStateManager.GoToState%2A> denetim bu durumda olduğunda <xref:System.Windows.VisualStateManager.GoToState%2A> hiçbir şey yapmaz, bu nedenle, denetimin geçerli durumunu denetlemek gerekmez.  Örneğin, varsa `Value` başka bir negatif sayı, film şeridi bir negatif sayıdan değişiklikleri `Negative` durumu kesintiye ve kullanıcı denetiminde bir değişikliği görmez.  
  
 <xref:System.Windows.VisualStateManager> Kullanan <xref:System.Windows.VisualStateGroup> çağırdığınızda çıkmak için hangi durumu belirlemek için nesneleri <xref:System.Windows.VisualStateManager.GoToState%2A>. Denetimin her zaman her bir durumda olduğundan <xref:System.Windows.VisualStateGroup> içinde tanımlandığından, <xref:System.Windows.Controls.ControlTemplate> ve başka bir duruma aynı geçtiğinde yalnızca bir durumda bırakır <xref:System.Windows.VisualStateGroup>. Örneğin, <xref:System.Windows.Controls.ControlTemplate> , `NumericUpDown` denetimini tanımlar `Positive` ve `Negative`<xref:System.Windows.VisualState> birindeki nesnelerin <xref:System.Windows.VisualStateGroup> ve `Focused` ve `Unfocused`<xref:System.Windows.VisualState> başka bir nesne. (Gördüğünüz `Focused` ve `Unfocused`<xref:System.Windows.VisualState> tanımlanan [tam bir örnek](#complete_example) denetim geçerse, bu konudaki bölüm `Positive` durumunu `Negative` durumu veya tam tersi de denetim kalır ya da `Focused` veya `Unfocused` durumu.  
  
 Bir denetimin durumunu burada değişebilir üç tipik yerler şunlardır:  
  
-   Zaman <xref:System.Windows.Controls.ControlTemplate> uygulanan <xref:System.Windows.Controls.Control>.  
  
-   Bir özellik değiştiğinde.  
  
-   Bir olay gerçekleştiğinde.  
  
 Aşağıdaki örnekler, durumunu güncelleme göstermektedir `NumericUpDown` bu gibi durumlarda denetimi.  
  
 Denetimde durumunu güncelleştirmeniz gerekir <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> yöntemi böylece denetim doğru yerde görünür duruma <xref:System.Windows.Controls.ControlTemplate> uygulanır. Aşağıdaki örnek çağrıları `UpdateStates` içinde <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> denetim uygun durumda olduğundan emin olmak için.  Örneğin, oluşturduğunuz düşünün bir `NumericUpDown` denetlemek ve ardından kendi <xref:System.Windows.Controls.Control.Foreground%2A> yeşil ve `Value` -5.  Değil çağırırsanız `UpdateStates` olduğunda <xref:System.Windows.Controls.ControlTemplate> uygulanan `NumericUpDown` denetim, denetimin değil `Negative` durumu ve değeri yerine kırmızı yeşil.  Çağırmalısınız `UpdateStates` denetim yerleştirmek için `Negative` durumu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Genellikle, bir özellik değiştiğinde bir denetim durumlarını güncelleştirmeniz gerekiyor. Aşağıdaki örnek, tüm gösterir `ValueChangedCallback` yöntemi. Çünkü `ValueChangedCallback` aldığında çağrılan `Value` değiştirir, yöntem çağrılarını `UpdateStates` durumunda `Value` negatif veya pozitif değiştirildi. Çağırmak için kabul edilebilir `UpdateStates` olduğunda `Value` değiştirir ancak bu durumda, Denetim durumlarını değişmez çünkü pozitif veya negatif kalır.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Bir olay meydana geldiğinde durumları güncelleştirmeniz gerekebilir. Aşağıdaki örnek, gösterir `NumericUpDown` çağrıları `UpdateStates` üzerinde <xref:System.Windows.Controls.Control> işlemek için <xref:System.Windows.UIElement.GotFocus> olay.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> Denetiminizin durumlarını yönetmenize yardımcı olur. Kullanarak <xref:System.Windows.VisualStateManager>, Denetim doğru durum arasında geçiş emin olun.  İle çalışmak için bu bölümde açıklanan önerileri uygulayın, <xref:System.Windows.VisualStateManager>, okunabilir ve sürdürülebilir denetiminizin kodu kalır.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>Denetim sözleşmesi sağlama  
 Bir denetim sözleşmesi sağlayan böylece <xref:System.Windows.Controls.ControlTemplate> yazarlar şablonda konulacaklar bilmeniz. Denetim sözleşmesi üç öğe vardır:  
  
-   Görsel öğeler denetimin mantığı kullanır.  
  
-   Denetim ve her durumun ait olduğu Grup durumları.  
  
-   Denetimin görsel olarak etkileyen genel özellikler.  
  
 Yeni bir oluşturan birinin <xref:System.Windows.Controls.ControlTemplate> bilmesi gereken <xref:System.Windows.FrameworkElement> nesneleri denetimin mantığı kullanır, ne tür oluşturduğunu ve adını. A <xref:System.Windows.Controls.ControlTemplate> Yazar ayrıca gereken olası her durum denetimi olabilir ve hangi adını bilmek <xref:System.Windows.VisualStateGroup> durumu yer.  
  
 Dönme `NumericUpDown` örnek, bir denetim bekliyor <xref:System.Windows.Controls.ControlTemplate> aşağıdaki olmasını <xref:System.Windows.FrameworkElement> nesneler:  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> adlı `UpButton`.  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> çağırılır `DownButton.`  
  
 Denetim, şu durumlarda olabilir:  
  
-   İçinde `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   İçinde `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Ne belirtmek için <xref:System.Windows.FrameworkElement> denetim nesneleri bekler, kullandığınız <xref:System.Windows.TemplatePartAttribute>, beklenen öğelerin türünü ve adını belirtir.  Olası durumlar denetimin belirtmek için kullandığınız <xref:System.Windows.TemplateVisualStateAttribute>, durumun adını ve hangi belirten <xref:System.Windows.VisualStateGroup> ait.  PUT <xref:System.Windows.TemplatePartAttribute> ve <xref:System.Windows.TemplateVisualStateAttribute> denetim sınıf tanımı.  
  
 Denetiminizin görünümünü etkileyen herhangi bir ortak özellik ayrıca Denetim sözleşmesi parçasıdır.  
  
 Aşağıdaki örnek belirtir <xref:System.Windows.FrameworkElement> nesne ve durumlarını `NumericUpDown` denetimi.  
  
 [!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, tüm <xref:System.Windows.Controls.ControlTemplate> için `NumericUpDown` denetimi.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 Aşağıdaki örnek, mantığını gösterir `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
- [Denetim Özelleştirme](control-customization.md)
