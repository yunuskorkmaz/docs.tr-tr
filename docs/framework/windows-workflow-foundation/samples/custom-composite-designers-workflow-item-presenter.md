---
title: Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 239f7ccd81d5bb60eed32298220df215b09e3e47
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038369"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu
, <xref:System.Activities.Presentation.WorkflowItemPresenter> WF Tasarımcısı programlama modelinde, rastgele bir etkinliğin yerleştirilebileceği bir "bırakma bölgesi" oluşturulmasına izin veren bir anahtar türüdür. Bu örnek, "bırakma bölgesi" gibi yüzeylere sahip bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.

 Bu örnek şunları gösterir:

## <a name="demonstrates"></a>Gösteriler

- İle özel etkinlik Tasarımcısı oluşturma <xref:System.Activities.Presentation.WorkflowItemPresenter>.

- Meta veri deposu kullanılarak özel tasarımcı kaydediliyor.

- Yeniden barındırılan araç kutusunu bildirimli ve imperatively olarak programlama.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Bu örnek için kod şunu gösterir:

- Özel etkinlik Tasarımcısı `SimpleNativeActivity` sınıfı için oluşturulmuştur.

- İle özel etkinlik tasarımcısının oluşturulması <xref:System.Activities.Presentation.WorkflowItemPresenter>.

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

 Bağlamak için WPF veri bağlamasının kullanımını göz önünde edin `ModelItem.Body`. `ModelItem`,, bu örnekte <xref:System.Activities.Presentation.ActivityDesigner> , **SimpleNativeActivity**' de tasarımcı 'nın kullanıldığı temeldeki nesneyi ifade eden özelliğidir.

#### <a name="to-setup-build-and-run-the-sample"></a>Örneği kurmak, derlemek ve çalıştırmak için

1. Visual Studio 2010 ' de çözümü açın.

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
