---
title: 'İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 7a4f84281da78068b5c6f7a505c8cb9225b31a39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma
Önbelleğe alma, verileri hızlı erişim için bellekte depolamanızı sağlar. Verileri yeniden erişildiğinde uygulamalar yerine özgün kaynak alma önbellekten veri alabilirsiniz. Bu, performans ve ölçeklenebilirlik iyileştirebilir. Ayrıca, veri kaynağı geçici olarak devre dışı olduğunda kullanılabilir hale getirir verileri önbelleğe alma.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Önbelleğe almayı kullanmanıza olanak sağlayan sınıflar sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar. Bu sınıfların bulunan <xref:System.Runtime.Caching> ad alanı.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching> Ad yeni [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Bu ad alanı yapar önbelleğe alma kullanılabilir tüm [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar. Önceki sürümlerinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], önbelleğe alma yalnızca kullanılabilir <xref:System.Web> ad alanı ve bu nedenle, bir bağımlılığı ASP.NET sınıfları gerekir.  
  
 Bu kılavuz, kullanılabilir önbellek işlevselliğinin nasıl kullanılacağını gösterir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] parçası olarak bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama. Bu kılavuzda, bir metin dosyasının içeriğini önbelleğe.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Bir WPF uygulaması projesi oluşturma.  
  
-   Bir başvuru ekleyerek [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
-   Bir önbellek başlatılıyor.  
  
-   Bir metin dosyasının içeriğini içeren bir önbellek girişi ekleme.  
  
-   Bir çıkarma ilkesi için önbellek girişi sağlama.  
  
-   Önbelleğe alınmış dosya yolunu izleme ve önbellek örneği hakkında bilgilendirmek için izlenen öğe değiştirir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Küçük miktarda metin içeren bir metin dosyası. (Metin dosyasının içeriğini bir ileti kutusu görüntülenir.) Örneklerde gösterilen kodu aşağıdaki dosyasıyla çalıştığınız varsayılır:  
  
     `c:\cache\cacheText.txt`  
  
     Ancak, herhangi bir metin dosyasını kullanın ve bu kılavuzda kod küçük değişiklikler yapmak.  
  
## <a name="creating-a-wpf-application-project"></a>Bir WPF uygulaması projesi oluşturma  
 Bir WPF uygulaması projesi oluşturarak başlar.  
  
#### <a name="to-create-a-wpf-application"></a>Bir WPF uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  İçinde **dosya** menüsünde tıklatın **yeni**ve ardından **yeni proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
3.  Altında **yüklü şablonlar**, kullanmak istediğiniz programlama dili seçin (**Visual Basic** veya **Visual C#**).  
  
4.  İçinde **yeni proje** iletişim kutusunda **WPF uygulaması**.  
  
    > [!NOTE]
    >  Görmüyorsanız, **WPF uygulaması** şablonu, bir sürümünü hedefleme emin olun [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WPF destekler. İçinde **yeni proje** iletişim kutusunda [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] listeden.  
  
5.  İçinde **adı** metin kutusuna, projeniz için bir ad girin. Örneğin, girebilirsiniz **WPFCaching**.  
  
6.  Seçin **çözüm için dizin oluştur** onay kutusu.  
  
7.  **Tamam**'ı tıklatın.  
  
     WPF Tasarımcısı açılır **tasarım** görüntülemek ve MainWindow.xaml dosyayı görüntüler. Visual Studio oluşturur **My proje** klasörü, Application.xaml dosyası ve MainWindow.xaml dosyası.  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>.NET Framework hedefleme ve önbelleğe alma derlemelerine başvuru ekleme  
 Varsayılan olarak, WPF uygulamalar hedef [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Kullanılacak <xref:System.Runtime.Caching> gerekir uygulama ad alanı bir WPF uygulamasında hedef [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (değil [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) ve ad alanı için bir başvuru içermelidir.  
  
 Bu nedenle, bir başvuru ekleyin ve .NET Framework hedef değiştirmek için sonraki adım olan <xref:System.Runtime.Caching> ad alanı.  
  
> [!NOTE]
>  .NET Framework hedef değiştirme yordamı, Visual Basic projesinde ve Visual C# projesinde farklıdır.  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Visual Basic'te .NET Framework hedef değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **özellikleri**.  
  
     Uygulama için Özellikler penceresi görüntülenir.  
  
2.  Tıklatın **derleme** sekmesi.  
  
3.  Pencerenin alt kısmındaki tıklatın **Gelişmiş derleme seçenekleri...** .  
  
     **Gelişmiş derleyici ayarları** iletişim kutusu görüntülenir.  
  
4.  İçinde **hedef Framework'ü (tüm yapılandırmaları)** listesinde [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Seçmeyin [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)  
  
5.  **Tamam**'ı tıklatın.  
  
     **Hedef Framework değişiklik** iletişim kutusu görüntülenir.  
  
6.  İçinde **hedef Framework değişiklik** iletişim kutusu, tıklatın **Evet**.  
  
     Proje kapatılır ve daha sonra yeniden açılacak.  
  
7.  Aşağıdaki adımları izleyerek önbelleğe alma derlemesine başvuru ekleyin:  
  
    1.  İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **Başvuru Ekle**.  
  
    2.  Seçin **.NET** sekmesine `System.Runtime.Caching`ve ardından **Tamam**.  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Visual C# projesinde hedef .NET Framework değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **özellikleri**.  
  
     Uygulama için Özellikler penceresi görüntülenir.  
  
2.  Tıklatın **uygulama** sekmesi.  
  
3.  İçinde **hedef framework** listesinde [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Seçmeyin **.NET Framework 4 istemci profili**.)  
  
4.  Aşağıdaki adımları izleyerek önbelleğe alma derlemesine başvuru ekleyin:  
  
    1.  Sağ **başvuruları** klasörünü ve ardından **Başvuru Ekle**.  
  
    2.  Seçin **.NET** sekmesine `System.Runtime.Caching`ve ardından **Tamam**.  
  
## <a name="adding-a-button-to-the-wpf-window"></a>WPF penceresi düğme ekleme  
 Ardından, işlemi düğme denetimi ekler ve düğmenin için bir olay işleyicisi oluşturun `Click` olay. Daha sonra Düğmeye tıkladığınızda, metin dosyasının içeriğini önbelleğe alınan görüntülenir ve böylece kod ekleyeceksiniz.  
  
#### <a name="to-add-a-button-control"></a>Düğme denetimi eklemek için  
  
1.  İçinde **Çözüm Gezgini**, açmak için MainWindow.xaml dosyasını çift tıklatın.  
  
2.  Gelen **araç**altında **genel WPF denetimlerinin**, sürükleyin bir `Button` denetimini `MainWindow` penceresi.  
  
3.  İçinde **özellikleri** penceresindeki ayarlayın `Content` özelliği `Button` denetimini **önbelleğe alma**.  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a>Önbelleği başlatılıyor ve bir giriş önbelleğe alma  
 Sonra aşağıdaki görevleri gerçekleştirmek için kod ekleyeceksiniz:  
  
-   Önbellek sınıfının bir örneğini oluşturma — diğer bir deyişle, yeni bir örneğini <xref:System.Runtime.Caching.MemoryCache> nesnesi.  
  
-   Önbellek kullandığını belirtirseniz bir <xref:System.Runtime.Caching.HostFileChangeMonitor> metin dosyasındaki değişiklikleri izlemek için nesne.  
  
-   Metin dosyası okuma ve içeriğinin bir önbellek girişi olarak önbelleğe.  
  
-   Önbelleğe alınan metin dosyasının içeriğini görüntüler.  
  
#### <a name="to-create-the-cache-object"></a>Önbellek nesnesi oluşturmak için  
  
1.  Olay işleyici MainWindow.xaml.cs veya MainWindow.Xaml.vb dosyasında oluşturmak için yeni eklenen düğmesine çift tıklayın.  
  
2.  (Önce sınıf bildirimi) dosyasının üst kısmında, aşağıdaki ekleyin `Imports` (Visual Basic) veya `using` deyimleri (C#):  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  Olay işleyicisi önbellek nesnesi örneği oluşturmak için aşağıdaki kodu ekleyin:  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <xref:System.Runtime.Caching.ObjectCache> Bir bellek içi nesne önbelleği sağlayan yerleşik bir sınıf bir sınıftır.  
  
4.  Adlı bir önbellek girişi içeriğini okumak için aşağıdaki kodu ekleyin `filecontents`:  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  Önbellek girdisi adlı olup olmadığını denetlemek için aşağıdaki kodu ekleyin `filecontents` bulunmaktadır:  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     Belirtilen önbellek girişi mevcut değilse, metin dosyası okuma ve önbelleğe bir önbellek girişi olarak ekleyin.  
  
6.  İçinde `if/then` engellemek, yeni bir oluşturmak için aşağıdaki kodu ekleyin <xref:System.Runtime.Caching.CacheItemPolicy> önbellek girişinin 10 saniye sonra süresi belirtir nesnesi.  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     Hiçbir çıkarma veya sona erme bilgileri verdiyse, varsayılan değer <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, önbellek girişlerinin başka bir deyişle, süresi dolmayacak tabanlı yalnızca mutlak bir saat. Bunun yerine, yalnızca bellek baskısı olduğunda önbellek girişlerinin süresinin. En iyi uygulama, mutlak veya kaplamayı sona erme her zaman açıkça sağlamalıdır.  
  
7.  İçinde `if/then` engelleme ve önceki adımda eklediğiniz kodun, izlemek ve metin dosyasının yolunu koleksiyona eklemek istediğiniz dosya yolları için bir koleksiyon oluşturmak için aşağıdaki kodu ekleyin:  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  Kullanmak istediğiniz metin dosyası olup olmadığını `c:\cache\cacheText.txt`, metin dosyasının bulunduğu kullanmak istediğiniz yolu belirtin.  
  
8.  Yeni bir eklemek için aşağıdaki kodu ekleyin önceki adımda eklediğiniz koddan <xref:System.Runtime.Caching.HostFileChangeMonitor> değişiklik koleksiyonuna nesnesi için önbellek girişi izler:  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <xref:System.Runtime.Caching.HostFileChangeMonitor> Nesne metin dosyanın yolu izler ve değişiklikleri oluştuğunda önbellek bildirir. Dosya içeriği değişirse bu örnekte, önbellek girişinin süresi dolar.  
  
9. Önceki adımda eklediğiniz koddan metin dosyasının içeriğini okumak için aşağıdaki kodu ekleyin:  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     Önbellek girişinin süresi dolduğunda görmeye olmayacaktır tarih ve saat damgası eklenir.  
  
10. Dosya içeriğini önbellek nesnesi olarak eklemek için aşağıdaki kodu ekleyin önceki adımda eklediğiniz koddan bir <xref:System.Runtime.Caching.CacheItem> örneği:  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     Nasıl önbellek girişi geçirerek çıkarılmasına hakkında bilgi belirtmek <xref:System.Runtime.Caching.CacheItemPolicy> parametre olarak daha önce oluşturduğunuz nesne.  
  
11. Sonra `if/then` engellemek, önbelleğe alınmış dosya içeriğini bir ileti kutusu içinde görüntülemek için aşağıdaki kodu ekleyin:  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. İçinde **yapı** menüsünde tıklatın **yapı WPFCaching** projenizi yapılandırmak için.  
  
## <a name="testing-caching-in-the-wpf-application"></a>WPF uygulamasında önbelleğe almayı test etme  
 Şimdi uygulamayı test edebilirsiniz.  
  
#### <a name="to-test-caching-in-the-wpf-application"></a>WPF uygulamasında önbelleğe alma işlemini sınamak için  
  
1.  Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.  
  
     `MainWindow` Penceresi görüntülenir.  
  
2.  Tıklatın **alma önbellek**.  
  
     Önbelleğe alınmış içeriği metin dosyasından bir ileti kutusu görüntülenir. Dosyanın zaman damgasını dikkat edin.  
  
3.  İleti kutusunu kapatın ve ardından **önbelleğe alma** yeniden **.**  
  
     Zaman damgası değiştirilmez. Bu, önbelleğe alınmış içeriği görüntülendiğini gösterir.  
  
4.  10 saniye veya daha fazla bekleyin ve ardından **önbelleğe alma** yeniden.  
  
     Bu yeni bir zaman damgası görüntülenir. Bu ilke sona önbellek girişi sağlar ve yeni önbelleğe alınmış içeriği görüntülendiğini gösterir.  
  
5.  Oluşturduğunuz metin dosyasını bir metin düzenleyicisinde açın. Herhangi bir değişiklik henüz yapmayın.  
  
6.  İleti kutusunu kapatın ve ardından **önbelleğe alma** yeniden **.**  
  
     Zaman damgası yeniden dikkat edin.  
  
7.  Metin dosyasına bir değişikliği yapın ve ardından dosyayı kaydedin.  
  
8.  İleti kutusunu kapatın ve ardından **önbelleğe alma** yeniden.  
  
     Bu ileti kutusu güncelleştirilmiş içerik metin dosyasını ve yeni bir zaman damgası içerir. Bu, hemen dosya değiştirildiğinde mutlak zaman aşımı süresi dolmamış olsa da ana bilgisayar dosyası değişiklik İzleyicisi önbellek girişi çıkarılacak olduğunu gösterir.  
  
    > [!NOTE]
    >  20 saniye veya daha fazla bilgi için dosyada değişiklik yapmak daha fazla süre izin vermek için çıkarma süresini artırabilir.  
  
## <a name="code-example"></a>Kod Örneği  
 Bu kılavuzu tamamladıktan sonra oluşturduğunuz proje kodunu aşağıdaki örnek benzer.  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [.NET Framework Uygulamalarında Önbelleğe Alma](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
