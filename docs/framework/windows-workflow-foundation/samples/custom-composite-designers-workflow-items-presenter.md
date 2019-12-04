---
title: Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 542440d6bf9d6809abee1ec37c85c44ce72fd132
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715166"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu

<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>, WF tasarımcı programlama modelinde içerilen öğelerin bir koleksiyonunun düzenlenmesine izin veren bir anahtar türüdür. Bu örnek, düzenlenebilir bir koleksiyonu yüzey olarak gösteren bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.

Bu örnek şunları gösterir:

- <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>ile özel etkinlik Tasarımcısı oluşturma.

- "Daraltılmış" ve "genişletilmiş" görünüm ile etkinlik Tasarımcısı oluşturma.

- Yeniden barındırılan bir uygulamada varsayılan tasarımcıyı geçersiz kılma.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Visual Studio 2010 ' de VB için veya için C# **Usingworkflowwitemspresenter. sln** örnek çözümünü açın.

2. Çözümü derleyin ve çalıştırın. Yeniden barındırılan bir iş akışı Tasarımcısı uygulamasının açılması gerekir ve etkinlikleri tuvalde sürükleyebilirsiniz.

## <a name="sample-highlights"></a>Örnek vurgular

Bu örnek için kod şunları gösterir:

- Tasarımcı için oluşturulan etkinlik: `Parallel`

- Bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>ile özel etkinlik Tasarımcısı oluşturma. Dikkat etmeniz gereken birkaç nokta vardır:

  - `ModelItem.Branches`bağlamak için WPF veri bağlamasının kullanımını göz önünde edin. `ModelItem`, tasarımcının kullanıldığı temel nesneye başvuran `WorkflowElementDesigner` özelliğidir, bu durumda `Parallel`.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType>, bir görseli koleksiyondaki tek öğeler arasında görüntülenmek üzere yerleştirmek için kullanılabilir.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> koleksiyondaki öğelerin yerleşimini belirlemede kullanabileceğiniz bir şablondur. Bu durumda, yatay yığın paneli kullanılır.

  Aşağıdaki örnek kod bunu gösterir.

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

- `Parallel` türüne `DesignerAttribute` ilişkilendirmesini gerçekleştirin ve sonra bildirilen özniteliklerin çıkışını yapın.

  - İlk olarak, tüm varsayılan tasarımcıları kaydedin.

    Kod örneği aşağıda verilmiştir.

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

  - Ardından `RegisterCustomMetadata` yöntemi paralel olarak geçersiz kılınır.

    Aşağıdaki kod, C# ve Visual Basic gösterir.

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

- Son olarak, `IsRootDesigner` özelliğine göre uygun şablonu seçmek için farklı veri şablonları ve Tetikleyicileri kullanın.

  Kod örneği aşağıda verilmiştir.

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
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
