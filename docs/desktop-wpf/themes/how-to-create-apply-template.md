---
title: WPF-.NET Desktop 'ta şablon oluşturma
description: Windows Presentation Foundation ve .NET Core 'da bir denetim şablonu oluşturmayı ve başvuruyu yapmayı öğrenin.
author: adegeo
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
ms.openlocfilehash: 8be38a2b4f046a43ab187ea3517335437ec49b08
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551900"
---
# <a name="create-a-template-for-a-control"></a>Denetim için şablon oluşturma

Windows Presentation Foundation (WPF) ile, var olan bir denetimin görsel yapısını ve davranışını kendi yeniden kullanılabilir şablonunuz ile özelleştirebilirsiniz. Şablonlar uygulamanıza, Windows ve sayfalarınıza Global olarak veya doğrudan denetimlere uygulanabilir. Yeni bir denetim oluşturmanızı gerektiren çoğu senaryo, var olan bir denetim için yeni bir şablon oluşturmak yerine tarafından ele alınabilir.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Bu makalede, denetim için yeni bir oluşturma keşfedeceksiniz <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> .

## <a name="when-to-create-a-controltemplate"></a>ControlTemplate ne zaman oluşturulur

Denetimlerin,, ve gibi birçok özelliği <xref:System.Windows.Controls.Border.Background%2A> vardır <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontFamily%2A> . Bu özellikler, denetimin görünümünün farklı yönlerini denetler, ancak bu özellikleri ayarlayarak yapabileceğiniz değişiklikler sınırlıdır. Örneğin, <xref:System.Windows.Controls.Control.Foreground%2A> özelliğini mavi ve italik olarak bir olarak ayarlayabilirsiniz <xref:System.Windows.Controls.Control.FontStyle%2A> <xref:System.Windows.Controls.CheckBox> . Denetimin diğer özelliklerinin yapabilecekleri ayarların ötesinde denetimin görünümünü özelleştirmek istediğinizde, bir oluşturursunuz <xref:System.Windows.Controls.ControlTemplate> .

Çoğu kullanıcı arabiriminde, bir düğme aynı genel görünüme sahiptir: metin içeren bir dikdörtgen. Yuvarlatılmış düğme oluşturmak isterseniz, düğmeden devralan yeni bir denetim oluşturabilir veya düğmenin işlevselliğini yeniden oluşturabilirsiniz. Ayrıca, Yeni Kullanıcı denetimi dairesel görseli sağlar.

Varolan bir denetimin görsel yerleşimini özelleştirerek yeni denetimler oluşturmaktan kaçınabilirsiniz. Yuvarlatılmış bir düğme ile, <xref:System.Windows.Controls.ControlTemplate> istenen görsel düzen ile bir oluşturabilirsiniz.

Öte yandan, yeni işlevlerle, farklı özelliklerde ve yeni ayarlarla bir denetime ihtiyacınız varsa yeni bir oluştur <xref:System.Windows.Controls.UserControl> .

## <a name="prerequisites"></a>Önkoşullar

Yeni bir WPF uygulaması oluşturun ve *MainWindow. xaml* içinde (veya tercih ettiğiniz başka bir pencerede) aşağıdaki özellikleri ayarlayın ** \: :: No-Loc ( <Window> ):::** öğesi:

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

** \: :: No-Loc ( <Window> ):::** öğesinin içeriğini şu XAML 'ye ayarlayın:

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Sonda, *MainWindow. xaml* dosyası şuna benzer şekilde görünmelidir:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Uygulamayı çalıştırırsanız, aşağıdaki gibi görünür:

![İki stilli düğme içeren WPF penceresi](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>ControlTemplate oluşturma

' In en yaygın yolu, bir <xref:System.Windows.Controls.ControlTemplate> xaml dosyasındaki bölümünde kaynak olarak kullanılır `Resources` . Şablonlar kaynaklar olduğundan, tüm kaynaklar için uygulanan aynı kapsam kurallarına uyar. Basitçe, şablonun nerede uygulanabileceğini etkileyen bir şablon bildirdiğiniz yere koyun. Örneğin, şablonu uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, şablon uygulamanızda herhangi bir yerde kullanılabilir. Şablonu bir pencerede tanımlarsanız, şablonu yalnızca o penceredeki denetimler kullanabilir.

İle başlamak için, `Window.Resources` *MainWindow. xaml* dosyanıza bir öğesi ekleyin:

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Yeni bir ** \: :: No-Loc ( <ControlTemplate> ):::** aşağıdaki özellikler kümesiyle oluşturun:

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

Bu denetim şablonu basit olacaktır:

- Denetim için bir kök öğe, <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Shapes.Ellipse>düğmenin yuvarlanmış görünümünü çizmek için bir
- <xref:System.Windows.Controls.ContentPresenter>Kullanıcı tarafından belirtilen düğme içeriğini görüntüleme

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

Yeni bir oluşturduğunuzda <xref:System.Windows.Controls.ControlTemplate> , denetimin görünümünü değiştirmek için yine de ortak özellikleri kullanmak isteyebilirsiniz. [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension) biçimlendirme uzantısı, içindeki bir öğesinin özelliğini <xref:System.Windows.Controls.ControlTemplate> Denetim tarafından tanımlanan ortak bir özelliğe bağlar. Bir [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension)kullandığınızda, denetimdeki özellikleri şablona parametre olarak davranacak şekilde etkinleştirin. Diğer bir deyişle, bir denetimdeki özellik ayarlandığında, bu değer üzerinde [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension) 'e sahip olan öğeye geçirilir.

### <a name="ellipse"></a>Elips

**:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** ** \: :: No-Loc ( <Ellipse> ):::** öğesinin ve özelliklerinin, denetimin <xref:System.Windows.Controls.Control.Foreground> ve özelliklerin ve özelliklerinin bağlandığını unutmayın <xref:System.Windows.Controls.Control.Background> .

### <a name="contentpresenter"></a>ContentPresenter

A [ \: :: No-Loc ( <ContentPresenter> ):::](xref:System.Windows.Controls.ContentPresenter) element de şablona eklenir. Bu şablon bir düğme için tasarlandığından, düğmenin Devralındığı göz önüne alın <xref:System.Windows.Controls.ContentControl> . Düğme, öğenin içeriğini gösterir. Düğmenin içinde düz metin veya başka bir denetim gibi her şeyi de ayarlayabilirsiniz. Aşağıdakilerden her ikisi de geçerli düğmelerdir:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

Yukarıdaki örneklerde, metin ve onay kutusu, [Button. Content](xref:System.Windows.Controls.ContentControl.Content) özelliği olarak ayarlanır. İçerik ne olursa olsun ** \: :: No-Loc ( <ContentPresenter> ):::**, bu, şablonun yaptığı şeydir.

' A gibi bir <xref:System.Windows.Controls.ControlTemplate> türe uygulanırsa, <xref:System.Windows.Controls.ContentControl> `Button` <xref:System.Windows.Controls.ContentPresenter> öğe ağacında için bir aranır. `ContentPresenter`Bulunursa, şablon denetimin özelliğini otomatik olarak <xref:System.Windows.Controls.ContentControl.Content> öğesine bağlar `ContentPresenter` .

## <a name="use-the-template"></a>Şablonu kullanma

Bu makalenin başlangıcında belirtilen düğmeleri bulun.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

İkinci düğmenin <xref:System.Windows.Controls.Control.Template> özelliğini kaynak olarak ayarlayın `roundbutton` :

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Projeyi çalıştırırsanız ve sonuca baktığınızda, düğmenin yuvarlatılmış bir arka plana sahip olduğunu görürsünüz.

![Tek şablon oval düğme içeren WPF penceresi](media/create-apply-template/styled-button.png)

Düğmenin bir daire olmadığını fark etmiş olabilirsiniz ancak eğriltilmiş olduğunu fark etmiş olabilirsiniz. ** \: :: No-Loc ( <Ellipse> ):::** öğesinin çalışma biçimi nedeniyle, her zaman kullanılabilir alanı dolduracak şekilde genişler. Düğme  **:::no-loc text="width":::** ve **:::no-loc text="height":::** özelliklerini aynı değere değiştirerek, daireyi tek tek yapın:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Bir şablon dairesel düğme içeren WPF penceresi](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Tetikleyici ekleme

Şablon uygulanmış bir düğme farklı görünse de, diğer düğmeyle aynı şekilde davranır. Düğmeye basarsanız <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay ateşlenir. Ancak, farenizi düğmenin üzerine getirdiğinizde düğmenin görselleri değişmeyin olduğunu fark etmiş olabilirsiniz. Bu görsel etkileşimler şablon tarafından tanımlanır.

WPF 'in sağladığı dinamik olay ve özellik sistemleri ile, bir değer için belirli bir özelliği izleyebilir ve uygun olduğunda şablonu yeniden oluşturabilirsiniz. Bu örnekte, düğmenin özelliğini izleyeceksiniz <xref:System.Windows.UIElement.IsMouseOver> . Fare denetimin üzerindeyken, ** \: :: No-Loc ( <Ellipse> ):::** yeni bir renkle stili. Bu tetikleyici türü bir *Propertytrigger*olarak bilinir.

Bunun çalışması için, başvurabileceksiniz ** \: :: No-Loc ( <Ellipse> )::** : öğesine bir ad eklemeniz gerekir. **BackgroundElement**adını verin.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Sonra, <xref:System.Windows.Trigger> [ControlTemplate. Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) koleksiyonuna yeni bir ekleyin. Tetikleyici, `IsMouseOver` değeri için olayını izleyen bir işlem görür `true` .

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Daha sonra,:: No-Loc ():::,:: No-Loc ** \: <Trigger> ** ()::: öğesinin **Fill** özelliğini ** \: <Setter> Yeni bir renge** değiştirir. ** \: <Ellipse> **

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Projeyi çalıştırın. Fareyi düğmenin üzerine getirdiğinizde, ** \: :: No-Loc ( <Ellipse> ):::** değişikliklerinin rengini görürsünüz.

![fare, tüm WPF düğmesine taşınıyor ve Fill rengini değiştirme](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>VisualState kullanma

Görsel durumlar, bir denetim tarafından tanımlanır ve tetiklenir. Örneğin, fare denetimin üzerine taşındığında `CommonStates.MouseOver` durum tetiklenir. Denetimin geçerli durumuna bağlı olarak özellik değişikliklerine animasyon uygulayabilirsiniz. Önceki bölümde, düğme ön planını özelliği olduğu zaman değiştirmek için:: ** \: No-Loc ( <PropertyTrigger> ):** :: kullanılmıştır `AliceBlue` `IsMouseOver` `true` . Bunun yerine, bu rengin değişikliğini canlandırarak kesintisiz bir geçiş sağlayan görsel bir durum oluşturun. *Visualstates*hakkında daha fazla bilgi için bkz. [WPF 'de stiller ve şablonlar](../fundamentals/styles-templates-overview.md#visual-states).

:: ** \: No-Loc ( <PropertyTrigger> ):::** ' ı bir hareketli görsel durumuna dönüştürmek için, önce **\<ControlTemplate.Triggers>** öğeyi şablonınızdan kaldırın.

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Ardından,:: No-Loc ( ** \: <Grid> ):::** denetim şablonunun kök dizininde:: No-Loc ( ** \: <VisualStateManager. VisualStateGroups>):** : ** \: No <VisualStateGroup> ** : `CommonStates` . İki durum tanımlayın `Normal` ve `MouseOver` .

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

Bir ** \: :: No-Loc ( <VisualState> ):::** içinde tanımlanan tüm animasyonlar, bu durum tetiklendiğinde uygulanır. Her durum için animasyonlar oluşturun. Animasyonlar ** \: :: No-Loc ( <Storyboard> ):::** öğesinin içine konur. Görsel Taslaklar hakkında daha fazla bilgi için bkz. [görsel taslakları genel bakış](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview).

- Normal

  Bu durum, elips dolgusunun animasyonunu, denetimin rengine geri yüklemeyi hareketlendirir `Background` .

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- Gelme olayından

  Bu durum, elips `Background` rengini yeni bir renkle hareketlendirir: `Yellow` .

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

** \: :: No-Loc ( <ControlTemplate> ):::** şimdi aşağıdaki gibi görünmelidir.

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Projeyi çalıştırın. Fareyi düğmenin üzerine getirdiğinizde, ** \: :: No-Loc ( <Ellipse> ):** :: hareketlendirir rengini görürsünüz.

![fare, tüm WPF düğmesine taşınıyor ve Fill rengini değiştirme](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Sonraki adımlar

- [WPF içindeki bir denetim için stil oluşturma](../fundamentals/styles-templates-create-apply-style.md)
- [WPF 'deki stiller ve şablonlar](../fundamentals/styles-templates-overview.md)
- [XAML kaynaklarına genel bakış](../fundamentals/xaml-resources-define.md)
