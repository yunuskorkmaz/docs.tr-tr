---
title: .NET Core'u kullanarak BIR REST istemcisi oluşturma
description: Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 5796df2d2fd8c4d9aaca783d720448c90858c067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156863"
---
# <a name="rest-client"></a>REST istemcisi

Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir. Öğreneceksin:

* .NET Core CLI'nin temelleri.
* C# Language özelliklerine genel bakış.
* NuGet ile bağımlılıkları yönetme
* HTTP İletişim
* JSON bilgilerinin işlenmesi
* Yapılandırmayı Özniteliklerle yönetme.

GitHub'daki bir REST hizmetine HTTP İstekleri veren bir uygulama oluşturursunuz. Bilgileri JSON formatında okuyacak ve bu JSON paketini C# nesnelerine dönüştüreceksiniz. Son olarak, C# nesneleri ile nasıl çalışacağınızı görürsünüz.

Bu öğretici birçok özelliği vardır. Onları teker teker inşa edelim.

Bu konu için son [örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte takip etmeyi tercih ederseniz, indirebilirsiniz. İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

## <a name="prerequisites"></a>Önkoşullar

.NET çekirdeğini çalıştırmak için makinenizi ayarlamanız gerekir. Yükleme yönergelerini [.NET Çekirdek İndirmeler](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Linux, macOS veya Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicisini yüklemeniz gerekir. Aşağıdaki açıklamalar, açık kaynak kodlu, çapraz platform düzenleyicisi olan [Visual Studio Code'u](https://code.visualstudio.com/)kullanabilmiştir. Ancak, hangi araçları ile rahat kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı Oluştur

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Bunu geçerli dizini yapın. Konsol penceresine aşağıdaki komutu girin:

```dotnetcli
dotnet new console --name WebApiClient
```

Bu, temel bir "Hello World" uygulaması için başlangıç dosyalarını oluşturur. Proje adı "WebApiClient"dır. Bu yeni bir proje olduğu için, bağımlılıkların hiçbiri yerinde değildir. İlk çalıştırma .NET Core çerçevesini karşıdan yükler, geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet paket yöneticisini çalıştıracaktır.

Değişiklik yapmaya başlamadan önce, `dotnet run` uygulamanızı çalıştırmak için komut istemine[(nota bakınız)](#dotnet-restore-note)yazın. `dotnet run`ortamınız `dotnet restore` bağımlılıkları eksikse otomatik olarak gerçekleştirir. Uygulamanızın `dotnet build` yeniden oluşturulması gerekiyorsa da gerçekleştirir.
İlk kurulumunuzdan sonra, yalnızca `dotnet restore` çalıştırmanız veya projeniz için anlamlı `dotnet build` olduğunda yapmanız gerekir.

## <a name="adding-new-dependencies"></a>Yeni Bağımlılıklar Ekleme

.NET Core'un temel tasarım hedeflerinden biri .NET yüklemesinin boyutunu en aza indirmektir. Bir uygulamanın bazı özellikleri için ek kitaplıklara ihtiyacı varsa, bu\*bağımlılıkları C# projenize (.csproj) dosyanıza eklersiniz. Örneğin, uygulamanızın JSON yanıtlarını `System.Runtime.Serialization.Json` işleme sayılabilmesi için paketi eklemeniz gerekir.

Bu uygulama için `System.Runtime.Serialization.Json` pakete ihtiyacınız olacak. Aşağıdaki [.NET CLI](../../core/tools/dotnet-add-package.md) komutunu çalıştırarak projenize ekleyin:

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Web İstekleri Yapma

Artık web'den veri almaya başlamaya hazırsınız. Bu uygulamada, [GitHub API'sinden](https://developer.github.com/v3/)gelen bilgileri okuyacaksınız. [.NET Foundation](https://www.dotnetfoundation.org/) şemsiyesi altındaki projelerle ilgili bilgileri okuyalım. Projeler hakkında bilgi almak için GitHub API'sine istekte bulunarak işe başlarsınız. Kullanacağınız bitiş noktası: <https://api.github.com/orgs/dotnet/repos>. Bu projelerle ilgili tüm bilgileri almak istediğinizden, http get isteği kullanırsınız.
Tarayıcınız http get isteklerini de kullanır, böylece hangi bilgileri alacağınızı ve işlediğinizi görmek için bu URL'yi tarayıcınıza yapıştırabilirsiniz.

<xref:System.Net.Http.HttpClient> Web istekleri yapmak için sınıfı kullanırsınız. Tüm modern .NET API'leri gibi, <xref:System.Net.Http.HttpClient> uzun süredir devam eden API'leri için yalnızca uyumlu yöntemleri destekler.
Bir async yöntemi yaparak başlayın. Uygulamanın işlevselliğini oluştururken uygulamayı doldurursunuz. Proje dizininizdeki dosyayı `program.cs` açarak ve `Program` sınıfa aşağıdaki yöntemi ekleyerek başlayın:

```csharp
private static async Task ProcessRepositories()
{
}
```

C# derleyicisinin `using` <xref:System.Threading.Tasks.Task> türünü tanıması için `Main` yönteminizin en üstüne bir yönerge eklemeniz gerekir:

```csharp
using System.Threading.Tasks;
```

Bu noktada projenizi oluşturursanız, herhangi `await` bir işleç içermediğinden ve eşzamanlı olarak çalışacağından, bu yöntem için oluşturulan bir uyarı alırsınız. Bunu şimdilik görmezden gelin; yöntemi doldururken `await` işleçler eklersiniz.

Ardından, `namespace` ifadede tanımlanan ad alanını varsayılanından `ConsoleApp` ' `WebAPIClient`' a yeniden adlandırın Daha sonra bu `repo` ad alanında bir sınıf tanımlayacağız.

Ardından, bu `Main` yöntemi çağırmak için yöntemi güncelleştirin. Yöntem `ProcessRepositories` bir görevi döndürür ve bu görev bitmeden programdan çıkmamalısınız. Bu nedenle, imzayı `Main`değiştirmeniz gerekir. `async` Değiştiriciyi ekleyin ve dönüş türünü `Task`' le değiştirin Daha sonra, yöntemin gövdesinde, bir `ProcessRepositories`çağrı ekleyin. Bu `await` yöntem çağrısına anahtar kelime ekleyin:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Şimdi, hiçbir şey yapmaz bir program var, ama eşzamanlı yok. Hadi geliştirelim.

İlk olarak web'den veri alabilen bir nesneye ihtiyacınız vardır; bunu yapmak <xref:System.Net.Http.HttpClient> için a kullanabilirsiniz. Bu nesne isteği ve yanıtları işler. `Program` *Program.cs* dosyasının içindeki sınıfta bu tür tek bir örneği anında seçin.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

Yönteme `ProcessRepositories` geri dönelim ve ilk sürümünü dolduralım:

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

Bunun derlemesi için dosyanın en üstüne iki yeni `using` yönerge eklemeniz gerekir:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Bu ilk sürüm, dotnet vakıf kuruluşu altındaki tüm depoların listesini okumak için bir web isteği yapar. (.NET Foundation için gitHub kimliği 'dotnet'tir). İlk birkaç satır bu <xref:System.Net.Http.HttpClient> istek için ayarlayın. İlk olarak, GitHub JSON yanıtlarını kabul etmek üzere yapılandırılmıştır.
Bu biçim sadece JSON olduğunu. Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üstbilgisi ekler. Bu iki üstbilgi GitHub sunucu kodu tarafından denetlenir ve GitHub'dan bilgi almak için gereklidir.

Yapılandırıldıktan <xref:System.Net.Http.HttpClient>sonra bir web isteği yapar ve yanıtı alırsınız. Bu ilk sürümde, <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemini kullanın. Bu kolaylık yöntemi, web isteği yapan bir görev başlatır ve istek döndüğünde yanıt akışını okur ve içeriği akıştan ayıklar. Yanıtın gövdesi bir <xref:System.String>. Görev tamamlandığında dize kullanılabilir.

Bu yöntemin son iki satırı bu görevi bekliyor ve ardından yanıtı konsola yazdırın.
Uygulamayı oluşturun ve çalıştırın. Şimdi bir `ProcessRepositories` `await` işleç içerdiğinden, yapı uyarısı artık gitti. JSON biçimlendirilmiş metnin uzun bir ekranını görürsünüz.

## <a name="processing-the-json-result"></a>JSON Sonucunun İşlenmesi

Bu noktada, bir web sunucusundan yanıt almak ve bu yanıtta bulunan metni görüntülemek için kodu yazdınız. Sonra, bu JSON yanıtını C# nesnelerine dönüştürelim.

Sınıf <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> nesneleri JSON'a serileştirir ve JSON'u nesnelere ayırıyor. GitHub API'sinden döndürülen JSON nesnesini `repo` temsil edecek bir sınıf tanımlayarak başlayın:

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

Yukarıdaki kodu 'repo.cs' adlı yeni bir dosyaya koyun. Sınıfın bu sürümü JSON verilerini işlemek için en basit yolu temsil eder. Sınıf adı ve üye adı, C# kurallarını takip etmek yerine JSON paketinde kullanılan adlarla eşleşir. Bunu daha sonra bazı yapılandırma öznitelikleri sağlayarak düzelteceksiniz. Bu sınıf JSON serileştirme ve deserialization başka önemli bir özelliği gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değildir.
JSON serileştiricisi, kullanılan sınıf türüne dahil olmayan bilgileri yoksayacaktır.
Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.

Şimdi türü oluşturduğunuza göre, onu deserialize edelim.

Daha sonra, JSON'u C# nesnelerine dönüştürmek için serileştiriciyi kullanırsınız. Aramayı <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> yönteminizde `ProcessRepositories` aşağıdaki üç satırla değiştirin:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Yeni bir ad alanı kullanıyorsanız, bu nedenle dosyanın en üstüne de eklemeniz gerekir:

```csharp
using System.Text.Json;
```

Şimdi yerine kullandığınıza <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> dikkat <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>edin. Serializer kaynağı olarak bir dize yerine bir akış kullanır. Önceki kod snippet'in ikinci satırında kullanılan C# dilinin birkaç özelliğini açıklayalım. İlk bağımsız <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> değişken `await` bir ifadedir. (Diğer iki parametre isteğe bağlıdır ve kod snippet atlanır.) Bekleyen ifadeler, şimdiye kadar bunları yalnızca atama deyiminin bir parçası olarak görmüş olsanız bile, kodunuzda hemen hemen her yerde görünebilir. Yöntem `Deserialize` *geneldir,* bu da JSON metninden ne tür nesnelerin oluşturulması gerektiğine yönelik tür bağımsız değişkenleri sağlamanız gerektiği anlamına gelir. Bu örnekte, başka bir genel `List<Repository>`nesne olan bir , <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Sınıf `List<>` nesnelerin bir koleksiyon depolar. Tür bağımsız `List<>`değişkeni, . JSON metni repo nesnelerinin bir koleksiyonunu temsil eder, bu nedenle tür bağımsız değişkeni `Repository`.

Bu bölümü neredeyse bitirdin. Artık JSON'u C# nesnelerine dönüştürdüğünüze göre, her deponun adını gösterelim. Aşağıdaki satırları değiştirin:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

aşağıdakilerle birlikte:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Uygulamayı derle ve çalıştır. .NET Foundation'ın bir parçası olan depoların adlarını yazdırır.

## <a name="controlling-serialization"></a>Serileştirmeyi Denetleme

Daha fazla özellik eklemeden önce, `name` özniteliği `[JsonPropertyName]` kullanarak özelliği ele alalım. repo.cs alan bildiriminde `name` aşağıdaki değişiklikleri yapın:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Öznitelik `[JsonPropertyName]` kullanmak `using` için, yönergelere <xref:System.Text.Json.Serialization> ad alanı eklemeniz gerekir:

```csharp
using System.Text.Json.Serialization;
```

Bu değişiklik, program.cs her deponun adını yazan kodu değiştirmeniz gerektiği anlamına gelir:

```csharp
Console.WriteLine(repo.Name);
```

Eşlemeleri doğru yaptığınızdan emin olmak için uygulayın. `dotnet run` Önceki yle aynı çıktıyı görmelisiniz.

Yeni özellikler eklemeden önce bir değişiklik daha yapalım. Yöntem `ProcessRepositories` async iş yapabilir ve depoların bir koleksiyon döndürebilir. Bu yöntemden `List<Repository>` döndürelim ve bilgileri yazan kodu `Main` yönteme taşıyalım.

Sonucu nesnelerin `ProcessRepositories` listesi olan bir görevi döndürmek `Repository` için imzayı değiştirin:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Sonra, sadece JSON yanıtı işledikten sonra depoları döndürün:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Derleyici, bu `Task<T>` yöntemi ' olarak `async`işaretlediğiniz için geri dönüş için nesne oluşturur
Daha sonra, `Main` bu sonuçları yakalar ve konsola her depo adı yazar şekilde yöntemi değiştirelim. Yönteminiz `Main` şimdi şuna benziyor:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Daha Fazla Bilgi Okuma

Bunu, GitHub API'sinden gönderilen JSON paketindeki birkaç özelliği daha işleyerek bitirelim. Her şeyi kapmak istemeyeceksiniz, ancak birkaç özellik eklemek C# dilinin birkaç özelliğini daha gösterir.

`Repository` Sınıf tanımına birkaç basit tür daha ekleyerek başlayalım. Bu özellikleri bu sınıfa ekleyin:

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

Bu özellikler, dize türünden (JSON paketlerinin içerdiği) hedef türe yerleşik dönüşümlere sahiptir. Türü <xref:System.Uri> sizin için yeni olabilir. Bir URI'yi veya bu durumda bir URL'yi temsil eder. `Uri` JSON paketi hedef türüne dönüştürmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum `int` oluşturur.

Bunları ekledikten sonra, bu `Main` öğeleri görüntülemek için yöntemi güncelleştirin:

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

Son adım olarak, son itme işlemi için bilgileri ekleyelim. Bu bilgiler JSON yanıtında bu şekilde biçimlendirilir:

```json
2016-02-08T21:27:00Z
```

Bu biçim, standart .NET <xref:System.DateTime> biçimlerinin hiçbirini izlemez. Bu nedenle, özel bir dönüştürme yöntemi yazmanız gerekir. Ayrıca büyük olasılıkla ham dize `Repository` sınıfın kullanıcılarına maruz istemiyorum. Öznitelikler de bunu denetlemeye yardımcı olabilir. İlk olarak, `public` `Repository` sınıfınızdaki tarih ve saatin dize temsilini `LastPush` `readonly` ve döndürülen tarihi temsil eden biçimlendirilmiş bir dize döndüren bir özelliği tanımla:

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

Az önce tanımladığımız yeni yapılara bakalım. Özellik, `LastPush` `get` erişimci için *ifade gövdeli* bir üye kullanılarak tanımlanır. Erişimci `set` yok. Erişime erişim amacını atlayarak C#'da salt okunur özelliği nasıl tanımladığınızdır. *read-only* `set` (Evet, C#'da *yalnızca yazma* özellikleri oluşturabilirsiniz, ancak değerleri sınırlıdır.) Yöntem, <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> bir dizeyi ayrıştırır ve sağlanan tarih biçimini kullanarak bir <xref:System.DateTime> nesne oluşturur ve `DateTime` kullanan `CultureInfo` nesneye ek meta veriler ekler. Ayrışdırıcı işlemi başarısız olursa, özellik erişimcisi bir özel durum atar.

Kullanmak <xref:System.Globalization.CultureInfo.InvariantCulture>için, <xref:System.Globalization> `using` aşağıdaki yönergelere ad alanını eklemeniz `repo.cs`gerekir:

```csharp
using System.Globalization;
```

Son olarak, konsola bir çıkış deyimi daha ekleyin ve bu uygulamayı yeniden oluşturmaya ve çalıştırmaya hazır sınız:

```csharp
Console.WriteLine(repo.LastPush);
```

Sürümünüz artık [bitmiş örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)eşleşmelidir.

## <a name="conclusion"></a>Sonuç

Bu öğretici, web isteklerini nasıl yapacağınızı, sonucu ayrıştırmayı ve bu sonuçların özelliklerini nasıl görüntülediğinizi göstermiştir. Ayrıca projenize bağımlılık olarak yeni paketler eklediniz. C# dilinin nesne yönelimli teknikleri destekleyen bazı özelliklerini gördünüz.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
