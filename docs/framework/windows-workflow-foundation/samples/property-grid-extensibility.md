---
description: 'Daha fazla bilgi edinin: Özellik Kılavuzu genişletilebilirliği'
title: Özellik Kılavuzu genişletilebilirliği-WF örneği
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: 784705146974ffca5cd2e6c21dba722598544771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741815"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="c8875-103">Özellik Kılavuzu genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="c8875-103">Property grid extensibility</span></span>

<span data-ttu-id="c8875-104">Geliştirici, tasarımcı içinde belirli bir etkinlik seçildiğinde görüntülenen özellik kılavuzunu özelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c8875-104">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="c8875-105">Bu, zengin bir Düzenle deneyimi oluşturmak için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8875-105">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="c8875-106">Bu örnek, bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8875-106">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c8875-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="c8875-107">Demonstrates</span></span>

<span data-ttu-id="c8875-108">Workflow Designer Özellik Kılavuzu genişletilebilirliği.</span><span class="sxs-lookup"><span data-stu-id="c8875-108">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8875-109">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8875-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8875-110">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c8875-110">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c8875-111">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c8875-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8875-112">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c8875-112">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="c8875-113">Tartışma</span><span class="sxs-lookup"><span data-stu-id="c8875-113">Discussion</span></span>

<span data-ttu-id="c8875-114">Özellik kılavuzunu genişletmek için, bir geliştiricinin bir özellik Kılavuzu düzenleyicisinin satır içi görünümünü özelleştirme seçenekleri vardır veya daha gelişmiş bir düzenleme yüzeyi için görüntülenen bir iletişim kutusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8875-114">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="c8875-115">Bu örnekte gösterilen iki farklı düzenleyici vardır; satır içi düzenleyici ve iletişim kutusu Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c8875-115">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="c8875-116">Satır içi düzenleyici</span><span class="sxs-lookup"><span data-stu-id="c8875-116">Inline editor</span></span>

<span data-ttu-id="c8875-117">Satır içi düzenleyici örneği şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="c8875-117">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="c8875-118">Öğesinden türetilen bir tür oluşturur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor> .</span><span class="sxs-lookup"><span data-stu-id="c8875-118">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="c8875-119">Oluşturucuda, <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değer bir Windows Presentation Foundation (WPF) veri şablonuyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c8875-119">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="c8875-120">Bu bir XAML şablonuna bağlanabilir, ancak bu örnekte, veri bağlamayı başlatmak için kod kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8875-120">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="c8875-121">Veri şablonunda, <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> özellik kılavuzunda işlenen öğenin bir veri bağlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="c8875-121">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="c8875-122">Aşağıdaki kodda (CustomInlineEditor.cs ' den) bu bağlamın daha sonra özelliğe bağladığına göz önünde `Value` .</span><span class="sxs-lookup"><span data-stu-id="c8875-122">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

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

- <span data-ttu-id="c8875-123">Etkinlik ve tasarımcı aynı derlemede olduğundan, etkinlik Tasarımcısı özniteliklerinin kaydı etkinliğin kendisinin statik oluşturucusunda, SimpleCodeActivity.cs ' den aşağıdaki örnekte gösterildiği gibi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8875-123">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="c8875-124">İletişim kutusu düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="c8875-124">Dialog editor</span></span>

<span data-ttu-id="c8875-125">İletişim kutusu Düzenleyicisi örneği şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="c8875-125">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="c8875-126">Öğesinden türetilen bir tür oluşturur <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor> .</span><span class="sxs-lookup"><span data-stu-id="c8875-126">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="c8875-127"><xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A>Oluşturucuda BIR WPF veri şablonuyla değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c8875-127">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a WPF data template.</span></span> <span data-ttu-id="c8875-128">Bu, XAML 'de oluşturulabilir, ancak bu örnekte kodda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8875-128">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="c8875-129">Veri şablonunda, <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> özellik kılavuzunda işlenen öğenin bir veri bağlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="c8875-129">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="c8875-130">Aşağıdaki kodda, bu daha sonra `Value` özelliğine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="c8875-130">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="c8875-131">Ayrıca, <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> FilePickerEditor.cs içinde iletişim başlatan düğmeyi sağlamak için bir de vardır.</span><span class="sxs-lookup"><span data-stu-id="c8875-131">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

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

4. <span data-ttu-id="c8875-132"><xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A>İletişim kutusunun görüntülenmesini işlemek için tasarımcı türündeki yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c8875-132">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="c8875-133">Bu örnekte, temel <xref:System.Windows.Forms.FileDialog> gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8875-133">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

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

5. <span data-ttu-id="c8875-134">Etkinlik ve tasarımcı aynı derlemede olduğundan, etkinlik Tasarımcısı özniteliklerinin kaydı etkinliğin kendisinin statik oluşturucusunda, SimpleCodeActivity.cs ' den aşağıdaki örnekte gösterildiği gibi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8875-134">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8875-135">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c8875-135">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c8875-136">Çözümü derleyin ve ardından Workflow1. xaml ' yi açın.</span><span class="sxs-lookup"><span data-stu-id="c8875-136">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="c8875-137">Araç kutusundan bir **SimpleCodeActivity** 'yi tasarımcı tuvaline sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c8875-137">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="c8875-138">**SimpleCodeActivity** ' ye tıklayın ve ardından bir kaydırıcı denetimi ve bir dosya seçme denetimi olduğu yerde özellik kılavuzunu açın.</span><span class="sxs-lookup"><span data-stu-id="c8875-138">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8875-139">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8875-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8875-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c8875-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c8875-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c8875-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8875-142">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c8875-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
