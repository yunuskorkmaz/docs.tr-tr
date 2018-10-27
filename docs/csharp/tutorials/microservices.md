---
title: Docker içinde barındırılan mikro Hizmetleri-C#
description: ASP.NET Docker kapsayıcılarında çalıştıracak bir Çekirdek Hizmetleri oluşturmayı öğrenin
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b1f7159a222ab4d68715844e9997ca922676bc80
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454492"
---
# <a name="microservices-hosted-in-docker"></a>Docker içinde barındırılan mikro hizmetler

Bu öğreticide oluşturun ve bir Docker kapsayıcısında bir ASP.NET Core mikro hizmet dağıtmak için gereken görevler açıklanmaktadır. Bu öğreticide Kurs sırasında şunları öğreneceksiniz:

* Bir ASP.NET Core uygulaması oluşturmak nasıl.
* Docker geliştirme ortamı oluşturma
* Mevcut bir görüntüyle bir Docker görüntüsünü oluşturmak nasıl.
* Hizmetiniz bir Docker kapsayıcısına dağıtma

Bu doğrultuda, ayrıca bazı görürsünüz C# dil özellikleri:

* Dönüştürme C# JSON yükü nesneleri.
* Sabit veri aktarımı nesneleri oluşturmak nasıl.
* HTTP yanıtı oluşturur ve gelen HTTP isteklerini işlemek nasıl.
* Boş değer atanabilen değer türleri ile çalışmayı öğrenin.

Yapabilecekleriniz [görüntülemek veya örnek uygulamasını indirin](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) için bu konuda. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="why-docker"></a>Neden Docker?

Docker hizmetlerinizi bir veri merkezinde barındırılacağını standart makine görüntülerini oluşturmak kolaylaştırır ve genel bulut. Docker görüntüsü yapılandırmak ve uygulamanın yüklenmesi ölçeklendirmek için gerektiği şekilde çoğaltmak sağlar.

Bu öğreticideki tüm kod herhangi bir .NET Core ortamında çalışır.
Docker yükleme için ek görevler, bir ASP.NET Core uygulaması için çalışır. 

## <a name="prerequisites"></a>Önkoşullar

.NET Core çalıştırmak için makinenizi ayarlamak gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.
Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.
Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir. Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu. Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.

Docker Altyapısı'nı gerekecektir. Bkz: [Docker yükleme sayfası](https://docs.docker.com/install/overview/) platformunuza yönelik yönergeler.
Docker, çok sayıda Linux dağıtımlarına, macOS veya Windows yüklenebilir. Yukarıda anılan sayfa her kullanılabilir yüklemeler bölümler içeriyor.

## <a name="create-the-application"></a>Uygulama oluşturma

Tüm Araçlar yüklediğinize göre sık kullanılan shell'de aşağıdaki komutu yürüterek "WeatherMicroservice" adlı bir dizinde yeni bir ASP.NET Core uygulaması oluşturun:

```console
dotnet new web -o WeatherMicroservice
```

`dotnet` .NET geliştirme için gerekli araçları komutu çalıştırır. Her bir fiil, farklı bir komutu yürütür.

`dotnet new` .Net Core oluşturmak için kullanılan komut projeleri.

`-o WeatherMicroservice` Sonra seçeneği `dotnet new` komutu, ASP.NET Core uygulaması oluşturmak için konum vermek için kullanılır.

"ASP.NET Core boş" şablonu kısa adını belirterek kullandığımız için bu mikro hizmet için basit ve en basit bir web uygulaması mümkün istiyoruz `web`.

Şablon dört dosyaları sizin için oluşturur:

* Startup.cs dosya. Bu, uygulamanın temel içerir.
* Program.cs dosyasının bir. Bu, uygulamanın giriş noktasını içerir.
* WeatherMicroservice.csproj dosya. Bu uygulama için derleme dosyasıdır.
* Properties/launchSettings.json dosya. Bu, IDE'ler tarafından kullanılan hata ayıklama ayarları içerir.

Artık şablon oluşturulan uygulamayı çalıştırabilirsiniz:

```console
dotnet run
```

Bu komut, ilk uygulamayı oluşturmak için gerekli bağımlılıkları geri yükler ve ardından uygulamayı oluşturacaksınız.

Varsayılan yapılandırma dinleyen `http://localhost:5000`. Bir tarayıcıda açabilir ve söz konusu sayfaya gidin ve bir "Hello World!" konusuna bakın. İleti.

İşiniz bittiğinde tuşlarına basarak uygulamayı kapatabilirsiniz <kbd>Ctrl</kbd>+<kbd>C</kbd>.

### <a name="anatomy-of-an-aspnet-core-application"></a>Bir ASP.NET Core uygulaması anatomisi

Uygulamayı oluşturduğunuza göre bu işlevselliği nasıl uygulandığını konumunda göz atalım. Bu noktada özellikle ilgi çekici oluşturulan dosyaların iki: WeatherMicroservice.csproj ve Startup.cs. 

.Csproj dosyasını proje hakkında bilgi içerir.
En ilginç iki düğümler `<TargetFramework>` ve `<PackageReference>`.

`<TargetFramework>` Düğümü Bu, uygulamanın çalıştırılacağı .NET sürümünü belirtir.

Her `<PackageReference>` düğüm, bu uygulama için gerekli olan bir paketi belirtmek için kullanılır.

Uygulama, Startup.cs içinde uygulanır. Bu dosya, başlangıç sınıfı içerir.

İki yöntem yapılandırmak ve uygulamayı çalıştırmak için ASP.NET Core altyapısı tarafından çağrılır. `ConfigureServices` Yöntemi, bu uygulama için gerekli olan hizmetlerini açıklar. Herhangi bir bağımlılığın yapılandırmak gerekli olmayan şekilde yalın bir mikro hizmet oluşturuyorsunuz. `Configure` Yöntemi için gelen HTTP isteklerini işleyicileri yapılandırır. Şablon 'Hello World!' metin herhangi bir istekle yanıt veren basit bir işleyici oluşturur.

## <a name="build-a-microservice"></a>Bir mikro hizmet oluşturun

İlerlememesi ileride oluşturmak için hizmet hava durumu raporları yerden verecektir dünya. Bir üretim uygulamasında, hava durumu verilerini almak için bazı hizmet çağırırsınız. Bizim Örneğimiz için rastgele bir hava durumu tahminini başlığında oluşturacağız. 

Birkaç rastgele hava durumu hizmetimiz uygulamak için gerçekleştirmeniz gereken görevler şunlardır:

* Enlem ve boylamını okumak için gelen istek ayrıştırılamıyor.
* Bazı rastgele tahmin veriler oluşturur.
* Bu rastgele tahmin verilerden dönüştürme C# JSON paketleri nesneleri.
* Yanıt üst bilgisi, hizmet gönderir JSON geri belirtmek üzere ayarlayın.
* Yanıt yazın.

Sonraki bölümlerde, bu adımların her biri yol.

### <a name="parsing-the-query-string"></a>Sorgu dizesini ayrıştırma

Sorgu dizesini ayrıştırarak başlarsınız. Hizmet, 'lat' ve 'uzun' bağımsız değişkenleri bu formda sorgu dizesini kabul eder:

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

Lambda ifadesi bağımsız değişkeni olarak tanımlanan almanız gereken tüm değişiklikleri bulunan `app.Run` başlangıç sınıfınızdaki.

Lambda ifadesi bağımsız değişkeni `HttpContext` istek için. Kendi özelliklerinden biri `Request` nesne. `Request` Nesnesinin bir `Query` özelliği içeren bir istek için sorgu dizesini tüm değerlerin sözlüğü. Enlem ve boylam değerleri bulmak için ilk toplama şöyledir:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

`Query` Sözlük değerler `StringValue` türü. Bu tür, dizelerden oluşan bir koleksiyonu içerebilir. Hava durumu hizmetiniz için her değeri tek bir dizedir. İşte bu çağrı yoktur `FirstOrDefault()` Yukarıdaki kod. 

Ardından, Double için dizeleri dönüştürmek gerekir. Double'a dize dönüştürmek için kullanacağınız yöntemdir `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Bu yöntem yararlanır C# out parametreleri için bir double dönüştürülebilir giriş dizesini belirtmek için. Dize geçerli bir çift temsili temsil ediyorsa true, döner ve `result` bağımsız değişken değeri içerir. Yöntemi, dize geçerli bir çift göstermiyor değilse false döndürür.

Bu API kullanımı ile uyum sağlayabilen bir *genişletme yöntemi* döndüren bir *boş değer atanabilir çift*. A *null değer türü* bazı değer türünü temsil eden bir türdür ve ayrıca bir eksik tutun veya null değeri. Boş değer atanabilir bir tür eklenerek temsil edilen `?` türü bildirimi için karakter. 

Genişletme yöntemleri statik yöntemler, ancak ekleyerek tanımladığınız yöntemlerdir `this` ilk parametre değiştiricisi, sınıf üyesi olduğu gibi sorgulamanıza çağrılabilir. Uzantı yöntemleri yalnızca statik sınıf içinde tanımlanabilir. Ayrıştırma için genişletme yöntemi içeren sınıf tanımı aşağıda verilmiştir:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

Genişletme yöntemi çağrılmadan önce geçerli kültürü için sabit değiştirin:

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

Bu, uygulama ayrıştırıyor numaralarının aynı varsayılan kültürünü bağımsız olarak herhangi bir sunucuda sağlar.

Artık sorgu dizesi bağımsız değişkenleri çift türüne dönüştürmeye genişletme yöntemini kullanabilirsiniz:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Kolayca ayrıştırma kodunu test etmek için bağımsız değişkenlerin değerlerini dahil etmek için yanıt güncelleştirin:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

Bu noktada, web uygulamasını çalıştırmak ve ayrıştırma kodunuzu çalışıp çalışmadığını. Bir tarayıcıda web isteği değerlerini ekleyin ve güncelleştirilmiş sonuçları görmeniz gerekir.

### <a name="build-a-random-weather-forecast"></a>Rastgele bir hava durumu tahminini oluşturun

Sonraki göreviniz, rastgele bir hava durumu tahminini oluşturmaktır. Bir hava durumu tahminini istediğiniz değerleri içeren bir veri depolayıcı başlayalım:

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

Ardından, bu değerleri rastgele ayarlayan bir oluşturucu oluşturun. Bu oluşturucu, enlem ve boylam çekirdek için değerleri kullanır. `Random` sayı üreteci. Bu tahmin aynı konumu için aynı anlamına gelir. Enlem ve boylamını bağımsız değişkenleri değiştirirseniz (farklı bir çekirdek ile başlatma için) farklı bir tahmin alırsınız.

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Bu gibi durumlarda, 5 günlük hava durumu tahminini artık yanıt yönteminizi oluşturabilirsiniz:

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a>JSON yanıtı oluşturun

Sunucuda son kod görev dönüştürülür `WeatherReport` listesine JSON belgesini ve istemciye gönderme. JSON belgesini oluşturarak başlayalım. Bağımlılıklar listesine Newtonsoft JSON serileştirici ekleyeceksiniz. Aşağıdakileri kullanarak bunu yapabilirsiniz `dotnet` komutu:

```console
dotnet add package Newtonsoft.Json
```

Daha sonra kullanabileceğiniz `JsonConvert` sınıfı nesne için bir dize yazmak için:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Yukarıdaki kod tahmin nesne dönüştürür (listesini `WeatherForecast` nesneleri) JSON belgesine. Yanıt belge oluşturduktan sonra içerik türü ayarlayın `application/json`ve dizeyi yazın.

Uygulama artık çalışır ve rastgele tahminlerini döndürür.

## <a name="build-a-docker-image"></a>Bir Docker görüntüsü oluşturun

Bizim son Docker uygulamayı çalıştırmak için bir görevdir. Uygulamamızı temsil eden bir Docker görüntüsü çalıştıran bir Docker kapsayıcı oluşturacağız.

A ***Docker görüntüsü*** uygulamayı çalıştırmak için ortamı tanımlayan bir dosyadır.

A ***Docker kapsayıcısı*** bir Docker görüntüsü çalışan bir örneğini temsil eder.

Benzerleme tarafından kadar aklınıza gelebilecek *Docker görüntüsü* olarak bir *sınıfı*ve *Docker kapsayıcısı* bir nesne veya söz konusu sınıfın bir örneği.  

Aşağıdaki Dockerfile, amaçlarımız doğrultusunda kullanılacak:

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Şimdi içeriğini geçelim.

İlk satırı, uygulama oluşturmak için kullanılan kaynak görüntüyü belirtir:

```
FROM microsoft/dotnet:2.1-sdk AS build
```

Docker, kaynak şablonu temel alan bir makine görüntüsü yapılandırmanıza olanak sağlar. Başlattığınızda, tüm makine parametreleri sağlamak zorunda olmadığınız anlamına yalnızca herhangi bir değişiklik sağlamanız gerekir. Uygulamamızı dahil etmek için değişiklikleri buraya olacaktır.

Bu örnekte, kullanacağız `2.1-sdk` sürümünü `dotnet` görüntü. Bu, çalışan bir Docker ortamında oluşturmak için en kolay yoludur. Bu görüntü, .NET Core çalışma zamanı ve .NET Core SDK'sını içerir.
Sayede başlamak ve derleme, ancak bu görüntü uygulama ve farklı bir görüntü oluşturmak için bunu kullanacağız için daha büyük bir görüntü oluşturun.

Sonraki satırı Kur ve uygulamanızı:

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

Bu proje dosyası için Docker VM geçerli dizinden kopyalayın ve tüm paketleri geri yükle. Dotnet CLI kullanılarak Docker görüntüsünü .NET Core SDK'sını içermelidir anlamına gelir. Bundan sonra uygulamanızın rest kopyalanır ve `dotnet
publish` komut oluşturur ve uygulama paketleri.

Son olarak, uygulamayı çalıştıran ikinci bir Docker görüntüsü oluşturun:

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Bu görüntüyü kullanan `2.1-aspnetcore-runtime` sürümünü `dotnet` ASP.NET Core uygulamaları çalıştırmak için gereken her şeyi içerir, ancak .NET Core SDK'sını içermeyen bir görüntü. Başka bir deyişle, bu görüntü, .NET Core uygulamaları oluşturmak için kullanılamaz, ancak Ayrıca son görüntü daha küçük olur.

Bunun çalışmasını sağlamak için biz oluşturulan uygulamayı ilk görüntüden ikinci birine kopyalayın.

`ENTRYPOINT` Komut Docker hizmeti hangi komut başlatır bildirir.

## <a name="building-and-running-the-image-in-a-container"></a>Oluşturma ve bir kapsayıcıda görüntünün çalıştırma

Şimdi bir görüntü oluşturun ve bir Docker kapsayıcısı içinde hizmet. Görüntüye kopyalanan yerel dizininizden tüm dosyaları istemezsiniz. Bunun yerine, uygulama kapsayıcısında oluşturacaksınız. Oluşturacağınız bir `.dockerignore` görüntüye kopyalanmaz dizinleri belirlemek için dosya. Kopyalanan derleme varlıkları istemezsiniz. Bir derleme belirleyin ve dizinlerde yayımlama `.dockerignore` dosyası:

```
bin/*
obj/*
out/*
```

Kullanarak yapı `docker build` komutu. Kodunuzu içeren dizininden aşağıdaki komutu çalıştırın.

```console
docker build -t weather-microservice .
```

Bu komut Dockerfile içindeki tüm bilgileri temel alan bir kapsayıcı görüntüsü oluşturur. `-t` Bağımsız değişkeni, bir etiket ya da bu kapsayıcı görüntüsü için bir ad sağlar. Yukarıdaki komut satırında Docker kapsayıcısı için kullanılan etikettir `weather-microservice`. Bu komut tamamlandığında, hizmetinizin yeni çalıştırmaya hazır bir kapsayıcı vardır. 

Kapsayıcı başlatın ve hizmetinizi başlatmak için aşağıdaki komutu çalıştırın:

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

`-d` Geçerli terminalden ayrılmış kapsayıcıyı çalıştırmak seçenek anlamına gelir. Komut çıktısı terminalinizde görmezsiniz anlamına gelir. `-p` Seçeneği, hizmet ile konak arasındaki bağlantı noktası eşlemesi gösterir. Burada 80 numaralı bağlantı noktasına gelen tüm istekler kapsayıcı üzerindeki 80 numaralı bağlantı noktasına iletilen olduğunu söylüyor. Eşleşen hizmetinizi dinlediği bağlantı üretim uygulamaları için varsayılan bağlantı noktası 80'i kullanarak. `--name` Çalışan kapsayıcınıza bağımsız değişken adları. Bu, bu kapsayıcı ile çalışmak için kullanabileceğiniz, kullanışlı bir addır.

Görüntü komutu denetleyerek çalışıp çalışmadığını görebilirsiniz:

```console
docker ps
```

Kapsayıcınızı çalışıyorsa, bu çalışan işlemler listeleyen bir satır görürsünüz. (Yalnızca biri olabilir.)

Bir tarayıcı açmak ve localhost için gezinme ve bir enlem ve boylamını belirten hizmetinizi test edebilirsiniz:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Bir çalışan kapsayıcıya ekleme

Hizmetiniz bir komut penceresinde çalıştırdığınızda, her istek için yazdırılan tanı bilgilerini görebilirsiniz. Kapsayıcınızı ayrılmış modda çalışırken bu bilgileri görmüyorum. Docker komut ekleme, günlük bilgilerini görebilmeniz için çalışan bir kapsayıcıya bağlayabilmenizi sağlar.  Komut penceresinden şu komutu çalıştırın:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Bağımsız değişken anlamına <kbd>Ctrl</kbd>+<kbd>C</kbd> komutları kapsayıcı işlemine gönderilen değil, ancak bunun yerine Durdur `docker attach` komutu. Kapsayıcıda verilen ad son bağımsız değişken olan `docker run` komutu. 

> [!NOTE]
> Docker kapsayıcı kimliği atanır, herhangi bir kapsayıcıya başvuran için de kullanabilirsiniz. Kapsayıcınızda için bir ad belirtirseniz yaramadı `docker run` kapsayıcı kimliği kullanmalıdır

Bir tarayıcı açın ve hizmetinize gidin. Ekli çalışmakta olan kapsayıcıyı komutu windows tanılama iletisini görürsünüz.

Tuşuna <kbd>Ctrl</kbd>+<kbd>C</kbd> ekleme işlemi durdurulamadı.

İşiniz bittiğinde kapsayıcı ile çalışma, durdurabilirsiniz:

```console
docker stop hello-docker
```

Kapsayıcı ve görüntü yeniden başlatmak için hala kullanılabilir.  Kapsayıcı makinenizden kaldırmak istiyorsanız, bu komutu kullanın:

```console
docker rm hello-docker
```

Kullanılmayan görüntüleri makinenizden kaldırmak istiyorsanız, bu komutu kullanın:

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>Sonuç 

Bu öğreticide bir ASP.NET Core mikro hizmet yerleşik ve birkaç basit özelliği eklendi.

Bir Docker kapsayıcı görüntüsü bu hizmet için oluşturulmuş ve bu kapsayıcı makinenizde çalıştı. Bir terminal penceresi servise bağlı ve tanılama iletileri hizmetinizden gördünüz.

Süreç boyunca birkaç özelliklerinin gördüğünüz C# eylem dili.
