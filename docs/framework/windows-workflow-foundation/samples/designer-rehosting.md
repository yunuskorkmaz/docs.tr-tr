---
title: Tasarımcı yeniden barındırma
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: ecbea5822825cca5f3f5cf40e20d5d249b17b07c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038190"
---
# <a name="designer-rehosting"></a>Tasarımcıyı Yeniden Barındırma
Tasarımcı yeniden barındırma, iş akışı tasarım tuvalinin özel bir uygulamanın içinde barındırılmasına işaret eden yaygın bir senaryodur. Çoğu kişinin en çok öğrenme uygulaması Visual Studio, ancak bir uygulamada iş akışı tasarımcısının gösterildiği birçok senaryo vardır:  
  
- Uygulamaları izleme (son kullanıcının işlemi görselleştirmesine ve şu anda etkin durum, toplu yürütme süresi verileri veya iş akışı örneğiyle ilgili diğer bilgiler gibi işlem hakkındaki çalışma zamanı verileri).  
  
- Kullanıcının işlemi sınırlı bir etkinlik kümesiyle özelleştirmesini sağlayan uygulamalar.  
  
 Bu uygulama türlerini desteklemek için, iş akışı Tasarımcısı .NET Framework içinde dağıtılır ve bir WPF uygulamasında veya uygun WPF barındırma kodu ile bir WinForms uygulamasında barındırılabilir. Bu örnek şunları gösterir:  
  
- WF tasarımcısını yeniden barındırma.  
  
- Yeniden barındırılan araç kutusu ve özellik kılavuzunu de kullanma.  
  
## <a name="rehosting-the-designer"></a>Tasarımcıyı yeniden barındırma  
 Bu örnek, aşağıdaki kılavuz düzeninde görülen, tasarımcıyı içeren WPF düzeninin nasıl oluşturulacağını gösterir (alan kaygıları için araç kutusu kodu atlandı). Tasarımcı ve özellik kılavuzunu içeren kenarlıkların adlandırmasını aklınızda bulundurun.  
  
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
  
 Örnek, tasarımcı oluşturur ve birincil <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> öğesini ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> Kullanıcı arabirimindeki uygun kapsayıcıyla ilişkilendirir. Aşağıdaki örnekte, biraz açıklama olan bazı ek kod satırları vardır. .NET Framework ile gönderilen etkinlikler için varsayılan etkinlik tasarımcılarını ilişkilendirmek için çağrıgerekir.<xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>, düzenlenecek WF öğesini geçirmek için çağırılır. Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil tuval) ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (Özellik Kılavuzu) Kullanıcı arabirimi yüzeyine yerleştirilir.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Yeniden barındırılan araç kutusunu kullanma  
 Bu örnekte, yeniden barındırılan araç kutusu denetimi XAML 'de bildirimli olarak kullanılmaktadır. Kodda bir türün <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> oluşturucuya bir tür geçirebileceğini unutmayın.  
  
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
  
#### <a name="using-the-sample"></a>Örneği kullanma  
  
1. Visual Studio 2010 ' de DesignerRehosting. sln çözümünü açın.  
  
2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.  
  
3. WPF uygulaması yeniden barındırılan bir tasarımcı ile başlar.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
