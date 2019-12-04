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
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="2487f-102">Özel Bileşik Tasarımcılar - İş Akışı Öğeleri Sunucu</span><span class="sxs-lookup"><span data-stu-id="2487f-102">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="2487f-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>, WF tasarımcı programlama modelinde içerilen öğelerin bir koleksiyonunun düzenlenmesine izin veren bir anahtar türüdür.</span><span class="sxs-lookup"><span data-stu-id="2487f-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="2487f-104">Bu örnek, düzenlenebilir bir koleksiyonu yüzey olarak gösteren bir etkinlik tasarımcısının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2487f-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="2487f-105">Bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="2487f-105">This sample demonstrates:</span></span>

- <span data-ttu-id="2487f-106"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>ile özel etkinlik Tasarımcısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2487f-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="2487f-107">"Daraltılmış" ve "genişletilmiş" görünüm ile etkinlik Tasarımcısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2487f-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="2487f-108">Yeniden barındırılan bir uygulamada varsayılan tasarımcıyı geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="2487f-108">Overriding a default designer in a rehosted application.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2487f-109">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2487f-109">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2487f-110">Visual Studio 2010 ' de VB için veya için C# **Usingworkflowwitemspresenter. sln** örnek çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="2487f-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in Visual Studio 2010.</span></span>

2. <span data-ttu-id="2487f-111">Çözümü derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2487f-111">Build and run the solution.</span></span> <span data-ttu-id="2487f-112">Yeniden barındırılan bir iş akışı Tasarımcısı uygulamasının açılması gerekir ve etkinlikleri tuvalde sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2487f-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="2487f-113">Örnek vurgular</span><span class="sxs-lookup"><span data-stu-id="2487f-113">Sample Highlights</span></span>

<span data-ttu-id="2487f-114">Bu örnek için kod şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="2487f-114">The code for this sample shows the following:</span></span>

- <span data-ttu-id="2487f-115">Tasarımcı için oluşturulan etkinlik: `Parallel`</span><span class="sxs-lookup"><span data-stu-id="2487f-115">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="2487f-116">Bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>ile özel etkinlik Tasarımcısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2487f-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2487f-117">Dikkat etmeniz gereken birkaç nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="2487f-117">A few things to point out:</span></span>

  - <span data-ttu-id="2487f-118">`ModelItem.Branches`bağlamak için WPF veri bağlamasının kullanımını göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="2487f-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="2487f-119">`ModelItem`, tasarımcının kullanıldığı temel nesneye başvuran `WorkflowElementDesigner` özelliğidir, bu durumda `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="2487f-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="2487f-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType>, bir görseli koleksiyondaki tek öğeler arasında görüntülenmek üzere yerleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2487f-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="2487f-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> koleksiyondaki öğelerin yerleşimini belirlemede kullanabileceğiniz bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="2487f-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="2487f-122">Bu durumda, yatay yığın paneli kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2487f-122">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="2487f-123">Aşağıdaki örnek kod bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2487f-123">This following example code shows this.</span></span>

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

- <span data-ttu-id="2487f-124">`Parallel` türüne `DesignerAttribute` ilişkilendirmesini gerçekleştirin ve sonra bildirilen özniteliklerin çıkışını yapın.</span><span class="sxs-lookup"><span data-stu-id="2487f-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="2487f-125">İlk olarak, tüm varsayılan tasarımcıları kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2487f-125">First, register all of the default designers.</span></span>

    <span data-ttu-id="2487f-126">Kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2487f-126">The following is the code example.</span></span>

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

  - <span data-ttu-id="2487f-127">Ardından `RegisterCustomMetadata` yöntemi paralel olarak geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="2487f-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="2487f-128">Aşağıdaki kod, C# ve Visual Basic gösterir.</span><span class="sxs-lookup"><span data-stu-id="2487f-128">The following code shows this in C# and Visual Basic.</span></span>

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

- <span data-ttu-id="2487f-129">Son olarak, `IsRootDesigner` özelliğine göre uygun şablonu seçmek için farklı veri şablonları ve Tetikleyicileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2487f-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="2487f-130">Kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2487f-130">The following is the code example.</span></span>

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
> <span data-ttu-id="2487f-131">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2487f-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2487f-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2487f-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2487f-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="2487f-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2487f-134">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2487f-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="2487f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2487f-135">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="2487f-136">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="2487f-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
