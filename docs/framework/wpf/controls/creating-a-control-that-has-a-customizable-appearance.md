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
ms.openlocfilehash: 9f539e7dbb105591375857122d738fddd87f6776
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558284"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Özelleştirilebilir Görünümü olan Denetim Oluşturma
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] görünümünü özelleştirilebilir bir denetim oluşturma olanağı sağlar. Örneğin, görünümünü değiştirebilirsiniz bir <xref:System.Windows.Controls.CheckBox> ötesinde hangi ayar özellikleri yeni oluşturarak ne yapacağını <xref:System.Windows.Controls.ControlTemplate>. Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.CheckBox> varsayılan kullanan <xref:System.Windows.Controls.ControlTemplate> ve <xref:System.Windows.Controls.CheckBox> özel kullanan <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Bir onay kutusu varsayılan denetim şablonu ile. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Varsayılan denetim şablonunu kullanan bir onay kutusu  
  
 ![Bir özel denetim şablonuyla bir onay kutusu. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Bir özel denetim şablonu kullanan bir onay kutusu  
  
 Bir denetim oluşturduğunuzda, bölümler ve durumlar modelini izlerseniz, denetiminizin görünümü özelleştirilebilir olur. Bu model izlediğinizde denetiminiz bu tür uygulamalarda özelleştirilebilir olması için Microsoft Expression Blend gibi tasarımcı araçları bölümler ve durumlar modelini destekler.  Bu konuda bölümler ve durumlar modeli ve kendi denetim oluşturduğunuzda izlemek nasıl ele alınmıştır. Bu konuda bir özel denetim örneği kullanan `NumericUpDown`, bu model felsefesi göstermek için.  `NumericUpDown` Denetimi, bir kullanıcı artırabilir veya azaltabilirsiniz denetimin düğmelerine tıklayarak bir sayısal bir değer görüntüler.  Aşağıdaki çizimde gösterildiği `NumericUpDown` bu konuda tartışılan denetim.  
  
 ![NumericUpDown özel denetimi. ] (../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP_NumericUPDown")  
Özel NumericUpDown denetimi  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Önkoşulları](#prerequisites)  
  
-   [Bölümler ve durumlar modeli](#parts_and_states_model)  
  
-   [Görsel yapı ve bir denetim görsel davranışını bir ControlTemplate tanımlama](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [Kodda ControlTemplate bölümlerini kullanma](#using_parts_of_the_controltemplate_in_code)  
  
-   [Denetim anlaşması sağlama](#providing_the_control_contract)  
  
-   [Tam örnek](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu yeni oluşturma bildiğinizi varsayar <xref:System.Windows.Controls.ControlTemplate> varolan bir denetim için bir denetim sözleşme öğeleri nelerdir ile deneyiminiz ve de açıklanan kavramları anlamanız [tarafından mevcut bir denetiminin görünümünü özelleştirme ControlTemplate oluşturma](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Özelleştirilmiş görünümünü olabilir bir denetim oluşturmak için öğesinden devralan bir denetim oluşturmak <xref:System.Windows.Controls.Control> sınıf veya onun alt sınıfların dışında biri <xref:System.Windows.Controls.UserControl>.  Öğesinden devralan bir denetim <xref:System.Windows.Controls.UserControl> hızlı oluşturulabilir bir denetimdir, ancak kullanmaz bir <xref:System.Windows.Controls.ControlTemplate> ve görünümünü özelleştiremezsiniz.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Bölümler ve durumlar modeli  
 Bölümler ve durumlar modeli görsel yapı ve bir denetim görsel davranışını tanımlamak nasıl belirtir. Bölümler ve durumlar modelini izlemek için aşağıdakileri yapmalısınız:  
  
-   Görsel yapı ve görsel davranışını tanımlamak <xref:System.Windows.Controls.ControlTemplate> denetimi.  
  
-   Denetim mantığının denetim şablonu bölümleriyle etkileşim kurduğunda bazı en iyi uygulamaları izleyin.  
  
-   Nelerin bulunması belirtmek için bir denetim sözleşme sağlamak <xref:System.Windows.Controls.ControlTemplate>.  
  
 Görsel yapı ve görsel davranışı tanımladığınızda <xref:System.Windows.Controls.ControlTemplate> bir denetimin uygulama yazarları görsel yapı ve görsel davranışını yeni oluşturarak değiştirebilirsiniz <xref:System.Windows.Controls.ControlTemplate> kod yazmak yerine.   Uygulama bildiren bir denetim anlaşması yazarlarına hangi sağlamalısınız <xref:System.Windows.FrameworkElement> içindeki nesneleri ve durumlarını tanımlanmalıdır <xref:System.Windows.Controls.ControlTemplate>. Bölümleri ile etkileşim sırasında bazı en iyi uygulamaları izlemelisiniz <xref:System.Windows.Controls.ControlTemplate> denetiminizi düzgün tamamlanmamış işler böylece <xref:System.Windows.Controls.ControlTemplate>.  Bu üç ilkeyi izlerseniz, uygulama yazarları oluşturabilmek için bir <xref:System.Windows.Controls.ControlTemplate> denetiminiz için gibi kolayca denetimleri ile birlikte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Aşağıdaki bölümde her öneriyi ayrıntılı açıklar.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Görsel yapı ve bir denetim görsel davranışını bir ControlTemplate tanımlama  
 Bölümler ve durumlar modelini kullanarak özel denetim oluşturduğunuzda, denetimin görsel yapısı ve görsel davranışını tanımlamak, <xref:System.Windows.Controls.ControlTemplate> yerine mantığındaki.  Bir denetim görsel yapısını bileşimi olur <xref:System.Windows.FrameworkElement> denetimini oluşturan nesneleri.  Görsel davranışını belirli bir durumda olduğunda denetim görünür yoludur.   Oluşturma hakkında daha fazla bilgi için bir <xref:System.Windows.Controls.ControlTemplate> görsel yapı ve bir denetim görsel davranışını belirtir, bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
 Örneğinde `NumericUpDown` denetim, görsel yapısı içeren iki <xref:System.Windows.Controls.Primitives.RepeatButton> denetimleri ve <xref:System.Windows.Controls.TextBlock>.  Bu denetimler kodunda eklerseniz `NumericUpDown` denetiminde--kendi oluşturucusu, örneğin--bu denetimleri konumlarını değiştirilemez olur.  Kendi kodunda denetimin görsel yapısı ve görsel davranışını tanımlamak yerine, içinde tanımlarsınız <xref:System.Windows.Controls.ControlTemplate>.  Düğmeleri konumunu özelleştirmek için sonra uygulama geliştiricisinin ve <xref:System.Windows.Controls.TextBlock> ve hangi davranış belirtin, `Value` negatif olduğundan <xref:System.Windows.Controls.ControlTemplate> değiştirilebilir.  
  
 Aşağıdaki örnek, görsel yapısını gösterir `NumericUpDown` içeren denetim bir <xref:System.Windows.Controls.Primitives.RepeatButton> artırmak için `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> azaltmak için `Value`ve bir <xref:System.Windows.Controls.TextBlock> görüntülemek için `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Görsel davranışını `NumericUpDown` denetimidir negatif ise değer kırmızı yazı tipinde olmasıdır.  Değiştirirseniz <xref:System.Windows.Controls.TextBlock.Foreground%2A> , <xref:System.Windows.Controls.TextBlock> buna kod ne zaman `Value` negatif `NumericUpDown` kırmızı bir negatif değer her zaman gösterir. Denetimin görsel davranışını belirtin <xref:System.Windows.Controls.ControlTemplate> ekleyerek <xref:System.Windows.VisualState> nesneleri <xref:System.Windows.Controls.ControlTemplate>.  Aşağıdaki örnekte gösterildiği <xref:System.Windows.VisualState> için nesneleri `Positive` ve `Negative` durumları.  `Positive` ve `Negative` olan birbirini dışlayan (denetimidir her zaman tam olarak iki birinde), bu nedenle örnek koyar <xref:System.Windows.VisualState> nesnelerini tek <xref:System.Windows.VisualStateGroup>.  Denetim gittiğinde içine `Negative` durumu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> , <xref:System.Windows.Controls.TextBlock> kırmızı kapatır.  Denetim olduğunda `Positive` durumu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> geri döndüğünde özgün değeri.  Tanımlama <xref:System.Windows.VisualState> nesnelerini bir <xref:System.Windows.Controls.ControlTemplate> daha ayrıntılı olarak ele alınmıştır [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Ayarladığınızdan emin olun <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> özelliği eklenmiş kök üzerinde <xref:System.Windows.FrameworkElement> , <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>Kodda ControlTemplate bölümlerini kullanma  
 A <xref:System.Windows.Controls.ControlTemplate> Yazar atlayabilir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.VisualState> nesneleri var veya yanlışlıkla, ancak denetim mantığının düzgün çalışması için bu bölümleri gerekebilir. Bölümler ve durumlar modeli denetiminizi dayanıklı olması gerektiğini belirtir. bir <xref:System.Windows.Controls.ControlTemplate> eksik olan <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.VisualState> nesneleri.  Denetim bir özel durum ya da rapor bir hata durumunda oluşturmamalıdır bir <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, veya <xref:System.Windows.VisualStateGroup> eksik <xref:System.Windows.Controls.ControlTemplate>. Bu bölümde ile etkileşmek için önerilen yöntemleri açıklar <xref:System.Windows.FrameworkElement> nesneleri ve durumlarını yönetme.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>Eksik FrameworkElement nesnelerini öngörme  
 Tanımladığınızda <xref:System.Windows.FrameworkElement> nesnelerini <xref:System.Windows.Controls.ControlTemplate>, denetim mantığının bazıları ile etkileşim kurmak için gerekli.  Örneğin, `NumericUpDown` denetim düğmelere abone <xref:System.Windows.Controls.Primitives.ButtonBase.Click> artırmak veya azaltmak için olay `Value` ve ayarlar <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği <xref:System.Windows.Controls.TextBlock> için `Value`. Özel bir varsa <xref:System.Windows.Controls.ControlTemplate> atlar <xref:System.Windows.Controls.TextBlock> veya düğmeleri, Denetim bazı işlevlerini kaybederse, ancak denetim hataya neden olmaz emin olmalısınız kabul edilebilir. Örneğin, varsa bir <xref:System.Windows.Controls.ControlTemplate> değiştirmek için düğmelerini içermiyor `Value`, `NumericUpDown` bu işlevselliği, ancak kullanan bir uygulamayı kaybederse <xref:System.Windows.Controls.ControlTemplate> çalışmaya devam eder.  
  
 Aşağıdaki yöntemler eksik denetiminizi düzgün yanıt sağlayacak <xref:System.Windows.FrameworkElement> nesneler:  
  
1.  Ayarlama `x:Name` her özniteliği <xref:System.Windows.FrameworkElement> , kodda başvurmanız gerekir.  
  
2.  Özel özellikler her biri için tanımlayın <xref:System.Windows.FrameworkElement> etkileşimde gereken.  
  
3.  Abone olma ve denetiminizin işlediği herhangi bir olayı aboneliğinizi <xref:System.Windows.FrameworkElement> özelliği erişimcisi küme.  
  
4.  Ayarlama <xref:System.Windows.FrameworkElement> tanımlanan özellikler adım 2 ' <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> yöntemi. Bu en kısa olduğundan, <xref:System.Windows.FrameworkElement> içinde <xref:System.Windows.Controls.ControlTemplate> denetimi için kullanılabilir. Kullanım `x:Name` , <xref:System.Windows.FrameworkElement> ondan almak için <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Denetleyin <xref:System.Windows.FrameworkElement> değil `null` üyelerine erişmeden önce.  Eğer öyleyse `null`, bir hata raporu gönderme.  
  
 Aşağıdaki örneklerde gösterildiği nasıl `NumericUpDown` denetim etkileşime <xref:System.Windows.FrameworkElement> önerileri yukarıdaki listede uygun olarak nesneleri.  
  
 Görsel yapısını tanımlayan örnekte `NumericUpDown` denetim <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton> , artırır `Value` sahip kendi `x:Name` özniteliği kümesine `UpButton`.  Aşağıdaki örnek adlı bir özelliği bildirir `UpButtonElement` temsil eden <xref:System.Windows.Controls.Primitives.RepeatButton> içinde bildirilen <xref:System.Windows.Controls.ControlTemplate>. `set` Erişimci aboneliğini iptal eder düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay varsa `UpDownElement` değil `null`özelliği ayarlar ve ardından abone olduğu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay. Ayrıca tanımlı, ancak burada diğer gösterilmeyen bir özellik olan <xref:System.Windows.Controls.Primitives.RepeatButton>adlı `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> için `NumericUpDown` denetim.  Örnek kullanır <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> almak için yöntemi <xref:System.Windows.FrameworkElement> nesnelerin <xref:System.Windows.Controls.ControlTemplate>.  Durumlara karşı koruduğu örneğe bildirimi <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> bulur bir <xref:System.Windows.FrameworkElement> belirtilen adla beklenen türde değil. Bu da belirtilen sahip öğeleri yoksaymak için en iyi uygulamadır `x:Name` ancak yanlış türde.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Önceki örneklerde gösterilen yöntemleri izleyerek, denetimin çalışmaya devam edeceğinden emin <xref:System.Windows.Controls.ControlTemplate> eksik bir <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>VisualStateManager durumları yönetmek için kullanma  
 <xref:System.Windows.VisualStateManager> Denetimin durumlarını izler ve durumları arasında geçiş için gereken mantığı gerçekleştirir. Eklediğinizde <xref:System.Windows.VisualState> nesneleri <xref:System.Windows.Controls.ControlTemplate>, bunları Ekle bir <xref:System.Windows.VisualStateGroup> ve ekleme <xref:System.Windows.VisualStateGroup> için <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> özelliği eklenmiş şekilde <xref:System.Windows.VisualStateManager> bunlara erişebilir.  
  
 Aşağıdaki örnek gösteren önceki örneği yineler <xref:System.Windows.VisualState> karşılık gelen nesneleri `Positive` ve `Negative` denetiminin durumları. <xref:System.Windows.Media.Animation.Storyboard> İçinde `Negative` <xref:System.Windows.VisualState> kapatır <xref:System.Windows.Controls.TextBlock.Foreground%2A> , <xref:System.Windows.Controls.TextBlock> kırmızı.   Zaman `NumericUpDown` denetimi `Negative` durumunda, film şeridi `Negative` durum başlar.  Ardından <xref:System.Windows.Media.Animation.Storyboard> içinde `Negative` denetimi döndüğünde durakları durum `Positive` durumu.  `Positive` <xref:System.Windows.VisualState> İçermesi gerekmez bir <xref:System.Windows.Media.Animation.Storyboard> çünkü zaman <xref:System.Windows.Media.Animation.Storyboard> için `Negative` durdurur, <xref:System.Windows.Controls.TextBlock.Foreground%2A> özgün rengine döndürür.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Unutmayın <xref:System.Windows.Controls.TextBlock> bir ad verilir ancak <xref:System.Windows.Controls.TextBlock> için Denetim sözleşmede değil `NumericUpDown` denetimin mantığı hiçbir zaman başvurduğundan <xref:System.Windows.Controls.TextBlock>.  İçinde başvurulan öğelerin <xref:System.Windows.Controls.ControlTemplate> adlara sahip, ancak denetim sözleşmesinin bir parçası olması gerekmez yeni <xref:System.Windows.Controls.ControlTemplate> denetimi o öğeye başvuru gerek olmayabileceği için.  Örneğin, birisi yeni oluşturan <xref:System.Windows.Controls.ControlTemplate> için `NumericUpDown` olduğunu göstermeyebilir karar verebilirsiniz `Value` değiştirerek negatifse <xref:System.Windows.Controls.Control.Foreground%2A>.  Bu durumda, hiçbiri kodu ya da <xref:System.Windows.Controls.ControlTemplate> başvuruları <xref:System.Windows.Controls.TextBlock> ada göre.  
  
 Denetimin mantığı denetimin durumunu değiştirmeden sorumludur. Aşağıdaki örnekte gösterilir `NumericUpDown` denetim çağrıları <xref:System.Windows.VisualStateManager.GoToState%2A> yerleştirilmesini yöntemi `Positive` duruma `Value` 0 veya daha büyük ve `Negative` duruma `Value` 0'dan küçük.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> Yöntemi film şeritleri uygun şekilde durdurmak ve başlatmak için gerekli mantığı gerçekleştirir. Bir denetim çağırdığında <xref:System.Windows.VisualStateManager.GoToState%2A> kendi durumunu değiştirmek için <xref:System.Windows.VisualStateManager> şunları yapar:  
  
-   Varsa <xref:System.Windows.VisualState> denetimi gittiği sahip bir <xref:System.Windows.Media.Animation.Storyboard>, film şeridi başlar. Ardından, eğer <xref:System.Windows.VisualState> denetimi geldiği sahip bir <xref:System.Windows.Media.Animation.Storyboard>, film şeridi sonlandırılır.  
  
-   Denetim zaten belirtilen durumda ise <xref:System.Windows.VisualStateManager.GoToState%2A> herhangi bir eylemi alıp döndüren `true`.  
  
-   Belirtilen durum yoksa <xref:System.Windows.Controls.ControlTemplate> , `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> herhangi bir eylemi alıp döndüren `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>VisualStateManager ile çalışmak için en iyi uygulamalar  
 Denetiminizin durumlarını korumak için aşağıdakileri yapmanız önerilir:  
  
-   Özelliklerini, durumunu izlemek için kullanın.  
  
-   Durumlar arasında geçiş için yardımcı bir yöntem oluşturun.  
  
 `NumericUpDown` Denetim kullanan kendi `Value` içinde olup olmadığını izlemek için özellik `Positive` veya `Negative` durumu.  `NumericUpDown` Denetimi de tanımlar `Focused` ve `UnFocused` durumlarını izleyen <xref:System.Windows.UIElement.IsFocused%2A> özelliği. Doğal olarak denetimi özelliğine karşılık gelmeyen durumları kullanırsanız, durumunu izlemek için özel bir özellik tanımlayabilirsiniz.  
  
 Tüm durumları güncelleştiren tek bir yöntem çağrıları için merkezi bir hale gelecektir. <xref:System.Windows.VisualStateManager> ve kodunuzun yönetilebilirliğini korur. Aşağıdaki örnekte gösterildiği `NumericUpDown` denetiminin yardımcı yöntemi, `UpdateStates`. Zaman `Value` büyük veya 0 olarak eşit <xref:System.Windows.Controls.Control> yer `Positive` durumu.  Zaman `Value` olan 0'dan küçük denetimi bulunduğu `Negative` durumu.  Zaman <xref:System.Windows.UIElement.IsFocused%2A> olan `true`, denetimin `Focused` durum; Aksi takdirde olduğu `Unfocused` durumu.  Denetim çağırabilirsiniz `UpdateStates` hangi durumu değişir bağımsız olarak kendi durumunu değiştirmek ihtiyaç duyduğunda.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 Bir durum adı geçirirseniz <xref:System.Windows.VisualStateManager.GoToState%2A> denetim o durumda olduğunda <xref:System.Windows.VisualStateManager.GoToState%2A> hiçbir şey yapmaz, bu nedenle denetimin geçerli durumunu denetlemek gerekmez.  Örneğin, varsa `Value` bir negatif sayıdan başka negatif sayı, film şeridi değişiklikler `Negative` durumu kesintiye ve kullanıcı denetimde değişiklik görmez.  
  
 <xref:System.Windows.VisualStateManager> Kullanan <xref:System.Windows.VisualStateGroup> çağırdığınızda çıkmak için hangi durumu belirlemek için nesneleri <xref:System.Windows.VisualStateManager.GoToState%2A>. Denetimi her zaman bir için her durumda <xref:System.Windows.VisualStateGroup> içinde tanımlanan kendi <xref:System.Windows.Controls.ControlTemplate> ve başka bir duruma aynı geçtiğinde yalnızca bir durumda bırakır <xref:System.Windows.VisualStateGroup>. Örneğin, <xref:System.Windows.Controls.ControlTemplate> , `NumericUpDown` denetimi tanımlar `Positive` ve `Negative` <xref:System.Windows.VisualState> nesnelerini <xref:System.Windows.VisualStateGroup> ve `Focused` ve `Unfocused` <xref:System.Windows.VisualState> başka bir nesne. (Gördüğünüz `Focused` ve `Unfocused` <xref:System.Windows.VisualState> tanımlanan [tam örnek](#complete_example) denetimi geçerse bu bölümde `Positive` durumunu `Negative` durumu veya tam tersi, Denetim ya da kalır `Focused` veya `Unfocused` durumu.  
  
 Bir denetimin durumunu burada değişebilir üç tipik yerde vardır:  
  
-   Zaman <xref:System.Windows.Controls.ControlTemplate> uygulanan <xref:System.Windows.Controls.Control>.  
  
-   Bir özellik değiştiğinde.  
  
-   Bir olay meydana geldiğinde.  
  
 Aşağıdaki örnekler durumunu güncelleştirme göstermek `NumericUpDown` bu gibi durumlarda denetim.  
  
 Denetimin durumu güncelleştirmeniz gerekir <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> yöntemi böylece denetim doğru durumda görünür duruma <xref:System.Windows.Controls.ControlTemplate> uygulanır. Aşağıdaki örnek çağrıları `UpdateStates` içinde <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> denetimi uygun durumda olduğundan emin olmak için.  Örneğin, oluşturduğunuz varsayalım bir `NumericUpDown` denetleyin ve sonra ayarlayın, <xref:System.Windows.Controls.Control.Foreground%2A> yeşil ve `Value` -5.  Değil çağırırsanız `UpdateStates` zaman <xref:System.Windows.Controls.ControlTemplate> uygulanan `NumericUpDown` denetimi, denetim içinde değil `Negative` durumu ve değeri yerine kırmızı yeşil.  Çağırmalısınız `UpdateStates` denetim yerleştirmek için `Negative` durumu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Genellikle bir özellik değiştiğinde denetimin durumlarını güncelleştirmeniz gerekir. Aşağıdaki örnek, tüm gösterir `ValueChangedCallback` yöntemi. Çünkü `ValueChangedCallback` aldığında çağrılan `Value` değişikliği, yöntem çağrılarını `UpdateStates` durumda `Value` pozitif negatif veya değiştirildi. Çağırmak için kabul edilebilir `UpdateStates` zaman `Value` değişir ancak çünkü bu durumda, Denetim durumları değiştirmez olumlu veya olumsuz kalır.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Bir olay oluştuğunda durumları güncelleştirmeniz gerekebilir. Aşağıdaki örnekte gösterilir `NumericUpDown` çağrıları `UpdateStates` üzerinde <xref:System.Windows.Controls.Control> işlemek için <xref:System.Windows.UIElement.GotFocus> olay.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> Denetiminizin durumlarını yönetmenize yardımcı olur. Kullanarak <xref:System.Windows.VisualStateManager>, Denetim doğru durumları arasında geçiş emin olun.  İle çalışmak için bu bölümde açıklanan önerileri izlerseniz <xref:System.Windows.VisualStateManager>, denetiminizin kodu okunabilir ve sürdürülebilir kalacaktır.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>Denetim anlaşması sağlama  
 Denetim anlaşması sağlamak için <xref:System.Windows.Controls.ControlTemplate> yazarlar bilmesi ne şablonda yerleştirilecek. Denetim anlaşması üç öğeye sahiptir:  
  
-   Denetimin mantığı kullanır görsel öğeler.  
  
-   Denetim ve Grup durumları her durum ait.  
  
-   Denetim görsel olarak etkileyen ortak özellikler.  
  
 Yeni bir oluşturan birinin <xref:System.Windows.Controls.ControlTemplate> ne bilmek ister <xref:System.Windows.FrameworkElement> nesnelerini denetimin mantığı kullandığını, ne tür oluşturduğunu ve adını. A <xref:System.Windows.Controls.ControlTemplate> yazarının ayrıca gerekiyor denetim içinde olabileceği olası her durum ve hangi adını bilmesi <xref:System.Windows.VisualStateGroup> durumu kullanılıyor.  
  
 Dönme `NumericUpDown` örnek, Denetim bekliyor <xref:System.Windows.Controls.ControlTemplate> aşağıdaki olmasını <xref:System.Windows.FrameworkElement> nesneler:  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> adlı `UpButton`.  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> çağrılır `DownButton.`  
  
 Denetimi şu durumlarda olabilir:  
  
-   İçinde `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   İçinde `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Ne belirtmek için <xref:System.Windows.FrameworkElement> denetimi nesneleri bekler, kullandığınız <xref:System.Windows.TemplatePartAttribute>, beklenen öğelerin türü ve adını belirtir.  Denetimin olası durumlarını belirtmek için kullandığınız <xref:System.Windows.TemplateVisualStateAttribute>, durumun adını ve hangi belirten <xref:System.Windows.VisualStateGroup> ait.  PUT <xref:System.Windows.TemplatePartAttribute> ve <xref:System.Windows.TemplateVisualStateAttribute> denetimin sınıf tanımı üzerinde.  
  
 Denetimin görünümünü etkileyen herhangi bir ortak özellik de denetim sözleşme parçasıdır.  
  
 Aşağıdaki örnek belirtir <xref:System.Windows.FrameworkElement> nesne ve durumlarını `NumericUpDown` denetim.  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki örnekte tüm olan <xref:System.Windows.Controls.ControlTemplate> için `NumericUpDown` denetim.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 Aşağıdaki örnek mantığını gösterir `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)  
 [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)
