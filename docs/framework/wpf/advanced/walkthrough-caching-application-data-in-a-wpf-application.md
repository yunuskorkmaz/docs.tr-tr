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
ms.openlocfilehash: 1d00c222dabf446c7c102307c3b904d3f1ff4bca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314405"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma
Önbelleğe alma, verileri hızlı erişim için bellekte depolamanızı sağlar. Verileri yeniden erişildiğinde uygulamaları özgün kaynaktan almak yerine önbellekten veri alabilirsiniz. Bu, performansı ve ölçeklenebilirliği artırabilir. Ayrıca, önbelleğe alma, veri kaynağının geçici olarak devre dışı olduğunda yaptığı veri yok.

 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Önbelleğe almayı kullanmanızı sağlar sınıfını sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar. Bu sınıfların bulunan <xref:System.Runtime.Caching> ad alanı.

> [!NOTE]
>  <xref:System.Runtime.Caching> Ad alanı yeni [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Bu ad alanı yaptığı önbelleğe alma, tüm kullanılabilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar. Önceki sürümlerinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], önbelleğe yalnızca <xref:System.Web> ad alanı ve bu nedenle ASP.NET sınıfları bir bağımlılık gerekli.

 Bu izlenecek yol, kullanılabilir önbellek işlevini nasıl kullanacağınızı gösterir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] parçası olarak bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama. Bu izlenecek yolda, bir metin dosyasının içeriğini önbelleğe alın.

 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   WPF uygulama projesi oluşturma.

-   Bir başvuru eklemeyi [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].

-   Bir önbelleği başlatılıyor.

-   Bir metin dosyasının içeriğini içeren bir önbellek girişi ekleniyor.

-   Önbellek girişi için bir çıkarma İlkesi sağlama.

-   Önbelleğe alınan dosya yolunu izleme ve önbellek örneği hakkında bilgilendirmek için izlenen öğe değiştirir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

-   Microsoft Visual Studio 2010.

-   Az miktarda metin içeren bir metin dosyası. (Metin dosyasının içeriğini bir ileti kutusunda görüntülenir.) Bu kılavuzda gösterilen kodu aşağıdaki dosyasıyla çalıştığınız varsayılır:

     `c:\cache\cacheText.txt`

     Ancak, herhangi bir metin dosyası kullanın ve bu kılavuzda açıklanan kodu küçük değişiklik.

## <a name="creating-a-wpf-application-project"></a>WPF uygulama projesi oluşturma
 Bir WPF uygulaması projesi oluşturarak başlar.

#### <a name="to-create-a-wpf-application"></a>Bir WPF uygulaması oluşturmak için

1. Visual Studio’yu çalıştırın.

2. İçinde **dosya** menüsünde tıklatın **yeni**ve ardından **yeni proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

3. Altında **yüklü şablonlar**, kullanmak istediğiniz programlama dili seçin (**Visual Basic** veya **Visual C#**).

4. İçinde **yeni proje** iletişim kutusunda **WPF uygulaması**.

    > [!NOTE]
    >  Görmüyorsanız, **WPF uygulaması** şablon sürümünü hedefleme emin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] , WPF destekler. İçinde **yeni proje** iletişim kutusunda [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] listeden.

5. İçinde **adı** metin kutusunda, projeniz için bir ad girin. Örneğin, girdiğiniz **WPFCaching**.

6. Seçin **çözüm için dizin oluştur** onay kutusu.

7. **Tamam**'ı tıklatın.

     WPF Tasarımcısı açılır **tasarım** görüntüleyin ve MainWindow.xaml dosyayı görüntüler. Visual Studio oluşturur **Projem** klasörünü, Application.xaml dosyasını ve MainWindow.xaml dosyasını.

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>.NET Framework hedefleme ve önbelleğe alma derlemelere başvuru ekleme
 Varsayılan olarak, WPF uygulamaları hedef [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Kullanılacak <xref:System.Runtime.Caching> gerekir ad alanı WPF uygulamasında uygulama hedef [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (değil [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) ve ad alanına bir başvuru içermelidir.

 Bu nedenle, .NET Framework hedefi ve bir başvuru eklemek için sonraki adım olan <xref:System.Runtime.Caching> ad alanı.

> [!NOTE]
>  .NET Framework hedef değiştirmek için bu yordamı, Visual Basic projesinde ve Visual C# projesinde farklıdır.

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Hedef .NET Framework'ü Visual Basic'te değiştirmek için

1. İçinde **Çözüm Gezgini**proje adına sağ tıklayın ve ardından **özellikleri**.

     Uygulama için Özellikler penceresi görüntülenir.

2. Tıklayın **derleme** sekmesi.

3. Pencerenin alt kısmında tıklayın **Gelişmiş derleme seçenekleri...** .

     **Gelişmiş derleyici ayarları** iletişim kutusu görüntülenir.

4. İçinde **hedef Framework'ü (tüm yapılandırmaları)** listesinden [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Seçmeyin [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)

5. **Tamam**'ı tıklatın.

     **Hedef Framework değişikliği** iletişim kutusu görüntülenir.

6. İçinde **hedef Framework değişikliği** iletişim kutusu, tıklayın **Evet**.

     Proje kapatıldı ve sonra yeniden açılmasını.

7. Aşağıdaki adımları izleyerek önbelleğe alma derlemesine bir başvuru ekleyin:

    1.  İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **Başvuru Ekle**.

    2.  Seçin **.NET** sekmesinde `System.Runtime.Caching`ve ardından **Tamam**.

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>' % S'hedef .NET Framework'ü Visual C# projesinde değiştirmek için

1. İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **özellikleri**.

     Uygulama için Özellikler penceresi görüntülenir.

2. Tıklayın **uygulama** sekmesi.

3. İçinde **hedef Framework'ü** listesinden [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Seçmeyin **.NET Framework 4 istemci profili**.)

4. Aşağıdaki adımları izleyerek önbelleğe alma derlemesine bir başvuru ekleyin:

    1.  Sağ **başvuruları** klasörünü ve ardından **Başvuru Ekle**.

    2.  Seçin **.NET** sekmesinde `System.Runtime.Caching`ve ardından **Tamam**.

## <a name="adding-a-button-to-the-wpf-window"></a>WPF penceresine bir düğme ekleme
 Ardından bir düğme denetimi ekleyin ve düğmenin için bir olay işleyicisi oluşturun `Click` olay. Düğmeye tıkladığınızda, metin dosyasının içeriğini önbelleğe alınan görüntülenir ve bu nedenle, daha sonra kod ekleyeceksiniz.

#### <a name="to-add-a-button-control"></a>Bir düğme denetimi eklemek için

1. İçinde **Çözüm Gezgini**, MainWindow.xaml dosyasını açmak için çift tıklatın.

2. Gelen **araç kutusu**altında **ortak WPF denetimleri**, sürükleyin bir `Button` denetimini `MainWindow` penceresi.

3. İçinde **özellikleri** penceresinde `Content` özelliği `Button` denetimini **önbelleğe alma**.

## <a name="initializing-the-cache-and-caching-an-entry"></a>Önbellek başlatılıyor ve bir giriş önbelleğe alma
 Sonra aşağıdaki görevleri gerçekleştirmek için kod ekleyeceksiniz:

-   Önbellek sınıfının bir örneğini oluşturun — diğer bir deyişle, yeni bir örneğini <xref:System.Runtime.Caching.MemoryCache> nesne.

-   Önbellek kullandığını belirtirseniz bir <xref:System.Runtime.Caching.HostFileChangeMonitor> metin dosyasındaki değişiklikleri izlemek için nesne.

-   Metin dosyası okuma ve içeriğinin bir önbellek girdisi önbelleğe alır.

-   Önbelleğe alınan metin dosyasının içeriğini görüntüler.

#### <a name="to-create-the-cache-object"></a>Önbellek nesnesi oluşturmak için

1. MainWindow.xaml.cs veya MainWindow.Xaml.vb dosyasında bir olay işleyicisi oluşturmak için eklediğiniz düğmeyi çift tıklatın.

2. (Önce sınıf bildiriminin) dosyasının en üstüne aşağıdakileri ekleyin `Imports` (Visual Basic) veya `using` deyimleri (C#):

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. Olay işleyicisi, önbellek nesnesi oluşturmak için aşağıdaki kodu ekleyin:

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache> Bir bellek içi nesne önbelleği sağlayan yerleşik bir sınıfı.

4. Adlı bir önbellek girdisi içeriğini okumak için aşağıdaki kodu ekleyin `filecontents`:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. Önbellek girdisi adlı olup olmadığını denetlemek için aşağıdaki kodu ekleyin `filecontents` bulunmaktadır:

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     Belirtilen önbellek girdisi yok, metin dosyası okuma ve önbelleğe bir önbellek girdisi ekleyin.

6. İçinde `if/then` engelleme, yeni bir oluşturmak için aşağıdaki kodu ekleyin <xref:System.Runtime.Caching.CacheItemPolicy> önbellek girdisi 10 saniye sonra süresi dolar belirten bir nesne.

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     Çıkarma veya sona erme bilgi sağlanmazsa, varsayılan değer <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, önbellek girişlerinin başka bir deyişle, süresi dolmayacak tabanlı yalnızca mutlak bir saat. Yalnızca bellek baskısı olduğunda, bunun yerine, önbellek girişlerinin süresinin. En iyi uygulama, her zaman açık mutlak ya da bir olmaadığını sağlamanız gerekir.

7. İçinde `if/then` engelleme ve önceki adımda eklediğiniz kodun, izlemek ve metin dosyasının yolu koleksiyona eklemek istediğiniz dosya yolları için bir koleksiyon oluşturmak için aşağıdaki kodu ekleyin:

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    >  Kullanmak istediğiniz metin dosyasını değilse `c:\cache\cacheText.txt`, metin dosyasının bulunduğu kullanmak istediğiniz yolu belirtin.

8. Önceki adımda eklediğiniz koddan sonra yeni bir eklemek için aşağıdaki kodu ekleyin <xref:System.Runtime.Caching.HostFileChangeMonitor> değişiklik koleksiyonuna nesnesi için önbellek girdisi izler:

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor> Nesne metin dosyası yolu izler ve değişiklikleri meydana gelirse, önbellek bildirir. Dosyanın içeriği değişirse, bu örnekte, önbellek girişi sona erecek.

9. Önceki adımda eklediğiniz koddan metin dosyasının içeriğini okumak için aşağıdaki kodu ekleyin:

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     Önbellek girişinin süresi dolduğunda görmeniz mümkün olmayacaktır, tarih ve saat damgası eklenir.

10. Önbellek nesnesi olarak dosyanın içeriği eklemek için aşağıdaki kodu ekleyin önceki adımda eklediğiniz koddan sonra bir <xref:System.Runtime.Caching.CacheItem> örneği:

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     Nasıl önbellek girişi geçirerek çıkarılmasına ilişkin bilgileri belirtin <xref:System.Runtime.Caching.CacheItemPolicy> , daha önce oluşturduğunuz bir parametre olarak nesne.

11. Sonra `if/then` engelleme, önbelleğe alınan dosya içeriğini bir ileti kutusu içinde görüntülemek için aşağıdaki kodu ekleyin:

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. İçinde **derleme** menüsünde tıklayın **derleme WPFCaching** projenizi yapılandırmak için.

## <a name="testing-caching-in-the-wpf-application"></a>WPF uygulamasında önbelleğe almayı test etme
 Artık uygulamayı test edebilirsiniz.

#### <a name="to-test-caching-in-the-wpf-application"></a>WPF uygulamasında önbelleğe almayı test etme için

1. Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.

     `MainWindow` Penceresi görüntülenir.

2. Tıklayın **önbelleğe alma**.

     Önbelleğe alınmış içeriği metin dosyasından bir ileti kutusunda görüntülenir. Zaman damgası dosya çubuğunda dikkat edin.

3. İleti kutusunu kapatmak ve ardından **önbelleğe alma** yeniden.

     Zaman damgası değiştirilmez. Bu, önbelleğe alınmış içeriği görüntülendiğini gösterir.

4. 10 saniye veya daha fazla bekleyin ve ardından **önbelleğe alma** yeniden.

     Bu süre, yeni bir zaman damgası gösterilir. Bu ilke sona önbellek girişi sağlar ve yeni önbelleğe alınmış içerikleri görüntülendiğini gösterir.

5. Oluşturduğunuz bir metin dosyasını bir metin düzenleyicisinde açın. Henüz herhangi bir değişiklik yapmayın.

6. İleti kutusunu kapatmak ve ardından **önbelleğe alma** yeniden.

     Zaman damgası yeniden dikkat edin.

7. Metin dosyası için bir değişiklik yapın ve ardından dosyayı kaydedin.

8. İleti kutusunu kapatmak ve ardından **önbelleğe alma** yeniden.

     Bu ileti kutusu güncelleştirilmiş içerikleri metin dosyasını ve yeni bir zaman damgası içerir. Bu dosya değiştirildiğinde mutlak zaman aşımı süresi dolmamış olsa da ana bilgisayar dosya değişikliği izleme önbellek girdisi çıkarılacak olduğunu gösterir.

    > [!NOTE]
    >  20 saniye veya daha fazla dosyada değişiklik yapmak daha fazla süre izin vermek için çıkarma süresini artırabilir.

## <a name="code-example"></a>Kod Örneği
 Oluşturduğunuz proje için kod, bu kılavuzu tamamladıktan sonra aşağıdaki örneğe benzer.

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [.NET Framework Uygulamalarında Önbelleğe Alma](../../performance/caching-in-net-framework-applications.md)
