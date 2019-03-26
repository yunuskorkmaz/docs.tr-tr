---
title: .NET Core kullanarak bir REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: a375215f2d31845333290c85f7701c1a7dfbe780
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412311"
---
# <a name="rest-client"></a>REST istemcisi

## <a name="introduction"></a>Giriş

Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir. Şunları öğreneceksiniz:

* Temel .NET Core komut satırı arabirimi (CLI).
* C# dili özellikleri genel bakış.
* NuGet ile bağımlılık Yönetimi
* HTTP iletişimleri
* JSON bilgilerini işleme
* Öznitelikleri yapılandırmasıyla yönetme.

GitHub üzerinde bir REST hizmeti için HTTP isteklerini veren bir uygulama oluşturacaksınız. JSON biçiminde bilgileri okuyun ve C# nesneler bu JSON paket dönüştürme. Son olarak, C# nesneleriyle çalışma konusunda görürsünüz.

Bu öğreticide birçok özellik vardır. Bunları tek tek oluşturalım.

İle birlikte izlemek isterseniz [son örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) yönelik bu konuda, indirebilirsiniz. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

.NET core çalıştırmak için makinenizi ayarlamanız gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası. Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.
Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir. Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/), açık kaynaklı, çapraz platform Düzenleyicisi olduğu. Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Bu, geçerli bir dizin oluşturun. Komut türü `dotnet new console` komut isteminde. Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.

Bir değişiklik yapmadan başlamadan önce basit bir Hello World uygulamasını çalıştırmak için adımlara Bahsedelim. Uygulamayı oluşturduktan sonra yazın `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut isteminde. Bu komut, NuGet paket geri yükleme işlemi çalıştırır. NuGet, .NET paket yöneticisidir. Bu komut tüm projeniz için eksik bağımlılıkların indirir. Bu yeni bir proje olduğundan, ilk çalıştırma .NET Core framework yükleyecek şekilde bağımlılıkları hiçbiri yerde değil. Bu ilk adımdan sonra yalnızca çalıştırmanız gerekir `dotnet restore` ([bkz. Not](#dotnet-restore-note)) yeni bağımlı paketler eklediğinizde, veya herhangi birini bağımlılıklarınızı sürümlerini güncelleştirin.

Paketleri geri yükledikten sonra çalıştırmanız `dotnet build`. Bu yapı altyapısının yürütür ve uygulamanızı oluşturur. Son olarak, yürüttüğünüz `dotnet run` uygulamanızı çalıştırmak için.

## <a name="adding-new-dependencies"></a>Yeni bağımlılıkları ekleme

.NET Core için önemli tasarım amaçlarından .NET yükleme boyutu en aza indirmektir. Bir uygulamanın bazı özelliklerin ek kitaplıklar gerekiyorsa bu bağımlılıkların C# projenize ekleyin (\*.csproj) dosyası. Bizim örneğimizde, eklemeniz gerekecektir `System.Runtime.Serialization.Json` uygulamanızın JSON yanıtları işleyebilmek için paket.

Açık, `csproj` proje dosyası. Dosyanın ilk satırı olarak görünmesi gerekir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Bu satırın hemen sonra aşağıdakileri ekleyin:

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

Çoğu kod düzenleyicilerinden, bu kitaplıkların farklı sürümleri için tamamlama sağlayacaktır. Genellikle, eklediğiniz herhangi bir paket en son sürümünü kullanmak isteyeceksiniz. Ancak, tüm paketlerin sürümlerinin eşleştiğinden ve .NET Core uygulaması framework sürümü de eşleştiğinden emin olmak önemlidir.

Bu değişiklikleri yaptıktan sonra çalıştırmalısınız `dotnet restore` ([bkz. Not](#dotnet-restore-note)) yeniden böylece paket sisteminize yüklenir.

## <a name="making-web-requests"></a>Web istekleri yapma

Artık Web'den veri almaya başlamak hazırsınız. Bilgileri okuyun bu uygulamada [GitHub API](https://developer.github.com/v3/). Projeleri hakkında bilgi okuyalım [.NET Foundation](https://www.dotnetfoundation.org/) terimdir. Projeler hakkında bilgi almak için GitHub API isteği yapan başlayacağız. Kullandığınız hesap uç noktadır: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos). Bir HTTP GET isteği kullanacaksınız böylece bu projeleri hakkındaki tüm bilgileri almak istediğiniz.
Tarayıcınız, ayrıca hangi bilgileri görmek için URL'yi tarayıcınıza aldığınız, yapıştırabilirsiniz HTTP GET istekleri ve işleme kullanır.

Kullandığınız <xref:System.Net.Http.HttpClient> web isteklerinde bulunmak için sınıf. İster modern tüm .NET API'lerini <xref:System.Net.Http.HttpClient> yalnızca zaman uyumsuz yöntemler için uzun süre çalışan API'ler destekler.
Zaman uyumsuz bir yöntem sağlayarak başlatın. Uygulamanın işlevselliğini oluşturdukça uygulamasında doldururlar. Başlangıç açarak `program.cs` dosya proje dizininde ve aşağıdaki yöntemi ekleyerek `Program` sınıfı:

```csharp
private static async Task ProcessRepositories()
{
}
```

Eklemeniz gerekecektir bir `using` en üstündeki deyimi, `Main` yöntemi C# derleyicisi tanımasını <xref:System.Threading.Tasks.Task> türü:

```csharp
using System.Threading.Tasks;
```

Bu noktada, projenizi derleme yaparsanız herhangi içermez çünkü bu yöntem için oluşturulan bir uyarı alırsınız `await` işleçler ve zaman uyumlu olarak çalışır. Şimdilik yoksayın; ekleyeceğiniz `await` yazarken işleçleri yöntemi doldurun.

Ardından, içinde tanımlanan ad alanı yeniden adlandırma `namespace` varsayılan deyimden `ConsoleApp` için `WebAPIClient`. Daha sonra tanımlarız bir `repo` bu ad alanındaki sınıfı.

Ardından, güncelleştirme `Main` bu yöntemi çağırmak için yöntem. `ProcessRepositories` Yöntemi bir görev döndürür ve bu görev tamamlanmadan önce programdan çıkmak olmamalıdır. Bu nedenle, kullanmalısınız `Wait` engelleyin ve görevin tamamlanmasını bekle yöntemi:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Artık, hiçbir şey yapılmaz, ancak zaman uyumsuz olarak mevcut bir program var. Şimdi geliştirebilir.

İlk veri Web'den yeteneğine sahip bir nesne gerekir; kullanabileceğiniz bir <xref:System.Net.Http.HttpClient> Bunu yapmak için. Bu nesne, istek ve yanıtları işler. Bu türde tek bir örneğini `Program` sınıf Program.cs dosyasının içinde.

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

Geri dönelim `ProcessRepositories` yöntemi ve ilk sürümü doldurun:

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

Ayrıca iki eklemeniz gerekecektir yeni deyimleri için bu dosyanın üst derlemeye kullanarak:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Bu ilk sürümü dotnet foundation kuruluş altındaki tüm depo listesi okumak için bir web isteği yapar. (GitHub .NET Foundation 'dotnet' kimliğidir). İlk birkaç satırı ayarlanan <xref:System.Net.Http.HttpClient> bu istek için. İlk olarak, bunu GitHub JSON yanıtları kabul edecek şekilde yapılandırılır.
Yalnızca JSON biçimidir. Sonraki satır, bu nesneden tüm istekler için bir kullanıcı aracısı üstbilgisi ekler. Bu iki üstbilgi GitHub sunucu kodu tarafından denetlenir ve Github'dan bilgileri almak gereklidir.

Yapılandırmayı tamamladığınızda <xref:System.Net.Http.HttpClient>, bir web isteği ve yanıtı almak olun. Bu ilk sürümde kullandığınız <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemi. Bu kolaylık yöntemi web isteği yapan bir görev başlatır ve ardından istek geri döndüğünde, yanıt akışına okur ve içeriği akıştan ayıklar. Yanıt gövdesi olarak döndürülen bir <xref:System.String>. Görev tamamlandığında kullanılabilir bir dizedir.

Bu yöntem son iki satırı, o görev await ve konsola yanıt yazdırın.
Uygulamayı oluşturun ve çalıştırın. Derleme uyarısı artık, çünkü kalktığını `ProcessRepositories` artık içeren bir `await` işleci. Biçimlendirilmiş metin JSON uzun bir görünümünü görürsünüz.

## <a name="processing-the-json-result"></a>JSON sonuç işleme

Bu noktada, bir web sunucusundan bir yanıt almak ve bu yanıt olarak yer alan metni görüntülemek için kod yazdığınız. Ardından, bu JSON yanıtı C# nesnelerini şimdi Dönüştür.

JSON serileştirici JSON verilerini C# nesnelerine dönüştürür. İlk göreviniz bu yanıttan kullandığınız bilgilerini içeren bir C# sınıf türü tanımlamaktır. Bu hiçbiriyse bunu başlangıç depo adını içeren bir basit C# türü ile oluşturalım:

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

Yukarıdaki kod, 'repo.cs' adlı yeni bir dosya içinde yerleştirin. Bu sürüm sınıfının, JSON verilerini işlemek için en basit yolu temsil eder. Sınıf adı ve üye adı yerine aşağıdaki C# kuralları JSON Pakette kullanılan adları aynı. Bazı configuration öznitelikleri daha sonra sağlayarak çözeceksiniz. Bu sınıf, JSON seri hale getirme ve seri durumundan çıkarma başka bir önemli özelliği gösterilmektedir: JSON paketteki tüm alanlar, bu sınıfın bir parçasıdır.
JSON serileştirici kullanılan sınıf türü içinde yer almayan bilgi yoksayar.
Bu özellik, yalnızca bir alt kümesi ile JSON paket alanlarda çalışan türleri oluşturmak kolaylaştırır.

Türü oluşturduğunuza göre şimdi bu seri durumdan. Oluşturmak ihtiyacınız olacak bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesne. Bu nesne, CLR türü beklenen JSON paket için bunu bilmeniz gerekir alır. Github depoları, bir dizi şekilde pakette bir `List<repo>` doğru türde. Aşağıdaki satırı ekleyin, `ProcessRepositories` yöntemi:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Bu da eklemeniz gerekir, böylece iki yeni ad alanları, kullanmakta olduğunuz:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Ardından, JSON C# nesnelerine dönüştürmek için seri hale getirici kullanacaksınız. Çağrısını <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> içinde `ProcessRepositories` aşağıdaki iki satır ile yöntemi:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Kullanmakta olduğunuz bildirimi <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> yerine <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Seri hale getirici bir akış, bir dize yerine, kaynağı olarak kullanır. Şimdi ikinci satırında yukarıdaki kullanılan birkaç C# dili özellikleri açıklanmaktadır. Bağımsız değişkeni <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> olduğu bir `await` ifade. Await ifadeleri neredeyse herhangi bir yerinde görünebilir kodunuzda şimdiye kadar yalnızca bunları Atama ifadesinin bir parçası olarak gördüğünüz olsa bile.

İkincisi, `as` işleci dönüştürür derleme zamanı türünden `object` için `List<repo>`.
Bildirimi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> türünde bir nesne döndürür bildirir <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> oluşturduğu zaman belirttiğiniz türü döndürür (`List<repo>` bu öğreticideki). Dönüştürme başarısız olursa `as` işleci değerlendirilen `null`, bir özel durum oluşturmaktansa.

Bu bölümde ile neredeyse hazırsınız. C# nesnelerini JSON dönüştürdükten sonra şimdi her depo adını görüntüler. Okuma satırları değiştirin:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

şunlarla birlikte:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Derleme ve uygulamayı çalıştırın. .NET Foundation'ın yer depolar adlarını yazdırılacağı.

## <a name="controlling-serialization"></a>Serileştirme denetleme

Daha fazla özellik eklemeden önce şimdi adres `repo` yazın ve daha fazla standart C# kurallarına uygun hale getirebilirsiniz. Bu açıklama ekleyerek yaparsınız `repo` tür *öznitelikleri* JSON serileştirici nasıl çalıştığını denetleyen. Sizin durumunuzda, bu öznitelikler JSON anahtar adlarını ve C# sınıf ve üye adları arasında bir eşleme tanımlamak için kullanırsınız. Kullanılan iki öznitelikleri <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri. Kural gereği, tüm öznitelik sınıfları soneki bitiş `Attribute`. Ancak, bir öznitelik uygulamak soneki kullanın gerekmez.

<xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri olan farklı bir kitaplıkta, bu nedenle bu kitaplığı, bağımlılık olarak C# proje dosyası eklemek gerekir. Aşağıdaki satırı ekleyin `<ItemGroup>` proje dosyanızın bölümü:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Dosyayı kaydettikten sonra çalıştırın `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bu paketi alınamadı.

Ardından, açık `repo.cs` dosya. Baş harfleri büyük kullanmanız ve tam adı yazım adı değiştirelim `Repository`. Biz yine de eklemeniz gerekecektir. Bu nedenle bu tür için JSON 'repo' düğümleri eşlemek istediğiniz <xref:System.Runtime.Serialization.DataContractAttribute> sınıf bildirimine özniteliği. Siz ayarlarsınız `Name` bu türüyle JSON düğüm adı özniteliğinin özelliği:

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> Üyesi <xref:System.Runtime.Serialization> ad alanı, bu nedenle uygun eklemeniz gerekir `using` deyimini dosyanın üst:

```csharp
using System.Runtime.Serialization;
```

Adını değiştirdiğinizi `repo` sınıfının `Repository`, bu nedenle aynı ad Program.cs içinde değişikliğini yapmanız gerekir (bazı düzenleyiciler otomatik olarak bu değişikliği yapmadan bir yeniden adlandırma düzenlemesi destekleyebilir:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Ardından, aynı değişikliği olalım `name` kullanarak alan <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı. Bildirimi için aşağıdaki değişiklikleri yapın `name` repo.cs alanındaki:

```csharp
[DataMember(Name="name")]
public string Name;
```

Bu değişiklik, program.cs içinde her deponun adını yazar kodu değiştirmek ihtiyacınız olduğu anlamına gelir:

```csharp
Console.WriteLine(repo.Name);
```

Yapmak bir `dotnet build` arkasından bir `dotnet run` gördüğümüz eşlemeleri doğru emin olmak için. Önce aynı çıktıyı görmeniz gerekir. Daha fazla değişiklik için size daha fazla özellik web sunucusundan işlemeden önce olalım `Repository` sınıfı. `Name` Üye ortak olarak erişilebilen bir alandır. Nesne yönelimli iyi değil, şimdi bunu bir özelliğini değiştirebilirsiniz. Amaçlarımız doğrultusunda alma veya özellik ayarlama, çalıştırmak için özel kod gerekmez, ancak bir özelliğe değiştirme kolaylaştırır kullanan herhangi bir kod bozup olmadan bu değişiklikleri daha sonra eklenecek `Repository` sınıfı.

Alan tanımını kaldırın ve değiştirin bir [otomatik uygulanan özellik](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Derleyici gövdesinin oluşturur `get` ve `set` erişimcileri, aynı zamanda özel bir alan adı depolamak için. El ile yazabilirsiniz aşağıdaki koda benzer olacaktır:

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Şimdi yeni özellikler eklemeden önce bir daha fazla değişiklik yapın. `ProcessRepositories` Yöntemi zaman uyumsuz çalışma yapmak ve depoları koleksiyonunu döndürür. Şimdi iade `List<Repository>` o yöntemi ve taşıma bilgilerini yazar kodu `Main` yöntemi.

İmzasını Değiştir `ProcessRepositories` bir görevin sonucu bir listedir döndürmek için `Repository` nesneler:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Ardından, yalnızca depolar JSON yanıtı işledikten sonra dönüş:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Derleyicinin oluşturduğu `Task<T>` çünkü bu yöntem olarak işaretlediğiniz için döndürülecek nesne `async`.
Ardından, değişiklik bakalım `Main` BT'nin bunlar yakalar, böylece yöntemi sonuçlarını ve her bir depo adı konsola yazar. `Main` Metodu artık şuna benzer:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Erişim `Result` bir görevin özelliği, görev tamamlanıncaya kadar engeller. Normalde, tercih `await` görüldüğü görevi tamamlanırken `ProcessRepositories` yöntemi ancak içinde kullanılamaz `Main` yöntemi.

## <a name="reading-more-information"></a>Daha fazla bilgi okuma

Şimdi bu GitHub API'den gidiyor JSON paket özelliklerinde, birkaç daha işleyerek tamamlayın. Her şeyi edinin istemezsiniz, ancak bazı özellikler ekleme, C# dilinin birkaç daha fazla özellik gösterilecektir.

Daha fazla birkaç basit türler için ekleyerek başlayalım `Repository` sınıf tanımını. Bu özellikler, o sınıfa ekleyin:

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

Bu özellikler hedef türe (olan JSON paketlerinin ne içermesi) dize türünden yerleşik dönüştürmeleri vardır. <xref:System.Uri> Türü için yeni olabilir. Bir URI'yı temsil veya bu durumda, bir URL. Durumunda, `Uri` ve `int` türleri, JSON paket hedef türe dönüştürülmeyecekse veri içeriyorsa, serileştirme eylemi bir özel durum oluşturur.

Bunlar ekledikten sonra güncelleştirme `Main` yöntemi bu öğeleri görüntülemek için:

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

Son adım olarak, son zorlama işlemi için bilgi ekleyelim. Bu bilgiler, JSON yanıtındaki bu şekilde biçimlendirilir:

```json
2016-02-08T21:27:00Z
```

Bu biçim standart .NET hiçbirini izlemez <xref:System.DateTime> biçimleri. Bu nedenle özel dönüştürme yöntemi yazma gerekecektir. Ayrıca bunu büyük olasılıkla kullanıcıları için kullanıma sunulan ham dize istemediğiniz `Repository` sınıfı. Öznitelikleri de bu denetim yardımcı olabilir. İlk olarak tanımlayan bir `private` tarih saat dize gösterimini tutacak özelliği, `Repository` sınıfı:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<xref:System.Runtime.Serialization.DataMemberAttribute> Öznitelik bildirir seri hale getirici bu işlenmesi gerektiğini, bir ortak üye olmasa bile. Ardından, geçerli bir dize dönüştürür genel bir salt okunur özelliği yazmanız gereken <xref:System.DateTime> nesne ve döndüren <xref:System.DateTime>:

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

Şimdi yeni yapıları üzerinden geçelim. `IgnoreDataMember` Özniteliği, bu tür okuma veya herhangi bir JSON nesnesinden yazılmış, seri hale getirici bildirir. Bu özellik yalnızca içeren bir `get` erişimcisi. Var olan hiçbir `set` erişimcisi. Nasıl tanımladığınızı olan bir *salt okunur* C# özelliği. (Evet, oluşturabileceğiniz *salt yazılır* C# ancak değerlerine özellikleri sınırlıdır.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Yöntemi bir dizeyi ayrıştırır ve oluşturan bir <xref:System.DateTime> sağlanan tarih biçimini kullanarak nesne ve ek meta veri için ekler `DateTime` kullanarak bir `CultureInfo` nesne. Ayrıştırma işlemi başarısız olursa, özellik erişimcisi özel durum oluşturur.

Kullanılacak <xref:System.Globalization.CultureInfo.InvariantCulture>, eklemeniz gerekecektir <xref:System.Globalization> ad alanına `using` deyimlerinde `repo.cs`:

```csharp
using System.Globalization;
```

Son olarak, bir deyim konsolunda daha çıkış ve oluşturup bu uygulamayı yeniden çalıştırmak hazır ekleyin:

```csharp
Console.WriteLine(repo.LastPush);
```

Sürümünüz artık eşleşmelidir [tamamlanan örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Sonuç

Bu öğreticide, web isteklerinde bulunmak, istemcinin sonucu ayrıştırması ve sonuçları özelliklerini görüntülemek nasıl gösterilmiştir. Projenizde bağımlılıklar olarak yeni paketler de ekledik. C# dilinin nesne yönelimli teknikleri destekleyen özelliklerden bazıları gördünüz.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
