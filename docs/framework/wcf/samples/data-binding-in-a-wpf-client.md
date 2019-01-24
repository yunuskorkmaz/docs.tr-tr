---
title: Windows Presentation Foundation İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 467a81c3f574137bc95390f70d6913a532da6ffe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626907"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="c4980-102">Windows Presentation Foundation İstemcisinde Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="c4980-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="c4980-103">Bu örnek, bir Windows Presentation Foundation (WPF) istemcisinde veri bağlama kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4980-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="c4980-104">Örnek, rastgele albümleri istemciye döndürmek için bir dizi oluşturur. bir Windows Communication Foundation (WCF) hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4980-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="c4980-105">Bir ad ve fiyat albüm parçaları listesini her albüm sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c4980-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="c4980-106">Albüm parçaları bir ad ve süresi vardır.</span><span class="sxs-lookup"><span data-stu-id="c4980-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="c4980-107">Hizmet tarafından döndürülen bilgileri otomatik olarak Windows Presentation Foundation (WPF) istemci tarafından sağlanan kullanıcı arabirimi (UI) bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4980-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4980-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c4980-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c4980-109">Veri bağlama, bir veri kaynağı için bir kullanıcı Arabirimi otomatik olarak bağlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4980-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="c4980-110">Program aracılığıyla her UI öğesi bir veri nesnesi ya da veri nesnelerinin bir dizisi verilerle güncelleştirmeniz gerekmez çünkü bu bir programlama modeli kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c4980-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="c4980-111">Tek bir kullanıcı Arabirimi öğesi veya bir dizi gibi birden fazla giriş alan bir denetim için bir nesne adlarınıza bağlayabileceğiniz bir `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c4980-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="c4980-112">Aşağıdaki kod, verilere bağlama işlemi gösterilmektedir `DataContext` UI öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4980-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="c4980-113">Önceki örnekte, `DataContext` için `grid` adlı Düzen öğesi `myPanel` tarafından döndürülen veriler için ayarlanmış `GetAlbumList` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4980-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="c4980-114">`DataContext` Kendi bağlamanın yolu gibi diğer özellikleri yanı sıra, bağlama için kullanılan veri kaynağı hakkında üst öğelerden bilgi öğelerin izin verir.</span><span class="sxs-lookup"><span data-stu-id="c4980-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="c4980-115">Sunucudaki veriler her güncelleştirildiğinde, kod satırının yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="c4980-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="c4980-116">Örneğin, pencerenin başlatıldığında ve yeni albümü eklendiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c4980-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="c4980-117">Aşağıdaki örnek kodda XAML, `ListBox` belirtir `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="c4980-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="c4980-118">Bu, en üst düzey bir kullanıcı Arabirimi öğesi için veriye bu denetimin (diğer bir deyişle, Albümler dizisi) bağlı olduğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4980-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="c4980-119">Ayrıca, `ItemTemplate="{StaticResource AlbumStyle}"` her öğe için kullanılacak veri şablonu belirtir `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c4980-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="c4980-120">Ayrıca, verileri nasıl biçimlendirilmesi gerektiğini belirtmek için veri şablonları da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4980-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="c4980-121">Uygulamadaki diğer kullanıcı Arabirimi öğeleri için şablonlar yeniden Bu avantajı veri şablonunun tanımlanır ve tek bir yerde tutulan verilerdir.</span><span class="sxs-lookup"><span data-stu-id="c4980-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="c4980-122">`AlbumStyle` İki içeren bir kılavuz düzenlediğinden veri şablonu `TextBlock`yan yana s.</span><span class="sxs-lookup"><span data-stu-id="c4980-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="c4980-123">Bir albümü adını albüm ve diğer iz sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4980-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="c4980-124">İkinci aşağıdaki XAML kodu oluşturur `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c4980-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="c4980-125">Kod için bir yol belirtir `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="c4980-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="c4980-126">Bu denetimin veriye değil en üst düzey veri ancak bir özelliğidir; adlı en üst düzey veri olduğunu gösterir `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="c4980-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="c4980-127">Bu özellik, parçaları albümü içinde yer alan dizi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c4980-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="c4980-128">Ayrıca, farklı bir `DataTemplate` adlı `TrackStyle` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c4980-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="c4980-129">Düzenini `TrackStyle` şablonudur benzer `AlbumStyle` şablonu, ancak `TextBlock`s farklı özelliklerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4980-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="c4980-130">Bu durum, iki şablonları, farklı veri nesneleriyle kullanılır çünkü.</span><span class="sxs-lookup"><span data-stu-id="c4980-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4980-131">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c4980-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c4980-132">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4980-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c4980-133">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4980-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c4980-134">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4980-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4980-135">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c4980-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c4980-136">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c4980-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c4980-137">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c4980-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4980-138">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c4980-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a><span data-ttu-id="c4980-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4980-139">See also</span></span>
