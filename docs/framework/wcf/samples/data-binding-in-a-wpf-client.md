---
description: 'Hakkında daha fazla bilgi edinin: Windows Presentation Foundation Istemcisinde veri bağlama'
title: Windows Presentation Foundation İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 8bab24dc8f3debb75ddfd712a06f2f035707d42f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755882"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="581b6-103">Windows Presentation Foundation İstemcisinde Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="581b6-103">Data Binding in a Windows Presentation Foundation Client</span></span>

<span data-ttu-id="581b6-104">Bu örnek, bir Windows Presentation Foundation (WPF) istemcisinde veri bağlamanın kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="581b6-104">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="581b6-105">Örnek, istemciye dönmek için bir albüm dizisini rastgele üreten bir Windows Communication Foundation (WCF) hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="581b6-105">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="581b6-106">Her albümün bir adı, fiyatı ve albüm izlemelerinin bir listesi vardır.</span><span class="sxs-lookup"><span data-stu-id="581b6-106">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="581b6-107">Albüm izlemelerinin adı ve süresi vardır.</span><span class="sxs-lookup"><span data-stu-id="581b6-107">The album tracks have a name and duration.</span></span> <span data-ttu-id="581b6-108">Hizmet tarafından döndürülen bilgiler, Windows Presentation Foundation (WPF) istemcisi tarafından verilen kullanıcı arabirimine (UI) otomatik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="581b6-108">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="581b6-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="581b6-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="581b6-110">Veri bağlama bir veri kaynağının bir kullanıcı arabirimine otomatik olarak bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="581b6-110">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="581b6-111">Bu, programlama modelini basitleştiğinden, her UI öğesini bir veri nesnesinden veya bir dizi veri nesnesinden verilerle programlı bir şekilde güncelleştirmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="581b6-111">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="581b6-112">Bir nesneyi tek bir UI öğesine veya bir diziye, gibi birden çok giriş alan bir denetime bağlayabilirsiniz `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="581b6-112">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="581b6-113">Aşağıdaki kod, bir UI öğesinin öğesine nasıl veri bağlanacağını gösterir `DataContext` .</span><span class="sxs-lookup"><span data-stu-id="581b6-113">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="581b6-114">Önceki örnekte, `DataContext` `grid` adlı düzen öğesi için `myPanel` yöntemi tarafından döndürülen verilere ayarlanır `GetAlbumList` .</span><span class="sxs-lookup"><span data-stu-id="581b6-114">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="581b6-115">, `DataContext` Öğelerin bağlama için kullanılan veri kaynağı ve yol gibi bağlamanın diğer özellikleri hakkında üst öğelerinden bilgi devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="581b6-115">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="581b6-116">Sunucudaki verilerin her güncelleştirildiği her seferinde kod satırının yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="581b6-116">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="581b6-117">Örneğin, pencere başlatıldığında ve yeni bir albüm eklendiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="581b6-117">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="581b6-118">Aşağıdaki örnek XAML kodunda, şunu `ListBox` belirtir `ItemsSource="{Binding }"` .</span><span class="sxs-lookup"><span data-stu-id="581b6-118">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="581b6-119">Bu, üst düzey UI öğesine bağlanan verilerin de bu denetime (yani Albümler dizisi) bağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="581b6-119">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="581b6-120">Ayrıca, `ItemTemplate="{StaticResource AlbumStyle}"` içindeki her öğe için kullanılacak veri şablonunu belirtir `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="581b6-120">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="581b6-121">Verilerin nasıl biçimlendirilmesi gerektiğini belirtmek için veri şablonları da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="581b6-121">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="581b6-122">Bu veri şablonları, uygulamadaki diğer kullanıcı arabirimi öğeleri için yeniden kullanılabilir. avantajı, veri şablonunun tek bir yerde tanımlanması ve saklanması olabilir.</span><span class="sxs-lookup"><span data-stu-id="581b6-122">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="581b6-123">`AlbumStyle`Veri şablonu iki s yan yana bir kılavuz yerleştirir `TextBlock` .</span><span class="sxs-lookup"><span data-stu-id="581b6-123">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="581b6-124">Bir tane, albümün adını ve albümdeki diğer parça sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="581b6-124">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="581b6-125">Aşağıdaki XAML kodu bir ikinci oluşturur `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="581b6-125">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="581b6-126">Kod, için bir yol belirtir `ItemsSource` .</span><span class="sxs-lookup"><span data-stu-id="581b6-126">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="581b6-127">Bu, bu denetime bağlanan verilerin en üst düzey veriler, ancak adlı en üst düzey verilerin bir özelliği olmadığı anlamına gelir `Tracks` .</span><span class="sxs-lookup"><span data-stu-id="581b6-127">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="581b6-128">Bu özellik, albümün içindeki izlemelerin dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="581b6-128">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="581b6-129">Ayrıca, farklı bir `DataTemplate` adlandırılmış `TrackStyle` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="581b6-129">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="581b6-130">`TrackStyle`Şablonun yerleşimi `AlbumStyle` şablonla benzerdir, ancak `TextBlock` öğeleri farklı özelliklere bağlanır.</span><span class="sxs-lookup"><span data-stu-id="581b6-130">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="581b6-131">Bunun nedeni, iki şablonun farklı veri nesneleriyle kullanıllarıdır.</span><span class="sxs-lookup"><span data-stu-id="581b6-131">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="581b6-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="581b6-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="581b6-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="581b6-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="581b6-134">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="581b6-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="581b6-135">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="581b6-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="581b6-136">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="581b6-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="581b6-137">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="581b6-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="581b6-138">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="581b6-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="581b6-139">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="581b6-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
