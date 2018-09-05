---
title: Özellik Kılavuzu genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: b7c3e3dbc3ccd95fc12dffd40927b3e2bbbc8226
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43660262"
---
# <a name="property-grid-extensibliity"></a><span data-ttu-id="001e8-102">Özellik Kılavuzu genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="001e8-102">Property Grid Extensibliity</span></span>
<span data-ttu-id="001e8-103">Bir geliştirici, belirli bir etkinlik Tasarımcısı'nda seçildiğinde görüntülenen özellik kılavuzunda özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="001e8-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="001e8-104">Bir zengin düzenleme deneyimi oluşturmak için bu yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="001e8-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="001e8-105">Bu örnek, bu nasıl yapılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="001e8-105">This sample shows how this can be done.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="001e8-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="001e8-106">Demonstrates</span></span>  
 <span data-ttu-id="001e8-107">İş Akışı Tasarımcısı özellik Kılavuzu genişletilebilirliği.</span><span class="sxs-lookup"><span data-stu-id="001e8-107">Workflow designer property grid extensibility.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="001e8-108">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="001e8-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="001e8-109">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="001e8-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="001e8-110">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="001e8-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="001e8-111">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="001e8-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a><span data-ttu-id="001e8-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="001e8-112">Discussion</span></span>  
 <span data-ttu-id="001e8-113">Özellik kılavuzunda genişletmek için bir geliştirici satır içi bir özellik Kılavuzu Düzenleyicisi özelleştirme ya da daha gelişmiş bir düzenleme yüzeyi için görünen bir iletişim sağlamak için seçenekleri vardır.</span><span class="sxs-lookup"><span data-stu-id="001e8-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="001e8-114">Bu örnekte gösterilen iki farklı düzenleyici vardır; bir satır içi Düzenleyicisi ve bir iletişim kutusu Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="001e8-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>  
  
## <a name="inline-editor"></a><span data-ttu-id="001e8-115">Satır içi Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="001e8-115">Inline Editor</span></span>  
 <span data-ttu-id="001e8-116">Satır içi Düzenleyici örneği aşağıda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="001e8-116">The inline editor sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="001e8-117">Türetilen bir türü oluşturur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="001e8-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>  
  
-   <span data-ttu-id="001e8-118">Oluşturucuya <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değeri, bir Windows Presentation Foundation (WPF) veri şablonu ile ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="001e8-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="001e8-119">Bu XAML şablona bağlı olabilir, ancak bu örnekte, ilgili kod ve veri bağlama başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="001e8-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>  
  
-   <span data-ttu-id="001e8-120">Bir veri bağlamı veri şablonda <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> öğesinin özellik kılavuzunda çizilir.</span><span class="sxs-lookup"><span data-stu-id="001e8-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="001e8-121">Bu bağlam için ardından bağlayan aşağıdaki koddan (CustomInlineEditor.cs) Not `Value` özelliği.</span><span class="sxs-lookup"><span data-stu-id="001e8-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>  
  
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
  
-   <span data-ttu-id="001e8-122">Etkinlik ve tasarımcı aynı bütünleştirilmiş kodda olduğundan, etkinlik Tasarımcısı özniteliklerini kayıt elde etkinliği kendisine statik oluşturucuda SimpleCodeActivity.cs aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="001e8-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a><span data-ttu-id="001e8-123">İletişim Kutusu Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="001e8-123">Dialog Editor</span></span>  
 <span data-ttu-id="001e8-124">İletişim kutusu Düzenleyicisi örneği aşağıda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="001e8-124">The dialog editor sample demonstrates the following:</span></span>  
  
1.  <span data-ttu-id="001e8-125">Türetilen bir türü oluşturur <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="001e8-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>  
  
2.  <span data-ttu-id="001e8-126">Kümeleri <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> oluşturucuyla değerinde bir [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] veri şablonu.</span><span class="sxs-lookup"><span data-stu-id="001e8-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="001e8-127">Şu XAML içinde oluşturulamıyor, ancak bu örnekte, bu kod oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="001e8-127">This can be created in XAML, but in this sample, this is created in code.</span></span>  
  
3.  <span data-ttu-id="001e8-128">Bir veri bağlamı veri şablonda <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> öğesinin özellik kılavuzunda çizilir.</span><span class="sxs-lookup"><span data-stu-id="001e8-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="001e8-129">Aşağıdaki kodda, daha sonra bu bağlar `Value` özelliği.</span><span class="sxs-lookup"><span data-stu-id="001e8-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="001e8-130">De önemli bir <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> iletişim kutusunda FilePickerEditor.cs başlatan düğme sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="001e8-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="001e8-131">Geçersiz kılmalar <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` iletişim görüntüsünü işlemek için tasarımcı türündeki yöntemi.</span><span class="sxs-lookup"><span data-stu-id="001e8-131">Overrides the <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="001e8-132">Bu örnekte, temel bir <xref:System.Windows.Forms.FileDialog> gösterilir.</span><span class="sxs-lookup"><span data-stu-id="001e8-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>  
  
    ```  
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)  
    {  
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();  
        if (ofd.ShowDialog() == true)  
        {  
            propertyValue.Value = ofd.FileName;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="001e8-133">Etkinlik ve tasarımcı aynı bütünleştirilmiş kodda olduğundan, etkinlik Tasarımcısı özniteliklerini kayıt elde etkinliği kendisine statik oluşturucuda SimpleCodeActivity.cs aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="001e8-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="001e8-134">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="001e8-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="001e8-135">Çözümü derleyin ve Workflow1.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="001e8-135">Build the solution, and then open Workflow1.xaml.</span></span>  
  
2.  <span data-ttu-id="001e8-136">Sürükleme bir **SimpleCodeActivity** Tasarımcı tuvaline araç kutusundan.</span><span class="sxs-lookup"><span data-stu-id="001e8-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>  
  
3.  <span data-ttu-id="001e8-137">Tıklayın **SimpleCodeActivity** ve özellik kılavuzunu bir kaydırıcı denetimi olduğu ve denetim çekme dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="001e8-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="001e8-138">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="001e8-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="001e8-139">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="001e8-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="001e8-140">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="001e8-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="001e8-141">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="001e8-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
