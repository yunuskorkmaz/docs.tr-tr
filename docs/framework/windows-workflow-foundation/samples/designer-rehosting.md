---
title: Tasarımcı Rehosting
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: b72e3450799db40988c8b99e4db3707de330d8ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182816"
---
# <a name="designer-rehosting"></a><span data-ttu-id="2a8eb-102">Tasarımcıyı Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="2a8eb-102">Designer Rehosting</span></span>
<span data-ttu-id="2a8eb-103">Tasarımcı yeniden barındırma, özel bir uygulamanın içinde iş akışı tasarım tuvalbarındırma anlamına gelen yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="2a8eb-104">Çoğu insanın aşina olduğu barındırma uygulaması Visual Studio'dur, ancak bir uygulamada iş akışı tasarımcısını göstermenin yararlı olabileceği bir dizi senaryo vardır:</span><span class="sxs-lookup"><span data-stu-id="2a8eb-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="2a8eb-105">Uygulamaları izleme (son kullanıcının işlemi görselleştirmesine ve şu anda etkin olan durum, toplu yürütme süresi verileri veya iş akışının bir örneği yle ilgili diğer bilgiler gibi işlemle ilgili çalışma zamanı verilerine izin verir).</span><span class="sxs-lookup"><span data-stu-id="2a8eb-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="2a8eb-106">Kullanıcının işlemi sınırlı bir etkinlik kümesiyle özelleştirmesine olanak tanıyan uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="2a8eb-107">Bu tür uygulamaları desteklemek için, iş akışı tasarımcısı .NET Framework içinde yer alabilir ve bir WPF uygulaması içinde veya uygun WPF barındırma koduna sahip bir WinForms uygulamasında barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="2a8eb-108">Bu örnek şunları göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2a8eb-108">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="2a8eb-109">WF tasarımcısı yeniden barındırma.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-109">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="2a8eb-110">Yeniden barındırılan araç kutusunu ve özellik ızgarasını da kullanma.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="2a8eb-111">Tasarımcıyı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="2a8eb-111">Rehosting the designer</span></span>  
 <span data-ttu-id="2a8eb-112">Bu örnek, aşağıdaki ızgara düzeninde görülen tasarımcıyı içerecek şekilde WPF düzeninin nasıl oluşturultuğa (alan sorunları için atlanan araç kutusu kodu) gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="2a8eb-113">Tasarımcı ve özellik ızgarası içeren kenarlıkların adlandırma dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="2a8eb-114">Sonraki örnek tasarımcıoluşturur ve birincil <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> kullanıcı arabiriminde uygun kapsayıcı ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="2a8eb-115">Aşağıdaki örnekte bazı açıklamaları hak eden birkaç ek kod satırı vardır.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="2a8eb-116">Çağrı, <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> .NET Framework ile gönderilen etkinlikler için varsayılan etkinlik tasarımcılarını ilişkilendirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="2a8eb-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>düzenlenecek WF öğesinde geçmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="2a8eb-118">Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> tuval) ve (özellik ızgarası) kullanıcı arabirimi yüzeyine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="2a8eb-119">Yeniden barındırılan araç kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="2a8eb-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="2a8eb-120">Bu örnek, XAML'de yeniden barındırılan araç kutusu denetimini bildirimsel olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="2a8eb-121">Kodda, bir tür <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> oluşturucuya geçebilirsiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="2a8eb-122">Örneği kullanma</span><span class="sxs-lookup"><span data-stu-id="2a8eb-122">Using the sample</span></span>  
  
1. <span data-ttu-id="2a8eb-123">Visual Studio 2010'da DesignerRehosting.sln çözümlerini açın.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="2a8eb-124">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-124">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="2a8eb-125">WPF uygulaması yeniden barındırılan bir tasarımcıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2a8eb-126">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2a8eb-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2a8eb-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2a8eb-129">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a8eb-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
