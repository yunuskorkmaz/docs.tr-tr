---
title: "Sunucu özel bileşik tasarımcıları - iş akışı öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3fa40a7a864ae65d15d787f5dec58a8da7b8e9a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="6d9be-102">Sunucu özel bileşik tasarımcıları - iş akışı öğesi</span><span class="sxs-lookup"><span data-stu-id="6d9be-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="6d9be-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> "Nerede rasgele bir etkinlik yerleştirilebilen bırakma bölgesi" oluşturulmasında verir WF Tasarımcı programlama modeli anahtar türü.</span><span class="sxs-lookup"><span data-stu-id="6d9be-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="6d9be-104">Bu örnek bir etkinlik Tasarımcısı bu yüzeyleri böyle bir "bırakma bölgesi." nasıl oluşturulacağını gösterir</span><span class="sxs-lookup"><span data-stu-id="6d9be-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>  
  
 <span data-ttu-id="6d9be-105">Bu örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6d9be-105">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6d9be-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="6d9be-106">Demonstrates</span></span>  
  
-   <span data-ttu-id="6d9be-107">Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="6d9be-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
-   <span data-ttu-id="6d9be-108">Meta veri deposu kullanarak özel Tasarımcısı kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="6d9be-108">Registering the custom designer using the metadata store.</span></span>  
  
-   <span data-ttu-id="6d9be-109">Rehosted araç programlama bildirimli olarak ve imperatively.</span><span class="sxs-lookup"><span data-stu-id="6d9be-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="6d9be-110">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="6d9be-110">Sample Details</span></span>  
 <span data-ttu-id="6d9be-111">Bu örnek kodu gösterilir:</span><span class="sxs-lookup"><span data-stu-id="6d9be-111">The code for this sample shows:</span></span>  
  
-   <span data-ttu-id="6d9be-112">Özel Etkinlik Tasarımcısı için yerleşik `SimpleNativeActivity` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6d9be-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>  
  
-   <span data-ttu-id="6d9be-113">Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="6d9be-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
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
  
 <span data-ttu-id="6d9be-114">WPF veri bağlama bağlamak için kullanımına dikkat edin `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="6d9be-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="6d9be-115">`ModelItem`özelliği açıktır <xref:System.Activities.Presentation.ActivityDesigner> Tasarımcı kullanılıyor olduğu için bu durumda, temel alınan nesnesine başvuruyor **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="6d9be-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>  
  
#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="6d9be-116">Kurulum, yapı ve örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6d9be-116">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6d9be-117">Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d9be-117">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d9be-118">Uygulamasını derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6d9be-118">Press F5 to compile and run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d9be-119">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d9be-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6d9be-120">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6d9be-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d9be-121">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6d9be-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d9be-122">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6d9be-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="6d9be-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d9be-123">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [<span data-ttu-id="6d9be-124">İş Akışı Tasarımcısı ile uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="6d9be-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
