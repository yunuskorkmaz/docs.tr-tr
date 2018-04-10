---
title: .NET Core kullanarak bir REST istemcisi oluşturma
description: Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 8cca71b9b8e09fd26f80d53618a3f1e278e28390
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="rest-client"></a>REST istemcisi

## <a name="introduction"></a>Giriş
Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir. Şunları öğreneceksiniz:
*   Temel .NET Core komut satırı arabirimi (CLI).
*   C# dili özelliklerine genel bakış.
*   Bağımlılıkları NuGet ile yönetme
*   HTTP iletişimleri
*   JSON bilgilerini işleme
*   Öznitelikleri yapılandırmayla yönetme. 

HTTP istekleri sorunlarını GitHub üzerinde bir REST hizmeti için bir uygulama oluşturmak. JSON biçiminde bilgileri okuyun ve C# nesnelerini bu JSON paket dönüştürme. Son olarak, C# nesneleriyle çalışmak nasıl görürsünüz.

Bu öğreticide birçok özellik vardır. Şimdi bunları tek tek oluşturun.

İle birlikte izlemek tercih ederseniz [son örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) yönelik bu konu, yükleyebilirsiniz. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar
.NET core çalışmasına, makine ayarlamanız gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası. Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir. Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/), platform Düzenleyicisi arası bir açık kaynak olduğu. Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.
## <a name="create-the-application"></a>Uygulama oluşturma
İlk adım, yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizin oluşturun. Komut türü `dotnet new console` komut isteminde. Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.

Değişiklik yapmaya başlamadan önce basit Hello World uygulamasını çalıştırmak için adımlara edelim. Uygulamayı oluşturduktan sonra yazın `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut isteminde. Bu komut, NuGet paket geri yükleme işlemi çalıştırır. NuGet, bir .NET paketi yöneticisidir. Bu komut, projeniz için eksik bağımlılıklar hiçbirini indirir. Yeni bir proje olarak ilk çalıştırmada .NET Core framework yükleyecek şekilde bağımlılıkları yerinde yok. Bu ilk adımı tamamlandıktan sonra yalnızca çalıştırmanız gerekir `dotnet restore` ([bkz. Not](#dotnet-restore-note)) yeni bağımlı paketler eklediğinizde, veya bağımlılıklarınızı hiçbirini sürümlerini güncelleştirin.  

Paketler geri yükledikten sonra çalıştırmanız `dotnet build`. Bu yapı altyapısı yürütür ve uygulamanızı oluşturur. Son olarak, yürütme `dotnet run` uygulamanızı çalıştırmak için.

## <a name="adding-new-dependencies"></a>Yeni bağımlılıkları ekleme
.NET Core için temel tasarım hedefleri .NET framework yükleme boyutu en aza indirmek için biridir. .NET Core uygulama çerçevesi yalnızca tam .NET framework'ün en yaygın öğeleri içerir. Bir uygulama ek kitaplıklara özelliklerinden bazıları için gerekirse, C# projenize bu bağımlılıkları ekleyin (\*.csproj) dosyası. Bizim örneğimizde, eklemeniz gerekir `System.Runtime.Serialization.Json` uygulamanızın JSON yanıtları işleyebilmek için paket.

Açık, `csproj` proje dosyası. Dosyanın ilk satırı olarak görünmelidir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Bu satırı hemen sonra aşağıdakini ekleyin: 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
Çoğu Kod Düzenleyicisi Bu kitaplıklar farklı sürümlerini tamamlanmasını sağlar. Genellikle eklediğiniz herhangi bir paket en yeni sürümünü kullanmak istersiniz. Bununla birlikte, tüm paketler sürümleri eşleşip eşleşmediğini ve .NET Core uygulama framework'ün sürümünü de eşleştiğinden emin emin olmak önemlidir.

Bu değişiklikleri yaptıktan sonra çalışması gerektiğini `dotnet restore` ([bkz. Not](#dotnet-restore-note)) yeniden böylece paket sisteminizde yüklenir.

## <a name="making-web-requests"></a>Yapma Web istekleri
Artık web sunucusundan veri alma başlatmaya hazırsınız. Bilgileri okuyun bu uygulamada [GitHub API](https://developer.github.com/v3/). Şimdi projeler altında hakkındaki bilgileri okumak [.NET Foundation](http://www.dotnetfoundation.org/) şemsiyesi. Projeler hakkında bilgi almak için GitHub API isteği yaparak başlayacağız. Uç noktası kullanmanız: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos). Bir HTTP GET isteği kullanacağınız için bu projeler, ilgili tüm bilgileri almak istiyor.
Tarayıcınız Ayrıca hangi bilgilerin görmek için URL'yi tarayıcınıza aldığınız, yapıştırabilirsiniz HTTP GET istekleri ve işleme kullanır.

Kullandığınız <xref:System.Net.Http.HttpClient> web isteği yapmak için sınıf. Gibi tüm modern .NET API'leri, <xref:System.Net.Http.HttpClient> , uzun süre çalışan API'ler yalnızca zaman uyumsuz yöntemleri destekler.
Zaman uyumsuz yöntem yaparak başlatın. Uygulamanın işlevselliğini yapı olarak uygulamasında doldurmanız. Başlangıç açarak `program.cs` dosya proje dizininde ve aşağıdaki yöntemi ekleme `Program` sınıfı:

```csharp
private static async Task ProcessRepositories()
{
    
}
```

Eklemeniz gerekir bir `using` en üstündeki deyimi, `Main` yöntemi C# Derleyici tanımasını <xref:System.Threading.Tasks.Task> türü:

```csharp
using System.Threading.Tasks;
```

Projenizi bu noktada yapılandırdıysanız, herhangi bir içermediği için bu yöntem için oluşturulan bir uyarı alırsınız `await` işleçler ve zaman uyumlu olarak çalışır. Şimdilik yoksay; ekleyeceksiniz `await` işleçleri yazarken yönteminde doldurun.

Ardından, tanımlanan ad alanı yeniden adlandırma `namespace` varsayılan from deyimi `ConsoleApp` için `WebAPIClient`. Daha sonra tanımlarız bir `repo` bu ad alanındaki sınıfı.

Ardından, güncelleştirme `Main` yöntemi bu yöntemi çağırın. `ProcessRepositories` Yöntemi bir görev döndürür ve bu görev tamamlanmadan önce programdan çıkmak döndürmemelidir. Bu nedenle, kullanmalısınız `Wait` engellemek ve görevin tamamlanmasını beklemek için yöntemi:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Artık, hiçbir şey yapmaz ancak zaman uyumsuz olarak mevcut bir program var. Şimdi geliştirin.

İlk web üzerinden veri almak yeteneğine sahip bir nesne gerekir; kullanabileceğiniz bir <xref:System.Net.Http.HttpClient> Bunu yapmak için. Bu nesne, istek ve yanıt işler. Bu türde tek bir örneğini `Program` sınıf Program.cs dosyasının içinde.

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

Ayrıca iki eklemeniz gerekecektir yeni bu dosyayı üst derlemek için using deyimleri:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Bu ilk sürüm dotnet foundation kuruluş altındaki tüm depoları listesi okumak için web isteği yapar. (GitHub .NET Foundation için 'dotnet' kimliğidir). İlk birkaç satırı ayarlamak <xref:System.Net.Http.HttpClient> bu istek için. İlk olarak, GitHub JSON yanıtları kabul edecek şekilde yapılandırılır.
Yalnızca JSON biçimidir. Sonraki satıra bir kullanıcı aracısı üstbilgisi tüm istekler bu nesneden ekler. Bu iki üstbilgileri GitHub sunucu kodu tarafından denetlenir ve Github'dan bilgileri almak gereklidir.

Sonra yapılandırdığınız <xref:System.Net.Http.HttpClient>, istek ve yanıt almak web olun. Bu ilk sürümünde kullandığınız <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemi. Bu kolaylık metodunun web istekte bir görev başlatır ve ardından istek geri döndüğünde, yanıt akışına okur ve akış içeriği ayıklar. Yanıt gövdesi olarak döndürülür bir <xref:System.String>. Görev tamamlandığında kullanılabilir bir dizedir. 

Bu yöntem son iki satırı görev bekler ve sonra konsol yanıtı yazdırın.
Uygulama oluşturun ve çalıştırın. Yapı uyarı artık, çünkü kayboluyor `ProcessRepositories` şimdi içeren bir `await` işleci. Biçimlendirilmiş metin JSON uzun görünümünü görürsünüz.   

## <a name="processing-the-json-result"></a>JSON sonuç işleme

Bu noktada, bir web sunucusundan bir yanıt almak ve bu yanıtta bulunan metni görüntülemek için kodu yazdıktan. Ardından, şimdi bu JSON yanıtını C# nesnelerini dönüştürün.

JSON serileştirici JSON verilerini C# nesnelerine dönüştürür. İlk göreviniz bu yanıttan kullandığınız bilgileri içeren bir C# sınıf türü tanımlamaktır. Şimdi bu yavaş depo adını içeren basit bir C# tür ile bunu başlangıç oluşturun:

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

Yukarıdaki kod 'repo.cs' adlı yeni bir dosyada yerleştirin. Bu sınıfın sürümü JSON veri işlemek için en basit yolu temsil eder. Sınıf adı ve üye adı aşağıdaki C# kuralları yerine JSON paketteki kullanılan adları eşleşir. Bazı configuration öznitelikleri daha sonra sağlayarak, düzeltme. Bu sınıf, JSON seri hale getirme ve seri durumdan çıkarma başka bir önemli özelliği gösterilmektedir: JSON paketteki tüm alanlar bu sınıf, bir parçasıdır.
JSON serileştirici kullanılan sınıf türünde bulunmayan bilgileri göz ardı eder.
Bu özellik yalnızca bir alt kümesini JSON paket alanları çalışmak türleri oluşturmak kolaylaştırır.

Türü oluşturduğunuza göre şimdi onu seri durumdan çıkarır. Oluşturmanız gerekecek bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesnesi. Bu nesne CLR türü beklenen JSON paket için bunu bilmelisiniz alır. Github'dan bir dizi depoları, böylece pakette bir `List<repo>` doğru türüdür. Aşağıdaki satırı ekleyin, `ProcessRepositories` yöntemi:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Bu de eklemeniz gerekir böylece iki yeni ad alanı kullanıyorsanız:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Ardından, C# nesnelerini JSON dönüştürmek için seri hale getirici kullanacaksınız. Çağrı Değiştir <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> içinde `ProcessRepositories` aşağıdaki iki satırı yöntemiyle:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Kullanmakta olduğunuz bildirim <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> yerine <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Seri hale getirici bir akış yerine bir dize, kaynağı olarak kullanır. Şimdi, yukarıdaki ikinci satırda kullanılmakta olan birkaç C# dil özellikleri açıklanmaktadır. Bağımsız değişkeni <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> olan bir `await` ifade. Await ifadeleri görünebilir neredeyse her yerden, kodunuzda şimdi kadar yalnızca bunları Atama ifadesinin bir parçası olarak gördüğünüz olsa bile.

İkincisi, `as` işleci dönüştürür derleme zamanı türünden `object` için `List<repo>`. Bildirimi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> türünde bir nesne döndürür bildirir <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Bu oluşturulan, belirttiğiniz türü döndürür (`List<repo>` bu öğreticideki). Dönüştürme başarılı olmazsa, `as` işleci hesaplar için `null`, bir özel durum atma yerine.

Bu bölümde ile bitmek üzere. C# nesnelerini JSON dönüştürdükten, şimdi her depo adını görüntüler. Okuma satırları değiştirin:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

Aşağıdaki ile:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Derleme ve uygulamayı çalıştırın. .NET Foundation parçası olan depoları adları yazdırır.

## <a name="controlling-serialization"></a>Seri hale getirme denetleme

Daha fazla özellik eklemeden önce şimdi adres `repo` yazın ve daha fazla standart C# kurallarına uygun kolaylaştırır. Bu açıklama ekleyerek gerçekleştirirsiniz `repo` ile yazın *öznitelikleri* kontrol eden JSON seri hale getirici nasıl çalışır. Sizin durumunuzda, JSON anahtar adları ve C# sınıfı ve üye adları arasında bir eşleme tanımlamak için bu öznitelikler kullanacaksınız. Kullanılan iki öznitelikleri `DataContract` özniteliği ve `DataMember` özniteliği. Kurala göre tüm öznitelik sınıfları soneki sona `Attribute`. Ancak, bir öznitelik uyguladığınızda, o soneki kullanan gerekmez. 

`DataContract` Ve `DataMember` öznitelikleridir farklı bir kitaplık için bu kitaplığı, C# projesi dosyanızı bağımlılık olarak eklemeniz gerekir. Aşağıdaki satırı ekleyin `<ItemGroup>` proje dosyanızı bölümünü:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Dosyayı kaydettikten sonra çalıştırmak `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bu paketi alınamadı.

Ardından, açık `repo.cs` dosya. Pascal kullanım ve tam adı yazım ad değiştirelim `Repository`. Biz yine eklemeniz gerekir böylece bu türe, JSON 'depodaki' düğümleri eşlemek istediğiniz `DataContract` özniteliği sınıf bildirimi. Ayarlarız `Name` bu türüyle eşleştirmek JSON düğümlerin adı özniteliğine özelliği:

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> Üyesi <xref:System.Runtime.Serialization> uygun eklemeniz gerekir böylece ad alanı, `using` deyimini dosyanın üst:

```csharp
using System.Runtime.Serialization;
```

Adının değişip `repo` sınıfının `Repository`, aynı ad Program.cs içinde değişikliğini yapmanız gerekir (bazı düzenleyicileri otomatik olarak bu değişikliği yapmadan bir yeniden adlandırma düzenlemesi destekleyebilir:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Ardından, aynı değişiklikle olalım `name` kullanarak alan <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı. Aşağıdaki değişiklik bildirimi için `name` repo.cs alanındaki:

```csharp
[DataMember(Name="name")]
public string Name;
```

Bu değişiklik program.cs içinde her depo adını yazar kodunu değiştirmek ihtiyaç duyacağınız anlamına gelir:

```csharp
Console.WriteLine(repo.Name);
```

Yapmak bir `dotnet build` arkasından bir `dotnet run` aldığınız eşlemeleri doğru olduğundan emin olmak. Önce aynı çıkışı görmeniz gerekir. Biz web sunucusundan daha fazla özellik işlemeden önce bir daha fazla değişiklik yapılmasını olalım `Repository` sınıfı. `Name` Üye genel olarak erişilebilir bir alandır. İyi bir nesne yönelimli uygulama değil, bu nedenle, bir özelliğe değiştirelim. Bizim amaçlarla özelliği alırken veya ayarlarken çalıştırmak için özel kod gerekmez, ancak bir özellik için değiştirme kolaylaştırır kullanan herhangi bir kod masraf yapmadan daha sonra bu değişiklikleri eklemek `Repository` sınıfı.

Alan tanımı kaldırın ve bunların yerine bir [otomatik uygulanan özelliği](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Derleyici gövdesini oluşturur `get` ve `set` erişimciler, hem de bir özel alan adı depolamak için. El ile yazabilirsiniz aşağıdaki kodu benzer olacaktır:

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Yeni özellikler eklemeden önce bir daha fazla değişiklik olalım. `ProcessRepositories` Yöntemi zaman uyumsuz iş yapın ve depoları koleksiyonunu döndürür. Şimdi iade `List<Repository>` , yöntemi ve taşıma içine bilgi yazar kod `Main` yöntemi.

İmzasını değiştirmek `ProcessRepositories` sonucu olan bir liste görev dönmek için `Repository` nesneler:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Sonra yalnızca JSON yanıt işledikten sonra depoları döndürün:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Derleyici oluşturur `Task<T>` bu yöntemi olarak işaretlendiğinden için dönüş nesne `async`.
Ardından, değiştirelim `Main` , BT'nin bunlar yakalar şekilde yöntemi sonuçlanır ve her bir havuz adı konsola yazar. `Main` Yöntemi şimdi aşağıdaki gibi görünür:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Erişme `Result` özelliği bir görevin görevin tamamlanmasını engeller. Normalde, tercih `await` giriş olarak görev tamamlandığında `ProcessRepositories` yöntemi, ancak kullanılamaz olarak `Main` yöntemi.

## <a name="reading-more-information"></a>Daha fazla bilgi okuma

Şimdi bu GitHub API'SİNDEN gönderilir JSON paket özelliklerinde, birkaç daha işleyerek tamamlayın. Her şeyi yakalayın istemezsiniz, ancak bazı özellikler ekleme C# dilinin birkaç daha fazla özelliği gösterilmektedir.

Daha fazla birkaç basit türler için ekleyerek başlayalım `Repository` sınıf tanımının. Bu özellikler, sınıfına ekleyin:

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

Bu özellikler hedef türe (olan ne JSON paketleri içeren) dize türünden yerleşik dönüştürmeleri vardır. <xref:System.Uri> Türü için yeni olabilir. Bir URI temsil eder ya da bu durumda, bir URL. Durumunda `Uri` ve `int` türleri, JSON paketi hedef türü dönüştürmez veri içeriyorsa, serileştirme eylem throw bir özel durum.

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
Son adım olarak, son gönderme işlemi için bilgi ekleyelim. Bu bilgiler, JSON yanıt bu şekilde biçimlendirilmiş:

```json
2016-02-08T21:27:00Z
```

Bu biçim herhangi bir standart .NET izlemez <xref:System.DateTime> biçimleri. Bu nedenle özel dönüştürme yöntemi yazma gerekecektir. Kullanıcılara gösterilen ham dizesini de büyük olasılıkla istemediğiniz `Repository` sınıfı. Öznitelikler de bu denetim yardımcı olabilir. İlk olarak tanımlayan bir `private` tarih saat dize gösterimini tutacak özelliği, `Repository` sınıfı:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

`DataMember` Özniteliği bildirir seri hale getirici bu işlenmesi gerektiğini, ortak üyesi olmasa bile. Ardından, geçerli bir dize dönüştürür genel bir salt okunur özelliği yazılamıyor ihtiyacınız <xref:System.DateTime> nesne ve döndüren <xref:System.DateTime>:

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

Yeni yapıları üzerinden edelim. `IgnoreDataMember` Özniteliği, bu tür için okuma veya herhangi bir JSON nesneden yazılmış, seri hale getirici bildirir. Bu özellik yalnızca içeren bir `get` erişimcisi. Var olan hiçbir `set` erişimcisi. Tanımladığınız nasıl olan bir *salt okunur* C# özelliği. (Evet, oluşturabileceğiniz *salt yazılır* C# ancak değerlerine özelliklerinde sınırlıdır.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Yöntemi bir dize ayrıştırır ve oluşturur bir <xref:System.DateTime> sağlanan tarih biçimini kullanarak nesne ve ek meta veri ekler `DateTime` kullanarak bir `CultureInfo` nesnesi. Özellik erişimcisi ayrıştırma işlemi başarısız olursa, bir özel durum oluşturur.

Kullanılacak <xref:System.Globalization.CultureInfo.InvariantCulture>, eklemeniz gerekir <xref:System.Globalization> ad alanına `using` deyimlerinde `repo.cs`:

```csharp
using System.Globalization;
```

Son olarak, bir konsol deyiminde daha çıkış ve oluşturmak ve bu uygulamayı tekrar çalıştırmak hazır ekleyin:

```csharp
Console.WriteLine(repo.LastPush);
```

Sürümünüz artık eşleşmelidir [tamamlanmış örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).
 
## <a name="conclusion"></a>Sonuç

Bu öğreticide web istekleri yapabilir, sonuç ayrıştırma ve bu sonuçlar özelliklerini görüntülemek nasıl oluşturulacağını gösterir. Ayrıca, yeni paketler bağımlılıklar olarak projenizde ekledik. Bazı nesne yönelimli teknikleri destekleyen C# dilinin özelliklerini gördünüz.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
