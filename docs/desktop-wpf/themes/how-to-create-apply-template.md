---
title: WPF - .NET Desktop'da şablon oluşturma
description: Windows Sunu Temeli ve .NET Core'da bir denetim şablonu oluşturmayı ve başvururmayı öğrenin.
author: thraka
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071250"
---
# <a name="create-a-template-for-a-control"></a>Denetim için şablon oluşturma

Windows Sunu Temeli (WPF) ile varolan bir denetimin görsel yapısını ve davranışını kendi yeniden kullanılabilir şablonunuzla özelleştirebilirsiniz. Şablonlar genel olarak uygulamanıza, pencerelere ve sayfalara veya doğrudan denetimlere uygulanabilir. Yeni bir denetim oluşturmanızı gerektiren çoğu senaryo, varolan bir denetim için yeni bir şablon oluşturmak yerine kapsanabilir.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Bu makalede, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> denetim için yeni bir oluşturma yı keşfedeceksiniz.

## <a name="when-to-create-a-controltemplate"></a>Denetim Şablonu ne zaman oluşturulacak?

Denetimlerin <xref:System.Windows.Controls.Border.Background%2A>, , <xref:System.Windows.Controls.Control.Foreground%2A>ve <xref:System.Windows.Controls.Control.FontFamily%2A>. Bu özellikler denetimin görünümünün farklı yönlerini denetler, ancak bu özellikleri ayarlayarak yapabileceğiniz değişiklikler sınırlıdır. Örneğin, <xref:System.Windows.Controls.Control.Foreground%2A> özelliği maviye ve <xref:System.Windows.Controls.Control.FontStyle%2A> italik bir <xref:System.Windows.Controls.CheckBox>'de ayarlayabilirsiniz. Denetimin görünümünü, denetimdeki diğer özelliklerin yapabileceklerinin ötesinde özelleştirmek istediğinizde, <xref:System.Windows.Controls.ControlTemplate>bir .

Çoğu kullanıcı arabiriminde, bir düğme aynı genel görünüme sahiptir: bazı metin içeren bir dikdörtgen. Yuvarlatılmış bir düğme oluşturmak istiyorsanız, düğmeden devralan veya düğmenin işlevselliğini yeniden oluşturan yeni bir denetim oluşturabilirsiniz. Buna ek olarak, yeni kullanıcı denetimi dairesel görsel sağlayacaktır.

Varolan bir denetimin görsel düzenini özelleştirerek yeni denetimler oluşturmaktan kaçınabilirsiniz. Yuvarlatılmış bir düğme yle, istenilen görsel düzene sahip bir düğme <xref:System.Windows.Controls.ControlTemplate> oluşturursunuz.

Diğer taraftan, yeni işlevsellik, farklı özellikler ve yeni ayarlarla bir denetime <xref:System.Windows.Controls.UserControl>ihtiyacınız varsa, yeni bir .

## <a name="prerequisites"></a>Önkoşullar

Yeni bir WPF uygulaması oluşturun ve *MainWindow.xaml'da* (veya seçtiğiniz başka bir pencerede) ** \<Pencere>** öğesindeki aşağıdaki özellikleri ayarlayın:

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

** \<Pencere>** öğesinin içeriğini aşağıdaki XAML'ye ayarlayın:

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Sonunda, *MainWindow.xaml* dosyası aşağıdakilere benzer olmalıdır:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Uygulamayı çalıştırarsanız, aşağıdaki gibi görünür:

![İki unstyled düğmeleri ile WPF penceresi](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>Denetim Şablonu Oluşturma

A'yı <xref:System.Windows.Controls.ControlTemplate> bildirmenin en yaygın yolu, `Resources` XAML dosyasındaki bölümde kaynak olarak dır. Şablonlar kaynak olduğundan, tüm kaynaklar için geçerli olan aynı kapsam kurallarına uyarlar. Basitçe söylemek gerekirse, şablonu beyan ettiğiniz yer şablonun uygulanabileceği yeri etkiler. Örneğin, şablonu uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, şablon uygulamanızın herhangi bir yerinde kullanılabilir. Şablonu bir pencerede tanımlarsanız, şablonu yalnızca bu penceredeki denetimler kullanabilir.

Başlangıç olarak, `Window.Resources` *MainWindow.xaml* dosyanıza bir öğe ekleyin:

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Aşağıdaki özellikleri ** \<** kümesi ile yeni bir Denetim Şablonu>oluşturun:

|     |     |
| --- | --- |
| **x:Anahtar**         | `roundbutton` |
| **TargetType**    | `Button` |

Bu denetim şablonu basit olacaktır:

- kontrol için bir kök öğesi, bir<xref:System.Windows.Controls.Grid>
- düğmenin yuvarlak görünümünü çizmek için bir <xref:System.Windows.Shapes.Ellipse>
- a <xref:System.Windows.Controls.ContentPresenter> kullanıcı tarafından belirtilen düğme içeriğini görüntülemek için

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>Templatebinding

Yeni <xref:System.Windows.Controls.ControlTemplate>bir , denetimin görünümünü değiştirmek için ortak özellikleri kullanmak isteyebilirsiniz. [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) biçimlendirme uzantısı, denetim tarafından tanımlanan bir kamu <xref:System.Windows.Controls.ControlTemplate> malında bulunan bir öğenin özelliğini bağlar. [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)kullandığınızda, denetimdeki özelliklerin şablona parametre olarak hareket etmesini sağlarsınız. Diğer bir şey, denetimüzerindeki bir özellik ayarlandığında, bu değer üzerinde [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) olan öğeye aktarılır.

### <a name="ellipse"></a>Elips

**:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> **Elips>öğesinin ve özelliklerinin denetimin ve özelliklerine bağlı \<** olduğuna dikkat edin.

### <a name="contentpresenter"></a>Contentpresenter

Şablona ContentPresenter>öğesi de eklenir. [ \<](xref:System.Windows.Controls.ContentPresenter) Bu şablon bir düğme için tasarlandığından, düğmenin <xref:System.Windows.Controls.ContentControl>'den devraldığı göz önünde bulundurulmalıdır. Düğme öğenin içeriğini sunar. Düz metin veya başka bir denetim gibi düğmenin içindeki her şeyi ayarlayabilirsiniz. Aşağıdakilerin her ikisi de geçerli düğmelerdir:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

Önceki örneklerin her ikisinde de metin ve onay kutusu [Button.Content](xref:System.Windows.Controls.ContentControl.Content) özelliği olarak ayarlanır. İçerik olarak ayarlanan ne olursa ** \< **olsun, şablonun yaptığı bir ContentPresenter>aracılığıyla sunulabilir.

A, a `Button`gibi <xref:System.Windows.Controls.ContentControl> bir türe uygulanırsa, <xref:System.Windows.Controls.ContentPresenter> öğe ağacında aranır. <xref:System.Windows.Controls.ControlTemplate> `ContentPresenter` Bulunursa, şablon denetimin <xref:System.Windows.Controls.ContentControl.Content> özelliğini otomatik olarak `ContentPresenter`.

## <a name="use-the-template"></a>Şablonu kullanma

Bu makalenin başında bildirilen düğmeleri bulun.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

İkinci düğmenin <xref:System.Windows.Controls.Control.Template> özelliğini kaynağa `roundbutton` ayarlayın:

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Projeyi çalıştırıp sonuca bakarsanız, düğmenin yuvarlak bir arka plana sahip olduğunu görürsünüz.

![Bir şablon oval düğmeile WPF penceresi](media/create-apply-template/styled-button.png)

Düğmenin bir daire olmadığını, eğri olduğunu fark etmiş olabilirsiniz. Elips>öğesinin çalışma şekli nedeniyle, her zaman kullanılabilir alanı doldurmak için genişler. ** \<** Düğmenin **:::no-loc text="width":::** ve **:::no-loc text="height":::** özelliklerinin aynı değere değiştirilmesiyle daireyi tek tipleştirin:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Tek şablon dairesel düğmeli WPF penceresi](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Tetikleyici Ekleme

Uygulamalı şabloniçeren bir düğme farklı görünse de, diğer düğmelerle aynı şekilde görünür. Düğmeye basarsanız, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay ateşler. Ancak, farenizi düğmenin üzerinde hareket ettirdiğinizde düğmenin görsellerinin değişmediğini fark etmiş olabilirsiniz. Bu görsel etkileşimlerin tümü şablon tarafından tanımlanır.

WPF'nin sağladığı dinamik olay ve özellik sistemleriyle, belirli bir özelliği bir değer için izleyebilir ve uygun olduğunda şablonu yeniden şekillendirebilirsiniz. Bu örnekte, düğmenin <xref:System.Windows.UIElement.IsMouseOver> özelliğini izlersiniz. Fare denetimin üzerindeyken, ** \<Elips>** yeni bir renkle şekillendirin. Bu tür tetikleyici *propertytrigger*olarak bilinir.

Bunun işe yaraması için ** \<Elips>** başvuruda bulunabileceğiniz bir ad eklemeniz gerekir. **Ona backgroundElement**adını verin.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Ardından, <xref:System.Windows.Trigger> [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) koleksiyonuna yeni bir ekleme. Tetikleyici değeri `true`için `IsMouseOver` olay izleyecek.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Ardından, ** \<Elips>** **Dolgu** özelliğini yeni bir renge değiştiren ** \<Tetikleyici>** bir ** \<Ayarlayıcı>** ekleyin.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Projeyi çalıştırın. Fareyi düğmenin üzerinde hareket ettirdiğinizde ** \<Elips'in** renginin>değişir.

![fare dolgu rengini değiştirmek için WPF tuşu üzerinde hareket eder](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>VisualState kullanma

Görsel durumlar bir denetim tarafından tanımlanır ve tetiklenir. Örneğin, fare denetimin üstüne taşındığında, `CommonStates.MouseOver` durum tetiklenir. Özellik değişikliklerini denetimin geçerli durumuna göre canlandırabilirsiniz. Önceki bölümde, bir ** \<PropertyTrigger>** özelliği ne zaman `IsMouseOver` düğmenin ön planda `true`değiştirmek için `AliceBlue` kullanılmıştır . Bunun yerine, düzgün bir geçiş sağlayarak bu rengin değişimini animasyona rendiren görsel bir durum oluşturun. *VisualStates*hakkında daha fazla bilgi için [WPF'deki Stiller ve şablonlara](../fundamentals/styles-templates-overview.md#visual-states)bakın.

PropertyTrigger>animasyonlu görsel duruma dönüştürmek için önce ** \<ControlTemplate.Triggers>** öğesini şablonunuzdan kaldırın. ** \<**

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Ardından, denetim şablonunun ** \<Grid>** kökünde ** \<VisualStateManager.VisualStateGroups>** öğesini ** \<visualStateGroup>** ile `CommonStates`ekleyin. İki durum `Normal` tanımlayın ve `MouseOver`.

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

VisualState>tanımlanan animasyonlar, bu durum tetiklendiğinde uygulanır. ** \<** Her durum için animasyonlar oluşturun. Animasyonlar bir ** \<Storyboard>** öğesinin içine konur. Storyboards hakkında daha fazla bilgi için [Storyboards Genel Bakış'a](../../framework/wpf/graphics-multimedia/storyboards-overview.md)bakın.

- Normal

  Bu durum elips dolgusu animasyonlar, kontrol `Background` renginde geri.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- Mouseover

  Bu durum, elips `Background` rengini yeni bir renge animasyona salar: `Yellow`.

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

DenetimŞablonu>artık aşağıdaki gibi görünmelidir. ** \<**

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Projeyi çalıştırın. Fareyi düğmenin üzerinde hareket ettirdiğinizde, ** \<Elips'in** renginin animasyon>dikkat edin.

![fare dolgu rengini değiştirmek için WPF tuşu üzerinde hareket eder](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Sonraki adımlar

- [WPF'de denetim için stil oluşturma](../fundamentals/styles-templates-create-apply-style.md)
- [WPF'deki stiller ve şablonlar](../fundamentals/styles-templates-overview.md)
- [XAML Kaynaklarına Genel Bakış](../fundamentals/xaml-resources-define.md)
