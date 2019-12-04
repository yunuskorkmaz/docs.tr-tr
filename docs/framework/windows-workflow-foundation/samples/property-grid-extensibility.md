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
# <a name="property-grid-extensibility"></a>Özellik Kılavuzu genişletilebilirliği

Geliştirici, tasarımcı içinde belirli bir etkinlik seçildiğinde görüntülenen özellik kılavuzunu özelleştirebilir. Bu, zengin bir Düzenle deneyimi oluşturmak için yapılabilir. Bu örnek, bunun nasıl yapılacağını gösterir.

## <a name="demonstrates"></a>Gösterir

Workflow Designer Özellik Kılavuzu genişletilebilirliği.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a>Tartışma

Özellik kılavuzunu genişletmek için, bir geliştiricinin bir özellik Kılavuzu düzenleyicisinin satır içi görünümünü özelleştirme seçenekleri vardır veya daha gelişmiş bir düzenleme yüzeyi için görüntülenen bir iletişim kutusu sağlar. Bu örnekte gösterilen iki farklı düzenleyici vardır; satır içi düzenleyici ve iletişim kutusu Düzenleyicisi.

## <a name="inline-editor"></a>Satır içi düzenleyici

Satır içi düzenleyici örneği şunları gösterir:

- <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>türetilen bir tür oluşturur.

- Oluşturucuda <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değeri bir Windows Presentation Foundation (WPF) veri şablonuyla ayarlanır. Bu bir XAML şablonuna bağlanabilir, ancak bu örnekte, veri bağlamayı başlatmak için kod kullanılır.

- Veri şablonunda, özellik kılavuzunda işlenen öğenin <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> bir veri bağlamı vardır. Aşağıdaki kodda (CustomInlineEditor.cs öğesinden) bu bağlamın daha sonra `Value` özelliğine bağladığına göz önünde edin.

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

- Etkinlik ve tasarımcı aynı derlemede olduğundan, etkinlik Tasarımcısı özniteliklerinin kaydı etkinliğin kendisinin statik oluşturucusunda, SimpleCodeActivity.cs ' den aşağıdaki örnekte gösterildiği gibi gerçekleştirilir.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a>İletişim kutusu düzenleyicisi

İletişim kutusu Düzenleyicisi örneği şunları gösterir:

1. <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>türetilen bir tür oluşturur.

2. Oluşturucuda <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değerini bir WPF veri şablonuyla ayarlar. Bu, XAML 'de oluşturulabilir, ancak bu örnekte kodda oluşturulur.

3. Veri şablonunda, özellik kılavuzunda işlenen öğenin <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> bir veri bağlamı vardır. Aşağıdaki kodda, bu daha sonra `Value` özelliğine bağlanır. Ayrıca, FilePickerEditor.cs içinde iletişim başlatan düğmeyi sağlamak için bir <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> de vardır.

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

4. İletişim kutusunun görüntülenmesini işlemek için tasarımcı türündeki <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> yöntemini geçersiz kılar. Bu örnekte, temel bir <xref:System.Windows.Forms.FileDialog> gösterilir.

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

5. Etkinlik ve tasarımcı aynı derlemede olduğundan, etkinlik Tasarımcısı özniteliklerinin kaydı etkinliğin kendisinin statik oluşturucusunda, SimpleCodeActivity.cs ' den aşağıdaki örnekte gösterildiği gibi gerçekleştirilir.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Çözümü derleyin ve ardından Workflow1. xaml ' yi açın.

2. Araç kutusundan bir **SimpleCodeActivity** 'yi tasarımcı tuvaline sürükleyin.

3. **SimpleCodeActivity** ' ye tıklayın ve ardından bir kaydırıcı denetimi ve bir dosya seçme denetimi olduğu yerde özellik kılavuzunu açın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
