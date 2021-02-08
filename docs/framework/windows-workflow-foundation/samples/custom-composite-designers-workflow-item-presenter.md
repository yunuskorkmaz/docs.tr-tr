---
description: 'Daha fazla bilgi edinin: özel bileşik tasarımcılar-Iş akışı öğe sunum'
title: Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 20a3bddf7efd69b6138d6b8a5caae250aa377999
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787818"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="08bb4-103">Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu</span><span class="sxs-lookup"><span data-stu-id="08bb4-103">Custom Composite Designers - Workflow Item Presenter</span></span>

<span data-ttu-id="08bb4-104">, <xref:System.Activities.Presentation.WorkflowItemPresenter> WF Tasarımcısı programlama modelinde, rastgele bir etkinliğin yerleştirilebileceği bir "bırakma bölgesi" oluşturulmasına izin veren bir anahtar türüdür.</span><span class="sxs-lookup"><span data-stu-id="08bb4-104">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="08bb4-105">Bu örnek, "bırakma bölgesi" gibi yüzeylere sahip bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08bb4-105">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

<span data-ttu-id="08bb4-106">Bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="08bb4-106">This sample demonstrates:</span></span>

- <span data-ttu-id="08bb4-107">İle özel etkinlik Tasarımcısı oluşturma <xref:System.Activities.Presentation.WorkflowItemPresenter> .</span><span class="sxs-lookup"><span data-stu-id="08bb4-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="08bb4-108">Meta veri deposu kullanılarak özel tasarımcı kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="08bb4-108">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="08bb4-109">Yeniden barındırılan araç kutusunu bildirimli ve imperatively olarak programlama.</span><span class="sxs-lookup"><span data-stu-id="08bb4-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="08bb4-110">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="08bb4-110">Sample Details</span></span>

<span data-ttu-id="08bb4-111">Bu örnek için kod şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="08bb4-111">The code for this sample shows:</span></span>

- <span data-ttu-id="08bb4-112">Özel etkinlik Tasarımcısı sınıfı için oluşturulmuştur `SimpleNativeActivity` .</span><span class="sxs-lookup"><span data-stu-id="08bb4-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="08bb4-113">İle özel etkinlik tasarımcısının oluşturulması <xref:System.Activities.Presentation.WorkflowItemPresenter> .</span><span class="sxs-lookup"><span data-stu-id="08bb4-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

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

 <span data-ttu-id="08bb4-114">Bağlamak için WPF veri bağlamasının kullanımını göz önünde edin `ModelItem.Body` .</span><span class="sxs-lookup"><span data-stu-id="08bb4-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="08bb4-115">`ModelItem` ,, <xref:System.Activities.Presentation.ActivityDesigner> Bu örnekte, **SimpleNativeActivity**' de tasarımcı 'nın kullanıldığı temeldeki nesneyi ifade eden özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="08bb4-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="08bb4-116">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="08bb4-116">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="08bb4-117">Visual Studio 'da çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="08bb4-117">Open the solution in Visual Studio.</span></span>

2. <span data-ttu-id="08bb4-118">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="08bb4-118">Press **F5** to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08bb4-119">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="08bb4-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="08bb4-120">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="08bb4-120">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="08bb4-121">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="08bb4-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08bb4-122">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="08bb4-122">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a><span data-ttu-id="08bb4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08bb4-123">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="08bb4-124">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="08bb4-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
