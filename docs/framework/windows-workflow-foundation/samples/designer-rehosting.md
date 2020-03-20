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
# <a name="designer-rehosting"></a>Tasarımcıyı Yeniden Barındırma
Tasarımcı yeniden barındırma, özel bir uygulamanın içinde iş akışı tasarım tuvalbarındırma anlamına gelen yaygın bir senaryodur. Çoğu insanın aşina olduğu barındırma uygulaması Visual Studio'dur, ancak bir uygulamada iş akışı tasarımcısını göstermenin yararlı olabileceği bir dizi senaryo vardır:  
  
- Uygulamaları izleme (son kullanıcının işlemi görselleştirmesine ve şu anda etkin olan durum, toplu yürütme süresi verileri veya iş akışının bir örneği yle ilgili diğer bilgiler gibi işlemle ilgili çalışma zamanı verilerine izin verir).  
  
- Kullanıcının işlemi sınırlı bir etkinlik kümesiyle özelleştirmesine olanak tanıyan uygulamalar.  
  
 Bu tür uygulamaları desteklemek için, iş akışı tasarımcısı .NET Framework içinde yer alabilir ve bir WPF uygulaması içinde veya uygun WPF barındırma koduna sahip bir WinForms uygulamasında barındırılabilir. Bu örnek şunları göstermektedir:  
  
- WF tasarımcısı yeniden barındırma.  
  
- Yeniden barındırılan araç kutusunu ve özellik ızgarasını da kullanma.  
  
## <a name="rehosting-the-designer"></a>Tasarımcıyı yeniden barındırma  
 Bu örnek, aşağıdaki ızgara düzeninde görülen tasarımcıyı içerecek şekilde WPF düzeninin nasıl oluşturultuğa (alan sorunları için atlanan araç kutusu kodu) gösterir. Tasarımcı ve özellik ızgarası içeren kenarlıkların adlandırma dikkat edin.  
  
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
  
 Sonraki örnek tasarımcıoluşturur ve birincil <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> ve <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> kullanıcı arabiriminde uygun kapsayıcı ile ilişkilendirir. Aşağıdaki örnekte bazı açıklamaları hak eden birkaç ek kod satırı vardır. Çağrı, <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> .NET Framework ile gönderilen etkinlikler için varsayılan etkinlik tasarımcılarını ilişkilendirmek için gereklidir. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>düzenlenecek WF öğesinde geçmek için çağrılır. Son olarak, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (birincil <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> tuval) ve (özellik ızgarası) kullanıcı arabirimi yüzeyine yerleştirilir.  
  
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
 Bu örnek, XAML'de yeniden barındırılan araç kutusu denetimini bildirimsel olarak kullanır. Kodda, bir tür <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> oluşturucuya geçebilirsiniz unutmayın.  
  
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
  
1. Visual Studio 2010'da DesignerRehosting.sln çözümlerini açın.  
  
2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.  
  
3. WPF uygulaması yeniden barındırılan bir tasarımcıyla başlar.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
