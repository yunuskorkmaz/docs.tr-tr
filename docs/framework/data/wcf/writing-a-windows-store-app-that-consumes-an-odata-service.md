---
title: "Bir OData hizmetini kullanan bir Windows mağazası uygulaması yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c1e2b9092abd54fd62848f58e2385bee5058553
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a><span data-ttu-id="65579-102">Bir OData hizmetini kullanan bir Windows mağazası uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="65579-102">Writing a Windows Store App that consumes an OData Service</span></span>
<span data-ttu-id="65579-103">Windows 8 uygulama yeni bir tür sunar: Windows mağazası uygulaması.</span><span class="sxs-lookup"><span data-stu-id="65579-103">Windows 8 introduces a new type of application: the Windows Store app.</span></span> <span data-ttu-id="65579-104">Windows mağazası uygulamaları yepyeni bir görünümüne sahip, çeşitli aygıtlarda çalıştırın ve Windows Mağazası'üzerinde kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="65579-104">Windows Store apps have a brand new look and feel, run on a variety of devices, and are made available on the Windows Store.</span></span> <span data-ttu-id="65579-105">Bu konuda, bir OData hizmeti, özellikle NetFlix katalog OData hizmeti kullanan bir Windows mağazası uygulaması yazma açıklar.</span><span class="sxs-lookup"><span data-stu-id="65579-105">This topic describes how to write a Windows Store app that consumes an OData service, specifically the NetFlix Catalog OData service.</span></span> <span data-ttu-id="65579-106">Windows mağazası uygulamaları hakkında daha fazla bilgi için lütfen okuyun [Windows mağazası uygulamaları ile çalışmaya başlama](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span><span class="sxs-lookup"><span data-stu-id="65579-106">For more information about Windows Store Apps, please read [Getting Started with Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="65579-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="65579-107">Prerequisites</span></span>  
  
1.  [<span data-ttu-id="65579-108">Microsoft Windows 8</span><span class="sxs-lookup"><span data-stu-id="65579-108">Microsoft Windows 8</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [<span data-ttu-id="65579-109">Microsoft Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="65579-109">Microsoft Visual Studio 2012</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [<span data-ttu-id="65579-110">WCF Veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="65579-110">WCF Data Services</span></span>](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a><span data-ttu-id="65579-111">Varsayılan Windows mağazası kılavuz uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="65579-111">Creating the default Windows Store Grid Application</span></span>  
  
1.  <span data-ttu-id="65579-112">Yeni bir Windows mağazası kılavuz C# ve XAML kullanarak uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="65579-112">Create a new Windows Store Grid Application using C# and XAML.</span></span> <span data-ttu-id="65579-113">OData.WindowsStore.NetflixDemo uygulama adı:</span><span class="sxs-lookup"><span data-stu-id="65579-113">Name the application OData.WindowsStore.NetflixDemo:</span></span>  
  
     <span data-ttu-id="65579-114">![Yeni Proje iletişim kutusu](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span><span class="sxs-lookup"><span data-stu-id="65579-114">![New Project Dialog](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span></span>  
  
2.  <span data-ttu-id="65579-115">Package.appxmanifest açın ve görünen adı metin kutusuna bir kolay ad girin.</span><span class="sxs-lookup"><span data-stu-id="65579-115">Open the Package.appxmanifest and enter a friendly name in the Display name text box.</span></span> <span data-ttu-id="65579-116">Bu, uygulama adı ile Windows 8 arama işlevini kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="65579-116">This specifies the application name used with the Windows 8 search functionality.</span></span>  
  
     <span data-ttu-id="65579-117">![Uygulama bildirim dosyasının](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span><span class="sxs-lookup"><span data-stu-id="65579-117">![Application manifest file](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span></span>  
  
3.  <span data-ttu-id="65579-118">Bir kolay ad girin \<uygulamaadı > App.xaml dosyasındaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="65579-118">Enter a friendly name in the \<AppName> element in the App.xaml file.</span></span> <span data-ttu-id="65579-119">Bu, uygulama başlatıldığında görüntülenen uygulama adını ayarlar:</span><span class="sxs-lookup"><span data-stu-id="65579-119">This sets the application name that is displayed when the application is launched:</span></span>  
  
     <span data-ttu-id="65579-120">![App.xaml dosyası](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span><span class="sxs-lookup"><span data-stu-id="65579-120">![App.xaml file](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span></span>  
  
4.  <span data-ttu-id="65579-121">Derleme ve uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="65579-121">Build and launch the application.</span></span> <span data-ttu-id="65579-122">İlk uygulamanın giriş ekranı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="65579-122">You first see the application’s splash screen.</span></span> <span data-ttu-id="65579-123">Aşağıdaki ekran görüntüsünde varsayılan giriş ekranı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65579-123">The screenshot below displays the default splash screen.</span></span> <span data-ttu-id="65579-124">Kullanılan görüntü projenin varlıklar klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="65579-124">The image used is stored in the project’s Assets folder.</span></span>  
  
     <span data-ttu-id="65579-125">![Varsayılan uygulama giriş ekranı](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span><span class="sxs-lookup"><span data-stu-id="65579-125">![The default app splash screen](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span></span>  
  
     <span data-ttu-id="65579-126">Ardından uygulamayı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65579-126">Then the application will be displayed.</span></span>  
  
     <span data-ttu-id="65579-127">![Varsayılan uygulama](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span><span class="sxs-lookup"><span data-stu-id="65579-127">![The default application](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span></span>  
  
     <span data-ttu-id="65579-128">Varsayılan uygulama sınıfları kümesi içinde SampleDataSource.cs tanımlar: SampleDataGroup ve her ikisi de türetilen SampleDataCommon, SampleDataItem kendisi BindableBase türetilir.</span><span class="sxs-lookup"><span data-stu-id="65579-128">The default application defines a set of classes in SampleDataSource.cs: SampleDataGroup and SampleDataItem, both of which are derived from SampleDataCommon, which itself is derived from BindableBase.</span></span> <span data-ttu-id="65579-129">SampleDataGroup ve SampleDataItem GridView varsayılan değere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65579-129">SampleDataGroup and SampleDataItem are bound to the default GridView.</span></span> <span data-ttu-id="65579-130">SampleDataSource.cs NetflixDemo projedeki DataModel klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="65579-130">SampleDataSource.cs is located in the DataModel folder within the NetflixDemo project.</span></span> <span data-ttu-id="65579-131">Uygulama gruplandırılmış bir koleksiyon görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65579-131">The application displays a grouped collection.</span></span> <span data-ttu-id="65579-132">Her Grup öğeleri, sırasıyla SampleDataGroup ve SampleDataItem, tarafından temsil edilen herhangi bir sayıda içerir.</span><span class="sxs-lookup"><span data-stu-id="65579-132">Each group contains any number of items, represented by SampleDataGroup and SampleDataItem, respectively.</span></span> <span data-ttu-id="65579-133">Önceki ekran görüntüsü, 1. grup başlığı ve tüm öğeleri birlikte görüntülenen grubunda adlı bir grup görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65579-133">In the previous screen shot you can see a group called Group Title 1 and all of the items in the group displayed together.</span></span>  
  
     <span data-ttu-id="65579-134">Ana uygulamanın GroupedItemsPage.xaml sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="65579-134">The main page of the application is GroupedItemsPage.xaml.</span></span> <span data-ttu-id="65579-135">SampleDataSource.cs sınıfı tarafından oluşturulan örnek verileri görüntüleyen GridView içerir.</span><span class="sxs-lookup"><span data-stu-id="65579-135">It contains a GridView that displays the sample data created by the SampleDataSource.cs class.</span></span> <span data-ttu-id="65579-136">GroupedItemsPage rootFrame.Navigate çağrıda App.xaml.cs tarafından yüklenir:</span><span class="sxs-lookup"><span data-stu-id="65579-136">The GroupedItemsPage is loaded by the App.xaml.cs in a call to rootFrame.Navigate:</span></span>  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     <span data-ttu-id="65579-137">Bu örneğinin oluşturulması GroupedItemsPage neden olur ve onun LoadState yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="65579-137">This causes the GroupedItemsPage to be instantiated and it’s LoadState method is called.</span></span> <span data-ttu-id="65579-138">LoadState SampleDataGroup nesneler koleksiyonunu oluşturan oluşturulacak, statik SampleDataSource örnek neden olur.</span><span class="sxs-lookup"><span data-stu-id="65579-138">LoadState causes the static SampleDataSource instance to be created, which creates a collection of SampleDataGroup objects.</span></span> <span data-ttu-id="65579-139">Her SampleDataGroup nesnesi SampleDataItem nesneler koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="65579-139">Each SampleDataGroup object contains a collection of SampleDataItem objects.</span></span> <span data-ttu-id="65579-140">LoadState SampleDataGroup nesneler koleksiyonunu DefaultViewModel depolar:</span><span class="sxs-lookup"><span data-stu-id="65579-140">LoadState stores the collection of SampleDataGroup objects in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="65579-141">DefaultViewModel sonra GridView bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65579-141">The DefaultViewModel is then bound to the GridView.</span></span> <span data-ttu-id="65579-142">Veri bağlama yapılandırırken bu GroupedItemsPage.xaml dosyasında başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="65579-142">This is referenced in the GroupedItemsPage.xaml file when configuring the data binding.</span></span>  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     <span data-ttu-id="65579-143">CollectionViewSource gruplandırılmış koleksiyonları işlemek için bir proxy sunucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65579-143">The CollectionViewSource is used as a proxy for handling grouped collections.</span></span> <span data-ttu-id="65579-144">Bağlama oluştuğunda GridView doldurmak için SampleDataGroup nesneleri toplulukta tekrarlanan.</span><span class="sxs-lookup"><span data-stu-id="65579-144">When binding occurs, it iterates through the collection of SampleDataGroup objects to populate the GridView.</span></span>  <span data-ttu-id="65579-145">ItemsPath özniteliği hangi özellik SampleDataItems bulmak için kullanmak üzere her SampleDataGroup nesnesinde içerdiği CollectionViewSource söyler.</span><span class="sxs-lookup"><span data-stu-id="65579-145">The ItemsPath attribute tells the CollectionViewSource what property on each SampleDataGroup object to use to find the SampleDataItems it contains.</span></span> <span data-ttu-id="65579-146">Bu durumda her SampleDataGroup nesnesi SampleDataItem nesneler TopItems koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="65579-146">In this case each SampleDataGroup object contains a TopItems collection of SampleDataItem objects.</span></span>  
  
     <span data-ttu-id="65579-147">Netflix uygulamanın filmler türe göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="65579-147">For the Netflix application, movies are grouped by genre.</span></span> <span data-ttu-id="65579-148">Bu nedenle uygulama türler sayısını ve bu tarz içinde film listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65579-148">So the application displays a number of genres and a list of movies within that genre.</span></span>  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a><span data-ttu-id="65579-149">Netflix OData hizmetine hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="65579-149">Add a Service Reference to the Netflix OData Service</span></span>  
  
1.  <span data-ttu-id="65579-150">Netflix OData hizmeti yapılan her çağrı yapabilmeniz için önce bir hizmet Başvurusu Ekle gerekir.</span><span class="sxs-lookup"><span data-stu-id="65579-150">Before we can make any calls to the Netflix OData service we need to add a service reference.</span></span> <span data-ttu-id="65579-151">Çözüm Gezgini'nde projeye sağ tıklayın ve hizmet Başvurusu Ekle seçin...</span><span class="sxs-lookup"><span data-stu-id="65579-151">Right-click the project in the Solution Explorer and select Add Service Reference…</span></span>  
  
     <span data-ttu-id="65579-152">![Hizmet Başvurusu Ekle iletişim kutusu](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span><span class="sxs-lookup"><span data-stu-id="65579-152">![Add Service Reference Dialog](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span></span>  
  
2.  <span data-ttu-id="65579-153">Adres çubuğundaki Netflix OData hizmeti URL'sini girin ve Git'i tıklatın.</span><span class="sxs-lookup"><span data-stu-id="65579-153">Enter the URL for the Netflix OData service in the Address bar and click Go.</span></span> <span data-ttu-id="65579-154">Hizmet başvurusu Netflix Namespace ayarlayın ve Tamam'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="65579-154">Set the Namespace of the service reference to Netflix and click OK.</span></span>  
  
     <span data-ttu-id="65579-155">![Hizmet başvurusu hatası eklemek](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span><span class="sxs-lookup"><span data-stu-id="65579-155">![Add Service Reference Error](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65579-156">Henüz yüklü değilse [Windows mağazası uygulamaları için WCF Veri Hizmetleri Araçları](http://go.microsoft.com/fwlink/p/?LinkId=266652), yukarıdaki bir gibi bir iletiyle istenir.</span><span class="sxs-lookup"><span data-stu-id="65579-156">If you have not yet installed [WCF Data Services Tools for Windows Store Apps](http://go.microsoft.com/fwlink/p/?LinkId=266652), you will be prompted with a message such as the one above.</span></span> <span data-ttu-id="65579-157">Devam etmek için bağlantıdaki başvurulan araçları yükleyip gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="65579-157">You will need to download and install the tools referenced in the link to continue.</span></span>  
  
 <span data-ttu-id="65579-158">Hizmet başvurusu kesinlikle oluşturur ekleme WCF Veri Hizmetleri Netflix OData hizmeti tarafından döndürülen OData ayrıştırmak için kullanacağı sınıfları belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="65579-158">Adding a service reference generates strongly typed classes that WCF Data Services will use to parse the OData returned by the Netflix OData service.</span></span> <span data-ttu-id="65579-159">Verileri oluşturulan OData istemci sınıflardan SampleDataSource.cs içinde tanımlanan bağlanabilirse sınıfları içine aktarmak ihtiyacımız şekilde SampleDataSource.cs içinde tanımlanan sınıflar için GridView bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="65579-159">The classes defined in SampleDataSource.cs can be bound to the GridView so we need to transfer the data from the generated OData client classes into the bindable classes defined in SampleDataSource.cs.</span></span>  <span data-ttu-id="65579-160">Bunu yapmak için biz SampleDataSource.cs içinde tanımlanan veri modeli için bazı değişiklikler yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="65579-160">In order to do this, we need to make some changes to the data model defined in SampleDataSource.cs.</span></span>  
  
#### <a name="update-the-data-model-for-the-application"></a><span data-ttu-id="65579-161">Uygulama için veri modelini güncelleştir</span><span class="sxs-lookup"><span data-stu-id="65579-161">Update the data model for the application</span></span>  
  
1.  <span data-ttu-id="65579-162">Koddan SampleDataSource.cs var olan kodda yerine [bu gist](https://gist.github.com/3419288).</span><span class="sxs-lookup"><span data-stu-id="65579-162">Replace the existing code in SampleDataSource.cs with the code from [this gist](https://gist.github.com/3419288).</span></span> <span data-ttu-id="65579-163">Güncelleştirilmiş kod Netflix OData hizmeti bir sorgu gerçekleştirir ve türler (allGroups) ve her bir tarzını filmler listesi içindeki bir listesini dolduran bir LoadMovies yöntemi (SampleDataSource sınıfına) ekler.</span><span class="sxs-lookup"><span data-stu-id="65579-163">The updated code adds a LoadMovies method (to the SampleDataSource class)  that performs a query against the Netflix OData service and populates a list of genres (allGroups) and within each genre a list of movies.</span></span> <span data-ttu-id="65579-164">SampleDataGroup sınıfı bir tarzını temsil etmek için kullanılır ve SampleDataItem sınıfı bir filmi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65579-164">The SampleDataGroup class is used to represent a genre and the SampleDataItem class is used to represent a movie.</span></span>  
  
    ```csharp  
    public static async void LoadMovies()  
    {  
        IEnumerable<Title> titles = await ((DataServiceQuery<Title>)Context.Titles  
            .Expand("Genres,AudioFormats,AudioFormats/Language,Awards,Cast")  
            .Where(t => t.Rating == "PG")  
            .OrderByDescending(t => t.ReleaseYear)  
            .Take(300)).ExecuteAsync();  
  
        foreach (Title title in titles)  
        {  
            foreach (Genre netflixGenre in title.Genres)  
            {  
                SampleDataGroup genre = GetGroup(netflixGenre.Name);  
                if (genre == null)  
                {  
                    genre = new SampleDataGroup(netflixGenre.Name, netflixGenre.Name, String.Empty, title.BoxArt.LargeUrl, String.Empty);  
                    Instance.AllGroups.Add(genre);  
                }  
                var content = new StringBuilder();  
                // Write additional things to content here if you want them to display in the item detail.  
                genre.Items.Add(new SampleDataItem(title.Id, title.Name, String.Format("{0}rnrn{1} ({2})", title.Synopsis, title.Rating, title.ReleaseYear), title.BoxArt.HighDefinitionUrl ?? title.BoxArt.LargeUrl, "Description", content.ToString()));  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="65579-165">[Görev tabanlı zaman uyumsuz desen](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) 300 (Al) son (OrderByDescending) zaman uyumsuz olarak almak için kullanılan PG derecelendirilmiş (filmler Netflix geri yerlerde).</span><span class="sxs-lookup"><span data-stu-id="65579-165">The [Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) is used to asynchronously get 300 (Take) recent (OrderByDescending) PG-rated (Where) movies back from Netflix.</span></span> <span data-ttu-id="65579-166">Kod geri kalanı, OData akışına döndürülmedi varlıklardaki SimpleDataItems ve SimpleDataGroups oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65579-166">The rest of the code constructs SimpleDataItems and SimpleDataGroups from the entities that were returned in the OData feed.</span></span>  
  
     <span data-ttu-id="65579-167">SampleDataSource sınıfı ayrıca bir basit search yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="65579-167">The SampleDataSource class also implements a simple search method.</span></span> <span data-ttu-id="65579-168">Bu durumda, bir basit yüklenmiş filmler bellek içi arama yapar.</span><span class="sxs-lookup"><span data-stu-id="65579-168">In this case, it does a simple in-memory search of the loaded movies.</span></span>  
  
    ```csharp  
    public static IEnumerable<SampleDataItem> Search(string searchString)  
    {  
            var regex = new Regex(searchString, RegexOptions.CultureInvariant | RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace);  
            return Instance.AllGroups  
                .SelectMany(g => g.Items)  
                .Where(m => regex.IsMatch(m.Title) || regex.IsMatch(m.Subtitle))  
                    .Distinct(new SampleDataItemComparer());  
    }  
    ```  
  
     <span data-ttu-id="65579-169">Ayrıca SampleDataSource.cs ExtensionMethods adlı bir sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="65579-169">Also in SampleDataSource.cs a class called ExtensionMethods is defined.</span></span> <span data-ttu-id="65579-170">Bu uzantı yöntemlerin her biri bir OData sorgusu UI engellenmeden yürütmek SampleDataSource izin vermek için DOKUNUN desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="65579-170">Each of these extension methods uses the TAP pattern to allow the SampleDataSource to execute an OData query without blocking the UI.</span></span> <span data-ttu-id="65579-171">Örneğin, aşağıdaki kod DOKUNUN uygulamak için Task.Factory.FromAsync yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="65579-171">For example, the following code uses the Task.Factory.FromAsync method to implement TAP.</span></span>  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     <span data-ttu-id="65579-172">Varsayılan uygulama olduğu gibi ana uygulamanın GroupedItemsPage sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="65579-172">As in the default application, the main page of the application is GroupedItemsPage.</span></span> <span data-ttu-id="65579-173">Bu süre, Bununla birlikte, türe göre gruplandırılmış Netflix alınır filmler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65579-173">This time, however, it displays the movies retrieved from Netflix grouped by genre.</span></span>  <span data-ttu-id="65579-174">LoadState yöntemi GroupedItemsPage örneği oluşturulduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="65579-174">When the GroupedItemsPage is instantiated, its LoadState method is called.</span></span> <span data-ttu-id="65579-175">LoadState oluşturulması statik SampleDataSource örnek daha önce bahsedildiği gibi Netflix OData hizmetine yapılan bir çağrı yaparak neden olur.</span><span class="sxs-lookup"><span data-stu-id="65579-175">LoadState causes the static SampleDataSource instance to be created, making a call to the Netflix OData service as discussed previously.</span></span> <span data-ttu-id="65579-176">LoadState türler (SampleDataGroup nesneler) koleksiyonunu DefaultViewModel depolar:</span><span class="sxs-lookup"><span data-stu-id="65579-176">LoadState stores the collection of genres (SampleDataGroup objects) in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="65579-177">Daha önce açıklandığı gibi DefaultViewModel GridView veri bağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65579-177">As described previously, the DefaultViewModel is then used to bind the data to the GridView.</span></span>  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a><span data-ttu-id="65579-178">Uygulamasının Windows aramasında katılmasına izin vermek için bir arama sözleşme Ekle</span><span class="sxs-lookup"><span data-stu-id="65579-178">Add a search contract to allow the application to participate in Windows search</span></span>  
  
1.  <span data-ttu-id="65579-179">Bir arama sözleşme uygulamaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="65579-179">Add a search contract to the application.</span></span> <span data-ttu-id="65579-180">Bu uygulamayı Windows 8 arama deneyimiyle tümleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="65579-180">This allows the application to integrate with the Windows 8 search experience.</span></span> <span data-ttu-id="65579-181">Arama sözleşme SearchResultsPage.xaml adı</span><span class="sxs-lookup"><span data-stu-id="65579-181">Name the search contract SearchResultsPage.xaml</span></span>  
  
     <span data-ttu-id="65579-182">![Bir arama sözleşme Ekle](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span><span class="sxs-lookup"><span data-stu-id="65579-182">![Add a search contract](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span></span>  
  
2.  <span data-ttu-id="65579-183">SearchResultsPage.xaml.cs 58 satırının queryText Katıştırılmış tırnak kaldırarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="65579-183">Modify line 58 of SearchResultsPage.xaml.cs by removing the embedded quotes around queryText.</span></span>  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  <span data-ttu-id="65579-184">Arama sonuçları almak için SearchResultsPage.xaml.cs 81 satırında aşağıdaki iki kod satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="65579-184">Insert the following two lines of code at line 81 in SearchResultsPage.xaml.cs to retrieve the search results.</span></span>  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 <span data-ttu-id="65579-185">Bir kullanıcı Windows arama, bir arama terimi türlerinde çağırır ve Netflix Demo uygulama simgesini arama çubuğunda dokunur SearchResultsPage LoadState yöntemi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="65579-185">When a user invokes Windows search, types in a search term and then touches the Netflix Demo app icon in the search bar, the LoadState method of the SearchResultsPage is executed.</span></span> <span data-ttu-id="65579-186">LoadState için gönderilen Gezinti parametre sorgu metni içerir.</span><span class="sxs-lookup"><span data-stu-id="65579-186">The navigation parameter sent to LoadState contains the query text.</span></span> <span data-ttu-id="65579-187">Sonraki Filter_SelectionChanged yöntemi çağırıldığı sonra SampleDataSource sınıfında Search yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="65579-187">Next the Filter_SelectionChanged method is called which then calls the Search method on the SampleDataSource class.</span></span> <span data-ttu-id="65579-188">Sonuçları döndürülen ve SearchResultsPage.xaml sayfasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65579-188">The results are returned and displayed in the SearchResultsPage.xaml page.</span></span>  
  
```csharp  
/// <summary>  
        /// Invoked when a filter is selected using the ComboBox in snapped view state.  
        /// </summary>  
        /// <param name="sender">The ComboBox instance.</param>  
        /// <param name="e">Event data describing how the selected filter was changed.</param>  
        void Filter_SelectionChanged(object sender, SelectionChangedEventArgs e)  
        {  
            // Determine what filter was selected  
            var selectedFilter = e.AddedItems.FirstOrDefault() as Filter;  
            if (selectedFilter != null)  
            {  
                // Mirror the results into the corresponding Filter object to allow the  
                // RadioButton representation used when not snapped to reflect the change  
                selectedFilter.Active = true;  
  
                // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                var searchValue = (string)this.DefaultViewModel["QueryText"];  
                this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
  
                // Ensure results are found  
                object results;  
                ICollection resultsCollection;  
                if (this.DefaultViewModel.TryGetValue("Results", out results) &&  
                    (resultsCollection = results as ICollection) != null &&  
                    resultsCollection.Count != 0)  
                {  
                    VisualStateManager.GoToState(this, "ResultsFound", true);  
                    return;  
                }  
            }  
  
            // Display informational text when there are no search results.  
            VisualStateManager.GoToState(this, "NoResultsFound", true);  
        }  
```  
  
 <span data-ttu-id="65579-189">Bir uygulama bakın, arama tümleştirme hakkında daha fazla bilgi için [arama: Windows 8 arama deneyim halinde entegre](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span><span class="sxs-lookup"><span data-stu-id="65579-189">For more information on integrating search into an application see, [Search: integrating into the Windows 8 search experience](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span></span>  
  
## <a name="run-the-application"></a><span data-ttu-id="65579-190">Uygulamayı çalıştırın</span><span class="sxs-lookup"><span data-stu-id="65579-190">Run the application</span></span>  
 <span data-ttu-id="65579-191">F5 tuşuna basarak uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="65579-191">Launch the application by pressing F5.</span></span> <span data-ttu-id="65579-192">Uygulama başlatma sırasında yansımaları yüklemek için birkaç saniye sürer unutmayın.</span><span class="sxs-lookup"><span data-stu-id="65579-192">Note that it will take a few seconds to load the images upon application launch.</span></span> <span data-ttu-id="65579-193">Ayrıca, ilk arama girişiminiz herhangi bir sonuç döndürmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="65579-193">Also, your first search attempt may not return any results.</span></span> <span data-ttu-id="65579-194">Gerçek dünya uygulamada hem de bu sorunların ile mücadele etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="65579-194">In a real-world application, you would want to deal with both of these issues.</span></span>  
  
 <span data-ttu-id="65579-195">Uygulama Netflix OData hizmeti çağrıları, oluşturulan OData istemci sınıflarda verileri alır ve bu verileri bağlanabilir veri sınıfları (SampleDataSource, SampleDataGroup ve SampleDataItem) aktarır.</span><span class="sxs-lookup"><span data-stu-id="65579-195">The application calls the Netflix OData service, receives the data in the generated OData client classes and then transfers that data to bindable data classes (SampleDataSource, SampleDataGroup, and SampleDataItem).</span></span> <span data-ttu-id="65579-196">GridView veri bağlamak için bu bağlanabilirse sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="65579-196">It uses these bindable classes to bind the data to the GridView.</span></span> <span data-ttu-id="65579-197">XAML databinding bkz: nasıl çalıştığı ile tanımıyorsanız [Grup öğeleri listesi veya kılavuz (C# / VB/C++ ve XAML kullanarak Windows mağazası uygulamaları) nasıl](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span><span class="sxs-lookup"><span data-stu-id="65579-197">If you are unfamiliar with how XAML databinding works see [How to group items in a list or grid (Windows Store apps using C#/VB/C++ and XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span></span>
