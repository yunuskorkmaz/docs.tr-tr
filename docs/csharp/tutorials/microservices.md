---
title: Docker içinde - C# barındırılan mikro
description: ASP.NET Docker kapsayıcılarında çalıştırmak Çekirdek Hizmetleri oluşturmayı öğrenin
ms.date: 02/03/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 7428051c1d9a29ba98ca1f28288b3c50ea36ae1a
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="microservices-hosted-in-docker"></a>Docker içinde barındırılan mikro

Bu öğretici oluşturmak ve ASP.NET Core mikro Docker kapsayıcısı içinde dağıtmak gerekli görevlerin ayrıntılarını verir. Bu öğreticinin sürecinde şunları öğreneceksiniz:

* Yeoman kullanarak bir ASP.NET Core uygulama oluşturma
* Bir geliştirme Docker ortamı oluşturma
* Varolan bir görüntüyü temel alarak bir Docker görüntü oluşturma.
* Nasıl bir Docker kapsayıcıya hizmetinizi dağıtılır.

Yol boyunca bazı C# dil özellikleri görürsünüz:

* C# nesnelerini JSON yüklerini dönüştürmek nasıl.
* Sabit veri aktarım nesneleri oluşturma
* Gelen HTTP isteklerini işleyen ve HTTP yanıtı oluşturmak nasıl
* Boş değer atanabilen değer türleri ile çalışma

Yapabilecekleriniz [görüntüleyebilir veya örnek uygulama indirebilirsiniz](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) Bu konu için. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="why-docker"></a>Neden Docker?

Docker hizmetlerinizi bir veri merkezinde barındırılacağını standart makine görüntülerini oluşturmak kolaylaştırır veya genel bulut. Docker yapılandırma resmi ve yükleme, uygulamanızın ölçeklendirmek için gerektiği şekilde çoğaltmak etkinleştirir.

Bu öğreticideki tüm kod tüm .NET Core ortamlarında çalışır.
Docker yükleme için ek görevler için bir ASP.NET Core uygulama çalışır. 

## <a name="prerequisites"></a>Önkoşullar
.NET core çalışmasına, makine Kurulum gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.
Bu uygulama, Windows, Ubuntu Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir. Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu. Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.

Docker altyapısına yüklemek gerekir. Bkz: [Docker yükleme sayfası](http://www.docker.com/products/docker) platformunuza ilişkin yönergeler için.
Docker, birçok Linux dağıtımları, macOS veya Windows yüklenebilir. Yukarıda başvurulan sayfa her bir kullanılabilir yüklemeler bölümleri içerir.

Çoğu bileşenin yüklü olmasını bir paket yöneticisi tarafından yapılır. Node.js'ın Paket Yöneticisi varsa `npm` yüklü bu adımı atlayabilirsiniz. Aksi takdirde son NodeJs gelen yükleyin [nodejs.org](https://nodejs.org) npm Paket Yöneticisi'ni yükler. 

Bu noktada bir dizi ASP.NET core geliştirme desteği komut satırı araçları yüklemeniz gerekir. Komut satırı şablonlarını Yeoman, Bower, Grunt ve Gulp kullanın. Aksi takdirde bunları yüklü iyi olan varsa, sık kullanılan kabuğundan aşağıdaki komutu yazın:

`npm install -g yo bower grunt-cli gulp`

`-g` Seçeneği gösteren bir genel yükleme olduğunu ve bu araçlar kullanılabilir sistem genelinde. (Yerel bir yükleme paketi tek bir proje kapsamları). Bu çekirdek araçları yükledikten sonra yeoman ASP.NET şablon oluşturucuları yüklemeniz gerekir:

`npm install -g generator-aspnet`

## <a name="create-the-application"></a>Uygulama oluşturma

Tüm Araçlar yüklediniz, yeni bir ASP.NET Core uygulaması oluşturun. Komut satırı Oluşturucu kullanmak için sık kullanılan Kabuğu'nda aşağıdaki yeoman komutu yürütün:

`yo aspnet`

Bu komutun ne tür bir uygulama oluşturmak istediğiniz seçmenizi ister. Bu mikro hizmet için basit ve en basit bir web uygulaması olası istediğiniz, bu nedenle 'Boş Web uygulaması' seçin. Şablon için bir ad ister. 'WeatherMicroservice' seçin. 

Şablon sekiz dosyaları oluşturur:

* ASP.NET Core uygulamaları için özelleştirilmiş bir .gitignore.
* Haline dosya. Bu uygulamanın temel içerir.
* Program.cs dosyasının. Bu uygulama giriş noktasını içerir.
* Bir WeatherMicroservice.csproj dosyası. Bu uygulama için yapı dosyasıdır.
* Bir Dockerfile. Bu komut, uygulama için bir Docker görüntü oluşturur.
* Bir README.md. Bu, diğer ASP.NET Core kaynaklarına bağlantılar içerir.
* Bir web.config dosyası. Bu, temel yapılandırma bilgilerini içerir.
* Bir runtimeconfig.template.json dosyası. IDE tarafından kullanılan hata ayıklama ayarları içerir.

Şimdi oluşturulan şablon uygulamayı çalıştırabilirsiniz. Bir dizi komut satırından araçları kullanarak yapmıştır. `dotnet` Komutu .NET geliştirme için gerekli araçları çalıştırır. Farklı bir komut her fiil çalıştırır

Tüm bağımlılıkları geri yüklemek için ilk adımdır bakın:

```console
dotnet restore
```

DotNet geri yükleme NuGet Paket Yöneticisi uygulama dizine tüm gerekli paketleri yüklemek için kullanır. Ayrıca, bir project.json.lock dosyası oluşturur. Bu dosya, başvurulan her paketi hakkında bilgi içerir. Tüm bağımlılıkları geri yüklendikten sonra uygulamayı derlediğinizde:

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Ve uygulama yapı sonra komut satırından çalıştırın:

```console
dotnet run
```

Varsayılan yapılandırma dinler `http://localhost:5000`. Bir tarayıcıda açabilir ve bu sayfaya gidin ve bir "Hello World!" konusuna bakın İleti.

### <a name="anatomy-of-an-aspnet-core-application"></a>Bir ASP.NET Core uygulama anatomisi

Uygulama oluşturduğunuza göre bu işlev nasıl uygulandığı konumundaki bakalım. Bu noktada özellikle ilginç oluşturulan dosyalar iki vardır: project.json ve haline. 

Project.JSON, proje hakkında bilgi içerir. Genellikle ile karşılaşmayacağınızı iki düğüm 'bağımlılıkları' ve 'çerçeveleri' dir. Bağımlılıklar düğümü bu uygulama için gerekli olan tüm paketleri listeler.
Şu anda bu web sunucusu çalıştıran paketleri ihtiyaç duyan, küçük bir düğümü olduğu.

'Çerçeveler' düğümü sürümleri ve bu, uygulamanın çalıştırılacağı .NET framework'ün yapılandırmaları belirtir.

Uygulama haline içinde uygulanır. Bu dosya başlangıç sınıfı içerir.

İki yöntem yapılandırmak ve uygulamayı çalıştırmak için ASP.NET Core altyapısı tarafından çağrılır. `ConfigureServices` Yöntemi bu uygulama için gerekli hizmetleri açıklar. Bağımlılıkları yapılandırmak gerekli olmayan şekilde yalın mikro hizmet oluşturmakta olduğunuz. `Configure` Yöntemi işleyiciler gelen HTTP isteklerini yapılandırır. Şablon 'Hello World!' metinle herhangi bir istek için yanıt veren basit bir işleyici oluşturur.

## <a name="build-a-microservice"></a>Bir mikro hizmet oluşturma

Giderek oluşturmak için hizmet hava raporları yerden teslim eder dünya. Bir üretim uygulamasında hava durumu verilerini almak için bazı hizmet çağırırdı. Bizim örnek için size rastgele hava tahmini oluşturacaksınız. 

Rastgele hava durumu hizmetimizi uygulamak üzere gerçekleştirmeniz gereken görevler vardır:

* Enlem ve boylam okumak için gelen istek ayrıştırılamıyor.
* Bazı rastgele tahmin verilerini oluşturur.
* Bu rastgele tahmin verilerini C# nesnelerden JSON paketlere dönüştürün.
* Hizmet gönderir JSON geri belirtmek için yanıt üstbilgisi ayarlayın.
* Yanıt yazma.

Sonraki bölümlerde, bu adımların her biri yol.

### <a name="parsing-the-query-string"></a>Sorgu dizesini ayrıştırma.

Sorgu dizesini ayrıştırarak başlarsınız. Hizmeti, 'lat' ve 'uzun' bağımsız değişkeni bu formda sorgu dizesini kabul eder:

`http://localhost:5000/?lat=-35.55&long=-12.35`  

Bağımsız değişken olarak tanımlanan lambda ifadesi almanız gereken tüm değişiklikleri bulunan `app.Run` başlangıç sınıfınızda.

Lambda ifadesi bağımsız değişkeni `HttpContext` istek için. Özelliklerinden biri olan `Request` nesnesi. `Request` Nesnesi bir `Query` istek için sorgu dizesinde tüm değerlerin sözlüğü içeren özelliği. Enlem ve boylam değerlerini bulmak için ilk ektir bakın:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

Sorgu sözlük değerler `StringValue` türü. Bu tür dizeleri koleksiyonu içerebilir. Hava durumu hizmetiniz için her bir değer tek bir dizedir. İşte çağrısı yok `FirstOrDefault()` Yukarıdaki kod. 

Ardından, çiftleri için dizeleri dönüştürmeniz gerekir. Dize için bir çift dönüştürmek için kullanılan yöntemi `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Bu yöntem C# out Parametreleri giriş dizesi bir double dönüştürülüp dönüştürülemeyeceğini belirtmek için yararlanır. Dize çift türü için geçerli bir temsili temsil ediyorsa, yöntem true döndürür ve `result` bağımsız değişken değeri içerir. Dize geçerli bir çift göstermiyor varsa yöntemi false değerini döndürür.

Bu API kullanarak uyarlayabilirsiniz bir *genişletme yöntemi* döndüren bir *boş değer atanabilir çift*. A *boş değer atanabilir değer türü* bazı değer türü temsil eden bir tür olduğundan ve ayrıca eksik tutun veya null değer. Boş değer atanabilir bir tür ekleyerek temsil edilen `?` türü bildirimi karakter. 

Genişletme yöntemleri statik yöntemler, ancak ekleyerek tanımlanan yöntemlerdir `this` o sınıfın üyeleri olsa gibi ilk parametre değiştirici çağrılamaz. Genişletme yöntemleri yalnızca statik sınıflarda tanımlanabilir. Ayrıştırma için genişletme yöntemi içeren sınıf tanımını şöyledir:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

`default(double?)` İfade için varsayılan değeri döndürür `double?` türü. Değeri null (ya da eksik) bu varsayılan değerdir.

Sorgu dizesi bağımsız değişkenleri çift türüne dönüştürmek için bu genişletme yöntemi kullanabilirsiniz:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Kolayca ayrıştırma kodu test etmek için bağımsız değişkenlerin değerlerini dahil etmek için yanıt güncelleştirin:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

Bu noktada, web uygulamasını çalıştırın ve ayrıştırma kodunuzu çalışıp çalışmadığını. Bir tarayıcıda web isteğine değerlerini ekleyin ve güncelleştirilmiş sonuçları görmeniz gerekir.

### <a name="build-a-random-weather-forecast"></a>Rastgele bir hava durumu tahmini derleme

Sonraki göreviniz rastgele hava tahmini oluşturmaktır. Hava tahmini için istediğiniz değerleri içeren bir veri kapsayıcısı ile başlayalım tıklatın:

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

Ardından, bu değerleri rastgele ayarlar bir oluşturucu oluşturun. Bu oluşturucu, rastgele sayı üreticisinin oluşturmak için enlem ve boylam değerlerini kullanır. Aynı konuma tahmin aynı olduğu anlamına gelir. Enlem ve boylam bağımsız değişkenleri değiştirirseniz, (farklı çekirdek ile başlatmak için.), farklı bir tahmin elde edersiniz

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Bu gibi durumlarda, 5 gün tahmin şimdi yanıt yönteminizi oluşturabilirsiniz:

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a>JSON yanıt oluşturun.

Son kodu sunucuda WeatherReport dizi JSON pakete dönüştürmek ve bu istemciye göndermek için bir görevdir. JSON paket oluşturarak başlayalım. Bağımlılıklar listesine NewtonSoft JSON seri hale getirici ekleyeceksiniz. Bu kullanarak yapabilirsiniz `dotnet` CLI:

```
dotnet add package Newtonsoft.Json
```

Ardından, kullanabileceğiniz `JsonConvert` dizeye nesne yazmak için sınıf:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Yukarıdaki kod tahmin nesne dönüştürür (listesini `WeatherForecast` nesneler) JSON paket. Yanıt paketi oluşturduktan sonra içerik türü ayarlayın `application/json`ve dize yazma.

Uygulamayı şimdi çalıştırır ve rastgele tahminlerini döndürür.

## <a name="build-a-docker-image"></a>Docker yansıması oluştur

Bizim son Docker içinde uygulamayı çalıştırmak için bir görevdir. Uygulamamız temsil eden bir Docker görüntü çalışan bir Docker kapsayıcısı oluşturacağız.

A ***Docker görüntü*** uygulamayı çalıştırmak için ortam tanımlayan bir dosyadır.

A ***Docker kapsayıcısı*** Docker görüntü çalışan bir örneğini temsil eder.

Benzerleme tarafından düşünebilirsiniz *Docker görüntü* olarak bir *sınıfı*ve *Docker kapsayıcısı* bir nesne ya da bu sınıfının bir örneği olarak.  

ASP.NET şablonu tarafından oluşturulan Dockerfile bizim amacıyla hizmet verecektir. Şimdi içeriğinin gidin.

İlk satırı kaynak görüntü belirtir:

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

Docker kaynak şablonunu temel alan bir makine görüntüsünün yapılandırmanıza olanak sağlar. Başlattığınızda tüm makine parametreler sağlamanız gerekmez anlamına yalnızca herhangi bir değişiklik sağlamanız gerekir. Değişiklikler burada uygulamamız eklenecek.

Bu ilk örnekte kullanacağız `1.1-sdk-msbuild` dotnet görüntüsü. Bu, çalışan bir Docker ortamı oluşturmak için en kolay yoludur. Bu görüntü dotnet çekirdeği çalışma zamanı ve SDK dotnet kapsar. Kolaylaştırır başlamak ve yapı, ancak daha büyük bir görüntü oluşturun.

Sonraki beş satır Kurulum ve uygulamanızı oluşturun:

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroService.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Bu proje dosyası Docker VM geçerli dizinden kopyalayın ve tüm paketler geri yükleme. Dotnet CLI kullanarak Docker görüntünün .NET Core SDK içermelidir anlamına gelir. Bundan sonra uygulamanızın rest kopyalanan ve dotnet komutu yapılar ve paketleri uygulamanızı yayımlayın.

Dosyanın son satırının uygulama çalışır:

```
ENTRYPOINT ["dotnet", "out/WeatherMicroService.dll", "--server.urls", "http://0.0.0.0:5000"]
```

Bu yapılandırılan bağlantı noktası başvuru `--server.urls` bağımsız değişkeni `dotnet` Dockerfile son satırında. `ENTRYPOINT` Komut hangi komut ve komut satırı seçenekleri hizmeti başlatmak Docker bildirir. 

## <a name="building-and-running-the-image-in-a-container"></a>Oluşturma ve görüntüyü bir kapsayıcıda çalıştırma.

Şimdi bir görüntü oluşturun ve Docker kapsayıcısı içinde hizmet çalıştırın. Yerel dizininizdeki görüntüsüne kopyalanan tüm dosyaları istemezsiniz. Bunun yerine, kapsayıcı uygulamada yapı. Oluşturacağınız bir `.dockerignore` dosya görüntüsüne kopyalanmaz dizinleri belirtin. Kopyalanan yapı varlıklar istemezsiniz. Yapı belirtin ve dizinlerde yayımlayın `.dockerignore` dosyası:

```
bin/*
obj/*
out/*
```

Görüntü kullanarak yapı `docker build` komutu. Kodunuzu içeren dizininden aşağıdaki komutu çalıştırın.

```console
docker build -t weather-microservice .
```

Bu komut, Dockerfile içindeki tüm bilgileri temel kapsayıcı görüntüsü oluşturur. `-t` Bağımsız değişkeni bir etiket veya bu kapsayıcı görüntü adı sağlar. Yukarıdaki komut satırında, Docker kapsayıcısı için kullanılan etiketi olan `weather-microservice`. Bu komut tamamlandığında, yeni hizmetinizi çalıştırılmaya hazır bir kapsayıcıya sahip. 

Kapsayıcı başlatmak ve hizmetinizi başlatmak için aşağıdaki komutu çalıştırın:

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

`-d` Geçerli terminal durumundan ayrılmış kapsayıcı çalıştırmak seçenek anlamına gelir. Terminalinizde komut çıktısı görmezsiniz anlamına gelir. `-p` Seçeneği, hizmet ve ana bilgisayar arasında bağlantı noktası eşleme gösterir. Burada herhangi bir gelen istek bağlantı noktası 80 üzerinde bağlantı noktası 5000 kapsayıcısı üzerinde iletilmesi gereken yazacaktır. 5000 kullanarak yukarıdaki Dockerfile belirtilen komut satırı bağımsız değişkenleri gelen üzerinde hizmetinizi dinleme bağlantı noktası ile eşleşir. `--name` Bağımsız değişken adları, çalışan kapsayıcı. Bu kapsayıcı ile çalışmak için kullanabileceğiniz bir kolay adıdır. 

Görüntü komutu denetleyerek çalışıp çalışmadığını görebilirsiniz:

```console
docker ps
```

Kapsayıcı çalışıyorsa, çalışan işlemler listeleyen bir satırı görürsünüz. (Yalnızca biri olabilir).

Bir tarayıcıda açmak ve localhost için gezinme ve enlem ve boylam belirterek hizmetinizi test edebilirsiniz:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Çalışan bir kapsayıcı ekleme

Bir komut penceresinde, hizmeti çalıştırdığınızda, her istek için yazdırılan tanılama bilgileri görebilir. Kapsayıcı ayrılmış modda çalışırken bu bilgileri görmüyorum. Docker komut ekleme, günlük bilgilerini görebilmeniz için çalışan bir kapsayıcıya eklenecek sağlar.  Bir komut penceresinde aşağıdaki komutu çalıştırın:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Bağımsız değişkeni anlamına `Ctrl-C` komutları kapsayıcı işleme gönderilen değil, ancak yerine Durdur `docker attach` komutu. Son bağımsız değişkeni kapsayıcısında verilen addır `docker run` komutu. 

> [!NOTE]
> Kapsayıcı kimliği atanan Docker, herhangi bir kapsayıcıya başvurmak için de kullanabilirsiniz. Kapsayıcı için bir ad belirtirseniz kaydetmedi `docker run` kapsayıcı kimliği kullanmanız gerekir.

Bir tarayıcı açın ve hizmetinize gidin. Tanılama iletileri ekli çalışan kapsayıcısından komutu Windows görürsünüz.

Tuşuna `Ctrl-C` ekleme işlemi durdurmak için.

İşiniz bittiğinde, kapsayıcı ile çalışma, durdurabilirsiniz:

```console
docker stop hello-docker
```

Kapsayıcı ve görüntü yeniden başlatmak için hala mevcut değil.  Kapsayıcı makinenizden kaldırmak istiyorsanız, bu komutu kullanın:

```console
docker rm hello-docker
```

Kullanılmayan görüntüleri makinenizden kaldırmak istiyorsanız, bu komutu kullanın:

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>Sonuç 

Bu öğreticide ASP.NET Core mikro hizmet yerleşik ve birkaç basit özellikler eklenir.

Bir Docker kapsayıcısı görüntü hizmetin yerleşik ve bu kapsayıcı, makinenizde çalıştı. Bir terminal penceresi hizmete bağlı ve tanılama iletileri hizmetinizden gördünüz.

Yol boyunca eylem C# dilinin çeşitli özellikler gördünüz.
