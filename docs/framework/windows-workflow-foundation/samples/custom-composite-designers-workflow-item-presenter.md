---
title: Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 31dfae70a8b95bdfd457efe7a20ce44c2ba9c61f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715191"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu
<xref:System.Activities.Presentation.WorkflowItemPresenter>, WF Tasarımcısı programlama modelinde, rastgele bir etkinliğin yerleştirilebileceği bir "bırakma bölgesi" oluşturulmasına izin veren bir anahtar türüdür. Bu örnek, "bırakma bölgesi" gibi yüzeylere sahip bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.

 Bu örnek şunları gösterir:

## <a name="demonstrates"></a>Gösterir

- <xref:System.Activities.Presentation.WorkflowItemPresenter>ile özel etkinlik Tasarımcısı oluşturma.

- Meta veri deposu kullanılarak özel tasarımcı kaydediliyor.

- Yeniden barındırılan araç kutusunu bildirimli ve imperatively olarak programlama.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Bu örnek için kod şunu gösterir:

- Özel etkinlik Tasarımcısı `SimpleNativeActivity` sınıfı için oluşturulmuştur.

- Bir <xref:System.Activities.Presentation.WorkflowItemPresenter>ile özel etkinlik Tasarımcısı oluşturma.

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 `ModelItem.Body`bağlamak için WPF veri bağlamasının kullanımını göz önünde edin. `ModelItem`, tasarımcı 'nın, bu örnekte **SimpleNativeActivity**' de kullanılan temel nesneye başvuran <xref:System.Activities.Presentation.ActivityDesigner> özelliğidir.

#### <a name="to-setup-build-and-run-the-sample"></a>Örneği kurmak, derlemek ve çalıştırmak için

1. Visual Studio 2010 ' de çözümü açın.

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
