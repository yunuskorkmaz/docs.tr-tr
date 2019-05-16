---
title: Özellik Kılavuzu genişletilebilirliği - WF örnek
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: d22b6e21fbf2d5deb4d47fce683553378e990000
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637673"
---
# <a name="property-grid-extensibility"></a>Özellik Kılavuzu genişletilebilirliği

Bir geliştirici, belirli bir etkinlik Tasarımcısı'nda seçildiğinde görüntülenen özellik kılavuzunda özelleştirebilirsiniz. Bir zengin düzenleme deneyimi oluşturmak için bu yapılabilir. Bu örnek, bu nasıl yapılabileceğini gösterir.

## <a name="demonstrates"></a>Gösteriler

İş Akışı Tasarımcısı özellik Kılavuzu genişletilebilirliği.

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a>Tartışma

Özellik kılavuzunda genişletmek için bir geliştirici satır içi bir özellik Kılavuzu Düzenleyicisi özelleştirme ya da daha gelişmiş bir düzenleme yüzeyi için görünen bir iletişim sağlamak için seçenekleri vardır. Bu örnekte gösterilen iki farklı düzenleyici vardır; bir satır içi Düzenleyicisi ve bir iletişim kutusu Düzenleyicisi.

## <a name="inline-editor"></a>Satır içi Düzenleyicisi

Satır içi Düzenleyici örneği aşağıda gösterilmektedir:

- Türetilen bir türü oluşturur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.

- Oluşturucuya <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değeri, bir Windows Presentation Foundation (WPF) veri şablonu ile ayarlanır. Bu XAML şablona bağlı olabilir, ancak bu örnekte, ilgili kod ve veri bağlama başlatmak için kullanılır.

- Bir veri bağlamı veri şablonda <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> öğesinin özellik kılavuzunda çizilir. Bu bağlam için ardından bağlayan aşağıdaki koddan (CustomInlineEditor.cs) Not `Value` özelliği.

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

- Etkinlik ve tasarımcı aynı bütünleştirilmiş kodda olduğundan, etkinlik Tasarımcısı özniteliklerini kayıt elde etkinliği kendisine statik oluşturucuda SimpleCodeActivity.cs aşağıdaki örnekte gösterildiği gibi.

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

İletişim kutusu Düzenleyicisi örneği aşağıda gösterilmektedir:

1. Türetilen bir türü oluşturur <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.

2. Kümeleri <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> oluşturucuyla değerinde bir [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] veri şablonu. Şu XAML içinde oluşturulamıyor, ancak bu örnekte, bu kod oluşturulur.

3. Bir veri bağlamı veri şablonda <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> öğesinin özellik kılavuzunda çizilir. Aşağıdaki kodda, daha sonra bu bağlar `Value` özelliği. De önemli bir <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> iletişim kutusunda FilePickerEditor.cs başlatan düğme sağlamak için.

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

4. Geçersiz kılmalar <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> iletişim görüntüsünü işlemek için tasarımcı türündeki yöntemi. Bu örnekte, temel bir <xref:System.Windows.Forms.FileDialog> gösterilir.

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

5. Etkinlik ve tasarımcı aynı bütünleştirilmiş kodda olduğundan, etkinlik Tasarımcısı özniteliklerini kayıt elde etkinliği kendisine statik oluşturucuda SimpleCodeActivity.cs aşağıdaki örnekte gösterildiği gibi.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Çözümü derleyin ve Workflow1.xaml açın.

2. Sürükleme bir **SimpleCodeActivity** Tasarımcı tuvaline araç kutusundan.

3. Tıklayın **SimpleCodeActivity** ve özellik kılavuzunu bir kaydırıcı denetimi olduğu ve denetim çekme dosyası açın.

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
