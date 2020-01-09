---
title: Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: d1047b8be35545e83eaa8788b53751b6b0056984
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338049"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="693f0-102">Özel Bileşik Tasarımcılar - İş Akışı Öğesi Sunucu</span><span class="sxs-lookup"><span data-stu-id="693f0-102">Custom Composite Designers - Workflow Item Presenter</span></span>

<span data-ttu-id="693f0-103"><xref:System.Activities.Presentation.WorkflowItemPresenter>, WF Tasarımcısı programlama modelinde, rastgele bir etkinliğin yerleştirilebileceği bir "bırakma bölgesi" oluşturulmasına izin veren bir anahtar türüdür.</span><span class="sxs-lookup"><span data-stu-id="693f0-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="693f0-104">Bu örnek, "bırakma bölgesi" gibi yüzeylere sahip bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="693f0-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

<span data-ttu-id="693f0-105">Bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="693f0-105">This sample demonstrates:</span></span>

- <span data-ttu-id="693f0-106"><xref:System.Activities.Presentation.WorkflowItemPresenter>ile özel etkinlik Tasarımcısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="693f0-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="693f0-107">Meta veri deposu kullanılarak özel tasarımcı kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="693f0-107">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="693f0-108">Yeniden barındırılan araç kutusunu bildirimli ve imperatively olarak programlama.</span><span class="sxs-lookup"><span data-stu-id="693f0-108">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="693f0-109">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="693f0-109">Sample Details</span></span>

<span data-ttu-id="693f0-110">Bu örnek için kod şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="693f0-110">The code for this sample shows:</span></span>

- <span data-ttu-id="693f0-111">Özel etkinlik Tasarımcısı `SimpleNativeActivity` sınıfı için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="693f0-111">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="693f0-112">Bir <xref:System.Activities.Presentation.WorkflowItemPresenter>ile özel etkinlik Tasarımcısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="693f0-112">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

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

 <span data-ttu-id="693f0-113">`ModelItem.Body`bağlamak için WPF veri bağlamasının kullanımını göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="693f0-113">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="693f0-114">`ModelItem`, tasarımcı 'nın, bu örnekte **SimpleNativeActivity**' de kullanılan temel nesneye başvuran <xref:System.Activities.Presentation.ActivityDesigner> özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="693f0-114">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="693f0-115">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="693f0-115">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="693f0-116">Visual Studio içinde çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="693f0-116">Open the solution in Visual Studio.</span></span>

2. <span data-ttu-id="693f0-117">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="693f0-117">Press **F5** to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="693f0-118">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="693f0-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="693f0-119">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="693f0-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="693f0-120">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="693f0-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="693f0-121">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="693f0-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a><span data-ttu-id="693f0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="693f0-122">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="693f0-123">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="693f0-123">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
