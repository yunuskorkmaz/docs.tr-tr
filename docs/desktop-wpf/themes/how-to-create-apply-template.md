---
title: WPF-.NET Desktop 'ta şablon oluşturma
description: Windows Presentation Foundation ve .NET Core 'da bir denetim şablonu oluşturmayı ve başvuruyu yapmayı öğrenin.
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

Windows Presentation Foundation (WPF) ile, var olan bir denetimin görsel yapısını ve davranışını kendi yeniden kullanılabilir şablonunuz ile özelleştirebilirsiniz. Şablonlar uygulamanıza, Windows ve sayfalarınıza Global olarak veya doğrudan denetimlere uygulanabilir. Yeni bir denetim oluşturmanızı gerektiren çoğu senaryo, var olan bir denetim için yeni bir şablon oluşturmak yerine tarafından ele alınabilir.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Bu makalede, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> denetim için yeni bir oluşturma keşfedeceksiniz.

## <a name="when-to-create-a-controltemplate"></a>ControlTemplate ne zaman oluşturulur

Denetimlerin,, ve <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontFamily%2A>gibi birçok özelliği vardır. Bu özellikler, denetimin görünümünün farklı yönlerini denetler, ancak bu özellikleri ayarlayarak yapabileceğiniz değişiklikler sınırlıdır. Örneğin, <xref:System.Windows.Controls.Control.Foreground%2A> özelliğini mavi ve <xref:System.Windows.Controls.Control.FontStyle%2A> italik olarak bir <xref:System.Windows.Controls.CheckBox>olarak ayarlayabilirsiniz. Denetimin diğer özelliklerinin yapabilecekleri ayarların ötesinde denetimin görünümünü özelleştirmek istediğinizde, bir <xref:System.Windows.Controls.ControlTemplate>oluşturursunuz.

Çoğu kullanıcı arabiriminde, bir düğme aynı genel görünüme sahiptir: metin içeren bir dikdörtgen. Yuvarlatılmış düğme oluşturmak isterseniz, düğmeden devralan yeni bir denetim oluşturabilir veya düğmenin işlevselliğini yeniden oluşturabilirsiniz. Ayrıca, Yeni Kullanıcı denetimi dairesel görseli sağlar.

Varolan bir denetimin görsel yerleşimini özelleştirerek yeni denetimler oluşturmaktan kaçınabilirsiniz. Yuvarlatılmış bir düğme ile, istenen görsel Düzen <xref:System.Windows.Controls.ControlTemplate> ile bir oluşturabilirsiniz.

Öte yandan, yeni işlevlerle, farklı özelliklerde ve yeni ayarlarla bir denetime ihtiyacınız varsa yeni <xref:System.Windows.Controls.UserControl>bir oluştur.

## <a name="prerequisites"></a>Önkoşullar

Yeni bir WPF uygulaması oluşturun ve *MainWindow. xaml* içinde (veya seçtiğiniz başka bir pencerede), ** \<pencere>** öğesinde aşağıdaki özellikleri ayarlayın:

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

Pencere>öğesinin içeriğini aşağıdaki xaml olarak ayarlayın: ** \<**

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Sonda, *MainWindow. xaml* dosyası şuna benzer şekilde görünmelidir:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Uygulamayı çalıştırırsanız, aşağıdaki gibi görünür:

![İki stilli düğme içeren WPF penceresi](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>ControlTemplate oluşturma

' In en yaygın yolu, bir <xref:System.Windows.Controls.ControlTemplate> xaml dosyasındaki `Resources` bölümünde kaynak olarak kullanılır. Şablonlar kaynaklar olduğundan, tüm kaynaklar için uygulanan aynı kapsam kurallarına uyar. Basitçe, şablonun nerede uygulanabileceğini etkileyen bir şablon bildirdiğiniz yere koyun. Örneğin, şablonu uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, şablon uygulamanızda herhangi bir yerde kullanılabilir. Şablonu bir pencerede tanımlarsanız, şablonu yalnızca o penceredeki denetimler kullanabilir.

İle başlamak için, `Window.Resources` *MainWindow. xaml* dosyanıza bir öğesi ekleyin:

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Aşağıdaki özellikler kümesiyle yeni ** \<bir ControlTemplate>** oluşturun:

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

Bu denetim şablonu basit olacaktır:

- Denetim için bir kök öğe,<xref:System.Windows.Controls.Grid>
- düğmenin <xref:System.Windows.Shapes.Ellipse> yuvarlanmış görünümünü çizmek için bir
- <xref:System.Windows.Controls.ContentPresenter> Kullanıcı tarafından belirtilen düğme içeriğini görüntüleme

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

Yeni <xref:System.Windows.Controls.ControlTemplate>bir oluşturduğunuzda, denetimin görünümünü değiştirmek için yine de ortak özellikleri kullanmak isteyebilirsiniz. [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) biçimlendirme uzantısı, <xref:System.Windows.Controls.ControlTemplate> içindeki bir öğesinin özelliğini Denetim tarafından tanımlanan ortak bir özelliğe bağlar. Bir [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)kullandığınızda, denetimdeki özellikleri şablona parametre olarak davranacak şekilde etkinleştirin. Diğer bir deyişle, bir denetimdeki özellik ayarlandığında, bu değer üzerinde [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 'e sahip olan öğeye geçirilir.

### <a name="ellipse"></a>Tir

**:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> **Elips \<>** öğesinin ve özelliklerinin, denetimin ve özelliklerin özelliklerine bağlandığını unutmayın.

### <a name="contentpresenter"></a>ContentPresenter

Bir [ \<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) öğesi şablona de eklenir. Bu şablon bir düğme için tasarlandığından, düğmenin Devralındığı göz önüne alın <xref:System.Windows.Controls.ContentControl>. Düğme, öğenin içeriğini gösterir. Düğmenin içinde düz metin veya başka bir denetim gibi her şeyi de ayarlayabilirsiniz. Aşağıdakilerden her ikisi de geçerli düğmelerdir:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

Yukarıdaki örneklerde, metin ve onay kutusu, [Button. Content](xref:System.Windows.Controls.ContentControl.Content) özelliği olarak ayarlanır. İçerik ne olursa olsun, bu, şablonun yaptığı bir ** \<ContentPresenter>** aracılığıyla sunulabilir.

' A gibi <xref:System.Windows.Controls.ContentControl> bir türe uygulanırsa, öğe ağacında için bir <xref:System.Windows.Controls.ContentPresenter> aranır. <xref:System.Windows.Controls.ControlTemplate> `Button` `ContentPresenter` Bulunursa, şablon denetimin <xref:System.Windows.Controls.ContentControl.Content> özelliğini otomatik olarak öğesine bağlar `ContentPresenter`.

## <a name="use-the-template"></a>Şablonu kullanma

Bu makalenin başlangıcında belirtilen düğmeleri bulun.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

İkinci düğmenin <xref:System.Windows.Controls.Control.Template> özelliğini `roundbutton` kaynak olarak ayarlayın:

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Projeyi çalıştırırsanız ve sonuca baktığınızda, düğmenin yuvarlatılmış bir arka plana sahip olduğunu görürsünüz.

![Tek şablon oval düğme içeren WPF penceresi](media/create-apply-template/styled-button.png)

Düğmenin bir daire olmadığını fark etmiş olabilirsiniz ancak eğriltilmiş olduğunu fark etmiş olabilirsiniz. Elips>öğenin çalışma biçimi nedeniyle, her zaman kullanılabilir alanı dolduracak şekilde genişler. ** \<** Düğme **:::no-loc text="width":::** ve özelliklerini aynı değere değiştirerek, **:::no-loc text="height":::** daireyi tek tek yapın:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Bir şablon dairesel düğme içeren WPF penceresi](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Tetikleyici ekleme

Şablon uygulanmış bir düğme farklı görünse de, diğer düğmeyle aynı şekilde davranır. Düğmeye basarsanız <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay ateşlenir. Ancak, farenizi düğmenin üzerine getirdiğinizde düğmenin görselleri değişmeyin olduğunu fark etmiş olabilirsiniz. Bu görsel etkileşimler şablon tarafından tanımlanır.

WPF 'in sağladığı dinamik olay ve özellik sistemleri ile, bir değer için belirli bir özelliği izleyebilir ve uygun olduğunda şablonu yeniden oluşturabilirsiniz. Bu örnekte, düğmenin <xref:System.Windows.UIElement.IsMouseOver> özelliğini izleyeceksiniz. Fare denetimin üzerindeyken, ** \<elipsi** yeni bir renkle>stil yapın. Bu tetikleyici türü bir *Propertytrigger*olarak bilinir.

Bunun çalışması için, ** \<>elips** 'e başvurabileceksiniz bir ad eklemeniz gerekir. **BackgroundElement**adını verin.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Sonra, <xref:System.Windows.Trigger> [ControlTemplate. Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) koleksiyonuna yeni bir ekleyin. Tetikleyici, değeri `IsMouseOver` `true`için olayını izleyen bir işlem görür.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Sonra,>**>, \<elipsin** **Fill** özelliğini yeni bir renge değiştiren ** \<tetikleyicisine** bir ** \<ayarlayıcı>** ekleyin.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Projeyi çalıştırın. Fareyi düğmenin üzerine getirdiğinizde ** \<elipsin renginin>** değişiklik olduğunu unutmayın.

![fare, tüm WPF düğmesine taşınıyor ve Fill rengini değiştirme](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>VisualState kullanma

Görsel durumlar, bir denetim tarafından tanımlanır ve tetiklenir. Örneğin, fare denetimin üzerine taşındığında `CommonStates.MouseOver` durum tetiklenir. Denetimin geçerli durumuna bağlı olarak özellik değişikliklerine animasyon uygulayabilirsiniz. Önceki bölümde, düğmenin ön planını `IsMouseOver` özelliğin olduğu `true` `AliceBlue` zaman değiştirmek için bir ** \<propertytrigger>** kullanıldı. Bunun yerine, bu rengin değişikliğini canlandırarak kesintisiz bir geçiş sağlayan görsel bir durum oluşturun. *Visualstates*hakkında daha fazla bilgi için bkz. [WPF 'de stiller ve şablonlar](../fundamentals/styles-templates-overview.md#visual-states).

Propertytrigger>, bir animasyonlu görsel durumuna dönüştürmek için, önce şablonınızdan ** \<ControlTemplate. Triggers>** öğesini kaldırın. ** \<**

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Sonra, denetim şablonunun ** \<kılavuzundaki>** kökünde, VisualStateManager ** \<. VisualStateGroups>** öğesini için `CommonStates`bir ** \<VisualStateGroup>** ekleyin. İki durum tanımlayın `Normal` ve `MouseOver`.

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

VisualState>tanımlı animasyonlar, bu durum tetiklendiğinde uygulanır. ** \<** Her durum için animasyonlar oluşturun. Animasyonlar, ** \<film şeridi>** öğesi içine konur. Görsel Taslaklar hakkında daha fazla bilgi için bkz. [görsel taslakları genel bakış](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

- Normal

  Bu durum, elips dolgusunun animasyonunu, denetimin `Background` rengine geri yüklemeyi hareketlendirir.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- Gelme olayından

  Bu durum, elips `Background` rengini yeni bir renkle hareketlendirir:. `Yellow`

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

ControlTemplate>artık aşağıdaki gibi görünmelidir. ** \<**

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Projeyi çalıştırın. Fareyi düğmenin üzerine getirdiğinizde, ** \<elips>** hareketlendirir ' ın rengini hareketlendirdiğine dikkat edin.

![fare, tüm WPF düğmesine taşınıyor ve Fill rengini değiştirme](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Sonraki adımlar

- [WPF içindeki bir denetim için stil oluşturma](../fundamentals/styles-templates-create-apply-style.md)
- [WPF 'deki stiller ve şablonlar](../fundamentals/styles-templates-overview.md)
- [XAML kaynaklarına genel bakış](../fundamentals/xaml-resources-define.md)
