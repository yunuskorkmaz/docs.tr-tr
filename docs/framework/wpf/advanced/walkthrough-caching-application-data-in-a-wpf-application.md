---
title: Önbellek uygulaması verileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: b7d999f94e2f2ae410a16e537d51c0f890def4e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728066"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma
Önbelleğe alma, verileri hızlı erişim için bellekte depolamanıza olanak sağlar. Verilere yeniden erişildiğinde, uygulamalar verileri özgün kaynaktan almak yerine önbellekten alabilir. Bu, performansı ve ölçeklenebilirliği iyileştirebilir. Ayrıca, veri kaynağı geçici olarak kullanılamadığında önbelleğe alma verilerin kullanılabilir olmasını sağlar.

 .NET Framework, .NET Framework uygulamalarda önbelleğe alma kullanmanıza olanak sağlayan sınıflar sağlar. Bu sınıflar <xref:System.Runtime.Caching> ad alanında bulunur.

> [!NOTE]
> <xref:System.Runtime.Caching> ad alanı .NET Framework 4 ' te yenidir. Bu ad alanı, önbelleğe alma işlemini tüm .NET Framework uygulamaları için kullanılabilir hale getirir. .NET Framework önceki sürümlerinde, önbelleğe alma yalnızca <xref:System.Web> ad alanında kullanılabilir ve bu nedenle ASP.NET sınıflarında bir bağımlılık gerektirdi.

 Bu izlenecek yol, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamasının bir parçası olarak .NET Framework bulunan önbelleğe alma işlevselliğinin nasıl kullanılacağını gösterir. İzlenecek yolda, bir metin dosyasının içeriğini önbelleğe alırsınız.

 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

- WPF uygulaması projesi oluşturma.

- .NET Framework 4 ' e başvuru ekleniyor.

- Önbellek başlatılıyor.

- Bir metin dosyasının içeriğini içeren bir önbellek girişi ekleme.

- Önbellek girdisi için çıkarma ilkesi sağlama.

- Önbelleğe alınan dosyanın yolunu izleme ve izlenen öğedeki değişikliklerle ilgili önbellek örneğine bildirme.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Visual Studio 2010.

- Az miktarda metin içeren bir metin dosyası. (Metin dosyasının içeriğini bir ileti kutusunda görüntüleyirsiniz.) İzlenecek yolda gösterilen kod, aşağıdaki dosyayla çalıştığınızı varsayar:

     `c:\cache\cacheText.txt`

     Ancak, herhangi bir metin dosyasını kullanabilir ve bu kılavuzda kodda küçük değişiklikler yapabilirsiniz.

## <a name="creating-a-wpf-application-project"></a>WPF uygulama projesi oluşturma
 Bir WPF uygulama projesi oluşturarak başlayacaksınız.

#### <a name="to-create-a-wpf-application"></a>WPF uygulaması oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde **Yeni**' ye ve ardından **Yeni proje**' ye tıklayın.

     **Yeni proje** iletişim kutusu görüntülenir.

3. **Yüklü şablonlar**altında kullanmak istediğiniz programlama dilini (**Visual Basic** veya **görsel C#** ) seçin.

4. **Yeni proje** Iletişim kutusunda **WPF uygulaması**' nı seçin.

    > [!NOTE]
    > **WPF uygulama** şablonunu GÖRMÜYORSANıZ, WPF 'yi destekleyen .NET Framework bir sürümünü hedeflediğinizden emin olun. **Yeni proje** iletişim kutusunda listeden .NET Framework 4 ' ü seçin.

5. **Ad** metin kutusuna projeniz için bir ad girin. Örneğin, **WPFCaching**girebilirsiniz.

6. **Çözüm için dizin oluştur** onay kutusunu seçin.

7. **Tamam**'ı tıklatın.

     WPF Tasarımcısı **Tasarım** görünümünde açılır ve MainWindow. xaml dosyasını görüntüler. Visual Studio **My projem** klasörünü, Application. xaml dosyasını ve MainWindow. xaml dosyasını oluşturur.

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>.NET Framework hedefleme ve önbelleğe alma derlemelerine başvuru ekleme
 WPF uygulamaları varsayılan olarak .NET Framework 4 Istemci profilini hedefler. Bir WPF uygulamasında <xref:System.Runtime.Caching> ad alanını kullanmak için, uygulamanın .NET Framework 4 ' ü (.NET Framework 4 Istemci profilini değil) hedeflemesi ve ad alanına bir başvuru içermesi gerekir.

 Bu nedenle, sonraki adım .NET Framework hedefini değiştirmek ve <xref:System.Runtime.Caching> ad alanına bir başvuru eklemektir.

> [!NOTE]
> .NET Framework hedefini değiştirme yordamı, bir Visual Basic projesinde ve bir görsel C# projede farklıdır.

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Visual Basic içindeki hedef .NET Framework değiştirmek için

1. **Çözüm Gezgini**' nde, proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

     Uygulamanın Özellikler penceresi görüntülenir.

2. **Derle** sekmesine tıklayın.

3. Pencerenin alt kısmında **Gelişmiş derleme seçenekleri...** öğesine tıklayın.

     **Gelişmiş derleyici ayarları** iletişim kutusu görüntülenir.

4. **Hedef Framework (tüm konfigürasyonlar)** listesinde .NET Framework 4 ' ü seçin. (.NET Framework 4 Istemci profili seçmeyin.)

5. **Tamam**'ı tıklatın.

     **Hedef Framework değişikliği** iletişim kutusu görüntülenir.

6. **Hedef çerçeve değişimi** Iletişim kutusunda **Evet**' e tıklayın.

     Proje kapatılıp yeniden açıldı.

7. Aşağıdaki adımları izleyerek önbelleğe alma derlemesine bir başvuru ekleyin:

    1. **Çözüm Gezgini**, projenin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

    2. **.Net** sekmesini seçin, `System.Runtime.Caching`öğesini seçin ve ardından **Tamam**' a tıklayın.

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Görsel C# projedeki hedef .NET Framework değiştirmek için

1. **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

     Uygulamanın Özellikler penceresi görüntülenir.

2. **Uygulama** sekmesine tıklayın.

3. **Hedef çerçeve** listesinde .NET Framework 4 ' ü seçin. ( **.NET Framework 4 Istemci profili**seçmeyin.)

4. Aşağıdaki adımları izleyerek önbelleğe alma derlemesine bir başvuru ekleyin:

    1. **Başvurular** klasörüne sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

    2. **.Net** sekmesini seçin, `System.Runtime.Caching`öğesini seçin ve ardından **Tamam**' a tıklayın.

## <a name="adding-a-button-to-the-wpf-window"></a>WPF penceresine düğme ekleme
 Ardından, düğme denetimi ekleyeceksiniz ve düğmenin `Click` olayı için bir olay işleyicisi oluşturacaksınız. Daha sonra, düğmesine tıkladığınızda metin dosyasının içeriği önbelleğe alınır ve görüntülenir.

#### <a name="to-add-a-button-control"></a>Düğme denetimi eklemek için

1. **Çözüm Gezgini**, açmak için MainWindow. xaml dosyasına çift tıklayın.

2. **Araç kutusundan**, **ortak WPF denetimleri**altında, bir `Button` denetimini `MainWindow` penceresine sürükleyin.

3. **Özellikler** penceresinde, **önbelleği almak**için `Button` denetiminin `Content` özelliğini ayarlayın.

## <a name="initializing-the-cache-and-caching-an-entry"></a>Önbelleği başlatma ve bir girişi önbelleğe alma
 Daha sonra, aşağıdaki görevleri gerçekleştirmek için kodu ekleyeceksiniz:

- Cache sınıfının bir örneğini oluşturun — diğer bir deyişle, yeni bir <xref:System.Runtime.Caching.MemoryCache> nesnesi örnekleyebilirsiniz.

- Önbelleğin metin dosyasındaki değişiklikleri izlemek için bir <xref:System.Runtime.Caching.HostFileChangeMonitor> nesnesi kullanacağını belirtin.

- Metin dosyasını okuyun ve içeriğini önbellek girişi olarak önbelleğe alın.

- Önbelleğe alınmış metin dosyasının içeriğini görüntüleyin.

#### <a name="to-create-the-cache-object"></a>Önbellek nesnesi oluşturmak için

1. MainWindow.xaml.cs veya MainWindow. xaml. vb dosyasında bir olay işleyicisi oluşturmak için yeni eklediğiniz düğmeye çift tıklayın.

2. Dosyanın üst kısmında (Sınıf bildiriminden önce) aşağıdaki `Imports` (Visual Basic) veya `using` (C#) deyimlerini ekleyin:

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. Olay işleyicisinde, önbellek nesnesinin örneğini oluşturmak için aşağıdaki kodu ekleyin:

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache> sınıfı, bellek içi nesne önbelleği sağlayan yerleşik bir sınıftır.

4. `filecontents`adlı bir önbellek girişinin içeriğini okumak için aşağıdaki kodu ekleyin:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. `filecontents` adlı önbellek girişinin var olup olmadığını denetlemek için aşağıdaki kodu ekleyin:

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     Belirtilen önbellek girdisi yoksa, metin dosyasını okuyup önbelleğe bir önbellek girişi olarak eklemeniz gerekir.

6. `if/then` bloğunda, önbellek girdisinin 10 saniye sonra süresinin dolacağını belirten yeni bir <xref:System.Runtime.Caching.CacheItemPolicy> nesnesi oluşturmak için aşağıdaki kodu ekleyin.

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     Çıkarma veya sona erme bilgisi sağlanmazsa, varsayılan değer <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, bu da önbellek girişlerinin yalnızca mutlak bir süre temelinde süresi dolmayacağı anlamına gelir. Bunun yerine, önbellek girişlerinin süreleri yalnızca bellek baskısı olduğunda sona erer. En iyi uygulama olarak her zaman kesin bir şekilde mutlak veya kayan bir süre sağlamanız gerekir.

7. `if/then` bloğu içinde ve önceki adımda eklediğiniz kodu izleyerek, izlemek istediğiniz dosya yolları için bir koleksiyon oluşturmak ve metin dosyasının yolunu koleksiyona eklemek için aşağıdaki kodu ekleyin:

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > Kullanmak istediğiniz metin dosyası `c:\cache\cacheText.txt`değilse, metin dosyasının kullanmak istediğiniz yolu belirtin.

8. Önceki adımda eklediğiniz kodu izleyerek, önbellek girdisi için değişiklik izleyicileri koleksiyonuna yeni bir <xref:System.Runtime.Caching.HostFileChangeMonitor> nesnesi eklemek için aşağıdaki kodu ekleyin:

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor> nesnesi, metin dosyasının yolunu izler ve değişiklik oluşursa önbelleğe bildirir. Bu örnekte, dosyanın içeriği değişirse önbellek girişinin kullanım süreleri dolacak.

9. Önceki adımda eklediğiniz kodu izleyerek, metin dosyasının içeriğini okumak için aşağıdaki kodu ekleyin:

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     Tarih ve saat zaman damgası eklenir, böylece önbellek girişinin süresinin ne zaman dolacağını görebileceksiniz.

10. Önceki adımda eklediğiniz kodu izleyerek, dosyanın içeriğini bir <xref:System.Runtime.Caching.CacheItem> örneği olarak Cache nesnesine eklemek için aşağıdaki kodu ekleyin:

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     Daha önce oluşturduğunuz <xref:System.Runtime.Caching.CacheItemPolicy> nesnesini bir parametre olarak geçirerek önbellek girişinin nasıl çıkarılamadığı hakkında bilgi belirtirsiniz.

11. `if/then` bloğundan sonra, önbelleğe alınmış dosya içeriğini bir ileti kutusunda göstermek için aşağıdaki kodu ekleyin:

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. **Build** menüsünde, projenizi derlemek Için **WPFCaching oluştur** ' a tıklayın.

## <a name="testing-caching-in-the-wpf-application"></a>WPF uygulamasında önbelleğe almayı test etme
 Artık uygulamayı test edebilirsiniz.

#### <a name="to-test-caching-in-the-wpf-application"></a>WPF uygulamasında önbelleğe almayı sınamak için

1. Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.

     `MainWindow` penceresi görüntülenir.

2. **Önbelleği al**' a tıklayın.

     Metin dosyasındaki önbelleğe alınmış içerik bir ileti kutusunda görüntülenir. Dosyadaki zaman damgasına dikkat edin.

3. İleti kutusunu kapatın ve ardından önbelleği yeniden **Al** ' ı tıklatın.

     Zaman damgası değiştirilmez. Bu, önbelleğe alınan içeriğin görüntülendiğini belirtir.

4. 10 saniye veya daha fazla bekleyip önbelleği yeniden **Al** ' a tıklayın.

     Bu kez yeni bir zaman damgası görüntülenir. Bu, ilkenin önbellek girişinin sona ereceğini ve önbelleğe alınmış yeni içeriğin görüntülendiğini belirtir.

5. Bir metin düzenleyicisinde, oluşturduğunuz metin dosyasını açın. Henüz herhangi bir değişiklik yapmayın.

6. İleti kutusunu kapatın ve ardından önbelleği yeniden **Al** ' ı tıklatın.

     Zaman damgasına yeniden dikkat edin.

7. Metin dosyasında bir değişiklik yapıp dosyayı kaydedin.

8. İleti kutusunu kapatın ve ardından önbelleği yeniden **Al** ' ı tıklatın.

     Bu ileti kutusunda metin dosyasındaki güncelleştirilmiş içerik ve yeni bir zaman damgası bulunur. Bu, mutlak zaman aşımı süresi dolmasa bile, ana bilgisayar dosyası değişiklik izleyicisinin, dosyayı değiştirdiğiniz sırada önbellek girdisini hemen kaldırdığını gösterir.

    > [!NOTE]
    > Dosyada değişiklik yapmanız için daha fazla zaman tanımak üzere çıkarma süresini 20 saniye veya daha fazla artırabilirsiniz.

## <a name="code-example"></a>Kod Örneği
 Bu yönergeyi tamamladıktan sonra, oluşturduğunuz projenin kodu aşağıdaki örneğe benzer olacaktır.

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [.NET Framework Uygulamalarında Önbelleğe Alma](../../performance/caching-in-net-framework-applications.md)
