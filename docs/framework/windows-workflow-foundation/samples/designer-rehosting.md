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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 005d6f98a7341954801c9b98e9eefdb1f0391d6c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="designer-rehosting"></a>Yeniden barındırma Tasarımcısı
Tasarımcı yeniden barındırılmasını başvuruda bulunan özel bir uygulama içinde iş akışı tasarım tuvale barındırmak için ortak bir senaryodur. Çoğu kişi bilginiz barındırma Visual Studio, ancak bir dizi vardır burada bir uygulamada iş akışı Tasarımcısı'nı gösteren yararlı olabilir senaryoları uygulamadır:  
  
-   (Şu anda etkin durumu, toplam yürütme süresi veri veya iş akışı örneği hakkında diğer bilgileri gibi işlemiyle ilgili çalışma zamanı verilerine yanı sıra işlem görselleştirmek bir son kullanıcı izin vererek) uygulamaları izleme.  
  
-   Etkinlikler sınırlı sayıda işlemine özelleştirmek bir kullanıcı izin uygulamalar.  
  
 Bu tür uygulamalar desteklemek için iş akışı Tasarımcısı'nı .NET Framework içinde gelir ve WPF uygulaması içinde veya bir WinForms uygulamasındaki kod barındırma uygun WPF ile barındırılabilir. Bu örnek gösterilmektedir:  
  
-   WF Tasarımcısı'nı yeniden barındırılmasını.  
  
-   Rehosted araç ve özellik Kılavuzu de kullanıyor.  
  
## <a name="rehosting-the-designer"></a>Tasarımcı yeniden barındırma  
 Bu örnek Tasarımcısı içerecek şekilde WPF düzeni oluşturulacağını gösterir (araç kutusu kodu alanı endişelerini atlanmış) aşağıdaki kılavuz düzeninde görülür. Adlandırma Tasarımcısı ve özellik Kılavuzu içeren kenarlıklarını unutmayın.  
  
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
  
 Sonraki örnek Tasarımcı oluşturur ve birincil ilişkilendirir <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> kullanıcı arabiriminde uygun bir kapsayıcı ile. Aşağıdaki örnek kod bazı açıklama belirlenmiştir birkaç ek satırları vardır. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Çağrıdır etkinlikleri ile birlikte gelen için varsayılan etkinlik tasarımcıları ilişkilendirmek için gerekli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>Düzenlenecek WF öğesinde geçirmek için çağrılır. Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil tuvale) ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (özellik Kılavuzu) kullanıcı arabirimi yüzeyine yerleştirilir.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Rehosted araç kutusunu kullanma  
 Bu örnek rehosted araç kutusu denetimi XAML'de bildirimli olarak kullanır. Kod içinde bir türüne geçirmek Not <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> Oluşturucusu.  
  
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
  
1.  DesignerRehosting.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Uygulamasını derlemek ve çalıştırmak için F5 tuşuna basın.  
  
3.  WPF uygulaması rehosted Tasarımcısı ile başlar.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`