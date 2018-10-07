---
title: Tasarımcıyı yeniden barındırma
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 885590604532fba76fc9ab3f6bcc69e077868403
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837367"
---
# <a name="designer-rehosting"></a><span data-ttu-id="da4c5-102">Tasarımcıyı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="da4c5-102">Designer Rehosting</span></span>
<span data-ttu-id="da4c5-103">Tasarımcı yeniden barındırma başvuran özel bir uygulama içinde iş akışı tasarım tuvali barındırmak için kullanılan yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="da4c5-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="da4c5-104">Çoğu kişi bilginiz barındırma kullanılabilen birkaç senaryolar burada iş akışı Tasarımcısı uygulamada gösteren yararlı olabilir ancak Visual Studio uygulamasıdır:</span><span class="sxs-lookup"><span data-stu-id="da4c5-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="da4c5-105">(Şu anda etkin durumuna, toplam yürütme süresi veri veya iş akışı örneği ile ilgili diğer bilgileri gibi işlemine ilişkin çalışma zamanı verilerinin yanı sıra işlem görselleştirmek bir son kullanıcı olanak tanır) uygulamalarını izleme.</span><span class="sxs-lookup"><span data-stu-id="da4c5-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="da4c5-106">Sınırlı bir dizi etkinliği ile işlem özelleştirmek bir kullanıcı izin uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="da4c5-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="da4c5-107">Bu tür uygulamaları desteklemek için iş akışı Tasarımcısı .NET Framework içinde birlikte gelen ve barındırma kodunu uygun WPF ile WPF uygulaması içinde veya bir WinForms uygulaması barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="da4c5-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="da4c5-108">Bu örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="da4c5-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="da4c5-109">WF tasarımcısını yeniden barındırma.</span><span class="sxs-lookup"><span data-stu-id="da4c5-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="da4c5-110">Yeniden barındırılan araç ve özellik Kılavuzu de kullanarak.</span><span class="sxs-lookup"><span data-stu-id="da4c5-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="da4c5-111">Tasarımcısını yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="da4c5-111">Rehosting the designer</span></span>  
 <span data-ttu-id="da4c5-112">Bu örnek, Tasarımcı içerecek şekilde WPF düzen oluşturma işlemi gösterilmektedir aşağıdaki kılavuz yerleşiminde (araç kutusu kodu ilgili alanı konuları atlanmış) görülür.</span><span class="sxs-lookup"><span data-stu-id="da4c5-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="da4c5-113">Tasarımcı ve özellik Kılavuzu içeren kenarlıklarını adlandırma unutmayın.</span><span class="sxs-lookup"><span data-stu-id="da4c5-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="da4c5-114">Sonraki örnek Tasarımcı oluşturur ve ilişkilendirir birincil <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> kullanıcı arabiriminde uygun bir kapsayıcı ile.</span><span class="sxs-lookup"><span data-stu-id="da4c5-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="da4c5-115">Aşağıdaki örnek kod bazı açıklama kadar geniştir birkaç ek satır vardır.</span><span class="sxs-lookup"><span data-stu-id="da4c5-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="da4c5-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Çağrıdır ile birlikte gelen etkinlikleri için varsayılan etkinlik tasarımcıları ilişkilendirmek için gerekli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da4c5-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="da4c5-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> Düzenlenecek WF öğesinde geçirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="da4c5-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="da4c5-118">Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil tuval) ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (özellik kılavuzunda) kullanıcı arabirimi yüzeyine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="da4c5-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="da4c5-119">Yeniden barındırılan araç kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="da4c5-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="da4c5-120">Bu örnek yeniden barındırılan araç kutusu denetimi, XAML içinde bildirimli olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="da4c5-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="da4c5-121">Kodda bir bir türe aktarın Not <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="da4c5-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="da4c5-122">Örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="da4c5-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="da4c5-123">Visual Studio 2010'da DesignerRehosting.sln çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="da4c5-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2.  <span data-ttu-id="da4c5-124">Derlemek ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="da4c5-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="da4c5-125">Bir WPF uygulamasını yeniden barındırılan bir tasarımcı ile başlar.</span><span class="sxs-lookup"><span data-stu-id="da4c5-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da4c5-126">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="da4c5-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da4c5-127">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="da4c5-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="da4c5-128">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="da4c5-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da4c5-129">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="da4c5-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`