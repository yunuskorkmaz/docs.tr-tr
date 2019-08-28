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
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="fdbd1-102">Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu</span><span class="sxs-lookup"><span data-stu-id="fdbd1-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="fdbd1-103">, <xref:System.Activities.Presentation.WorkflowItemPresenter> WF Tasarımcısı programlama modelinde, rastgele bir etkinliğin yerleştirilebileceği bir "bırakma bölgesi" oluşturulmasına izin veren bir anahtar türüdür.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="fdbd1-104">Bu örnek, "bırakma bölgesi" gibi yüzeylere sahip bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

 <span data-ttu-id="fdbd1-105">Bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="fdbd1-105">This sample demonstrates:</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fdbd1-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="fdbd1-106">Demonstrates</span></span>

- <span data-ttu-id="fdbd1-107">İle özel etkinlik Tasarımcısı oluşturma <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="fdbd1-108">Meta veri deposu kullanılarak özel tasarımcı kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-108">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="fdbd1-109">Yeniden barındırılan araç kutusunu bildirimli ve imperatively olarak programlama.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="fdbd1-110">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fdbd1-110">Sample Details</span></span>
 <span data-ttu-id="fdbd1-111">Bu örnek için kod şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="fdbd1-111">The code for this sample shows:</span></span>

- <span data-ttu-id="fdbd1-112">Özel etkinlik Tasarımcısı `SimpleNativeActivity` sınıfı için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="fdbd1-113">İle özel etkinlik tasarımcısının oluşturulması <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

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

 <span data-ttu-id="fdbd1-114">Bağlamak için WPF veri bağlamasının kullanımını göz önünde edin `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="fdbd1-115">`ModelItem`,, bu örnekte <xref:System.Activities.Presentation.ActivityDesigner> , **SimpleNativeActivity**' de tasarımcı 'nın kullanıldığı temeldeki nesneyi ifade eden özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="fdbd1-116">Örneği kurmak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fdbd1-116">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="fdbd1-117">Visual Studio 2010 ' de çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-117">Open the solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="fdbd1-118">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-118">Press F5 to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fdbd1-119">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fdbd1-120">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="fdbd1-121">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fdbd1-122">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="fdbd1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-123">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="fdbd1-124">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="fdbd1-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
