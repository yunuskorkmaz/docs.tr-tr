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
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="ea707-102">Özel bileşik tasarımcılar - iş akışı öğesi sunucu</span><span class="sxs-lookup"><span data-stu-id="ea707-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="ea707-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> İçin "bir bırakma bölgesi rastgele bir etkinlik nereye yerleştirilebileceğini" oluşturulmasına izin verir WF Tasarımcı programlama modeli içinde bir anahtar türü.</span><span class="sxs-lookup"><span data-stu-id="ea707-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="ea707-104">Bu örnek, bu yüzeyleri böyle bir "bırakma bölgesi." bir etkinlik Tasarımcısı oluşturma gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea707-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

 <span data-ttu-id="ea707-105">Bu örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="ea707-105">This sample demonstrates:</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ea707-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="ea707-106">Demonstrates</span></span>

-   <span data-ttu-id="ea707-107">Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="ea707-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

-   <span data-ttu-id="ea707-108">Meta veri deposu kullanarak özel Tasarımcı kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="ea707-108">Registering the custom designer using the metadata store.</span></span>

-   <span data-ttu-id="ea707-109">Yeniden barındırılan araç bildirimli olarak ve kesin programlama.</span><span class="sxs-lookup"><span data-stu-id="ea707-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="ea707-110">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ea707-110">Sample Details</span></span>
 <span data-ttu-id="ea707-111">Bu örneğe yönelik kodun gösterir:</span><span class="sxs-lookup"><span data-stu-id="ea707-111">The code for this sample shows:</span></span>

-   <span data-ttu-id="ea707-112">Özel Etkinlik Tasarımcısı oluşturulmuştur `SimpleNativeActivity` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea707-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

-   <span data-ttu-id="ea707-113">Özel Etkinlik Tasarımcısı ile oluşturulmasını bir <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="ea707-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

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

 <span data-ttu-id="ea707-114">WPF verilerini bağlama bağlamak için kullanımına dikkat edin `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="ea707-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="ea707-115">`ModelItem` özelliği açıktır <xref:System.Activities.Presentation.ActivityDesigner> Tasarımcı kullanılmıştır, bu durumda, arka plandaki nesneye başvuran **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="ea707-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="ea707-116">Kurulum, derleme ve örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ea707-116">To setup, build, and run the sample</span></span>

1.  <span data-ttu-id="ea707-117">Çözümü Visual Studio 2010'da açın.</span><span class="sxs-lookup"><span data-stu-id="ea707-117">Open the solution in Visual Studio 2010.</span></span>

2.  <span data-ttu-id="ea707-118">Derlemek ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ea707-118">Press F5 to compile and run the application.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ea707-119">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ea707-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ea707-120">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ea707-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ea707-121">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ea707-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea707-122">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ea707-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="ea707-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea707-123">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [<span data-ttu-id="ea707-124">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="ea707-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
