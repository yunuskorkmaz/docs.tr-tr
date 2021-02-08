---
description: 'Daha fazla bilgi edinin: tasarımcı yeniden barındırma'
title: Tasarımcı yeniden barındırma
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 84401ba7cfc2b5515a9dcfda36289893e55660e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792537"
---
# <a name="designer-rehosting"></a><span data-ttu-id="6fca1-103">Tasarımcıyı Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="6fca1-103">Designer Rehosting</span></span>

<span data-ttu-id="6fca1-104">Tasarımcı yeniden barındırma, iş akışı tasarım tuvalinin özel bir uygulamanın içinde barındırılmasına işaret eden yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="6fca1-104">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="6fca1-105">Çoğu kişinin en çok öğrenme uygulaması Visual Studio, ancak bir uygulamada iş akışı tasarımcısının gösterildiği birçok senaryo vardır:</span><span class="sxs-lookup"><span data-stu-id="6fca1-105">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="6fca1-106">Uygulamaları izleme (son kullanıcının işlemi görselleştirmesine ve şu anda etkin durum, toplu yürütme süresi verileri veya iş akışı örneğiyle ilgili diğer bilgiler gibi işlem hakkındaki çalışma zamanı verileri).</span><span class="sxs-lookup"><span data-stu-id="6fca1-106">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="6fca1-107">Kullanıcının işlemi sınırlı bir etkinlik kümesiyle özelleştirmesini sağlayan uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="6fca1-107">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="6fca1-108">Bu uygulama türlerini desteklemek için, iş akışı Tasarımcısı .NET Framework içinde dağıtılır ve bir WPF uygulamasında veya uygun WPF barındırma kodu ile bir WinForms uygulamasında barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6fca1-108">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="6fca1-109">Bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="6fca1-109">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="6fca1-110">WF tasarımcısını yeniden barındırma.</span><span class="sxs-lookup"><span data-stu-id="6fca1-110">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="6fca1-111">Yeniden barındırılan araç kutusu ve özellik kılavuzunu de kullanma.</span><span class="sxs-lookup"><span data-stu-id="6fca1-111">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="6fca1-112">Tasarımcıyı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="6fca1-112">Rehosting the designer</span></span>  

 <span data-ttu-id="6fca1-113">Bu örnek, aşağıdaki kılavuz düzeninde görülen, tasarımcıyı içeren WPF düzeninin nasıl oluşturulacağını gösterir (alan kaygıları için araç kutusu kodu atlandı).</span><span class="sxs-lookup"><span data-stu-id="6fca1-113">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="6fca1-114">Tasarımcı ve özellik kılavuzunu içeren kenarlıkların adlandırmasını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6fca1-114">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="6fca1-115">Örnek, tasarımcı oluşturur ve birincil öğesini <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> Kullanıcı arabirimindeki uygun kapsayıcıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="6fca1-115">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="6fca1-116">Aşağıdaki örnekte, biraz açıklama olan bazı ek kod satırları vardır.</span><span class="sxs-lookup"><span data-stu-id="6fca1-116">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="6fca1-117"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A>.NET Framework ile gönderilen etkinlikler için varsayılan etkinlik tasarımcılarını ilişkilendirmek için çağrı gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fca1-117">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="6fca1-118"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> , düzenlenecek WF öğesini geçirmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="6fca1-118"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="6fca1-119">Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil tuval) ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (Özellik Kılavuzu) Kullanıcı arabirimi yüzeyine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6fca1-119">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="6fca1-120">Yeniden barındırılan araç kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="6fca1-120">Using the rehosted toolbox</span></span>  

 <span data-ttu-id="6fca1-121">Bu örnekte, yeniden barındırılan araç kutusu denetimi XAML 'de bildirimli olarak kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6fca1-121">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="6fca1-122">Kodda bir türün oluşturucuya bir tür geçirebileceğini unutmayın <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> .</span><span class="sxs-lookup"><span data-stu-id="6fca1-122">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="6fca1-123">Örneği kullanma</span><span class="sxs-lookup"><span data-stu-id="6fca1-123">Using the sample</span></span>  
  
1. <span data-ttu-id="6fca1-124">Visual Studio 2010 ' de DesignerRehosting. sln çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="6fca1-124">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="6fca1-125">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6fca1-125">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="6fca1-126">WPF uygulaması yeniden barındırılan bir tasarımcı ile başlar.</span><span class="sxs-lookup"><span data-stu-id="6fca1-126">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6fca1-127">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6fca1-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6fca1-128">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6fca1-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6fca1-129">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6fca1-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6fca1-130">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6fca1-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
