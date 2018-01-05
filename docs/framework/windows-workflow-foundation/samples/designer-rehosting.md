---
title: "Yeniden barındırma Tasarımcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44577450bb81e255caf22f306dcd0276821d262c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="designer-rehosting"></a><span data-ttu-id="7ed3e-102">Yeniden barındırma Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="7ed3e-102">Designer ReHosting</span></span>
<span data-ttu-id="7ed3e-103">Tasarımcı yeniden barındırılmasını başvuruda bulunan özel bir uygulama içinde iş akışı tasarım tuvale barındırmak için ortak bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="7ed3e-104">Çoğu kişi bilginiz barındırma Visual Studio, ancak bir dizi vardır burada bir uygulamada iş akışı Tasarımcısı'nı gösteren yararlı olabilir senaryoları uygulamadır:</span><span class="sxs-lookup"><span data-stu-id="7ed3e-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="7ed3e-105">(Şu anda etkin durumu, toplam yürütme süresi veri veya iş akışı örneği hakkında diğer bilgileri gibi işlemiyle ilgili çalışma zamanı verilerine yanı sıra işlem görselleştirmek bir son kullanıcı izin vererek) uygulamaları izleme.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="7ed3e-106">Etkinlikler sınırlı sayıda işlemine özelleştirmek bir kullanıcı izin uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="7ed3e-107">Bu tür uygulamalar desteklemek için iş akışı Tasarımcısı'nı .NET Framework içinde gelir ve WPF uygulaması içinde veya bir WinForms uygulamasındaki kod barındırma uygun WPF ile barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="7ed3e-108">Bu örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7ed3e-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="7ed3e-109">WF Tasarımcısı'nı yeniden barındırılmasını.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="7ed3e-110">Rehosted araç ve özellik Kılavuzu de kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="7ed3e-111">Tasarımcı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="7ed3e-111">Rehosting the designer</span></span>  
 <span data-ttu-id="7ed3e-112">Bu örnek Tasarımcısı içerecek şekilde WPF düzeni oluşturulacağını gösterir (araç kutusu kodu alanı endişelerini atlanmış) aşağıdaki kılavuz düzeninde görülür.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="7ed3e-113">Adlandırma Tasarımcısı ve özellik Kılavuzu içeren kenarlıklarını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="7ed3e-114">Sonraki örnek Tasarımcı oluşturur ve birincil ilişkilendirir <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> kullanıcı arabiriminde uygun bir kapsayıcı ile.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="7ed3e-115">Aşağıdaki örnek kod bazı açıklama belirlenmiştir birkaç ek satırları vardır.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="7ed3e-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Çağrıdır etkinlikleri ile birlikte gelen için varsayılan etkinlik tasarımcıları ilişkilendirmek için gerekli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ed3e-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="7ed3e-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>Düzenlenecek WF öğesinde geçirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="7ed3e-118">Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil tuvale) ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (özellik Kılavuzu) kullanıcı arabirimi yüzeyine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="7ed3e-119">Rehosted araç kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="7ed3e-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="7ed3e-120">Bu örnek rehosted araç kutusu denetimi XAML'de bildirimli olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="7ed3e-121">Kod içinde bir türüne geçirmek Not <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="7ed3e-122">Örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="7ed3e-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="7ed3e-123">DesignerRehosting.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ed3e-123">Open the DesignerRehosting.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7ed3e-124">Uygulamasını derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="7ed3e-125">WPF uygulaması rehosted Tasarımcısı ile başlar.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7ed3e-126">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7ed3e-127">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7ed3e-128">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7ed3e-129">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7ed3e-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`