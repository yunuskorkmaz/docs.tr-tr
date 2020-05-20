---
title: .NET Core kullanarak REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve C# dilinde birçok özellik öğretir.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 4a3a76d1ec9893c2c3e0353e305a19e59c586fe5
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420389"
---
# <a name="rest-client"></a>REST istemcisi

Bu öğretici, .NET Core ve C# dilinde birçok özellik öğretir. Şunları öğreneceksiniz:

* .NET Core CLI temel kavramları.
* C# dil özelliklerine genel bakış.
* NuGet ile bağımlılıkları yönetme
* HTTP Iletişimleri
* JSON bilgilerini işleme
* Yapılandırmayı özniteliklerle yönetme.

GitHub 'da REST hizmetine HTTP Istekleri veren bir uygulama oluşturacaksınız. JSON biçiminde bilgileri okur ve bu JSON paketini C# nesnelerine dönüştürürsünüz. Son olarak C# nesneleriyle nasıl çalışacaksınız görürsünüz.

Bu öğreticide birçok özellik vardır. Bunları birer birer oluşturalım.

Bu konuyla ilgili [son örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte izlemeyi tercih ediyorsanız, indirebilirsiniz. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Ön koşullar

Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/)kullanır. Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı oluşturma

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizini oluşturun. Konsol penceresine aşağıdaki komutu girin:

```dotnetcli
dotnet new console --name WebApiClient
```

Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur. Proje adı "WebApiClient" dir. Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir. İlk çalıştırma .NET Core Framework 'ü indirir, bir geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet Paket Yöneticisi 'ni çalıştırır.

Değişiklik yapmaya başlamadan önce, `dotnet run` uygulamanızı çalıştırmak için komut isteminde ([bkz. Note](#dotnet-restore-note)) yazın. `dotnet run``dotnet restore`ortamınızda bağımlılıklar eksik olursa otomatik olarak gerçekleştirilir. Uygulamanızın yeniden oluşturulması gerekiyorsa de çalışır `dotnet build` .
İlk kurulumdan sonra, yalnızca `dotnet restore` `dotnet build` projeniz için anlamlı olduğunda veya çalıştırmanız gerekir.

## <a name="adding-new-dependencies"></a>Yeni bağımlılıklar ekleniyor

.NET Core için önemli tasarım amaçlarından biri, .NET yüklemesinin boyutunu en aza indirmektir. Bir uygulamanın bazı özellikleri için ek kitaplıklar gerekiyorsa, bu bağımlılıkları C# projeniz ( \* . csproj) dosyanıza eklersiniz. Örneğimiz için, `System.Runtime.Serialization.Json` UYGULAMANıZıN JSON yanıtlarını işleyebilmesi için paketini eklemeniz gerekir.

`System.Runtime.Serialization.Json`Bu uygulama için pakete ihtiyacınız olacak. Aşağıdaki [.net CLI](../../core/tools/dotnet-add-package.md) komutunu çalıştırarak projenize ekleyin:

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Web Istekleri yapma

Artık Web 'den veri almaya başlamaya hazırsınız. Bu uygulamada, [GITHUB API](https://developer.github.com/v3/)'sindeki bilgileri okuyacaksınız. [.Net Foundation](https://www.dotnetfoundation.org/) şemsiye kapsamındaki projelerle ilgili bilgileri okuyalim. Projeler hakkındaki bilgileri almak için GitHub API 'sine istek yaparak başlayacaksınız. Kullanacağınız uç nokta: <https://api.github.com/orgs/dotnet/repos> . Bu projelerle ilgili tüm bilgileri almak istiyorsunuz, bu nedenle bir HTTP GET isteği kullanacaksınız.
Tarayıcınız ayrıca HTTP GET isteklerini kullanır; bu nedenle, hangi bilgileri almak ve işlemek istediğinizi görmek için bu URL 'YI tarayıcınıza yapıştırabilirsiniz.

<xref:System.Net.Http.HttpClient>Web istekleri yapmak için sınıfını kullanırsınız. Tüm modern .NET API 'Lerinde olduğu gibi, <xref:System.Net.Http.HttpClient> uzun süre çalışan API 'ler için yalnızca zaman uyumsuz yöntemleri destekler.
Zaman uyumsuz bir yöntem yaparak başlayın. Uygulamanın işlevlerini oluştururken uygulamayı doldurursunuz. `program.cs`Dosyayı proje dizininizde açıp sınıfına aşağıdaki yöntemi ekleyerek başlayın `Program` :

```csharp
private static async Task ProcessRepositories()
{
}
```

`using` `Main` C# derleyicisinin türü tanıması için yönteminizin en üstüne bir yönerge eklemeniz gerekir <xref:System.Threading.Tasks.Task> :

```csharp
using System.Threading.Tasks;
```

Bu noktada projenizi oluşturursanız, herhangi bir `await` işleç içermediğinden ve zaman uyumlu olarak çalışacağı için bu yöntem için bir uyarı alırsınız. Şimdilik bunu yoksayın; yöntemi doldurduktan sonra `await` işleçleri ekleyeceksiniz.

Sonra, yöntemini `Main` çağırmak için yöntemini güncelleştirin `ProcessRepositories` . `ProcessRepositories`Yöntemi bir görevi döndürür ve bu görev tamamlanmadan önce programdan çıkmamanız gerekir. Bu nedenle, imzasını değiştirmeniz gerekir `Main` . Değiştiricisini ekleyin `async` ve dönüş türünü olarak değiştirin `Task` . Ardından, yönteminin gövdesinde öğesine bir çağrı ekleyin `ProcessRepositories` . `await`Anahtar sözcüğünü bu yöntem çağrısına ekleyin:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Artık hiçbir şey yapmaz ancak zaman uyumsuz olarak bunu yapar. Bunu geliştirelim.

Önce, Web 'den veri alan bir nesne gerekir; <xref:System.Net.Http.HttpClient>bunu yapmak için kullanabilirsiniz. Bu nesne, isteği ve yanıtları işler. `Program` *Program.cs* dosyasının içindeki sınıfta bu türün tek bir örneğini oluşturun.

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

`ProcessRepositories`Yönteme dönüp ilk bir sürümünü dolduralım:

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

`using`Bunun derlenmesi için dosyanın en üstüne iki yeni yönergeler de eklemeniz gerekir:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Bu ilk sürüm, DotNet Foundation kuruluşundaki tüm depoların listesini okumak için bir Web isteği oluşturur. (.NET Foundation için gitHub KIMLIĞI ' DotNet '). İlk birkaç satır <xref:System.Net.Http.HttpClient> Bu istek için ayarlayın. İlk olarak, GitHub JSON yanıtlarını kabul edecek şekilde yapılandırılmıştır.
Bu biçim yalnızca JSON 'dir. Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üst bilgisi ekler. Bu iki üst bilgi GitHub sunucusu kodu tarafından denetlenir ve GitHub 'dan bilgi almak için gereklidir.

Yapılandırmasını yaptıktan sonra <xref:System.Net.Http.HttpClient> bir Web isteği yapar ve yanıtı alırsınız. Bu ilk sürümde, <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemini kullanırsınız. Bu kolaylık yöntemi, web isteğini yapan bir görevi başlatır ve ardından istek döndürüldüğünde yanıt akışını okur ve içeriği akıştan ayıklar. Yanıtın gövdesi bir olarak döndürülür <xref:System.String> . Dize, görev tamamlandığında kullanılabilir.

Bu yöntemin son iki satırı bu görevi bekler ve ardından yanıtı konsola yazdırır.
Uygulamayı derleyin ve çalıştırın. `ProcessRepositories`Şimdi bir işleç içerdiğinden, derleme uyarısı şimdi çıktı `await` . JSON biçimli metnin uzun bir görüntüsünü görürsünüz.

## <a name="processing-the-json-result"></a>JSON sonucunu işleme

Bu noktada, bir Web sunucusundan yanıt almak için kodu yazmış ve bu yanıtta bulunan metni görüntüdiniz. Ardından, bu JSON yanıtını C# nesnelerine dönüştürelim.

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>Sınıfı, NESNELERI JSON 'a seri hale getirir ve JSON 'ı nesnelere yeniden ayırır. `repo`GITHUB API 'sinden döndürülen JSON nesnesini temsil eden bir sınıf tanımlayarak başlayın:

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

Yukarıdaki kodu ' repo. cs ' adlı yeni bir dosyaya yerleştirin. Sınıfının bu sürümü JSON verilerini işlemek için en basit yolu temsil eder. Sınıf adı ve üye adı, aşağıdaki C# kuralları yerine JSON paketinde kullanılan adlarla eşleşir. Daha sonra bazı yapılandırma öznitelikleri sağlayarak bunu düzeltireceksiniz. Bu sınıf, JSON serileştirme ve seri durumdan çıkarma için başka bir önemli özellik gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değil.
JSON seri hale getiricisi, kullanılmakta olan sınıf türünde bulunmayan bilgileri yoksayacaktır.
Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.

Türü oluşturduğunuza göre, artık bunu serisini çıkaralım.

Ardından, seri hale getirici kullanarak JSON 'u C# nesnelerine dönüştürebilirsiniz. <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` Yöntemdeki çağrısını aşağıdaki satırlarla değiştirin:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Yeni ad alanları kullanıyorsunuz, bu yüzden dosyanın en üstüne de eklemeniz gerekir:

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

Artık yerine kullandığınızdan emin olun <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> . Serileştirici, kaynağı olarak bir dize yerine bir akış kullanır. Önceki kod parçacığının ikinci satırında kullanılmakta olan C# dilinin birkaç özelliği açıklanalım. İçin ilk bağımsız değişken <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> bir `await` ifadedir. (Diğer iki parametre isteğe bağlıdır ve kod parçacığında atlanır.) Await ifadeleri kodunuzda neredeyse her yerde görünebilir, ancak şu anda yalnızca bir atama bildiriminin parçası olarak gördünüz. `Deserialize`Yöntemi *geneldir*, yani JSON metninde ne tür nesneler oluşturulması gerektiği için tür bağımsız değişkenleri sağlamanız gerekir. Bu örnekte, `List<Repository>` başka bir genel nesne olan olan ' a bir tane olarak serisini halyorsunuz <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> . `List<>`Sınıfı bir nesne koleksiyonunu depolar. Tür bağımsız değişkeni içinde depolanan nesne türlerini bildirir `List<>` . JSON metni, bir depo nesnesi koleksiyonunu temsil eder, bu nedenle tür bağımsız değişkeni olur `Repository` .

Bu bölümde neredeyse işiniz bitti. JSON 'u C# nesnelerine dönüştürdüğüne göre, her deponun adını görüntülim. Okunan satırları değiştirin:

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

Daha fazla özellik eklemeden önce `name` özniteliğini kullanarak özelliği ele alalım `[JsonPropertyName]` . Repo.cs içindeki alanın bildiriminde aşağıdaki değişiklikleri yapın `name` :

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Özniteliğini kullanmak için `[JsonPropertyName]` , bu <xref:System.Text.Json.Serialization> ad alanını yönergelere eklemeniz gerekir `using` :

```csharp
using System.Text.Json.Serialization;
```

Bu değişiklik, program.cs içindeki her deponun adını yazan kodu değiştirmeniz gereken anlamına gelir:

```csharp
Console.WriteLine(repo.Name);
```

`dotnet run`Eşlemeleri doğru olduğundan emin olmak için yürütün. Önceki ile aynı çıktıyı görmeniz gerekir.

Yeni özellikler eklemeden önce bir değişiklik yapalim. `ProcessRepositories`Yöntemi zaman uyumsuz çalışmayı yapabilir ve depoların bir koleksiyonunu döndürebilir. `List<Repository>`Bu yöntemden ' ı dönelim ve bilgileri yöntemine yazan kodu taşıyalim `Main` .

`ProcessRepositories`Sonucunu bir nesne listesi olan bir görevi döndürmek için imzasını değiştirin `Repository` :

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Ardından, JSON yanıtını işledikten sonra depoları geri döndürün:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

`Task<T>`Bu yöntemi olarak işaretlediğiniz için derleyici, döndürme için nesnesi oluşturur `async` .
Ardından, `Main` yöntemi bu sonuçları yakalayıp, her depo adını konsola yazar şekilde değiştirelim. `Main`Yönteminiz şu şekilde görünür:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Daha fazla bilgi okunuyor

Bu işlemi, GitHub API 'sinden gönderilen JSON paketindeki özelliklerden daha fazlasını işleyerek tamamlayalim. Her şeyi almak istemezsiniz, ancak birkaç özelliği eklemek C# dilinin daha fazla özelliği gösterir.

Daha fazla basit türü `Repository` sınıf tanımına ekleyerek başlayalım. Bu özellikleri bu sınıfa ekleyin:

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

Bu özellikler dize türünden (JSON paketlerinin içerdiği), hedef türüne yerleşik Dönüştürmelere sahiptir. <xref:System.Uri>Tür sizin için yeni olabilir. Bir URI 'yi veya bu durumda bir URL 'yi temsil eder. Ve türleri söz konusu olduğunda `Uri` `int` , JSON paketi hedef türüne Dönüştürülmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum oluşturur.

Bunları ekledikten sonra, `Main` Bu öğeleri göstermek için yöntemini güncelleştirin:

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

Bu biçim Eşgüdümlü Evrensel Saat (UTC) biçiminde olduğundan, özelliği olan bir <xref:System.DateTime> değer alırsınız <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc> . Saat diliminizde temsil edilen bir tarihi tercih ediyorsanız, özel bir dönüştürme yöntemi yazmanız gerekir. İlk olarak, `public` sınıfınızın tarih ve SAATININ UTC gösterimini `Repository` ve `LastPush` `readonly` yerel saate Dönüştürülecek tarihi döndüren bir özelliği tanımlar:

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

Şimdi tanımladığımız yeni yapıları inceleyelim. `LastPush`Özelliği, erişimci için *ifade-Bodied üyesi* kullanılarak tanımlanır `get` . `set`Erişimci yok. `set`Erişimcinin atlanması, C# ' de *salt okunurdur* bir özelliği nasıl tanımlayacağınızı belirler. (Evet, C# dilinde *salt yazılır* özellikler oluşturabilirsiniz, ancak bunların değeri sınırlı olur.)

Son olarak, konsolda bir çıkış bildirisi daha ekleyin ve bu uygulamayı yeniden oluşturup çalıştırmak için hazırsınız:

```csharp
Console.WriteLine(repo.LastPush);
```

Sürümünüz artık [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)eşleşmelidir.

## <a name="conclusion"></a>Sonuç

Bu öğretici, Web istekleri oluşturma, sonucu ayrıştırma ve bu sonuçların özelliklerini görüntüleme konusunda sizi gösterdi. Ayrıca, yeni paketleri projenize bağımlılıklar olarak eklediniz. Nesne odaklı teknikleri destekleyen C# dilinin bazı özelliklerini gördünüz.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
