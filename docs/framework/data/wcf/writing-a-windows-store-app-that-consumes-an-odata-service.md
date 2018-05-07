---
title: Bir OData hizmetini kullanan bir Windows mağazası uygulaması yazma
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
ms.openlocfilehash: 105e7c06c6ca5253b931c1a8e60c6eee28e92cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a>Bir OData hizmetini kullanan bir Windows mağazası uygulaması yazma
Windows 8 uygulama yeni bir tür sunar: Windows mağazası uygulaması. Windows mağazası uygulamaları yepyeni bir görünümüne sahip, çeşitli aygıtlarda çalıştırın ve Windows Mağazası'üzerinde kullanılabilir hale getirilir. Bu konuda, bir OData hizmeti, özellikle NetFlix katalog OData hizmeti kullanan bir Windows mağazası uygulaması yazma açıklar. Windows mağazası uygulamaları hakkında daha fazla bilgi için lütfen okuyun [Windows mağazası uygulamaları ile çalışmaya başlama](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).  
  
## <a name="prerequisites"></a>Önkoşullar  
  
1.  [Microsoft Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [Microsoft Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [WCF Veri Hizmetleri](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a>Varsayılan Windows mağazası kılavuz uygulaması oluşturma  
  
1.  Yeni bir Windows mağazası kılavuz C# ve XAML kullanarak uygulaması oluşturun. OData.WindowsStore.NetflixDemo uygulama adı:  
  
     ![Yeni Proje iletişim kutusu](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")  
  
2.  Package.appxmanifest açın ve görünen adı metin kutusuna bir kolay ad girin. Bu, uygulama adı ile Windows 8 arama işlevini kullanılan belirtir.  
  
     ![Uygulama bildirim dosyasının](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")  
  
3.  Bir kolay ad girin \<uygulamaadı > App.xaml dosyasındaki öğesi. Bu, uygulama başlatıldığında görüntülenen uygulama adını ayarlar:  
  
     ![App.xaml dosyası](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")  
  
4.  Derleme ve uygulamayı başlatın. İlk uygulamanın giriş ekranı görürsünüz. Aşağıdaki ekran görüntüsünde varsayılan giriş ekranı görüntüler. Kullanılan görüntü projenin varlıklar klasöründe depolanır.  
  
     ![Varsayılan uygulama giriş ekranı](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")  
  
     Ardından uygulamayı görüntülenir.  
  
     ![Varsayılan uygulama](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")  
  
     Varsayılan uygulama sınıfları kümesi içinde SampleDataSource.cs tanımlar: SampleDataGroup ve her ikisi de türetilen SampleDataCommon, SampleDataItem kendisi BindableBase türetilir. SampleDataGroup ve SampleDataItem GridView varsayılan değere bağlıdır. SampleDataSource.cs NetflixDemo projedeki DataModel klasöründe bulunur. Uygulama gruplandırılmış bir koleksiyon görüntüler. Her Grup öğeleri, sırasıyla SampleDataGroup ve SampleDataItem, tarafından temsil edilen herhangi bir sayıda içerir. Önceki ekran görüntüsü, 1. grup başlığı ve tüm öğeleri birlikte görüntülenen grubunda adlı bir grup görebilirsiniz.  
  
     Ana uygulamanın GroupedItemsPage.xaml sayfasıdır. SampleDataSource.cs sınıfı tarafından oluşturulan örnek verileri görüntüleyen GridView içerir. GroupedItemsPage rootFrame.Navigate çağrıda App.xaml.cs tarafından yüklenir:  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     Bu örneğinin oluşturulması GroupedItemsPage neden olur ve onun LoadState yöntemi çağrılır. LoadState SampleDataGroup nesneler koleksiyonunu oluşturan oluşturulacak, statik SampleDataSource örnek neden olur. Her SampleDataGroup nesnesi SampleDataItem nesneler koleksiyonunu içerir. LoadState SampleDataGroup nesneler koleksiyonunu DefaultViewModel depolar:  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     DefaultViewModel sonra GridView bağlıdır. Veri bağlama yapılandırırken bu GroupedItemsPage.xaml dosyasında başvuruluyor.  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     CollectionViewSource gruplandırılmış koleksiyonları işlemek için bir proxy sunucu olarak kullanılır. Bağlama oluştuğunda GridView doldurmak için SampleDataGroup nesneleri toplulukta tekrarlanan.  ItemsPath özniteliği hangi özellik SampleDataItems bulmak için kullanmak üzere her SampleDataGroup nesnesinde içerdiği CollectionViewSource söyler. Bu durumda her SampleDataGroup nesnesi SampleDataItem nesneler TopItems koleksiyonunu içerir.  
  
     Netflix uygulamanın filmler türe göre gruplandırılır. Bu nedenle uygulama türler sayısını ve bu tarz içinde film listesini görüntüler.  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a>Netflix OData hizmetine hizmet Başvurusu Ekle  
  
1.  Netflix OData hizmeti yapılan her çağrı yapabilmeniz için önce bir hizmet Başvurusu Ekle gerekir. Çözüm Gezgini'nde projeye sağ tıklayın ve hizmet Başvurusu Ekle seçin...  
  
     ![Hizmet Başvurusu Ekle iletişim kutusu](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")  
  
2.  Adres çubuğundaki Netflix OData hizmeti URL'sini girin ve Git'i tıklatın. Hizmet başvurusu Netflix Namespace ayarlayın ve Tamam'ı tıklatın.  
  
     ![Hizmet başvurusu hatası eklemek](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")  
  
    > [!NOTE]
    >  Henüz yüklü değilse [Windows mağazası uygulamaları için WCF Veri Hizmetleri Araçları](http://go.microsoft.com/fwlink/p/?LinkId=266652), yukarıdaki bir gibi bir iletiyle istenir. Devam etmek için bağlantıdaki başvurulan araçları yükleyip gerekecektir.  
  
 Hizmet başvurusu kesinlikle oluşturur ekleme WCF Veri Hizmetleri Netflix OData hizmeti tarafından döndürülen OData ayrıştırmak için kullanacağı sınıfları belirtilmiş. Verileri oluşturulan OData istemci sınıflardan SampleDataSource.cs içinde tanımlanan bağlanabilirse sınıfları içine aktarmak ihtiyacımız şekilde SampleDataSource.cs içinde tanımlanan sınıflar için GridView bağlı olabilir.  Bunu yapmak için biz SampleDataSource.cs içinde tanımlanan veri modeli için bazı değişiklikler yapmanız gerekir.  
  
#### <a name="update-the-data-model-for-the-application"></a>Uygulama için veri modelini güncelleştir  
  
1.  Koddan SampleDataSource.cs var olan kodda yerine [bu gist](https://gist.github.com/3419288). Güncelleştirilmiş kod Netflix OData hizmeti bir sorgu gerçekleştirir ve türler (allGroups) ve her bir tarzını filmler listesi içindeki bir listesini dolduran bir LoadMovies yöntemi (SampleDataSource sınıfına) ekler. SampleDataGroup sınıfı bir tarzını temsil etmek için kullanılır ve SampleDataItem sınıfı bir filmi temsil etmek için kullanılır.  
  
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
  
     [Görev tabanlı zaman uyumsuz desen](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) 300 (Al) son (OrderByDescending) zaman uyumsuz olarak almak için kullanılan PG derecelendirilmiş (filmler Netflix geri yerlerde). Kod geri kalanı, OData akışına döndürülmedi varlıklardaki SimpleDataItems ve SimpleDataGroups oluşturur.  
  
     SampleDataSource sınıfı ayrıca bir basit search yöntemini uygular. Bu durumda, bir basit yüklenmiş filmler bellek içi arama yapar.  
  
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
  
     Ayrıca SampleDataSource.cs ExtensionMethods adlı bir sınıf tanımlanır. Bu uzantı yöntemlerin her biri bir OData sorgusu UI engellenmeden yürütmek SampleDataSource izin vermek için DOKUNUN desen kullanır. Örneğin, aşağıdaki kod DOKUNUN uygulamak için Task.Factory.FromAsync yöntemi kullanır.  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     Varsayılan uygulama olduğu gibi ana uygulamanın GroupedItemsPage sayfasıdır. Bu süre, Bununla birlikte, türe göre gruplandırılmış Netflix alınır filmler görüntüler.  LoadState yöntemi GroupedItemsPage örneği oluşturulduğunda çağrılır. LoadState oluşturulması statik SampleDataSource örnek daha önce bahsedildiği gibi Netflix OData hizmetine yapılan bir çağrı yaparak neden olur. LoadState türler (SampleDataGroup nesneler) koleksiyonunu DefaultViewModel depolar:  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     Daha önce açıklandığı gibi DefaultViewModel GridView veri bağlamak için kullanılır.  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a>Uygulamasının Windows aramasında katılmasına izin vermek için bir arama sözleşme Ekle  
  
1.  Bir arama sözleşme uygulamaya ekleyin. Bu uygulamayı Windows 8 arama deneyimiyle tümleştirmenize olanak sağlar. Arama sözleşme SearchResultsPage.xaml adı  
  
     ![Bir arama sözleşme Ekle](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")  
  
2.  SearchResultsPage.xaml.cs 58 satırının queryText Katıştırılmış tırnak kaldırarak değiştirin.  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  Arama sonuçları almak için SearchResultsPage.xaml.cs 81 satırında aşağıdaki iki kod satırı ekleyin.  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 Bir kullanıcı Windows arama, bir arama terimi türlerinde çağırır ve Netflix Demo uygulama simgesini arama çubuğunda dokunur SearchResultsPage LoadState yöntemi yürütülür. LoadState için gönderilen Gezinti parametre sorgu metni içerir. Sonraki Filter_SelectionChanged yöntemi çağırıldığı sonra SampleDataSource sınıfında Search yöntemini çağırır. Sonuçları döndürülen ve SearchResultsPage.xaml sayfasında görüntülenir.  
  
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
  
 Bir uygulama bakın, arama tümleştirme hakkında daha fazla bilgi için [arama: Windows 8 arama deneyim halinde entegre](http://go.microsoft.com/fwlink/p/?LinkId=266650).  
  
## <a name="run-the-application"></a>Uygulamayı çalıştırın  
 F5 tuşuna basarak uygulamayı başlatın. Uygulama başlatma sırasında yansımaları yüklemek için birkaç saniye sürer unutmayın. Ayrıca, ilk arama girişiminiz herhangi bir sonuç döndürmeyebilir. Gerçek dünya uygulamada hem de bu sorunların ile mücadele etmek istersiniz.  
  
 Uygulama Netflix OData hizmeti çağrıları, oluşturulan OData istemci sınıflarda verileri alır ve bu verileri bağlanabilir veri sınıfları (SampleDataSource, SampleDataGroup ve SampleDataItem) aktarır. GridView veri bağlamak için bu bağlanabilirse sınıfları kullanır. XAML databinding bkz: nasıl çalıştığı ile tanımıyorsanız [Grup öğeleri listesi veya kılavuz (C# / VB/C++ ve XAML kullanarak Windows mağazası uygulamaları) nasıl](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).
