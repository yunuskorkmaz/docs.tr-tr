---
title: Windows Presentation Foundation İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 7bc389056872841905336dcf658a07223906bf82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183815"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="dcac4-102">Windows Presentation Foundation İstemcisinde Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="dcac4-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="dcac4-103">Bu örnek, bir Windows Sunu Temeli (WPF) istemcisinde veri bağlama kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="dcac4-104">Örnek, istemciye dönmek için rasgele bir dizi albüm oluşturan bir Windows Communication Foundation (WCF) hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="dcac4-105">Her albümün bir adı, bir fiyatı ve albüm parçalarının bir listesi vardır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="dcac4-106">Albüm parçalarının bir adı ve süresi var.</span><span class="sxs-lookup"><span data-stu-id="dcac4-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="dcac4-107">Hizmet tarafından döndürülen bilgiler, Windows Sunu Temeli (WPF) istemcisi tarafından sağlanan kullanıcı arabirimine (UI) otomatik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcac4-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="dcac4-109">Veri bağlama, bir veri kaynağının otomatik olarak kullanıcı arasına bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dcac4-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="dcac4-110">Bu, her kullanıcı arabirimi öğesini bir veri nesnesinden veya bir veri nesnesi dizisinden gelen verilerle programlı bir şekilde güncelleştirmenizi gerektirmediği için programlama modelini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="dcac4-111">Bir nesneyi tek bir UI öğesine veya diziye `ListBox`bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcac4-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="dcac4-112">Aşağıdaki kod, verileri bir Web-Posta öğesine nasıl bağlanınca `DataContext` gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="dcac4-113">`DataContext` Önceki örnekte, `grid` adlı `myPanel` düzen öğesi `GetAlbumList` yöntem tarafından döndürülen verilere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="dcac4-114">Öğelerin `DataContext` bağlama için kullanılan veri kaynağı hakkında üst öğelerinden bilgileri ve yol gibi bağlamanın diğer özelliklerini devralmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="dcac4-115">Kod satırı, sunucudaki veriler her güncelleştirilince yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="dcac4-116">Örneğin, pencere başharfe geçtiğinde ve yeni bir albüm eklendiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dcac4-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="dcac4-117">Aşağıdaki örnekxAML kodunda, `ListBox` `ItemsSource="{Binding }"`belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="dcac4-118">Bu, üst düzey Web Bilgisi öğesine bağlı verilerin de bu denetime (diğer bir şekilde Albümler dizisine) bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="dcac4-119">Buna ek `ItemTemplate="{StaticResource AlbumStyle}"` olarak, her öğe için kullanılacak veri `ListBox`şablonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="dcac4-120">Verilerin nasıl biçimlendirilmesi gerektiğini belirtmek için veri şablonları da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcac4-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="dcac4-121">Bu veri şablonları uygulamadaki diğer Kullanıcı Arabirimi öğeleri için yeniden kullanılabilir, avantajı veri şablonu tanımlanır ve tek bir yerde korunur.</span><span class="sxs-lookup"><span data-stu-id="dcac4-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="dcac4-122">Veri `AlbumStyle` şablonu yan yana iki `TextBlock`s ile bir ızgara ortaya koyar.</span><span class="sxs-lookup"><span data-stu-id="dcac4-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="dcac4-123">Biri Albümün adını, diğeri ise albümdeki Parça sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="dcac4-124">Aşağıdaki XAML kodu ikinci `ListBox`bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dcac4-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="dcac4-125">Kod için bir yol `ItemsSource`belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="dcac4-126">Bu, bu denetime bağlı verilerin üst düzey veriler değil, adı geçen `Tracks`üst düzey verilerin bir özelliği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="dcac4-127">Bu özellik, albüm içinde bulunan parça dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dcac4-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="dcac4-128">Buna ek olarak, farklı `DataTemplate` bir adlandırılmış `TrackStyle` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="dcac4-129">`TrackStyle` Şablonun düzeni `AlbumStyle` şablonunkine benzer, ancak `TextBlock`s farklı özelliklere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="dcac4-130">Bunun nedeni, iki şablonun farklı veri nesneleri ile kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dcac4-131">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="dcac4-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dcac4-132">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="dcac4-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dcac4-133">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dcac4-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dcac4-134">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dcac4-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dcac4-135">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="dcac4-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dcac4-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dcac4-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dcac4-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="dcac4-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dcac4-138">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="dcac4-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
