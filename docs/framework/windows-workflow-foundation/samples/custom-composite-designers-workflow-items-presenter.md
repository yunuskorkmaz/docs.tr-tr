---
title: Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: f4db3325081a820a37a8791849d2ad9697d15151
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118111"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Düzenlemek kapsanan öğelerin koleksiyonunu için izin veren WF Tasarımcı programlama modeli içinde bir anahtar türü. Bu örnek, düzenlenebilir bir koleksiyon ortaya çıkarır bir etkinlik Tasarımcısı oluşturma gösterilmektedir.

 Bu örnek gösterir:

-   Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.

-   Bir etkinlik Tasarımcısı ile "daraltılmış" ve "genişletilmiş" Görünüm oluşturuluyor.

-   Yeniden barındırılan bir uygulamanın varsayılan tasarımcıda geçersiz kılma.

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1.  Açık **UsingWorkflowItemsPresenter.sln** için C# veya VB Visual Studio 2010 için örnek çözümü.

2.  Derleme ve çözümü çalıştırın. Yeniden barındırılan iş akışı Tasarımcısı uygulamayı açmalıdır ve etkinlikleri tuvale sürükleyin.

## <a name="sample-highlights"></a>Örnek öne çıkan özellikleri
 Bu örneğe yönelik kodun aşağıda gösterilmiştir:

-   Bir tasarımcı etkinlik oluşturulmuştur:  `Parallel`

-   Özel Etkinlik Tasarımcısı ile oluşturulmasını bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Tablonuzu gereken bazı noktalar:

    -   WPF verilerini bağlama bağlamak için kullanımına dikkat edin `ModelItem.Branches`. `ModelItem` özelliği açıktır `WorkflowElementDesigner` Tasarımcı kullanılmıştır, bu durumda, arka plandaki nesneye başvuran bizim `Parallel`.

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Koleksiyondaki bireysel öğeleri arasında görüntülemek için bir görsel yerleştirme için kullanılabilir.

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> koleksiyondaki öğelerin düzeni belirlemek için sağlanan bir şablonudur. Bu durumda, yatay yığın paneli kullanılır.

 Bu aşağıdaki kod örneği bunu gösterir.

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

-   Son olarak, farklı veri şablonları ve temel uygun şablonu seçmek için Tetikleyiciler kullanımına dikkat edin `IsRootDesigner` özelliği.

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
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [İş Akışı Tasarımcısı ile uygulama geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
