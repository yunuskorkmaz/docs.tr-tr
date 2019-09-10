---
title: .NET Core kullanarak REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850981"
---
# <a name="rest-client"></a>REST istemcisi

## <a name="introduction"></a>Giriş

Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir. Şunları öğreneceksiniz:

* .NET Core komut satırı arabirimi (CLı) temelleri.
* C# Dil özelliklerine genel bakış.
* NuGet ile bağımlılıkları yönetme
* HTTP Iletişimleri
* JSON bilgilerini işleme
* Yapılandırmayı özniteliklerle yönetme.

GitHub 'da REST hizmetine HTTP Istekleri veren bir uygulama oluşturacaksınız. JSON biçiminde bilgileri okuyacaksınız ve bu JSON paketini C# nesnelerine dönüştürürsünüz. Son olarak, C# nesneleriyle nasıl çalışacaksınız görürsünüz.

Bu öğreticide birçok özellik vardır. Bunları birer birer oluşturalım.

Bu konuyla ilgili [son örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte izlemeyi tercih ediyorsanız, indirebilirsiniz. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/)kullanır. Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı oluşturma

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizini oluşturun. `dotnet new console` Komutu komut istemine yazın. Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur. Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core Framework 'ü indirir, bir geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet Paket Yöneticisi 'ni çalıştırır.

Değişiklik yapmaya başlamadan önce, uygulamanızı çalıştırmak `dotnet run` için komut isteminde ([bkz. Note](#dotnet-restore-note)) yazın. `dotnet run`ortamınızda bağımlılıklar `dotnet restore` eksik olursa otomatik olarak gerçekleştirilir. Uygulamanızın yeniden oluşturulması `dotnet build` gerekiyorsa de çalışır.
İlk kurulumdan sonra, yalnızca projeniz için anlamlı olduğunda veya `dotnet restore` `dotnet build` çalıştırmanız gerekir.

## <a name="adding-new-dependencies"></a>Yeni bağımlılıklar ekleniyor

.NET Core için önemli tasarım amaçlarından biri, .NET yüklemesinin boyutunu en aza indirmektir. Bir uygulamanın bazı özellikleri için ek kitaplıklar gerekiyorsa, bu bağımlılıkları C# proje (\*. csproj) dosyanıza eklersiniz. Örneğimiz için, uygulamanızın JSON yanıtlarını işleyebilmesi için `System.Runtime.Serialization.Json` paketini eklemeniz gerekir.

`csproj` Proje dosyanızı açın. Dosyanın ilk satırı şöyle görünmelidir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Bu satırdan hemen sonra aşağıdakini ekleyin:

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

Çoğu kod Düzenleyicisi, bu kitaplıkların farklı sürümleri için tamamlama sağlar. Genellikle eklediğiniz herhangi bir paketin en son sürümünü kullanmak isteyeceksiniz. Ancak, tüm paketlerin sürümlerinin eşleştiğinden ve ayrıca .NET Core uygulama çerçevesinin sürümüyle eşleştiğinden emin olmak önemlidir.

Bu değişiklikleri yaptıktan sonra, paketin sisteminizde yüklü `dotnet restore` olması için yürütün ([bkz. Note](#dotnet-restore-note)).

## <a name="making-web-requests"></a>Web Istekleri yapma

Artık Web 'den veri almaya başlamaya hazırsınız. Bu uygulamada, [GITHUB API](https://developer.github.com/v3/)'sindeki bilgileri okuyacaksınız. [.Net Foundation](https://www.dotnetfoundation.org/) şemsiye kapsamındaki projelerle ilgili bilgileri okuyalim. Projeler hakkındaki bilgileri almak için GitHub API 'sine istek yaparak başlayacaksınız. Kullanacağınız uç nokta: <https://api.github.com/orgs/dotnet/repos>. Bu projelerle ilgili tüm bilgileri almak istiyorsunuz, bu nedenle bir HTTP GET isteği kullanacaksınız.
Tarayıcınız ayrıca HTTP GET isteklerini kullanır; bu nedenle, hangi bilgileri almak ve işlemek istediğinizi görmek için bu URL 'YI tarayıcınıza yapıştırabilirsiniz.

Web istekleri yapmak <xref:System.Net.Http.HttpClient> için sınıfını kullanırsınız. Tüm modern .NET API 'lerinde olduğu <xref:System.Net.Http.HttpClient> gibi, uzun süre çalışan API 'ler için yalnızca zaman uyumsuz yöntemleri destekler.
Zaman uyumsuz bir yöntem yaparak başlayın. Uygulamanın işlevlerini oluştururken uygulamayı doldurursunuz. `program.cs` Dosyayı proje dizininizde açıp `Program` sınıfına aşağıdaki yöntemi ekleyerek başlayın:

```csharp
private static async Task ProcessRepositories()
{
}
```

Derleyicinin türü tanıması `using` `Main` için yönteminizin en üstüne bir ifade eklemeniz gerekir: <xref:System.Threading.Tasks.Task> C#

```csharp
using System.Threading.Tasks;
```

Bu noktada projenizi oluşturursanız, herhangi `await` bir işleç içermediğinden ve zaman uyumlu olarak çalışacağı için bu yöntem için bir uyarı alırsınız. Şimdilik bunu yoksayın; yöntemi doldurduktan sonra `await` işleçleri ekleyeceksiniz.

Sonra, `namespace` bildiriminde tanımlanan ad alanını öğesinin varsayılan değerini `ConsoleApp` olarak `WebAPIClient`yeniden adlandırın. Daha sonra bu ad alanında `repo` bir sınıf tanımlayacağız.

Sonra, `Main` yöntemi bu yöntemi çağırmak için güncelleştirin. `ProcessRepositories` Yöntemi bir görevi döndürür ve bu görev tamamlanmadan önce programdan çıkmamanız gerekir. Bu nedenle, görevi engellemek ve `Wait` görevin bitmesini beklemek için yöntemini kullanmanız gerekir:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Artık hiçbir şey yapmaz ancak zaman uyumsuz olarak bunu yapar. Bunu geliştirelim.

Önce, Web 'den veri alan bir nesne gerekir; Bunu yapmak <xref:System.Net.Http.HttpClient> için kullanabilirsiniz. Bu nesne, isteği ve yanıtları işler. Program.cs dosyasının içindeki `Program` sınıfta bu türün tek bir örneğini oluşturun.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

`ProcessRepositories` Yönteme dönüp ilk bir sürümünü dolduralım:

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

Bu ilk sürüm, DotNet Foundation kuruluşundaki tüm depoların listesini okumak için bir Web isteği oluşturur. (.NET Foundation için gitHub KIMLIĞI ' DotNet '). İlk birkaç satır bu istek <xref:System.Net.Http.HttpClient> için ayarlayın. İlk olarak, GitHub JSON yanıtlarını kabul edecek şekilde yapılandırılmıştır.
Bu biçim yalnızca JSON 'dir. Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üst bilgisi ekler. Bu iki üst bilgi GitHub sunucusu kodu tarafından denetlenir ve GitHub 'dan bilgi almak için gereklidir.

Yapılandırmasını <xref:System.Net.Http.HttpClient>yaptıktan sonra bir Web isteği yapar ve yanıtı alırsınız. Bu ilk sürümde, <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemini kullanırsınız. Bu kolaylık yöntemi, web isteğini yapan bir görevi başlatır ve ardından istek döndürüldüğünde yanıt akışını okur ve içeriği akıştan ayıklar. Yanıtın gövdesi bir <xref:System.String>olarak döndürülür. Dize, görev tamamlandığında kullanılabilir.

Bu yöntemin son iki satırı bu görevi bekler ve ardından yanıtı konsola yazdırır.
Uygulamayı derleyin ve çalıştırın. `ProcessRepositories` Şimdi bir`await` işleç içerdiğinden, derleme uyarısı şimdi çıktı. JSON biçimli metnin uzun bir görüntüsünü görürsünüz.

## <a name="processing-the-json-result"></a>JSON sonucunu işleme

Bu noktada, bir Web sunucusundan yanıt almak için kodu yazmış ve bu yanıtta bulunan metni görüntüdiniz. Sonra, bu JSON yanıtını C# nesnelere dönüştürelim.

JSON seri hale getirici JSON verilerini C# nesnelerine dönüştürür. İlk göreviniz, bu yanıttan kullandığınız bilgileri C# içeren bir sınıf türü tanımlamaktır. Bunu yavaş oluşturalım, bu nedenle deponun adını içeren basit C# bir türle başlayın:

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
```

Yukarıdaki kodu ' repo. cs ' adlı yeni bir dosyaya yerleştirin. Sınıfının bu sürümü JSON verilerini işlemek için en basit yolu temsil eder. Sınıf adı ve üye adı, aşağıdaki C# kurallar yerine JSON paketinde kullanılan adlarla eşleşir. Daha sonra bazı yapılandırma öznitelikleri sağlayarak bunu düzeltireceksiniz. Bu sınıf, JSON serileştirme ve seri durumundan çıkarma için başka bir önemli özelliği gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değil.
JSON seri hale getiricisi, kullanılmakta olan sınıf türünde bulunmayan bilgileri yoksayacaktır.
Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.

Türü oluşturduğunuza göre, artık bunu serisini çıkaralım. Bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesnesi oluşturmanız gerekir. Bu nesne, aldığı JSON paketi için beklenen CLR türünü bilmelidir. GitHub ' dan paket, bir `List<repo>` dizi depo içerir, bu nedenle, doğru türdür. Aşağıdaki satırı `ProcessRepositories` yöntemine ekleyin:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

İki yeni ad alanı kullanıyorsunuz, bu nedenle bunları da eklemeniz gerekir:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Ardından, JSON 'ı C# nesnelere dönüştürmek için seri hale getirici 'yi kullanacaksınız. Yöntemdeki`ProcessRepositories` çağrısını <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> aşağıdaki iki satır ile değiştirin:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> Artık<xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>yerine kullandığınızdan emin olun. Serileştirici, kaynağı olarak bir dize yerine bir akış kullanır. Yukarıdaki ikinci satırda kullanılmakta olan C# dilin birkaç özelliğini açıklayalim. Bağımsız değişkeni <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> bir `await` ifadedir. Await ifadeleri kodunuzda neredeyse her yerde görünebilir, ancak şu anda yalnızca bir atama bildiriminin parçası olarak gördünüz.

İkinci olarak, `as` işleç derleme zaman `object` türünden öğesine `List<repo>`dönüştürür.
Bildirimi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> , türünde <xref:System.Object?displayProperty=nameWithType>bir nesne döndüren bildirir. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>, oluşturduğunuzda belirttiğiniz türü döndürür (`List<repo>` Bu öğreticide). Dönüştürme başarılı olmazsa, `as` bir özel durum oluşturmak yerine işleci olarak `null`değerlendirilir.

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

Daha fazla özellik eklemeden önce, `repo` türü ele alalım ve daha standart C# Kurallara uyalım. Bunu, JSON seri hale getiricinin `repo` nasıl çalıştığını denetleyen *özniteliklerle* türe açıklama ekleyerek yapabilirsiniz. Bu durumda, JSON anahtar adları ve C# sınıf ile üye adları arasında bir eşleme tanımlamak için bu öznitelikleri kullanacaksınız. Kullanılan iki öznitelik <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleridir. Kurala göre, tüm öznitelik sınıfları sonta `Attribute`sona erdir. Ancak, bir özniteliği uyguladığınızda o soneki kullanmanız gerekmez.

Ve öznitelikleri farklı bir kitaplıkta olduğundan, bu kitaplığı C# proje dosyanıza bağımlılık olarak eklemeniz gerekir. <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataContractAttribute> Aşağıdaki satırı `<ItemGroup>` proje dosyanızın bölümüne ekleyin:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Dosyayı kaydettikten sonra, bu paketi almak `dotnet restore` için ([bkz. Note](#dotnet-restore-note)) öğesini çalıştırın.

Sonra `repo.cs` dosyayı açın. Bu adı, Pascal durumunu kullanacak şekilde değiştirelim ve adı `Repository`tamamen heceleyin. Hala bu tür JSON ' repo ' düğümlerini eşlemek istiyoruz, bu nedenle <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği sınıf bildirimine eklemeniz gerekir. Özniteliğin `Name` özelliğini, bu türle eşlenen json düğümlerinin adına ayarlayacaksınız:

```csharp
[DataContract(Name="repo")]
public class Repository
```

, Ad alanının bir üyesidir `using` , bu yüzden dosyanın en üstüne uygun ifadeyi eklemeniz gerekir: <xref:System.Runtime.Serialization> <xref:System.Runtime.Serialization.DataContractAttribute>

```csharp
using System.Runtime.Serialization;
```

`repo` Sınıfının adını olarak `Repository`değiştirdiniz. bu nedenle, program.cs içinde aynı ad değişikliğini yapmanız gerekir (bazı düzenleyiciler, bu değişikliği otomatik olarak yapan bir yeniden adlandırma yeniden düzenlemesi destekleyebilir:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Daha sonra, `name` <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfını kullanarak aynı değişikliği alanla yapalim. Repo.cs içindeki `name` alanın bildiriminde aşağıdaki değişiklikleri yapın:

```csharp
[DataMember(Name="name")]
public string Name;
```

Bu değişiklik, program.cs içindeki her deponun adını yazan kodu değiştirmeniz gereken anlamına gelir:

```csharp
Console.WriteLine(repo.Name);
```

Eşlemelerinizin doğru olduğundan emin `dotnet run` olmak için bir takipedin.`dotnet build` Önceki ile aynı çıktıyı görmeniz gerekir. Web sunucusundan daha fazla özellik işleyebilmemiz için `Repository` , sınıfa daha fazla değişiklik yapalım. `Name` Üye, herkese açık bir alandır. Bu iyi bir nesne odaklı uygulama değildir, bu nedenle bunu bir özellik olarak değiştirelim. Özelliği alırken veya ayarlarken çalıştırmak için belirli bir kod gerekmez, ancak bir özelliği değiştirmek, bu değişiklikleri `Repository` sınıfını kullanan kodları bozmadan daha sonra eklemeyi kolaylaştırır.

Alan tanımını kaldırın ve [Otomatik uygulanan bir özellik](../programming-guide/classes-and-structs/auto-implemented-properties.md)ile değiştirin:

```csharp
public string Name { get; set; }
```

Derleyici, `get` ve erişimcilerinin gövdesini ve `set` adı depolamak için özel bir alanı üretir. Bu, el ile yazabileceğiniz aşağıdaki koda benzer olacaktır:

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Yeni özellikler eklemeden önce bir değişiklik yapalim. `ProcessRepositories` Yöntemi zaman uyumsuz çalışmayı yapabilir ve depoların bir koleksiyonunu döndürebilir. Bu yöntemden ' ı `List<Repository>` dönelim ve bilgileri `Main` yöntemine yazan kodu taşıyalim.

Sonucunu bir `Repository` nesne listesi `ProcessRepositories` olan bir görevi döndürmek için imzasını değiştirin:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Ardından, JSON yanıtını işledikten sonra depoları geri döndürün:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Bu yöntemi olarak `async`işaretlediğiniz `Task<T>` için derleyici, döndürme için nesnesi oluşturur.
Ardından, `Main` yöntemi bu sonuçları yakalayıp, her depo adını konsola yazar şekilde değiştirelim. `Main` Yönteminiz şu şekilde görünür:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Görev tamamlanana kadar görev bloklarının özelliğineerişme.`Result` Normalde, `ProcessRepositories` yönteminde olduğu gibi, `await` ancak `Main` yönteminde izin verilmeyen görevi tamamlamayı tercih edersiniz.

## <a name="reading-more-information"></a>Daha fazla bilgi okunuyor

Bu işlemi, GitHub API 'sinden gönderilen JSON paketindeki özelliklerden daha fazlasını işleyerek tamamlayalim. Her şeyi almak istemezsiniz, ancak birkaç özelliği eklemek C# dilin birkaç özelliğini gösterir.

Daha fazla basit türü `Repository` sınıf tanımına ekleyerek başlayalım. Bu özellikleri bu sınıfa ekleyin:

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

Bu özellikler dize türünden (JSON paketlerinin içerdiği), hedef türüne yerleşik Dönüştürmelere sahiptir. <xref:System.Uri> Tür sizin için yeni olabilir. Bir URI 'yi veya bu durumda bir URL 'yi temsil eder. `Uri` Ve`int` türleri söz konusu olduğunda, JSON paketi hedef türüne Dönüştürülmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum oluşturur.

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

Bu biçim standart .net <xref:System.DateTime> biçimlerinden hiçbirini izlemez. Bu nedenle, özel bir dönüştürme yöntemi yazmanız gerekir. Ham dizenin, `Repository` sınıfın kullanıcılarına gösterilmesini de istemezsiniz. Öznitelikleri, bu da denetim sağlanmasına yardımcı olabilir. İlk olarak, sınıfınıza `private` `Repository` ait tarih saatinin dize gösterimini tutacak bir özellik tanımlayın:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<xref:System.Runtime.Serialization.DataMemberAttribute> Özniteliği, seri hale getiricinin, ortak üye olmasa bile bu işleme yönelik olduğunu bildirir. Sonra, dizeyi geçerli <xref:System.DateTime> bir nesneye dönüştüren ortak bir salt okunurdur ve bu <xref:System.DateTime>özelliği yazmanız gerekir:

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

Yukarıdaki yeni yapıları inceleyelim. `IgnoreDataMember` Özniteliği, seri hale getirici bu türün herhangi bir JSON nesnesine okunmamalıdır veya yazılamaz olması gerektiğini söyler. Bu özellik yalnızca bir `get` erişimci içerir. `set` Erişimci yok. İçinde C# *salt okunurdur* bir özelliği nasıl tanımlayacaksınız. (Evet, öğesinde C# *salt yazılır* özellikler oluşturabilirsiniz, ancak değerleri sınırlıdır.) Yöntemi bir dizeyi ayrıştırır ve bir <xref:System.DateTime> nesne `DateTime` kullanarak `CultureInfo` bir nesne oluşturur. <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Ayrıştırma işlemi başarısız olursa, özellik erişimcisi bir özel durum oluşturur.

Kullanmak <xref:System.Globalization.CultureInfo.InvariantCulture>için, <xref:System.Globalization> ad alanını `using` içindeki `repo.cs`deyimlere eklemeniz gerekir:

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
