---
title: Özel bileşik tasarımcılar - iş akışı öğesi sunucu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 7a3089f1b96cfc766143dd62d9f917fb014af636
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776932"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Özel bileşik tasarımcılar - iş akışı öğesi sunucu
<xref:System.Activities.Presentation.WorkflowItemPresenter> İçin "bir bırakma bölgesi rastgele bir etkinlik nereye yerleştirilebileceğini" oluşturulmasına izin verir WF Tasarımcı programlama modeli içinde bir anahtar türü. Bu örnek, bu yüzeyleri böyle bir "bırakma bölgesi." bir etkinlik Tasarımcısı oluşturma gösterir.

 Bu örnek gösterir:

## <a name="demonstrates"></a>Gösteriler

-   Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemPresenter>.

-   Meta veri deposu kullanarak özel Tasarımcı kaydediliyor.

-   Yeniden barındırılan araç bildirimli olarak ve kesin programlama.

## <a name="sample-details"></a>Örnek Ayrıntıları
 Bu örneğe yönelik kodun gösterir:

-   Özel Etkinlik Tasarımcısı oluşturulmuştur `SimpleNativeActivity` sınıfı.

-   Özel Etkinlik Tasarımcısı ile oluşturulmasını bir <xref:System.Activities.Presentation.WorkflowItemPresenter>.

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

 WPF verilerini bağlama bağlamak için kullanımına dikkat edin `ModelItem.Body`. `ModelItem` özelliği açıktır <xref:System.Activities.Presentation.ActivityDesigner> Tasarımcı kullanılmıştır, bu durumda, arka plandaki nesneye başvuran **SimpleNativeActivity**.

#### <a name="to-setup-build-and-run-the-sample"></a>Kurulum, derleme ve örneği çalıştırmak için

1.  Çözümü Visual Studio 2010'da açın.

2.  Derlemek ve uygulamayı çalıştırmak için F5 tuşuna basın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
