---
title: Özellik Kılavuzu genişletilebilirliği-WF örneği
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: 130d8702795bccf0d5f28b5c0940bd7c25be3556
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715599"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="37984-102">Özellik Kılavuzu genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="37984-102">Property grid extensibility</span></span>

<span data-ttu-id="37984-103">Geliştirici, tasarımcı içinde belirli bir etkinlik seçildiğinde görüntülenen özellik kılavuzunu özelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="37984-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="37984-104">Bu, zengin bir Düzenle deneyimi oluşturmak için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="37984-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="37984-105">Bu örnek, bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="37984-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="37984-106">Gösterir</span><span class="sxs-lookup"><span data-stu-id="37984-106">Demonstrates</span></span>

<span data-ttu-id="37984-107">Workflow Designer Özellik Kılavuzu genişletilebilirliği.</span><span class="sxs-lookup"><span data-stu-id="37984-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37984-108">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="37984-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37984-109">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="37984-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="37984-110">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="37984-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37984-111">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="37984-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="37984-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="37984-112">Discussion</span></span>

<span data-ttu-id="37984-113">Özellik kılavuzunu genişletmek için, bir geliştiricinin bir özellik Kılavuzu düzenleyicisinin satır içi görünümünü özelleştirme seçenekleri vardır veya daha gelişmiş bir düzenleme yüzeyi için görüntülenen bir iletişim kutusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="37984-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="37984-114">Bu örnekte gösterilen iki farklı düzenleyici vardır; satır içi düzenleyici ve iletişim kutusu Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="37984-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="37984-115">Satır içi düzenleyici</span><span class="sxs-lookup"><span data-stu-id="37984-115">Inline editor</span></span>

<span data-ttu-id="37984-116">Satır içi düzenleyici örneği şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="37984-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="37984-117"><xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>türetilen bir tür oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37984-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="37984-118">Oluşturucuda <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değeri bir Windows Presentation Foundation (WPF) veri şablonuyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="37984-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="37984-119">Bu bir XAML şablonuna bağlanabilir, ancak bu örnekte, veri bağlamayı başlatmak için kod kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37984-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="37984-120">Veri şablonunda, özellik kılavuzunda işlenen öğenin <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> bir veri bağlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="37984-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="37984-121">Aşağıdaki kodda (CustomInlineEditor.cs öğesinden) bu bağlamın daha sonra `Value` özelliğine bağladığına göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="37984-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- <span data-ttu-id="37984-122">Etkinlik ve tasarımcı aynı derlemede olduğundan, etkinlik Tasarımcısı özniteliklerinin kaydı etkinliğin kendisinin statik oluşturucusunda, SimpleCodeActivity.cs ' den aşağıdaki örnekte gösterildiği gibi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="37984-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="37984-123">İletişim kutusu düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="37984-123">Dialog editor</span></span>

<span data-ttu-id="37984-124">İletişim kutusu Düzenleyicisi örneği şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="37984-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="37984-125"><xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>türetilen bir tür oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37984-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="37984-126">Oluşturucuda <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değerini bir WPF veri şablonuyla ayarlar.</span><span class="sxs-lookup"><span data-stu-id="37984-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a WPF data template.</span></span> <span data-ttu-id="37984-127">Bu, XAML 'de oluşturulabilir, ancak bu örnekte kodda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="37984-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="37984-128">Veri şablonunda, özellik kılavuzunda işlenen öğenin <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> bir veri bağlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="37984-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="37984-129">Aşağıdaki kodda, bu daha sonra `Value` özelliğine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="37984-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="37984-130">Ayrıca, FilePickerEditor.cs içinde iletişim başlatan düğmeyi sağlamak için bir <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> de vardır.</span><span class="sxs-lookup"><span data-stu-id="37984-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. <span data-ttu-id="37984-131">İletişim kutusunun görüntülenmesini işlemek için tasarımcı türündeki <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="37984-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="37984-132">Bu örnekte, temel bir <xref:System.Windows.Forms.FileDialog> gösterilir.</span><span class="sxs-lookup"><span data-stu-id="37984-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="37984-133">Etkinlik ve tasarımcı aynı derlemede olduğundan, etkinlik Tasarımcısı özniteliklerinin kaydı etkinliğin kendisinin statik oluşturucusunda, SimpleCodeActivity.cs ' den aşağıdaki örnekte gösterildiği gibi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="37984-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37984-134">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="37984-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="37984-135">Çözümü derleyin ve ardından Workflow1. xaml ' yi açın.</span><span class="sxs-lookup"><span data-stu-id="37984-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="37984-136">Araç kutusundan bir **SimpleCodeActivity** 'yi tasarımcı tuvaline sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="37984-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="37984-137">**SimpleCodeActivity** ' ye tıklayın ve ardından bir kaydırıcı denetimi ve bir dosya seçme denetimi olduğu yerde özellik kılavuzunu açın.</span><span class="sxs-lookup"><span data-stu-id="37984-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37984-138">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="37984-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37984-139">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="37984-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="37984-140">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="37984-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37984-141">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="37984-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
