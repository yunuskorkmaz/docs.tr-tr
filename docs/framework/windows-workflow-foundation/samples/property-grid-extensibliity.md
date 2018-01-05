---
title: "Özellik Kılavuzu Extensibliity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3069e97a1696b37d56728eb86161cc2487dfdfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="property-grid-extensibliity"></a>Özellik Kılavuzu Extensibliity
Bir geliştirici, belirli bir etkinlik Tasarımcısı'nda seçildiğinde görüntülenen özellik Kılavuzu özelleştirebilirsiniz. Bu bir zengin düzenleme deneyimi oluşturmak için yapılabilir. Bu örnek, bu nasıl yapılabilir göstermektedir.  
  
## <a name="demonstrates"></a>Gösteriler  
 İş Akışı Tasarımcısı özelliği kılavuz genişletilebilirliği.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a>Tartışma  
 Özellik Kılavuzu genişletmek için bir geliştirici özellik kılavuz Düzenleyici satır içi görünüşünü özelleştirme veya görünen bir iletişim kutusu için daha gelişmiş bir düzenleme yüzey sağlamak için seçenekleri vardır. Bu örnekte gösterilen iki farklı düzenleyicileri vardır; bir satır içi düzenleyici ve bir iletişim kutusu Düzenleyicisi.  
  
## <a name="inline-editor"></a>Satır içi Düzenleyicisi  
 Satır içi Düzenleyicisi örnek şunlar gösterilmektedir:  
  
-   Türetilen bir tür oluşturur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.  
  
-   Oluşturucu, <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> değeri ayarlandığında bir [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] veri şablonu yok. Bu bir XAML şablona bağlı olabilir, ancak bu örnekte, veri bağlama başlatmak için kod kullanılır.  
  
-   Bir veri bağlamı veri şablonu bulunan <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> özellik kılavuzunda çizilir öğesi. Bu bağlamda sonra bağlar aşağıdaki kodu (ile CustomInlineEditor.cs) Not `Value` özelliği.  
  
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
  
-   Etkinlik ve tasarımcı aynı bütünleştirilmiş kodda olduğundan, etkinlik Tasarımcısı özniteliklerinin kayıt elde etkinlik kendisini statik oluşturucuda SimpleCodeActivity.cs aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a>İletişim Kutusu Düzenleyicisi  
 İletişim kutusu Düzenleyicisi örnek şunlar gösterilmektedir:  
  
1.  Türetilen bir tür oluşturur <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.  
  
2.  Ayarlar <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> Oluşturucu değerinde bir [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] veri şablonu yok. Bu XAML içinde oluşturulabilir, ancak bu örnekte, bu kod içinde oluşturulur.  
  
3.  Bir veri bağlamı veri şablonu bulunan <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> özellik kılavuzunda çizilir öğesi. Bu daha sonra aşağıdaki kodda bağlar `Value` özelliği. De dahil etmek için kritik bir <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> FilePickerEditor.cs iletişim başlatır düğmesi sağlayacak şekilde.  
  
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
  
4.  Geçersiz kılmaları <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` iletişim görüntüsünü işlemek için tasarımcı türündeki yöntemi. Bu örnekte, temel bir <xref:System.Windows.Forms.FileDialog> gösterilir.  
  
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
  
5.  Etkinlik ve tasarımcı aynı bütünleştirilmiş kodda olduğundan, etkinlik Tasarımcısı özniteliklerinin kayıt elde etkinlik kendisini statik oluşturucuda SimpleCodeActivity.cs aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözümü derlemek ve Workflow1.xaml açın.  
  
2.  Sürükleme bir **SimpleCodeActivity** Tasarımcı tuvaline Kutusu'ndan.  
  
3.  Tıklatın **SimpleCodeActivity** ve özellik ızgarasının kaydırıcı denetimi olduğu ve denetim çekme bir dosya açın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
