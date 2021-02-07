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
# <a name="property-grid-extensibility"></a>Özellik Kılavuzu genişletilebilirliği

Geliştirici, tasarımcı içinde belirli bir etkinlik seçildiğinde görüntülenen özellik kılavuzunu özelleştirebilir. Bu, zengin bir Düzenle deneyimi oluşturmak için yapılabilir. Bu örnek, bunun nasıl yapılacağını gösterir.

## <a name="demonstrates"></a>Gösteriler

Workflow Designer Özellik Kılavuzu genişletilebilirliği.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a>Tartışma

Özellik kılavuzunu genişletmek için, bir geliştiricinin bir özellik Kılavuzu düzenleyicisinin satır içi görünümünü özelleştirme seçenekleri vardır veya daha gelişmiş bir düzenleme yüzeyi için görüntülenen bir iletişim kutusu sağlar. Bu örnekte gösterilen iki farklı düzenleyici vardır; satır içi düzenleyici ve iletişim kutusu Düzenleyicisi.

## <a name="inline-editor"></a>Satır içi düzenleyici

Satır içi düzenleyici örneği şunları gösterir:

- Öğesinden türetilen bir tür oluşturur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor> .

- Oluşturucuda, <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değer bir Windows Presentation Foundation (WPF) veri şablonuyla ayarlanır. Bu bir XAML şablonuna bağlanabilir, ancak bu örnekte, veri bağlamayı başlatmak için kod kullanılır.

- Veri şablonunda, <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> özellik kılavuzunda işlenen öğenin bir veri bağlamı vardır. Aşağıdaki kodda (CustomInlineEditor.cs ' den) bu bağlamın daha sonra özelliğe bağladığına göz önünde `Value` .

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

1. Öğesinden türetilen bir tür oluşturur <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor> .

2. <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A>Oluşturucuda BIR WPF veri şablonuyla değeri ayarlar. Bu, XAML 'de oluşturulabilir, ancak bu örnekte kodda oluşturulur.

3. Veri şablonunda, <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> özellik kılavuzunda işlenen öğenin bir veri bağlamı vardır. Aşağıdaki kodda, bu daha sonra `Value` özelliğine bağlanır. Ayrıca, <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> FilePickerEditor.cs içinde iletişim başlatan düğmeyi sağlamak için bir de vardır.

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

4. <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A>İletişim kutusunun görüntülenmesini işlemek için tasarımcı türündeki yöntemi geçersiz kılar. Bu örnekte, temel <xref:System.Windows.Forms.FileDialog> gösterilmektedir.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
