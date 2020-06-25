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
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325724"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="43f4b-103">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="43f4b-103">Create a template for a control</span></span>

<span data-ttu-id="43f4b-104">Windows Presentation Foundation (WPF) ile, var olan bir denetimin görsel yapısını ve davranışını kendi yeniden kullanılabilir şablonunuz ile özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="43f4b-105">Şablonlar uygulamanıza, Windows ve sayfalarınıza Global olarak veya doğrudan denetimlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="43f4b-106">Yeni bir denetim oluşturmanızı gerektiren çoğu senaryo, var olan bir denetim için yeni bir şablon oluşturmak yerine tarafından ele alınabilir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="43f4b-107">Bu makalede, denetim için yeni bir oluşturma keşfedeceksiniz <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="43f4b-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="43f4b-108">ControlTemplate ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="43f4b-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="43f4b-109">Denetimlerin,, ve gibi birçok özelliği <xref:System.Windows.Controls.Border.Background%2A> vardır <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontFamily%2A> .</span><span class="sxs-lookup"><span data-stu-id="43f4b-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="43f4b-110">Bu özellikler, denetimin görünümünün farklı yönlerini denetler, ancak bu özellikleri ayarlayarak yapabileceğiniz değişiklikler sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="43f4b-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="43f4b-111">Örneğin, <xref:System.Windows.Controls.Control.Foreground%2A> özelliğini mavi ve italik olarak bir olarak ayarlayabilirsiniz <xref:System.Windows.Controls.Control.FontStyle%2A> <xref:System.Windows.Controls.CheckBox> .</span><span class="sxs-lookup"><span data-stu-id="43f4b-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="43f4b-112">Denetimin diğer özelliklerinin yapabilecekleri ayarların ötesinde denetimin görünümünü özelleştirmek istediğinizde, bir oluşturursunuz <xref:System.Windows.Controls.ControlTemplate> .</span><span class="sxs-lookup"><span data-stu-id="43f4b-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="43f4b-113">Çoğu kullanıcı arabiriminde, bir düğme aynı genel görünüme sahiptir: metin içeren bir dikdörtgen.</span><span class="sxs-lookup"><span data-stu-id="43f4b-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="43f4b-114">Yuvarlatılmış düğme oluşturmak isterseniz, düğmeden devralan yeni bir denetim oluşturabilir veya düğmenin işlevselliğini yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="43f4b-115">Ayrıca, Yeni Kullanıcı denetimi dairesel görseli sağlar.</span><span class="sxs-lookup"><span data-stu-id="43f4b-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="43f4b-116">Varolan bir denetimin görsel yerleşimini özelleştirerek yeni denetimler oluşturmaktan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="43f4b-117">Yuvarlatılmış bir düğme ile, <xref:System.Windows.Controls.ControlTemplate> istenen görsel düzen ile bir oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="43f4b-118">Öte yandan, yeni işlevlerle, farklı özelliklerde ve yeni ayarlarla bir denetime ihtiyacınız varsa yeni bir oluştur <xref:System.Windows.Controls.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="43f4b-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43f4b-119">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="43f4b-119">Prerequisites</span></span>

<span data-ttu-id="43f4b-120">Yeni bir WPF uygulaması oluşturun ve *MainWindow. xaml* içinde (veya tercih ettiğiniz başka bir pencerede) öğesi için aşağıdaki özellikleri ayarlayın **\<Window>** :</span><span class="sxs-lookup"><span data-stu-id="43f4b-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

<span data-ttu-id="43f4b-121">**\<Window>** Öğesinin içeriğini AŞAĞıDAKI xaml olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="43f4b-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="43f4b-122">Sonda, *MainWindow. xaml* dosyası şuna benzer şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="43f4b-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="43f4b-123">Uygulamayı çalıştırırsanız, aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="43f4b-123">If you run the application, it looks like the following:</span></span>

![İki stilli düğme içeren WPF penceresi](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="43f4b-125">ControlTemplate oluşturma</span><span class="sxs-lookup"><span data-stu-id="43f4b-125">Create a ControlTemplate</span></span>

<span data-ttu-id="43f4b-126">' In en yaygın yolu, bir <xref:System.Windows.Controls.ControlTemplate> xaml dosyasındaki bölümünde kaynak olarak kullanılır `Resources` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="43f4b-127">Şablonlar kaynaklar olduğundan, tüm kaynaklar için uygulanan aynı kapsam kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="43f4b-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="43f4b-128">Basitçe, şablonun nerede uygulanabileceğini etkileyen bir şablon bildirdiğiniz yere koyun.</span><span class="sxs-lookup"><span data-stu-id="43f4b-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="43f4b-129">Örneğin, şablonu uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, şablon uygulamanızda herhangi bir yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="43f4b-130">Şablonu bir pencerede tanımlarsanız, şablonu yalnızca o penceredeki denetimler kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="43f4b-131">İle başlamak için, `Window.Resources` *MainWindow. xaml* dosyanıza bir öğesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43f4b-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="43f4b-132">**\<ControlTemplate>** Aşağıdaki özellikler kümesiyle yeni bir oluştur:</span><span class="sxs-lookup"><span data-stu-id="43f4b-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="43f4b-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="43f4b-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="43f4b-134">Bu denetim şablonu basit olacaktır:</span><span class="sxs-lookup"><span data-stu-id="43f4b-134">This control template will be simple:</span></span>

- <span data-ttu-id="43f4b-135">Denetim için bir kök öğe,<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="43f4b-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="43f4b-136"><xref:System.Windows.Shapes.Ellipse>düğmenin yuvarlanmış görünümünü çizmek için bir</span><span class="sxs-lookup"><span data-stu-id="43f4b-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="43f4b-137"><xref:System.Windows.Controls.ContentPresenter>Kullanıcı tarafından belirtilen düğme içeriğini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="43f4b-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="43f4b-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="43f4b-138">TemplateBinding</span></span>

<span data-ttu-id="43f4b-139">Yeni bir oluşturduğunuzda <xref:System.Windows.Controls.ControlTemplate> , denetimin görünümünü değiştirmek için yine de ortak özellikleri kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="43f4b-140">[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) biçimlendirme uzantısı, içindeki bir öğesinin özelliğini <xref:System.Windows.Controls.ControlTemplate> Denetim tarafından tanımlanan ortak bir özelliğe bağlar.</span><span class="sxs-lookup"><span data-stu-id="43f4b-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="43f4b-141">Bir [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)kullandığınızda, denetimdeki özellikleri şablona parametre olarak davranacak şekilde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="43f4b-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="43f4b-142">Diğer bir deyişle, bir denetimdeki özellik ayarlandığında, bu değer üzerinde [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 'e sahip olan öğeye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="43f4b-143">Elips</span><span class="sxs-lookup"><span data-stu-id="43f4b-143">Ellipse</span></span>

<span data-ttu-id="43f4b-144">**:::no-loc text="Fill":::** Öğesinin ve özelliklerinin, **:::no-loc text="Stroke":::** **\<Ellipse>** denetimin <xref:System.Windows.Controls.Control.Foreground> ve <xref:System.Windows.Controls.Control.Background> özelliklerin özelliklerine bağlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="43f4b-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="43f4b-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="43f4b-145">ContentPresenter</span></span>

<span data-ttu-id="43f4b-146">[\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter)Şablona de bir öğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="43f4b-147">Bu şablon bir düğme için tasarlandığından, düğmenin Devralındığı göz önüne alın <xref:System.Windows.Controls.ContentControl> .</span><span class="sxs-lookup"><span data-stu-id="43f4b-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="43f4b-148">Düğme, öğenin içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-148">The button presents the content of the element.</span></span> <span data-ttu-id="43f4b-149">Düğmenin içinde düz metin veya başka bir denetim gibi her şeyi de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="43f4b-150">Aşağıdakilerden her ikisi de geçerli düğmelerdir:</span><span class="sxs-lookup"><span data-stu-id="43f4b-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="43f4b-151">Yukarıdaki örneklerde, metin ve onay kutusu, [Button. Content](xref:System.Windows.Controls.ContentControl.Content) özelliği olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="43f4b-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="43f4b-152">İçerik, şablon tarafından ne kadar olursa olsun, tarafından sunulur **\<ContentPresenter>** .</span><span class="sxs-lookup"><span data-stu-id="43f4b-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="43f4b-153">' A gibi bir <xref:System.Windows.Controls.ControlTemplate> türe uygulanırsa, <xref:System.Windows.Controls.ContentControl> `Button` <xref:System.Windows.Controls.ContentPresenter> öğe ağacında için bir aranır.</span><span class="sxs-lookup"><span data-stu-id="43f4b-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="43f4b-154">`ContentPresenter`Bulunursa, şablon denetimin özelliğini otomatik olarak <xref:System.Windows.Controls.ContentControl.Content> öğesine bağlar `ContentPresenter` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="43f4b-155">Şablonu kullanma</span><span class="sxs-lookup"><span data-stu-id="43f4b-155">Use the template</span></span>

<span data-ttu-id="43f4b-156">Bu makalenin başlangıcında belirtilen düğmeleri bulun.</span><span class="sxs-lookup"><span data-stu-id="43f4b-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="43f4b-157">İkinci düğmenin <xref:System.Windows.Controls.Control.Template> özelliğini kaynak olarak ayarlayın `roundbutton` :</span><span class="sxs-lookup"><span data-stu-id="43f4b-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="43f4b-158">Projeyi çalıştırırsanız ve sonuca baktığınızda, düğmenin yuvarlatılmış bir arka plana sahip olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Tek şablon oval düğme içeren WPF penceresi](media/create-apply-template/styled-button.png)

<span data-ttu-id="43f4b-160">Düğmenin bir daire olmadığını fark etmiş olabilirsiniz ancak eğriltilmiş olduğunu fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="43f4b-161">**\<Ellipse>** Öğenin çalışma biçimi nedeniyle, her zaman kullanılabilir alanı dolduracak şekilde genişler.</span><span class="sxs-lookup"><span data-stu-id="43f4b-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="43f4b-162">Düğme **:::no-loc text="width":::** ve **:::no-loc text="height":::** özelliklerini aynı değere değiştirerek, daireyi tek tek yapın:</span><span class="sxs-lookup"><span data-stu-id="43f4b-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Bir şablon dairesel düğme içeren WPF penceresi](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="43f4b-164">Tetikleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="43f4b-164">Add a Trigger</span></span>

<span data-ttu-id="43f4b-165">Şablon uygulanmış bir düğme farklı görünse de, diğer düğmeyle aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="43f4b-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="43f4b-166">Düğmeye basarsanız <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="43f4b-167">Ancak, farenizi düğmenin üzerine getirdiğinizde düğmenin görselleri değişmeyin olduğunu fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="43f4b-168">Bu görsel etkileşimler şablon tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="43f4b-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="43f4b-169">WPF 'in sağladığı dinamik olay ve özellik sistemleri ile, bir değer için belirli bir özelliği izleyebilir ve uygun olduğunda şablonu yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="43f4b-170">Bu örnekte, düğmenin özelliğini izleyeceksiniz <xref:System.Windows.UIElement.IsMouseOver> .</span><span class="sxs-lookup"><span data-stu-id="43f4b-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="43f4b-171">Fare denetimin üzerindeyken, stili **\<Ellipse>** Yeni bir renkle stillidir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="43f4b-172">Bu tetikleyici türü bir *Propertytrigger*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="43f4b-173">Bunun çalışması için, başvurabileceksiniz öğesine bir ad eklemeniz gerekir **\<Ellipse>** .</span><span class="sxs-lookup"><span data-stu-id="43f4b-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="43f4b-174">**BackgroundElement**adını verin.</span><span class="sxs-lookup"><span data-stu-id="43f4b-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="43f4b-175">Sonra, <xref:System.Windows.Trigger> [ControlTemplate. Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) koleksiyonuna yeni bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="43f4b-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="43f4b-176">Tetikleyici, `IsMouseOver` değeri için olayını izleyen bir işlem görür `true` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="43f4b-177">Sonra, **\<Setter>** **\<Trigger>** öğesinin **Fill** özelliğini yeni bir renge değiştiren öğesine bir ekleyin **\<Ellipse>** .</span><span class="sxs-lookup"><span data-stu-id="43f4b-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="43f4b-178">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43f4b-178">Run the project.</span></span> <span data-ttu-id="43f4b-179">Fareyi düğmenin üzerine getirdiğinizde, değişikliklerin rengini görürsünüz **\<Ellipse>** .</span><span class="sxs-lookup"><span data-stu-id="43f4b-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![fare, tüm WPF düğmesine taşınıyor ve Fill rengini değiştirme](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="43f4b-181">VisualState kullanma</span><span class="sxs-lookup"><span data-stu-id="43f4b-181">Use a VisualState</span></span>

<span data-ttu-id="43f4b-182">Görsel durumlar, bir denetim tarafından tanımlanır ve tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="43f4b-183">Örneğin, fare denetimin üzerine taşındığında `CommonStates.MouseOver` durum tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="43f4b-184">Denetimin geçerli durumuna bağlı olarak özellik değişikliklerine animasyon uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f4b-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="43f4b-185">Önceki bölümde, **\<PropertyTrigger>** düğme ön planını `AliceBlue` özelliği olduğu zaman değiştirmek için kullanılmıştır `IsMouseOver` `true` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="43f4b-186">Bunun yerine, bu rengin değişikliğini canlandırarak kesintisiz bir geçiş sağlayan görsel bir durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43f4b-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="43f4b-187">*Visualstates*hakkında daha fazla bilgi için bkz. [WPF 'de stiller ve şablonlar](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="43f4b-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="43f4b-188">**\<PropertyTrigger>**' I bir hareketli görsel durumuna dönüştürmek için, önce **\<ControlTemplate.Triggers>** öğeyi şablonınızdan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="43f4b-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="43f4b-189">Sonra, **\<Grid>** denetim şablonunun kökünde **\<VisualStateManager.VisualStateGroups>** öğesi için öğesine ekleyin **\<VisualStateGroup>** `CommonStates` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="43f4b-190">İki durum tanımlayın `Normal` ve `MouseOver` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="43f4b-191">İçinde tanımlanan tüm animasyonlar, **\<VisualState>** Bu durum tetiklendiğinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="43f4b-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="43f4b-192">Her durum için animasyonlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43f4b-192">Create animations for each state.</span></span> <span data-ttu-id="43f4b-193">Animasyonlar, bir öğesinin içine konur **\<Storyboard>** .</span><span class="sxs-lookup"><span data-stu-id="43f4b-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="43f4b-194">Görsel Taslaklar hakkında daha fazla bilgi için bkz. [görsel taslakları genel bakış](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="43f4b-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="43f4b-195">Normal</span><span class="sxs-lookup"><span data-stu-id="43f4b-195">Normal</span></span>

  <span data-ttu-id="43f4b-196">Bu durum, elips dolgusunun animasyonunu, denetimin rengine geri yüklemeyi hareketlendirir `Background` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="43f4b-197">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="43f4b-197">MouseOver</span></span>

  <span data-ttu-id="43f4b-198">Bu durum, elips `Background` rengini yeni bir renkle hareketlendirir: `Yellow` .</span><span class="sxs-lookup"><span data-stu-id="43f4b-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="43f4b-199">**\<ControlTemplate>** Şimdi aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="43f4b-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="43f4b-200">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43f4b-200">Run the project.</span></span> <span data-ttu-id="43f4b-201">Fareyi düğmenin üzerine getirdiğinizde, hareketçın rengi olan ' ın rengini görürsünüz **\<Ellipse>** .</span><span class="sxs-lookup"><span data-stu-id="43f4b-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![fare, tüm WPF düğmesine taşınıyor ve Fill rengini değiştirme](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="43f4b-203">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="43f4b-203">Next steps</span></span>

- [<span data-ttu-id="43f4b-204">WPF içindeki bir denetim için stil oluşturma</span><span class="sxs-lookup"><span data-stu-id="43f4b-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="43f4b-205">WPF 'deki stiller ve şablonlar</span><span class="sxs-lookup"><span data-stu-id="43f4b-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="43f4b-206">XAML kaynaklarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="43f4b-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
