---
title: Tasarımcıyı yeniden barındırma
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 1901df62ccdeec3f75ce0d8cd85484f46fac4541
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274102"
---
# <a name="designer-rehosting"></a>Tasarımcıyı yeniden barındırma
Tasarımcı yeniden barındırma başvuran özel bir uygulama içinde iş akışı tasarım tuvali barındırmak için kullanılan yaygın bir senaryodur. Çoğu kişi bilginiz barındırma kullanılabilen birkaç senaryolar burada iş akışı Tasarımcısı uygulamada gösteren yararlı olabilir ancak Visual Studio uygulamasıdır:  
  
-   (Şu anda etkin durumuna, toplam yürütme süresi veri veya iş akışı örneği ile ilgili diğer bilgileri gibi işlemine ilişkin çalışma zamanı verilerinin yanı sıra işlem görselleştirmek bir son kullanıcı olanak tanır) uygulamalarını izleme.  
  
-   Sınırlı bir dizi etkinliği ile işlem özelleştirmek bir kullanıcı izin uygulamalar.  
  
 Bu tür uygulamaları desteklemek için iş akışı Tasarımcısı .NET Framework içinde birlikte gelen ve barındırma kodunu uygun WPF ile WPF uygulaması içinde veya bir WinForms uygulaması barındırılabilir. Bu örnek gösterir:  
  
-   WF tasarımcısını yeniden barındırma.  
  
-   Yeniden barındırılan araç ve özellik Kılavuzu de kullanarak.  
  
## <a name="rehosting-the-designer"></a>Tasarımcısını yeniden barındırma  
 Bu örnek, Tasarımcı içerecek şekilde WPF düzen oluşturma işlemi gösterilmektedir aşağıdaki kılavuz yerleşiminde (araç kutusu kodu ilgili alanı konuları atlanmış) görülür. Tasarımcı ve özellik Kılavuzu içeren kenarlıklarını adlandırma unutmayın.  
  
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
  
 Sonraki örnek Tasarımcı oluşturur ve ilişkilendirir birincil <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> kullanıcı arabiriminde uygun bir kapsayıcı ile. Aşağıdaki örnek kod bazı açıklama kadar geniştir birkaç ek satır vardır. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Çağrıdır ile birlikte gelen etkinlikleri için varsayılan etkinlik tasarımcıları ilişkilendirmek için gerekli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> Düzenlenecek WF öğesinde geçirmek için çağrılır. Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil tuval) ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (özellik kılavuzunda) kullanıcı arabirimi yüzeyine yerleştirilir.  
  
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
 Bu örnek yeniden barındırılan araç kutusu denetimi, XAML içinde bildirimli olarak kullanır. Kodda bir bir türe aktarın Not <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> Oluşturucusu.  
  
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
  
#### <a name="using-the-sample"></a>Örnek kullanma  
  
1.  DesignerRehosting.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derlemek ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
3.  Bir WPF uygulamasını yeniden barındırılan bir tasarımcı ile başlar.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`