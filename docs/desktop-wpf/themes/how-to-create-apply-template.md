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
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="cef45-103">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="cef45-103">Create a template for a control</span></span>

<span data-ttu-id="cef45-104">Windows Sunu Temeli (WPF) ile varolan bir denetimin görsel yapısını ve davranışını kendi yeniden kullanılabilir şablonunuzla özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="cef45-105">Şablonlar genel olarak uygulamanıza, pencerelere ve sayfalara veya doğrudan denetimlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cef45-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="cef45-106">Yeni bir denetim oluşturmanızı gerektiren çoğu senaryo, varolan bir denetim için yeni bir şablon oluşturmak yerine kapsanabilir.</span><span class="sxs-lookup"><span data-stu-id="cef45-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="cef45-107">Bu makalede, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> denetim için yeni bir oluşturma yı keşfedeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="cef45-108">Denetim Şablonu ne zaman oluşturulacak?</span><span class="sxs-lookup"><span data-stu-id="cef45-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="cef45-109">Denetimlerin <xref:System.Windows.Controls.Border.Background%2A>, , <xref:System.Windows.Controls.Control.Foreground%2A>ve <xref:System.Windows.Controls.Control.FontFamily%2A>.</span><span class="sxs-lookup"><span data-stu-id="cef45-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="cef45-110">Bu özellikler denetimin görünümünün farklı yönlerini denetler, ancak bu özellikleri ayarlayarak yapabileceğiniz değişiklikler sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="cef45-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="cef45-111">Örneğin, <xref:System.Windows.Controls.Control.Foreground%2A> özelliği maviye ve <xref:System.Windows.Controls.Control.FontStyle%2A> italik bir <xref:System.Windows.Controls.CheckBox>'de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="cef45-112">Denetimin görünümünü, denetimdeki diğer özelliklerin yapabileceklerinin ötesinde özelleştirmek istediğinizde, <xref:System.Windows.Controls.ControlTemplate>bir .</span><span class="sxs-lookup"><span data-stu-id="cef45-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="cef45-113">Çoğu kullanıcı arabiriminde, bir düğme aynı genel görünüme sahiptir: bazı metin içeren bir dikdörtgen.</span><span class="sxs-lookup"><span data-stu-id="cef45-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="cef45-114">Yuvarlatılmış bir düğme oluşturmak istiyorsanız, düğmeden devralan veya düğmenin işlevselliğini yeniden oluşturan yeni bir denetim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="cef45-115">Buna ek olarak, yeni kullanıcı denetimi dairesel görsel sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="cef45-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="cef45-116">Varolan bir denetimin görsel düzenini özelleştirerek yeni denetimler oluşturmaktan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="cef45-117">Yuvarlatılmış bir düğme yle, istenilen görsel düzene sahip bir düğme <xref:System.Windows.Controls.ControlTemplate> oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="cef45-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="cef45-118">Diğer taraftan, yeni işlevsellik, farklı özellikler ve yeni ayarlarla bir denetime <xref:System.Windows.Controls.UserControl>ihtiyacınız varsa, yeni bir .</span><span class="sxs-lookup"><span data-stu-id="cef45-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cef45-119">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cef45-119">Prerequisites</span></span>

<span data-ttu-id="cef45-120">Yeni bir WPF uygulaması oluşturun ve *MainWindow.xaml'da* (veya seçtiğiniz başka bir pencerede) \*\* \<Pencere>\*\* öğesindeki aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cef45-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

<span data-ttu-id="cef45-121">\*\* \<Pencere>\*\* öğesinin içeriğini aşağıdaki XAML'ye ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cef45-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="cef45-122">Sonunda, *MainWindow.xaml* dosyası aşağıdakilere benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="cef45-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="cef45-123">Uygulamayı çalıştırarsanız, aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="cef45-123">If you run the application, it looks like the following:</span></span>

![İki unstyled düğmeleri ile WPF penceresi](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="cef45-125">Denetim Şablonu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cef45-125">Create a ControlTemplate</span></span>

<span data-ttu-id="cef45-126">A'yı <xref:System.Windows.Controls.ControlTemplate> bildirmenin en yaygın yolu, `Resources` XAML dosyasındaki bölümde kaynak olarak dır.</span><span class="sxs-lookup"><span data-stu-id="cef45-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="cef45-127">Şablonlar kaynak olduğundan, tüm kaynaklar için geçerli olan aynı kapsam kurallarına uyarlar.</span><span class="sxs-lookup"><span data-stu-id="cef45-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="cef45-128">Basitçe söylemek gerekirse, şablonu beyan ettiğiniz yer şablonun uygulanabileceği yeri etkiler.</span><span class="sxs-lookup"><span data-stu-id="cef45-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="cef45-129">Örneğin, şablonu uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, şablon uygulamanızın herhangi bir yerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cef45-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="cef45-130">Şablonu bir pencerede tanımlarsanız, şablonu yalnızca bu penceredeki denetimler kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="cef45-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="cef45-131">Başlangıç olarak, `Window.Resources` *MainWindow.xaml* dosyanıza bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cef45-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="cef45-132">Aşağıdaki özellikleri \*\* \<\*\* kümesi ile yeni bir Denetim Şablonu>oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cef45-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="cef45-133">**x:Anahtar**</span><span class="sxs-lookup"><span data-stu-id="cef45-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="cef45-134">Bu denetim şablonu basit olacaktır:</span><span class="sxs-lookup"><span data-stu-id="cef45-134">This control template will be simple:</span></span>

- <span data-ttu-id="cef45-135">kontrol için bir kök öğesi, bir<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="cef45-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="cef45-136">düğmenin yuvarlak görünümünü çizmek için bir <xref:System.Windows.Shapes.Ellipse></span><span class="sxs-lookup"><span data-stu-id="cef45-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="cef45-137">a <xref:System.Windows.Controls.ContentPresenter> kullanıcı tarafından belirtilen düğme içeriğini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="cef45-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="cef45-138">Templatebinding</span><span class="sxs-lookup"><span data-stu-id="cef45-138">TemplateBinding</span></span>

<span data-ttu-id="cef45-139">Yeni <xref:System.Windows.Controls.ControlTemplate>bir , denetimin görünümünü değiştirmek için ortak özellikleri kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="cef45-140">[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) biçimlendirme uzantısı, denetim tarafından tanımlanan bir kamu <xref:System.Windows.Controls.ControlTemplate> malında bulunan bir öğenin özelliğini bağlar.</span><span class="sxs-lookup"><span data-stu-id="cef45-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="cef45-141">[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)kullandığınızda, denetimdeki özelliklerin şablona parametre olarak hareket etmesini sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="cef45-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="cef45-142">Diğer bir şey, denetimüzerindeki bir özellik ayarlandığında, bu değer üzerinde [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) olan öğeye aktarılır.</span><span class="sxs-lookup"><span data-stu-id="cef45-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="cef45-143">Elips</span><span class="sxs-lookup"><span data-stu-id="cef45-143">Ellipse</span></span>

<span data-ttu-id="cef45-144">**:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> **Elips>öğesinin ve özelliklerinin denetimin ve özelliklerine bağlı \<** olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cef45-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="cef45-145">Contentpresenter</span><span class="sxs-lookup"><span data-stu-id="cef45-145">ContentPresenter</span></span>

<span data-ttu-id="cef45-146">Şablona ContentPresenter>öğesi de eklenir. [ \<](xref:System.Windows.Controls.ContentPresenter)</span><span class="sxs-lookup"><span data-stu-id="cef45-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="cef45-147">Bu şablon bir düğme için tasarlandığından, düğmenin <xref:System.Windows.Controls.ContentControl>'den devraldığı göz önünde bulundurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cef45-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="cef45-148">Düğme öğenin içeriğini sunar.</span><span class="sxs-lookup"><span data-stu-id="cef45-148">The button presents the content of the element.</span></span> <span data-ttu-id="cef45-149">Düz metin veya başka bir denetim gibi düğmenin içindeki her şeyi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="cef45-150">Aşağıdakilerin her ikisi de geçerli düğmelerdir:</span><span class="sxs-lookup"><span data-stu-id="cef45-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="cef45-151">Önceki örneklerin her ikisinde de metin ve onay kutusu [Button.Content](xref:System.Windows.Controls.ContentControl.Content) özelliği olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cef45-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="cef45-152">İçerik olarak ayarlanan ne olursa \*\* \< \*\*olsun, şablonun yaptığı bir ContentPresenter>aracılığıyla sunulabilir.</span><span class="sxs-lookup"><span data-stu-id="cef45-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="cef45-153">A, a `Button`gibi <xref:System.Windows.Controls.ContentControl> bir türe uygulanırsa, <xref:System.Windows.Controls.ContentPresenter> öğe ağacında aranır. <xref:System.Windows.Controls.ControlTemplate></span><span class="sxs-lookup"><span data-stu-id="cef45-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="cef45-154">`ContentPresenter` Bulunursa, şablon denetimin <xref:System.Windows.Controls.ContentControl.Content> özelliğini otomatik olarak `ContentPresenter`.</span><span class="sxs-lookup"><span data-stu-id="cef45-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="cef45-155">Şablonu kullanma</span><span class="sxs-lookup"><span data-stu-id="cef45-155">Use the template</span></span>

<span data-ttu-id="cef45-156">Bu makalenin başında bildirilen düğmeleri bulun.</span><span class="sxs-lookup"><span data-stu-id="cef45-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="cef45-157">İkinci düğmenin <xref:System.Windows.Controls.Control.Template> özelliğini kaynağa `roundbutton` ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cef45-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="cef45-158">Projeyi çalıştırıp sonuca bakarsanız, düğmenin yuvarlak bir arka plana sahip olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="cef45-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Bir şablon oval düğmeile WPF penceresi](media/create-apply-template/styled-button.png)

<span data-ttu-id="cef45-160">Düğmenin bir daire olmadığını, eğri olduğunu fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="cef45-161">Elips>öğesinin çalışma şekli nedeniyle, her zaman kullanılabilir alanı doldurmak için genişler. \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="cef45-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="cef45-162">Düğmenin **:::no-loc text="width":::** ve **:::no-loc text="height":::** özelliklerinin aynı değere değiştirilmesiyle daireyi tek tipleştirin:</span><span class="sxs-lookup"><span data-stu-id="cef45-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Tek şablon dairesel düğmeli WPF penceresi](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="cef45-164">Tetikleyici Ekleme</span><span class="sxs-lookup"><span data-stu-id="cef45-164">Add a Trigger</span></span>

<span data-ttu-id="cef45-165">Uygulamalı şabloniçeren bir düğme farklı görünse de, diğer düğmelerle aynı şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="cef45-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="cef45-166">Düğmeye basarsanız, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay ateşler.</span><span class="sxs-lookup"><span data-stu-id="cef45-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="cef45-167">Ancak, farenizi düğmenin üzerinde hareket ettirdiğinizde düğmenin görsellerinin değişmediğini fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="cef45-168">Bu görsel etkileşimlerin tümü şablon tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cef45-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="cef45-169">WPF'nin sağladığı dinamik olay ve özellik sistemleriyle, belirli bir özelliği bir değer için izleyebilir ve uygun olduğunda şablonu yeniden şekillendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="cef45-170">Bu örnekte, düğmenin <xref:System.Windows.UIElement.IsMouseOver> özelliğini izlersiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="cef45-171">Fare denetimin üzerindeyken, \*\* \<Elips>\*\* yeni bir renkle şekillendirin.</span><span class="sxs-lookup"><span data-stu-id="cef45-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="cef45-172">Bu tür tetikleyici *propertytrigger*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="cef45-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="cef45-173">Bunun işe yaraması için \*\* \<Elips>\*\* başvuruda bulunabileceğiniz bir ad eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cef45-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="cef45-174">**Ona backgroundElement**adını verin.</span><span class="sxs-lookup"><span data-stu-id="cef45-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="cef45-175">Ardından, <xref:System.Windows.Trigger> [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) koleksiyonuna yeni bir ekleme.</span><span class="sxs-lookup"><span data-stu-id="cef45-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="cef45-176">Tetikleyici değeri `true`için `IsMouseOver` olay izleyecek.</span><span class="sxs-lookup"><span data-stu-id="cef45-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="cef45-177">Ardından, \*\* \<Elips>\*\* **Dolgu** özelliğini yeni bir renge değiştiren \*\* \<Tetikleyici>\*\* bir \*\* \<Ayarlayıcı>\*\* ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cef45-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="cef45-178">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cef45-178">Run the project.</span></span> <span data-ttu-id="cef45-179">Fareyi düğmenin üzerinde hareket ettirdiğinizde \*\* \<Elips'in\*\* renginin>değişir.</span><span class="sxs-lookup"><span data-stu-id="cef45-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![fare dolgu rengini değiştirmek için WPF tuşu üzerinde hareket eder](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="cef45-181">VisualState kullanma</span><span class="sxs-lookup"><span data-stu-id="cef45-181">Use a VisualState</span></span>

<span data-ttu-id="cef45-182">Görsel durumlar bir denetim tarafından tanımlanır ve tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cef45-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="cef45-183">Örneğin, fare denetimin üstüne taşındığında, `CommonStates.MouseOver` durum tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cef45-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="cef45-184">Özellik değişikliklerini denetimin geçerli durumuna göre canlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef45-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="cef45-185">Önceki bölümde, bir \*\* \<PropertyTrigger>\*\* özelliği ne zaman `IsMouseOver` düğmenin ön planda `true`değiştirmek için `AliceBlue` kullanılmıştır .</span><span class="sxs-lookup"><span data-stu-id="cef45-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="cef45-186">Bunun yerine, düzgün bir geçiş sağlayarak bu rengin değişimini animasyona rendiren görsel bir durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cef45-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="cef45-187">*VisualStates*hakkında daha fazla bilgi için [WPF'deki Stiller ve şablonlara](../fundamentals/styles-templates-overview.md#visual-states)bakın.</span><span class="sxs-lookup"><span data-stu-id="cef45-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="cef45-188">PropertyTrigger>animasyonlu görsel duruma dönüştürmek için önce \*\* \<ControlTemplate.Triggers>\*\* öğesini şablonunuzdan kaldırın. \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="cef45-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="cef45-189">Ardından, denetim şablonunun \*\* \<Grid>\*\* kökünde \*\* \<VisualStateManager.VisualStateGroups>\*\* öğesini \*\* \<visualStateGroup>\*\* ile `CommonStates`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cef45-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="cef45-190">İki durum `Normal` tanımlayın ve `MouseOver`.</span><span class="sxs-lookup"><span data-stu-id="cef45-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="cef45-191">VisualState>tanımlanan animasyonlar, bu durum tetiklendiğinde uygulanır. \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="cef45-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="cef45-192">Her durum için animasyonlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cef45-192">Create animations for each state.</span></span> <span data-ttu-id="cef45-193">Animasyonlar bir \*\* \<Storyboard>\*\* öğesinin içine konur.</span><span class="sxs-lookup"><span data-stu-id="cef45-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="cef45-194">Storyboards hakkında daha fazla bilgi için [Storyboards Genel Bakış'a](../../framework/wpf/graphics-multimedia/storyboards-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="cef45-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="cef45-195">Normal</span><span class="sxs-lookup"><span data-stu-id="cef45-195">Normal</span></span>

  <span data-ttu-id="cef45-196">Bu durum elips dolgusu animasyonlar, kontrol `Background` renginde geri.</span><span class="sxs-lookup"><span data-stu-id="cef45-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="cef45-197">Mouseover</span><span class="sxs-lookup"><span data-stu-id="cef45-197">MouseOver</span></span>

  <span data-ttu-id="cef45-198">Bu durum, elips `Background` rengini yeni bir renge animasyona salar: `Yellow`.</span><span class="sxs-lookup"><span data-stu-id="cef45-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="cef45-199">DenetimŞablonu>artık aşağıdaki gibi görünmelidir. \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="cef45-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="cef45-200">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cef45-200">Run the project.</span></span> <span data-ttu-id="cef45-201">Fareyi düğmenin üzerinde hareket ettirdiğinizde, \*\* \<Elips'in\*\* renginin animasyon>dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cef45-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![fare dolgu rengini değiştirmek için WPF tuşu üzerinde hareket eder](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="cef45-203">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cef45-203">Next steps</span></span>

- [<span data-ttu-id="cef45-204">WPF'de denetim için stil oluşturma</span><span class="sxs-lookup"><span data-stu-id="cef45-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="cef45-205">WPF'deki stiller ve şablonlar</span><span class="sxs-lookup"><span data-stu-id="cef45-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="cef45-206">XAML Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cef45-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
