---
title: .NET Core kullanarak REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 9478966598a9aaa1e9f592b72afce8f878a38abf
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964416"
---
# <a name="rest-client"></a>REST istemcisi

## <a name="introduction"></a>Giriş

Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir. Şunları öğrenirsiniz:

* .NET Core komut satırı arabirimi (CLı) temelleri.
* C# Dil özelliklerine genel bakış.
* NuGet ile bağımlılıkları yönetme
* HTTP Iletişimleri
* JSON bilgilerini işleme
* Yapılandırmayı özniteliklerle yönetme.

GitHub 'da REST hizmetine HTTP Istekleri veren bir uygulama oluşturacaksınız. JSON biçiminde bilgileri okuyacaksınız ve bu JSON paketini C# nesnelerine dönüştürürsünüz. Son olarak, C# nesneleriyle nasıl çalışacaksınız görürsünüz.

Bu öğreticide birçok özellik vardır. Bunları birer birer oluşturalım.

Bu konuyla ilgili [son örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte izlemeyi tercih ediyorsanız, indirebilirsiniz. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Prerequisites

Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/)kullanır. Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı oluşturma

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizini oluşturun. Konsol penceresine aşağıdaki komutu girin:

```dotnetcli
dotnet new console --name WebApiClient
```

Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur. Proje adı "WebApiClient" dir. Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core Framework 'ü indirir, bir geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet Paket Yöneticisi 'ni çalıştırır.

Değişiklik yapmaya başlamadan önce, uygulamanızı çalıştırmak için komut isteminde `dotnet run` ([bkz. Note](#dotnet-restore-note)) yazın. `dotnet run`, ortamınızda bağımlılıklar eksik ise `dotnet restore` otomatik olarak gerçekleştirilir. Uygulamanızın yeniden oluşturulması gerekiyorsa `dotnet build` de gerçekleştirir.
İlk kurulumdan sonra, yalnızca projeniz için anlamlı olduğunda `dotnet restore` veya `dotnet build` çalıştırmanız gerekir.

## <a name="adding-new-dependencies"></a>Yeni bağımlılıklar ekleniyor

.NET Core için önemli tasarım amaçlarından biri, .NET yüklemesinin boyutunu en aza indirmektir. Bir uygulamanın bazı özellikleri için ek kitaplıklar gerekiyorsa, bu bağımlılıkları C# proje (\*. csproj) dosyanıza eklersiniz. Örneğimizde, uygulamanızın JSON yanıtlarını işleyebilmesi için `System.Runtime.Serialization.Json` paketini eklemeniz gerekir.

Bu uygulama için `System.Runtime.Serialization.Json` pakete ihtiyacınız olacak. Aşağıdaki [.net CLI](../../core/tools/dotnet-add-package.md) komutunu çalıştırarak projenize ekleyin:

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Web Istekleri yapma

Artık Web 'den veri almaya başlamaya hazırsınız. Bu uygulamada, [GITHUB API](https://developer.github.com/v3/)'sindeki bilgileri okuyacaksınız. [.Net Foundation](https://www.dotnetfoundation.org/) şemsiye kapsamındaki projelerle ilgili bilgileri okuyalim. Projeler hakkındaki bilgileri almak için GitHub API 'sine istek yaparak başlayacaksınız. Kullanacağınız uç nokta: <https://api.github.com/orgs/dotnet/repos>. Bu projelerle ilgili tüm bilgileri almak istiyorsunuz, bu nedenle bir HTTP GET isteği kullanacaksınız.
Tarayıcınız ayrıca HTTP GET isteklerini kullanır; bu nedenle, hangi bilgileri almak ve işlemek istediğinizi görmek için bu URL 'YI tarayıcınıza yapıştırabilirsiniz.

Web istekleri yapmak için <xref:System.Net.Http.HttpClient> sınıfını kullanırsınız. Tüm modern .NET API 'Leri gibi <xref:System.Net.Http.HttpClient>, uzun süre çalışan API 'Ler için yalnızca zaman uyumsuz yöntemleri destekler.
Zaman uyumsuz bir yöntem yaparak başlayın. Uygulamanın işlevlerini oluştururken uygulamayı doldurursunuz. `program.cs` dosyasını proje dizininizde açıp `Program` sınıfına aşağıdaki yöntemi ekleyerek başlayın:

```csharp
private static async Task ProcessRepositories()
{
}
```

C# Derleyicinin <xref:System.Threading.Tasks.Task> türünü tanıması için `Main` yönteminizin en üstüne `using` bir ifade eklemeniz gerekir:

```csharp
using System.Threading.Tasks;
```

Projenizi bu noktada oluşturursanız, hiçbir `await` işleci içermediğinden ve zaman uyumlu olarak çalışacağı için bu yöntem için bir uyarı alırsınız. Şimdilik bunu yoksayın; yöntemi doldurduktan sonra `await` işleçleri ekleyeceksiniz.

Sonra, `namespace` deyiminizde tanımlanan ad alanını `ConsoleApp` varsayılan olan `WebAPIClient`olarak yeniden adlandırın. Daha sonra bu ad alanında bir `repo` sınıfı tanımlayacağız.

Sonra, bu yöntemi çağırmak için `Main` yöntemini güncelleştirin. `ProcessRepositories` yöntemi bir görevi döndürür ve bu görev tamamlanmadan önce programdan çıkmamanız gerekir. Bu nedenle, `Main`imzasını değiştirmeniz gerekir. `async` değiştiricisini ekleyin ve dönüş türünü `Task`olarak değiştirin. Ardından, yönteminin gövdesinde `ProcessRepositories`bir çağrı ekleyin. Bu yöntem çağrısında `await` anahtar sözcüğünü ekleyin:

```csharp
static Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Artık hiçbir şey yapmaz ancak zaman uyumsuz olarak bunu yapar. Bunu geliştirelim.

Önce, Web 'den veri alan bir nesne gerekir; Bunu yapmak için bir <xref:System.Net.Http.HttpClient> kullanabilirsiniz. Bu nesne, isteği ve yanıtları işler. Program.cs dosyasının içindeki `Program` sınıfında bu türün tek bir örneğini oluşturun.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static Task Main(string[] args)
        {
            //...
        }
    }
}
```

`ProcessRepositories` yöntemine geri dönüp bir ilk sürümü dolduralım:

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

Bunun derlenmesi için dosyanın en üstüne iki yeni using deyimi de eklemeniz gerekir:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Bu ilk sürüm, DotNet Foundation kuruluşundaki tüm depoların listesini okumak için bir Web isteği oluşturur. (.NET Foundation için gitHub KIMLIĞI ' DotNet '). İlk birkaç satır bu istek için <xref:System.Net.Http.HttpClient> ayarlar. İlk olarak, GitHub JSON yanıtlarını kabul edecek şekilde yapılandırılmıştır.
Bu biçim yalnızca JSON 'dir. Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üst bilgisi ekler. Bu iki üst bilgi GitHub sunucusu kodu tarafından denetlenir ve GitHub 'dan bilgi almak için gereklidir.

<xref:System.Net.Http.HttpClient>yapılandırdıktan sonra, bir Web isteği yapar ve yanıtı alabilirsiniz. Bu ilk sürümde <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kullanışlı yöntemini kullanırsınız. Bu kolaylık yöntemi, web isteğini yapan bir görevi başlatır ve ardından istek döndürüldüğünde yanıt akışını okur ve içeriği akıştan ayıklar. Yanıtın gövdesi bir <xref:System.String>olarak döndürülür. Dize, görev tamamlandığında kullanılabilir.

Bu yöntemin son iki satırı bu görevi bekler ve ardından yanıtı konsola yazdırır.
Uygulamayı derleyin ve çalıştırın. Artık `ProcessRepositories` bir `await` işleci içerdiğinden, derleme uyarısı şimdi çıktı. JSON biçimli metnin uzun bir görüntüsünü görürsünüz.

## <a name="processing-the-json-result"></a>JSON sonucunu işleme

Bu noktada, bir Web sunucusundan yanıt almak için kodu yazmış ve bu yanıtta bulunan metni görüntüdiniz. Sonra, bu JSON yanıtını C# nesnelere dönüştürelim.

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> sınıfı, nesneleri JSON 'a seri hale getirir ve JSON nesnelerini nesnelere yeniden ayırır. GitHub API 'sinden döndürülen `repo` JSON nesnesini temsil eden bir sınıf tanımlayarak başlayın:

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; };
    }
}
```

Yukarıdaki kodu ' repo. cs ' adlı yeni bir dosyaya yerleştirin. Sınıfının bu sürümü JSON verilerini işlemek için en basit yolu temsil eder. Sınıf adı ve üye adı, aşağıdaki C# kurallar yerine JSON paketinde kullanılan adlarla eşleşir. Daha sonra bazı yapılandırma öznitelikleri sağlayarak bunu düzeltireceksiniz. Bu sınıf, JSON serileştirme ve seri durumdan çıkarma için başka bir önemli özellik gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değil.
JSON seri hale getiricisi, kullanılmakta olan sınıf türünde bulunmayan bilgileri yoksayacaktır.
Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.

Türü oluşturduğunuza göre, artık bunu serisini çıkaralım. 

Ardından, JSON 'ı C# nesnelere dönüştürmek için seri hale getirici 'yi kullanacaksınız. `ProcessRepositories` yönteminizin <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> çağrısını aşağıdaki üç satır ile değiştirin:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Yeni bir ad alanı kullanıyorsunuz, bu yüzden dosyanın en üstüne de eklemeniz gerekir:

```csharp
using System.Text.Json;
```

Artık <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>yerine <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> kullandığınızı fark edersiniz. Serileştirici, kaynağı olarak bir dize yerine bir akış kullanır. Önceki kod parçacığının ikinci satırında kullanılmakta olan C# dilin birkaç özelliğini açıklayalim. <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> ilk bağımsız değişkeni `await` bir ifadedir. (Diğer iki parametre isteğe bağlıdır ve kod parçacığında atlanır.) Await ifadeleri kodunuzda neredeyse her yerde görünebilir, ancak şu anda yalnızca bir atama bildiriminin parçası olarak gördünüz. `Deserialize` yöntemi *geneldir*, yani JSON metninde ne tür nesneler oluşturulması gerektiği için tür bağımsız değişkenleri sağlamanız gerekir. Bu örnekte, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>başka bir genel nesne olan `List<Repository>`serisini kaldırma işlemi yaptığınız anlamına gelir. `List<>` sınıfı bir nesne koleksiyonunu depolar. Tür bağımsız değişkeni, `List<>`depolanan nesne türlerini bildirir. JSON metni, depo nesnelerinin bir koleksiyonunu temsil eder, bu nedenle tür bağımsız değişkeni `Repository`.

Bu bölümde neredeyse işiniz bitti. JSON 'ı C# nesnelere dönüştürdüğüne göre, her deponun adını görüntülim. Okunan satırları değiştirin:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

aşağıdakiler ile:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Uygulamayı derleyin ve çalıştırın. .NET Foundation 'ın parçası olan Depoların adlarını yazdıracaktır.

## <a name="controlling-serialization"></a>Serileştirme denetleniyor

Daha fazla özellik eklemeden önce `[JsonPropertyName]` özniteliğini kullanarak `name` özelliğini ele alalım. Repo.cs içinde `name` alanının bildiriminde aşağıdaki değişiklikleri yapın:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Bu değişiklik, program.cs içindeki her deponun adını yazan kodu değiştirmeniz gereken anlamına gelir:

```csharp
Console.WriteLine(repo.Name);
```

Eşlemelerinizin doğru olduğundan emin olmak için `dotnet run` yürütün. Önceki ile aynı çıktıyı görmeniz gerekir.

Yeni özellikler eklemeden önce bir değişiklik yapalim. `ProcessRepositories` yöntemi zaman uyumsuz çalışmayı yapabilir ve depoların bir koleksiyonunu döndürebilir. Bu yöntemden `List<Repository>` dönelim ve bilgileri yazan kodu `Main` yöntemine taşıyalim.

`ProcessRepositories` imzasını, sonucu bir `Repository` nesneleri listesi olan bir görevi döndürecek şekilde değiştirin:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Ardından, JSON yanıtını işledikten sonra depoları geri döndürün:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Bu yöntemi `async`olarak işaretlediğiniz için derleyici, return için `Task<T>` nesnesini oluşturur.
Sonra, `Main` yöntemini bu sonuçları yakalayıp, her depo adını konsola yazar şekilde değiştirelim. `Main` yönteminiz şu şekilde görünür:

```csharp
public static Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Daha fazla bilgi okunuyor

Bu işlemi, GitHub API 'sinden gönderilen JSON paketindeki özelliklerden daha fazlasını işleyerek tamamlayalim. Her şeyi almak istemezsiniz, ancak birkaç özelliği eklemek C# dilin birkaç özelliğini gösterir.

`Repository` sınıf tanımına birkaç basit tür ekleyerek başlayalım. Bu özellikleri bu sınıfa ekleyin:

```csharp
[JsonPropertyName(Name="description")]
public string Description { get; set; }

[JsonPropertyName(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName(Name="homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName(Name="watchers")]
public int Watchers { get; set; }
```

Bu özellikler dize türünden (JSON paketlerinin içerdiği), hedef türüne yerleşik Dönüştürmelere sahiptir. <xref:System.Uri> türü sizin için yeni olabilir. Bir URI 'yi veya bu durumda bir URL 'yi temsil eder. `Uri` ve `int` türlerinde, JSON paketi hedef türüne Dönüştürülmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum oluşturur.

Bunları ekledikten sonra, bu öğeleri göstermek için `Main` yöntemini güncelleştirin:

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

Son bir adım olarak, son gönderme işlemi için bilgileri ekleyelim. Bu bilgiler, JSON yanıtında bu biçimde biçimlendirilir:

```json
2016-02-08T21:27:00Z
```

Bu biçim standart .NET <xref:System.DateTime> biçimlerinden hiçbirini izlemez. Bu nedenle, özel bir dönüştürme yöntemi yazmanız gerekir. Ham dizenin `Repository` sınıfının kullanıcılarına sunulamayada istemezsiniz. Öznitelikleri, bu da denetim sağlanmasına yardımcı olabilir. İlk olarak, `Repository` sınıfınıza tarih ve saatin dize gösterimini ve döndürülen tarihi temsil eden biçimli bir dize döndüren bir `LastPush` `readonly` özelliğini tutan bir `public` özelliği tanımlayın:

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

Şimdi tanımladığımız yeni yapıları inceleyelim. `LastPush` özelliği, `get` erişimcisi için *ifade-Bodied üyesi* kullanılarak tanımlanır. `set` erişimcisi yok. `set` erişimcinin atlanması, içinde C# *salt okunurdur* bir özelliği nasıl tanımlayacağınızı belirler. (Evet, öğesinde C# *salt yazılır* özellikler oluşturabilirsiniz, ancak değerleri sınırlıdır.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> yöntemi bir dizeyi ayrıştırır ve sağlanmış bir tarih biçimi kullanarak bir <xref:System.DateTime> nesnesi oluşturur ve bir `CultureInfo` nesnesi kullanarak `DateTime` ek meta veri ekler. Ayrıştırma işlemi başarısız olursa, özellik erişimcisi bir özel durum oluşturur.

<xref:System.Globalization.CultureInfo.InvariantCulture>kullanmak için, `repo.cs`içindeki `using` deyimlerine <xref:System.Globalization> ad alanı eklemeniz gerekir:

```csharp
using System.Globalization;
```

Son olarak, konsolda bir çıkış bildirisi daha ekleyin ve bu uygulamayı yeniden oluşturup çalıştırmak için hazırsınız:

```csharp
Console.WriteLine(repo.LastPush);
```

Sürümünüz artık [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)eşleşmelidir.

## <a name="conclusion"></a>Sonuç

Bu öğretici, Web istekleri oluşturma, sonucu ayrıştırma ve bu sonuçların özelliklerini görüntüleme konusunda sizi gösterdi. Ayrıca, yeni paketleri projenize bağımlılıklar olarak eklediniz. Nesne odaklı teknikleri destekleyen C# dilin bazı özelliklerini gördünüz.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
