---
title: "Özel bileşik tasarımcıları - iş akışı öğeleri sunum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b708d39ba6e5f53579f575d5e228de43db3d90a9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Özel bileşik tasarımcıları - iş akışı öğeleri sunum
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> İçerilen öğelerin bir koleksiyonu düzenleme için izin veren WF Tasarımcı programlama modeli anahtar türü. Bu örnek düzenlenebilir bir koleksiyonu ortaya çıkarır bir etkinlik Tasarımcısı nasıl oluşturulacağını gösterir.  
  
 Bu örnek gösterilmektedir:  
  
-   Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.  
  
-   Bir etkinlik Tasarımcısı ile bir "daraltılmış" ve "genişletilmiş" görünümü oluşturma.  
  
-   Rehosted uygulama varsayılan tasarımcısında geçersiz kılma.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Açık **UsingWorkflowItemsPresenter.sln** VB içinde veya C# için örnek çözümü [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın. Rehosted iş akışı Tasarımcısı uygulaması açmanız gerekir ve etkinlikleri tuvale sürükleyin.  
  
## <a name="sample-highlights"></a>Örnek öne çıkan özellikleri  
 Bu örnek kod aşağıda gösterilmiştir:  
  
-   Bir tasarımcı etkinlik için yerleşik olarak bulunur:`Parallel`  
  
-   Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. İşaret etmek için bazı noktalar:  
  
    -   WPF veri bağlama bağlamak için kullanımına dikkat edin `ModelItem.Branches`. `ModelItem`özelliği açıktır `WorkflowElementDesigner` Tasarımcı kullanılıyor olduğu için bu durumda, temel alınan nesnesine başvuruyor bizim `Parallel`.  
  
    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Koleksiyonunda tek tek öğeler arasındaki görüntülemek için bir görsel yerleştirme için kullanılabilir.  
  
    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType>koleksiyondaki öğelerin düzenini belirlemek için sağlanan bir şablondur. Bu durumda, yatay yığın paneli kullanılır.  
  
 Bu aşağıdaki kod örneği bu gösterir.  
  
```xaml  
<sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                              Items="{Binding Path=ModelItem.Branches}">  
    <sad:WorkflowItemsPresenter.SpacerTemplate>  
      <DataTemplate>  
        <Ellipse Width="10" Height="10" Fill="Black"/>  
      </DataTemplate>  
    </sad:WorkflowItemsPresenter.SpacerTemplate>  
    <sad:WorkflowItemsPresenter.ItemsPanel>  
      <ItemsPanelTemplate>  
        <StackPanel Orientation="Horizontal"/>  
      </ItemsPanelTemplate>  
    </sad:WorkflowItemsPresenter.ItemsPanel>  
  </sad:WorkflowItemsPresenter>  
```  
  
-   İlişkilendirmesini gerçekleştirmek `DesignerAttribute` için `Parallel` türü ve ardından çıkış öznitelikleri bildirdi.  
  
    -   İlk olarak, tüm varsayılan tasarımcıları kaydedin.  
  
 Kod örneği verilmiştir.  
  
```csharp  
// register metadata  
(new DesignerMetadata()).Register();  
RegisterCustomMetadata();  
```  
  
```vb  
' register metadata  
Dim metadata = New DesignerMetadata()  
metadata.Register()  
' register custom metadata  
RegisterCustomMetadata()  
```  
  
    -   Ardından, paralel olarak geçersiz kılma `RegisterCustomMetadata` yöntemi.  
  
 Aşağıdaki kod, C# ve Visual Basic'te bu gösterir.  
 
```csharp  
void RegisterCustomMetadata()  
{  
      AttributeTableBuilder builder = new AttributeTableBuilder();  
      builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
      MetadataStore.AddAttributeTable(builder.CreateTable());  
}  
```  
  
```vb  
Sub RegisterCustomMetadata()  
   Dim builder As New AttributeTableBuilder()  
   builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))  
   MetadataStore.AddAttributeTable(builder.CreateTable())  
End Sub  
```  
  
-   Son olarak, farklı veri şablonları ve temel uygun şablonu seçmek için Tetikleyiciler kullanımını Not `IsRootDesigner` özelliği.  
  
 Kod örneği verilmiştir.  
  
```xaml  
<sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"  
    xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">  
  <sad:ActivityDesigner.Resources>  
    <DataTemplate x:Key="Expanded">  
      <StackPanel>  
        <TextBlock>This is the Expanded View</TextBlock>  
        <sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                    Items="{Binding Path=ModelItem.Branches}">  
          <sad:WorkflowItemsPresenter.SpacerTemplate>  
            <DataTemplate>  
              <Ellipse Width="10" Height="10" Fill="Black"/>  
            </DataTemplate>  
          </sad:WorkflowItemsPresenter.SpacerTemplate>  
          <sad:WorkflowItemsPresenter.ItemsPanel>  
            <ItemsPanelTemplate>  
              <StackPanel Orientation="Horizontal"/>  
            </ItemsPanelTemplate>  
          </sad:WorkflowItemsPresenter.ItemsPanel>  
        </sad:WorkflowItemsPresenter>  
      </StackPanel>  
    </DataTemplate>  
    <DataTemplate x:Key="Collapsed">  
      <TextBlock>This is the Collapsed View</TextBlock>  
    </DataTemplate>  
    <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
      <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
      <Style.Triggers>  
        <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">  
          <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
        </DataTrigger>  
      </Style.Triggers>  
    </Style>  
  </sad: ActivityDesigner.Resources>  
  <Grid>  
    <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
  </Grid>  
</sad: ActivityDesigner>  
```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [İş Akışı Tasarımcısı ile uygulamaları geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
