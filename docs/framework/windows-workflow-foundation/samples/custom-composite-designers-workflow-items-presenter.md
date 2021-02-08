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
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="b56ee-103">Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu</span><span class="sxs-lookup"><span data-stu-id="b56ee-103">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="b56ee-104">, <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> WF tasarımcı programlama modelinde içerilen öğelerin bir koleksiyonunun düzenlenmesine izin veren bir anahtar türüdür.</span><span class="sxs-lookup"><span data-stu-id="b56ee-104">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="b56ee-105">Bu örnek, düzenlenebilir bir koleksiyonu yüzey olarak gösteren bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b56ee-105">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="b56ee-106">Bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="b56ee-106">This sample demonstrates:</span></span>

- <span data-ttu-id="b56ee-107">İle özel etkinlik Tasarımcısı oluşturma <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b56ee-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="b56ee-108">"Daraltılmış" ve "genişletilmiş" görünüm ile etkinlik Tasarımcısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b56ee-108">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="b56ee-109">Yeniden barındırılan bir uygulamada varsayılan tasarımcıyı geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="b56ee-109">Overriding a default designer in a rehosted application.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="b56ee-110">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b56ee-110">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="b56ee-111">C# veya Visual Studio 2010 ' de Visual Basic için **using Workflowwitemspresenter. sln** örnek çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="b56ee-111">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for Visual Basic in Visual Studio 2010.</span></span>

2. <span data-ttu-id="b56ee-112">Çözümü derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b56ee-112">Build and run the solution.</span></span>

   <span data-ttu-id="b56ee-113">Yeniden barındırılan bir iş akışı Tasarımcısı uygulaması açılır ve etkinlikleri tuvalde sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b56ee-113">A rehosted workflow designer application opens, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="b56ee-114">Örnek vurgular</span><span class="sxs-lookup"><span data-stu-id="b56ee-114">Sample Highlights</span></span>

<span data-ttu-id="b56ee-115">Bu örnek için kod şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="b56ee-115">The code for this sample shows the following:</span></span>

- <span data-ttu-id="b56ee-116">Bir tasarımcının oluşturulduğu etkinlik:  `Parallel`</span><span class="sxs-lookup"><span data-stu-id="b56ee-116">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="b56ee-117">İle özel etkinlik tasarımcısının oluşturulması <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b56ee-117">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b56ee-118">Dikkat etmeniz gereken birkaç nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="b56ee-118">A few things to point out:</span></span>

  - <span data-ttu-id="b56ee-119">Bağlamak için WPF veri bağlamasının kullanımını göz önünde edin `ModelItem.Branches` .</span><span class="sxs-lookup"><span data-stu-id="b56ee-119">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="b56ee-120">`ModelItem` , üzerinde tasarımcı 'nın `WorkflowElementDesigner` kullanıldığı temel nesneye başvurur, bu örnekte `Parallel` .</span><span class="sxs-lookup"><span data-stu-id="b56ee-120">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="b56ee-121">, <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Bir görseli koleksiyondaki tek öğeler arasında görüntülenmek üzere yerleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b56ee-121">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="b56ee-122"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> , koleksiyondaki öğelerin yerleşimini belirlemede kullanılabilecek bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="b56ee-122"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="b56ee-123">Bu durumda, yatay yığın paneli kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b56ee-123">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="b56ee-124">Aşağıdaki örnek kod bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b56ee-124">This following example code shows this.</span></span>

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

- <span data-ttu-id="b56ee-125">Türüne ilişkilendirmesini yapın `DesignerAttribute` `Parallel` ve ardından bildirilen özniteliklerin çıkışını yapın.</span><span class="sxs-lookup"><span data-stu-id="b56ee-125">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="b56ee-126">İlk olarak, tüm varsayılan tasarımcıları kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b56ee-126">First, register all of the default designers.</span></span>

    <span data-ttu-id="b56ee-127">Kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b56ee-127">The following is the code example.</span></span>

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

  - <span data-ttu-id="b56ee-128">Sonra, paralel yöntemi geçersiz kılın `RegisterCustomMetadata` .</span><span class="sxs-lookup"><span data-stu-id="b56ee-128">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="b56ee-129">Aşağıdaki kod bunu C# ve Visual Basic gösterir.</span><span class="sxs-lookup"><span data-stu-id="b56ee-129">The following code shows this in C# and Visual Basic.</span></span>

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

- <span data-ttu-id="b56ee-130">Son olarak, özelliği temel alan uygun şablonu seçmek için farklı veri şablonlarının ve tetikleyicilerin kullanımını aklınızda yapın `IsRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="b56ee-130">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="b56ee-131">Kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b56ee-131">The following is the code example.</span></span>

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
> <span data-ttu-id="b56ee-132">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b56ee-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b56ee-133">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b56ee-133">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b56ee-134">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b56ee-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b56ee-135">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b56ee-135">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="b56ee-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b56ee-136">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="b56ee-137">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="b56ee-137">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
