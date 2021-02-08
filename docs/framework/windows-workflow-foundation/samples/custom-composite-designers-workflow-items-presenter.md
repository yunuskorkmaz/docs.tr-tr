---
description: 'Daha fazla bilgi edinin: özel bileşik tasarımcılar-Iş akışı öğeleri sunucu'
title: Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 07970763e12eccd981370f1241642cc28f675824
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792589"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu

, <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> WF tasarımcı programlama modelinde içerilen öğelerin bir koleksiyonunun düzenlenmesine izin veren bir anahtar türüdür. Bu örnek, düzenlenebilir bir koleksiyonu yüzey olarak gösteren bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.

Bu örnek şunları gösterir:

- İle özel etkinlik Tasarımcısı oluşturma <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> .

- "Daraltılmış" ve "genişletilmiş" görünüm ile etkinlik Tasarımcısı oluşturma.

- Yeniden barındırılan bir uygulamada varsayılan tasarımcıyı geçersiz kılma.

## <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma

1. C# veya Visual Studio 2010 ' de Visual Basic için **using Workflowwitemspresenter. sln** örnek çözümünü açın.

2. Çözümü derleyin ve çalıştırın.

   Yeniden barındırılan bir iş akışı Tasarımcısı uygulaması açılır ve etkinlikleri tuvalde sürükleyebilirsiniz.

## <a name="sample-highlights"></a>Örnek vurgular

Bu örnek için kod şunları gösterir:

- Bir tasarımcının oluşturulduğu etkinlik:  `Parallel`

- İle özel etkinlik tasarımcısının oluşturulması <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> . Dikkat etmeniz gereken birkaç nokta vardır:

  - Bağlamak için WPF veri bağlamasının kullanımını göz önünde edin `ModelItem.Branches` . `ModelItem` , üzerinde tasarımcı 'nın `WorkflowElementDesigner` kullanıldığı temel nesneye başvurur, bu örnekte `Parallel` .

  - , <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Bir görseli koleksiyondaki tek öğeler arasında görüntülenmek üzere yerleştirmek için kullanılabilir.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> , koleksiyondaki öğelerin yerleşimini belirlemede kullanılabilecek bir şablondur. Bu durumda, yatay yığın paneli kullanılır.

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

- Türüne ilişkilendirmesini yapın `DesignerAttribute` `Parallel` ve ardından bildirilen özniteliklerin çıkışını yapın.

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

  - Sonra, paralel yöntemi geçersiz kılın `RegisterCustomMetadata` .

    Aşağıdaki kod bunu C# ve Visual Basic gösterir.

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

- Son olarak, özelliği temel alan uygun şablonu seçmek için farklı veri şablonlarının ve tetikleyicilerin kullanımını aklınızda yapın `IsRootDesigner` .

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
