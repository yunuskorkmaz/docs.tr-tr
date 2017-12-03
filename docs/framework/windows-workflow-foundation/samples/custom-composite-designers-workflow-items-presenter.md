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
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="ac3cf-102">Özel bileşik tasarımcıları - iş akışı öğeleri sunum</span><span class="sxs-lookup"><span data-stu-id="ac3cf-102">Custom Composite Designers - Workflow Items Presenter</span></span>
<span data-ttu-id="ac3cf-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> İçerilen öğelerin bir koleksiyonu düzenleme için izin veren WF Tasarımcı programlama modeli anahtar türü.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="ac3cf-104">Bu örnek düzenlenebilir bir koleksiyonu ortaya çıkarır bir etkinlik Tasarımcısı nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>  
  
 <span data-ttu-id="ac3cf-105">Bu örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ac3cf-105">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="ac3cf-106">Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="ac3cf-107">Bir etkinlik Tasarımcısı ile bir "daraltılmış" ve "genişletilmiş" görünümü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>  
  
-   <span data-ttu-id="ac3cf-108">Rehosted uygulama varsayılan tasarımcısında geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-108">Overriding a default designer in a rehosted application.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ac3cf-109">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="ac3cf-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ac3cf-110">Açık **UsingWorkflowItemsPresenter.sln** VB içinde veya C# için örnek çözümü [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac3cf-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ac3cf-111">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-111">Build and run the solution.</span></span> <span data-ttu-id="ac3cf-112">Rehosted iş akışı Tasarımcısı uygulaması açmanız gerekir ve etkinlikleri tuvale sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>  
  
## <a name="sample-highlights"></a><span data-ttu-id="ac3cf-113">Örnek öne çıkan özellikleri</span><span class="sxs-lookup"><span data-stu-id="ac3cf-113">Sample Highlights</span></span>  
 <span data-ttu-id="ac3cf-114">Bu örnek kod aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ac3cf-114">The code for this sample shows the following:</span></span>  
  
-   <span data-ttu-id="ac3cf-115">Bir tasarımcı etkinlik için yerleşik olarak bulunur:`Parallel`</span><span class="sxs-lookup"><span data-stu-id="ac3cf-115">The activity a designer is built for:  `Parallel`</span></span>  
  
-   <span data-ttu-id="ac3cf-116">Özel Etkinlik Tasarımcısı ile oluşturma bir <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac3cf-117">İşaret etmek için bazı noktalar:</span><span class="sxs-lookup"><span data-stu-id="ac3cf-117">A few things to point out:</span></span>  
  
    -   <span data-ttu-id="ac3cf-118">WPF veri bağlama bağlamak için kullanımına dikkat edin `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="ac3cf-119">`ModelItem`özelliği açıktır `WorkflowElementDesigner` Tasarımcı kullanılıyor olduğu için bu durumda, temel alınan nesnesine başvuruyor bizim `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>  
  
    -   <span data-ttu-id="ac3cf-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Koleksiyonunda tek tek öğeler arasındaki görüntülemek için bir görsel yerleştirme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>  
  
    -   <span data-ttu-id="ac3cf-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType>koleksiyondaki öğelerin düzenini belirlemek için sağlanan bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="ac3cf-122">Bu durumda, yatay yığın paneli kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-122">In this case, a horizontal stack panel is used.</span></span>  
  
 <span data-ttu-id="ac3cf-123">Bu aşağıdaki kod örneği bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-123">This following example code shows this.</span></span>  
  
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
  
-   <span data-ttu-id="ac3cf-124">İlişkilendirmesini gerçekleştirmek `DesignerAttribute` için `Parallel` türü ve ardından çıkış öznitelikleri bildirdi.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>  
  
    -   <span data-ttu-id="ac3cf-125">İlk olarak, tüm varsayılan tasarımcıları kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-125">First, register all of the default designers.</span></span>  
  
 <span data-ttu-id="ac3cf-126">Kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-126">The following is the code example.</span></span>  
  
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
  
    -   <span data-ttu-id="ac3cf-127">Ardından, paralel olarak geçersiz kılma `RegisterCustomMetadata` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>  
  
 <span data-ttu-id="ac3cf-128">Aşağıdaki kod, C# ve Visual Basic'te bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-128">The following code shows this in C# and Visual Basic.</span></span>  
 
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
  
-   <span data-ttu-id="ac3cf-129">Son olarak, farklı veri şablonları ve temel uygun şablonu seçmek için Tetikleyiciler kullanımını Not `IsRootDesigner` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>  
  
 <span data-ttu-id="ac3cf-130">Kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-130">The following is the code example.</span></span>  
  
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
>  <span data-ttu-id="ac3cf-131">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ac3cf-132">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ac3cf-133">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ac3cf-134">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="ac3cf-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac3cf-135">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [<span data-ttu-id="ac3cf-136">İş Akışı Tasarımcısı ile uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="ac3cf-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
