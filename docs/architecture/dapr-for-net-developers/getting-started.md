---
title: Davpr ile çalışmaya başlama
description: Yerel geliştirme ortamınızı hazırlamaya ve ilk .NET uygulamalarınızı Davpr ile oluşturmaya yönelik bir kılavuz.
author: amolenk
ms.date: 02/25/2021
ms.openlocfilehash: 68b1982c7283e0717ff7e1e254e5f313cd480d7b
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206621"
---
# <a name="get-started-with-dapr"></a>Davpr ile çalışmaya başlama

İlk iki bölümde, Davpr hakkında temel kavramları öğrendiniz. Bunu bir *sınama sürücüsü* için alma zamanı. Bu bölüm, yerel geliştirme ortamınızı hazırlama ve iki Davpr .NET uygulaması oluşturma konusunda size kılavuzluk eder.

## <a name="install-dapr-into-your-local-environment"></a>Yerel ortamınıza Davpr 'yi yükler

Geliştirme bilgisayarınıza Dadpr 'yi yükleyerek başlayacaksınız. Tamamlandıktan sonra, [kendi kendine barındırılan modda](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/)dadpr uygulamaları oluşturup çalıştırabilirsiniz.

1. [Davpr CLI 'Yı yükler](https://docs.dapr.io/getting-started/install-dapr-cli/). Bu, Davpr örneklerini başlatmanıza, çalıştırmanıza ve yönetmenize olanak sağlar. Hata ayıklama desteği de sağlar.

1. [Docker Desktop](https://docs.docker.com/get-docker/)'ı yükler. Windows üzerinde çalıştırıyorsanız, **Windows Için Docker Desktop** ' ın Linux kapsayıcıları kullanacak şekilde yapılandırıldığından emin olun.

> [!NOTE]
> Varsayılan olarak, Davpr size en iyi kullanıma hazır deneyim sağlamak için Docker Kapsayıcıları kullanır. PAPR 'yi Docker dışında çalıştırmak için, bu adımı atlayabilir ve [ *ince* bir başlatma yürütebilirsiniz](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/). Bu bölümdeki örneklerde Docker Kapsayıcıları kullanmanız gerekir.

1. [Davpr 'Yi başlatın](https://docs.dapr.io/getting-started/install-dapr/). Bu adım, en son Davpr ikililerini ve kapsayıcı görüntülerini yükleyerek geliştirme ortamınızı ayarlar.

1. [.NET Core 3,1 SDK 'sını](https://dotnet.microsoft.com/download/dotnet/3.1)yükler.

Artık, bu, ilk bir Davpr uygulamanızı oluşturmak için gereklidir!

## <a name="build-your-first-dapr-application"></a>İlk Davpr uygulamanızı oluşturma

Bu, [Davpr durum yönetimi](state-management.md) yapı taşını tüketen basit bir .NET konsol uygulaması oluşturarak başlar.

### <a name="create-the-application"></a>Uygulama oluşturma

1. Seçtiğiniz komut kabuğunu veya terminali açın. [Visual Studio Code](https://code.visualstudio.com/)içindeki Terminal özelliklerini göz önünde bulundurmayabilirsiniz. Uygulamanızı derlemek istediğiniz kök klasöre gidin. Bu kez, yeni bir .NET konsol uygulaması oluşturmak için aşağıdaki komutu girin:

    ```dotnetcli
    dotnet new console -o DaprCounter
    ```

    Komut, basit bir "Merhaba Dünya" .NET Core uygulamasını yasaklıyor.

1. Ardından, önceki komutla oluşturulan yeni dizine gidin:

    ```console
    cd DaprCounter
    ```

1. Komutunu kullanarak yeni oluşturulan uygulamayı çalıştırın `dotnet run` . "Merhaba Dünya!" yazıyorsa konsol ekranına:

    ```dotnetcli
    dotnet run
    ```

### <a name="add-dapr-state-management"></a>Davpr durum yönetimi ekleme

Daha sonra, programda durum bilgisi olan bir sayaç uygulamak için, Davpr [durum yönetimi yapı taşını](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) kullanacaksınız.

HTTP ve gRPC için, Davpr 'nin yerel desteğini kullanarak herhangi bir geliştirme platformunda, Davpr API 'Leri çağırabilirsiniz. Ancak, .NET geliştiricileri, Davpr .NET SDK 'sını daha doğal ve sezgisel olarak bulacaktır. Bu, Davpr API 'Lerini çağırmak için türü kesin belirlenmiş bir .NET istemcisi sağlar. .NET SDK Ayrıca ASP.NET Core sıkı bir şekilde tümleşir.

1. Terminal penceresinde, `Dapr.Client` NuGet paketini uygulamanıza ekleyin:

    ```dotnetcli
    dotnet add package Dapr.Client
    ```

    > [!NOTE]
    > Bir Davpr 'nin yayın öncesi sürümüyle çalışıyorsanız, bayrağını komuta eklediğinizden emin olun `--prerelease` .

1. Dosyayı en `Program.cs` sevdiğiniz düzenleyicide açın ve içeriğini aşağıdaki kodla güncelleştirin:

    ```csharp
    using System;
    using System.Threading.Tasks;
    using Dapr.Client;

    namespace DaprCounter
    {
        class Program
        {
            static async Task Main(string[] args)
            {
                const string storeName = "statestore";
                const string key = "counter";

                var daprClient = new DaprClientBuilder().Build();
                var counter = await daprClient.GetStateAsync<int>(storeName, key);

                while (true)
                {
                    Console.WriteLine($"Counter = {counter++}");

                    await daprClient.SaveStateAsync(storeName, key, counter);
                    await Task.Delay(1000);
                }
            }
        }
    }
    ```

    Güncelleştirilmiş kod aşağıdaki adımları uygular:

    - İlk olarak yeni bir `DaprClient` örnek örneği oluşturulur. Bu sınıf, Davpr sidecar ile etkileşim kurmanıza olanak sağlar.
    - Durum deposundan, `DaprClient.GetStateAsync` anahtarın değerini getirir `counter` . Anahtar yoksa, varsayılan `int` değer (yani `0` ) döndürülür.
    - Daha sonra kod, `counter` değeri konsola yazarak ve artan bir değeri durum deposuna kaydederek yinelenir.

1. Davpr CLı `run` komutu uygulamayı başlatır. Temel alınan Davpr çalışma zamanını çağırır ve hem uygulama hem de Davpr sepet birlikte çalışmasını etkinleştirir. ' I atlarsanız, `app-id` davpr uygulama için benzersiz bir ad oluşturacaktır. Komutun son segmenti, `dotnet run` Davpr çalışma zamanına .NET Core uygulamasını çalıştırmasını söyler.

    > [!IMPORTANT]
    > Durum yönetimi yapı taşı kullanılırken her zaman açık bir parametre iletilmesi için dikkatli olunmalıdır `app-id` . Blok, uygulama kimliği değerini her anahtar/değer çiftinin durum anahtarı için bir *ön ek* olarak kullanır. Uygulama kimliği değişirse, daha önce depolanan duruma artık erişemezsiniz.

    Şimdi aşağıdaki komutla uygulamayı çalıştırın:

    ```console
    dapr run --app-id DaprCounter dotnet run
    ```

    Uygulamayı durdurmayı ve yeniden başlatmayı deneyin. Sayacın sıfırlandığını görürsünüz. Bunun yerine, daha önce kaydedilen durumdan devam eder. Davpr yapı taşı, uygulamanın durum bilgisi olmasını sağlar.

> [!IMPORTANT]
> Örnek uygulamanızın önceden yapılandırılmış bir durum bileşeniyle iletişim kuracağını anlamak önemlidir, ancak buna doğrudan bağımlılığı yoktur. Davpr, bağımlılığı dışarıda bir şekilde soyutlar. Kısa bir süre sonra, temel alınan durum deposu bileşeni bir basit yapılandırma güncelleştirmesiyle değiştirilebilir.

Durum tam olarak nerede depolanabileceğini merak ediyor olabilirsiniz mi?

## <a name="component-configuration-files"></a>Bileşen yapılandırma dosyaları

Yerel ortamınız için ilk olarak Davpr 'yi başlattığınızda, otomatik olarak Redsıs kapsayıcısı temin edilir. Daha sonra, bir bileşen yapılandırma dosyası olan, Redsıs kapsayıcısını varsayılan durum deposu bileşeni olarak Yapılandır `statestore.yaml` İçeriğine göz atın:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!NOTE]
> Varsayılan bileşen yapılandırma dosyaları `$HOME/.dapr/components` , Linux/macOS klasöründe ve `%USERPROFILE%\.dapr\components` Windows üzerindeki klasörde depolanır.

Önceki bileşen yapılandırma dosyasının biçimini aklınızda yazın:

- Her bileşenin bir adı vardır. Yukarıdaki örnekte, bileşen adlandırılır `statestore` . Bu adı, ilk kod örneğimizde bu adı kullandık ve hangi bileşenin kullanılacağını gösteren bir vapr dışarıdan çekme.
- Her bileşen yapılandırma dosyasının bir `spec` bölümü vardır. `type`Bileşen türünü belirten bir alan içerir. `version`Alan, bileşen sürümünü belirtir. `metadata`Alan, bileşenin gerektirdiği, bağlantı ayrıntıları ve diğer ayarlar gibi bilgileri içerir. Meta veri değerleri farklı bileşen türleri için farklılık gösterecektir.

Bir davpr sepet, uygulamanızda yapılandırılmış herhangi bir davpr bileşenini kullanabilir. Ancak, bir bileşenin erişilebilirliğini sınırlamak için mimari gerekçe varsa ne olacak? Redin bileşenini yalnızca bir üretim ortamında çalışan Davpr sıfları ile kısıtlayabiliyor musunuz?

Bunu yapmak için, `namespace` üretim ortamı için bir tanımlayabilirsiniz. Bu adı yazabilirsiniz `production` . Şirket içinde barındırılan modda, ortam değişkenini ayarlayarak bir davpr sepet ad alanını belirtirsiniz `NAMESPACE` . Yapılandırıldığında, davpr sepet yalnızca ad alanıyla eşleşen bileşenleri yükler. Kubernetes dağıtımları için Kubernetes ad alanı yüklenen bileşenleri belirler. Aşağıdaki örnek, bir ad alanına yerleştirilmiş olan redo bileşenini gösterir `production` . `namespace`Öğesindeki bildirime göz önünde edin `metadata` :

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!IMPORTANT]
> Bir gösterilemez bileşeni yalnızca aynı ad alanında çalışan uygulamalar için erişilebilir. Eğer Davpr uygulamanız bir bileşeni yükleyemediğinde, uygulama ad alanının bileşen ad alanıyla eşleştiğinden emin olun. Bu, uygulama ad alanının bir ortam değişkeninde depolandığı, kendi kendine barındırılan modda özellikle karmaşık olabilir `NAMESPACE` .

Gerekirse, bir bileşeni belirli bir uygulamayla daha fazla kısıtlayabilirsiniz. `production`Ad alanı içinde, Redo önbelleğinin erişimini yalnızca uygulamayla sınırlamak isteyebilirsiniz `DaprCounter` . Bunu, `scopes` bileşen yapılandırmasında belirterek yapabilirsiniz. Aşağıdaki örnek, `statestore` ad alanındaki uygulamaya redsıs bileşenine erişimin nasıl kısıtlanacağını göstermektedir `DaprCounter` `production` :

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
  scopes:
  - DaprCounter
```

## <a name="build-a-multi-container-dapr-application"></a>Çok kapsayıcılı bir Davpr uygulaması oluşturun

İlk örnekte, bir Davpr sidecar ile yan yana çalıştırılan bir basit .NET konsol uygulaması oluşturdunuz. Ancak modern dağıtılmış uygulamalar genellikle birçok hareketli parçadan oluşur. Bağımsız mikro hizmetleri eşzamanlı olarak çalıştırabilirler. Bu modern uygulamalar genellikle Kapsayıcılı hale getirilir ve Docker Compose veya Kubernetes gibi kapsayıcı düzenleme araçları gerektirir.

Sonraki örnekte, çok kapsayıcılı bir uygulama oluşturacaksınız. Ayrıca, hizmetler arasında iletişim kurmak için de [Davpr hizmet çağırma](service-invocation.md) yapı taşını kullanacaksınız. Çözüm, Web API 'sinden Hava durumu tahminlerini alan bir Web uygulamasından oluşur. Her biri bir Docker kapsayıcısında çalıştırılır. Kapsayıcıyı yerel olarak çalıştırmak ve hata ayıklama yeteneklerini etkinleştirmek için Docker Compose kullanacaksınız.

Inpr için yerel ortamınızı yapılandırdığınızdan ve [.NET Core 3,1 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) 'nı yüklediğinizden emin olun (Bu bölümün başlangıcında yönergeler mevcuttur).

Ayrıca, **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) kullanarak bu örneği doldurmanız gerekir.

### <a name="create-the-application"></a>Uygulama oluşturma

1. Visual Studio 2019 ' de bir **ASP.NET Core Web uygulaması** projesi oluşturun:

    :::image type="content" source="./media/getting-started/multicontainer-createproject.png" alt-text="Yeni proje oluşturma ekran görüntüsü":::

1. Projenizi `DaprFrontEnd` ve çözümünüzü adlandırın `DaprMultiContainer` :

    :::image type="content" source="./media/getting-started/multicontainer-configureproject.png" alt-text="Yeni projenizi yapılandırma ekran görüntüsü":::

1. Razor sayfaları olan bir Web uygulaması oluşturmak için **Web uygulaması** ' nı seçin. **Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

    :::image type="content" source="./media/getting-started/multicontainer-createwebapp.png" alt-text="Yeni bir ASP.NET Core Web uygulaması oluşturma ekran görüntüsü":::

1. Aynı çözüme bir ASP.NET Core Web API projesi ekleyin ve bu uygulamayı yeniden _arka uca_ çağırın. Proje türü olarak **API 'yi** seçin. Varsayılan olarak, bir davpr sepet, genel API 'sine erişimi sınırlandırmak için ağ sınırını kullanır. Bu nedenle, **https Için yapılandırma** onay kutusunu temizleyin.

    :::image type="content" source="./media/getting-started/multicontainer-createwebapi.png" alt-text="Web API 'sini oluşturma ekran görüntüsü":::

### <a name="add-dapr-service-invocation"></a>Davpr hizmeti çağrısı Ekle

Şimdi, Davpr [hizmet çağırma yapı](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)taşı kullanan hizmetler arasındaki iletişimi yapılandıracaksınız. Web API 'sinden Hava durumu tahminlerini almak için Web uygulamasını etkinleştireceksiniz. Hizmet çağırma oluşturma bloğu birçok avantaj sunar. Hizmet bulma, otomatik yeniden denemeler, ileti şifreleme (mTLS kullanarak) ve geliştirilmiş Observability içerir. Davpr sidecar üzerinde hizmet çağırma API 'sini çağırmak için, Davpr .NET SDK 'sını kullanacaksınız.

1. Visual Studio 'da Paket Yöneticisi konsolunu (**araçlar > NuGet paket yöneticisi > Paket Yöneticisi konsolu**) açın ve bunun varsayılan proje olduğundan emin olun `DaprFrontEnd` . Konsolundan `Dapr.AspNetCore` NuGet paketini projeye ekleyin:

    ```powershell
    Install-Package Dapr.AspNetCore
    ```

    > [!NOTE]
    > Uygulamasının ön sürümde olan bir sürümünü hedefliyorsanız `Dapr.AspNetCore` , bayrağını belirtmeniz gerekir `-Prerelease` .

1. Projesinde, `DaprFrontEnd` *Startup.cs* dosyasını açın ve `ConfigureServices` yöntemi aşağıdaki kodla değiştirin:

    ```csharp
    // This method gets called by the runtime. Use this method to add services to the container.
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers().AddDapr();
        services.AddRazorPages();
    }
    ```

    ' A çağrı, `AddDapr` `DaprClient` ASP.NET Core bağımlılık ekleme sistemiyle birlikte kaydedilir. Bu `DaprClient` sınıfı daha sonra, Davpr sidecar ile iletişim kurmak için kullanacaksınız.

1. Projeye *dalgalı tahmin tahmini* adlı yeni bir C# sınıf dosyası ekleyin `DaprFrontEnd` :

    ```csharp
    using System;

    namespace DaprFrontEnd
    {
        public class WeatherForecast
        {
            public DateTime Date { get; set; }

            public int TemperatureC { get; set; }

            public int TemperatureF { get; set; }

            public string Summary { get; set; }
        }
    }
    ```

1. *Sayfalar* klasöründe *Index.cshtml.cs* dosyasını açın ve içeriğini şu kodla değiştirin:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Net.Http;
    using System.Threading.Tasks;
    using Dapr.Client;
    using Microsoft.AspNetCore.Mvc.RazorPages;

    namespace DaprFrontEnd.Pages
    {
        public class IndexModel : PageModel
        {
            private readonly DaprClient _daprClient;

            public IndexModel(DaprClient daprClient)
            {
                _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
            }

            public async Task OnGet()
            {
                var forecasts = await _daprClient.InvokeMethodAsync<IEnumerable<WeatherForecast>>(
                    HttpMethod.Get,
                    "daprbackend",
                    "weatherforecast");

                ViewData["WeatherForecastData"] = forecasts;
            }
        }
    }
    ```

    Ekleme sınıfını oluşturucuya ekleyerek, Web uygulamasına Davpr özellikleri ekleyin `DaprClient` `IndexModel` . `OnGet`Yönteminde, API hizmetini Davpr hizmet çağırma yapı taşı ile çağırabilirsiniz. `OnGet`Yöntemi, bir kullanıcı giriş sayfasını ziyaret ettiğinde çağrılır. `DaprClient.InvokeMethodAsync`Yöntemi, hizmetin yöntemini çağırmak için kullanılır `weatherforecast` `daprbackend` . Web API 'sini, `daprbackend` uygulama kimliği olarak kullanmak üzere bir daha sonra, bu uygulamayı, Davpr ile çalışacak şekilde yapılandırırken yapılandıracaksınız. Son olarak, hizmet yanıtı Görünüm verilerini içine kaydedilir.

1. *Sayfalar* klasöründeki *Index. cshtml* dosyasının içeriğini aşağıdaki kodla değiştirin. Görüntüleme verilerinde depolanan Hava durumu tahminlerini kullanıcıya görüntüler:

    ```razor
    @page
    @model IndexModel
    @{
        ViewData["Title"] = "Home page";
    }

    <div class="text-center">
        <h1 class="display-4">Welcome</h1>
        <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
        @foreach (var forecast in (IEnumerable<WeatherForecast>)ViewData["WeatherForecastData"])
        {
            <p>The forecast for @forecast.Date is @forecast.Summary!</p>
        }
    </div>
    ```

### <a name="add-container-support"></a>Kapsayıcı desteği ekle

Bu örneğin son bölümünde kapsayıcı desteği ekleyecek ve Docker Compose kullanarak çözümü çalıştıracaksınız.

1. Projeye sağ tıklayın `DaprFrontEnd` ve   >  **kapsayıcı Orchestrator desteği** Ekle ' yi seçin. **Kapsayıcı Orchestrator desteği ekle** iletişim kutusu görünür:

    :::image type="content" source="./media/getting-started/multicontainer-addorchestrator.png" alt-text="Kapsayıcı Orchestrator desteği ekleme ekran görüntüsü":::

    **Docker Compose** seçin.

1. Sonraki iletişim kutusunda, hedef işletim sistemi olarak **Linux** ' u seçin:

    :::image type="content" source="./media/getting-started/multicontainer-targetos.png" alt-text="Docker hedef işletim sistemini seçme ekran görüntüsü":::

    Visual Studio, çözümdeki **Docker-Compose** klasöründe bir *Docker-Compose. yml* dosyası ve bir *. dockerıgnore* dosyası oluşturur:

    :::image type="content" source="./media/getting-started/multicontainer-dockersolution.png" alt-text="Docker-Compose projesinin ekran görüntüsü":::

    *Docker-Compose. yml* dosyası aşağıdaki içeriğe sahiptir:

    ```yaml
    version: "3.4"

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
    ```

    *. Dockerıgnore* dosyası, Docker 'ın kapsayıcıya dahil etmesini istemediğiniz dosya türlerini ve uzantılarını içerir. Bu dosyalar geliştirme ortamı ve kaynak denetimiyle ilişkilendirilir ve dağıttığınız uygulama veya hizmetten değildir.

    *Dadprön uç* proje dizininin kökünde yeni bir *dockerfile* oluşturulmuştur. *Dockerfile* , bir görüntü oluşturmak için kullanılan komutların bir dizisidir. Daha fazla bilgi için bkz. [Dockerfile başvurusu](https://docs.docker.com/engine/reference/builder).

    *Dockerfile* , YAML 'yi içerir:

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80
    EXPOSE 443

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprFrontEnd/DaprFrontEnd.csproj", "DaprFrontEnd/"]
    RUN dotnet restore "DaprFrontEnd/DaprFrontEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprFrontEnd"
    RUN dotnet build "DaprFrontEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprFrontEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprFrontEnd.dll"]
    ```

    Yukarıdaki *Dockerfile* , çağrıldığında aşağıdaki adımları sırayla gerçekleştirir:

    1. Görüntüyü çeker `mcr.microsoft.com/dotnet/aspnet:3.1` ve adlandırır `base` .
    1. Çalışma dizinini */App* olarak ayarlar.
    1. Bağlantı noktasını `80` ve sunar `443` .
    1. Görüntüyü çeker `mcr.microsoft.com/dotnet/sdk:3.1` ve adlandırır `build` .
    1. Çalışma dizinini */src* olarak ayarlar.
    1. , _Davprön uç/Davprön uç. csproj_ değerini, *dadprön uç/* adlı yeni bir dizine kopyalar.
    1. [`dotnet restore`](../../core/tools/dotnet-restore.md)Projedeki çağrılar.
    1. Kök dizindeki her şeyi görüntünün köküne kopyalar.
    1. Çalışma dizinini _/src/DaprFrontEnd_ olarak ayarlar.
    1. [`dotnet build`](../../core/tools/dotnet-build.md)Projedeki çağrılar.
        - **Yayın** yapılandırmasını hedefleme ve */App/Build*'e çıktılar.
    1. Varolan temel görüntüden yeni bir yapı aşaması başlatır `build` ve bunu adlandırır `publish` .
    1. `dotnet publish`Projedeki çağrılar.
        - **Yayın** yapılandırmasını hedefleme ve */App/Publish*'e çıktılar.
    1. Varolan temel görüntüden yeni bir yapı aşaması başlatır `publish` ve bunu adlandırır `final` .
    1. Çalışma dizinini */App* olarak ayarlar.
    1. `/app/publish`Dizindeki dizini görüntünün köküne kopyalar `publish` `final` .
    1. Giriş noktasını resim olarak ayarlar `dotnet` ve `DaprFrontEnd.dll` bir bağımsız değişken olarak geçirir.

1. `DaprBackEnd`Web API projesinde, proje düğümüne sağ tıklayın ve   >  **kapsayıcı Orchestrator desteği** Ekle ' yi seçin. **Docker Compose** öğesini seçin ve ardından hedef işletim sistemi olarak **Linux** ' u yeniden seçin.

    _Dadprarka uç_ proje dizininin kökünde yeni bir *dockerfile* oluşturuldu. *Dockerfile* aşağıdaki YAML 'yi içerir:

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprBackEnd/DaprBackEnd.csproj", "DaprBackEnd/"]
    RUN dotnet restore "DaprBackEnd/DaprBackEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprBackEnd"
    RUN dotnet build "DaprBackEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprBackEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprBackEnd.dll"]
    ```

    *Docker-Compose. yıml* dosyasını yeniden açın ve içeriğini inceleyin. Visual Studio **Docker Compose** dosyasını güncelleştirmiştir. Artık her iki hizmet de dahil edilmiştir:

    ```yaml
    version: '3.4'

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
    ```

1. Kapsayıcılı bir uygulamanın içinden Davpr yapı taşlarını kullanmak için, oluşturma dosyanıza Davpr sıdecars kapsayıcıları eklemeniz gerekir. *Docker-Compose. yıml* dosyasının içeriğini aşağıdaki örnekle eşleşecek şekilde dikkatle güncelleştirin. Biçimlendirme ve aralığa yakın bir ilgi ödeyin ve sekmeleri kullanmayın.

    ```yaml
    version: '3.4'
    
    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
        ports:
          - "51000:50001"

      daprfrontend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprfrontend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprfrontend"

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
        ports:
          - "52000:50001"

      daprbackend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprbackend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprbackend"
    ```

    Güncelleştirilmiş dosyada, `daprfrontend-dapr` `daprbackend-dapr` `daprfrontend` ve `daprbackend` hizmetlerini sırasıyla ve hizmetleri için ekledik. Güncelleştirilmiş dosyada, aşağıdaki değişikliklere dikkat edin:

    - Sıfları `daprio/daprd:latest` kapsayıcı görüntüsünü kullanır. Etiket kullanımı, `latest` Üretim senaryolarında önerilmez. Üretim için belirli bir sürüm numarası kullanmak daha iyidir.
    - Oluşturma dosyasında tanımlanan her bir hizmetin ağ yalıtımı amacıyla kendi ağ ad alanı vardır. Bu kişilerin `network_mode: "service:..."` uygulamayla aynı ağ ad alanında çalıştırıldıklarından emin olmak için kullanılır. Bunun yapılması, dışarıdan ve uygulamanın kullanarak iletişim kurmasına izin verir `localhost` .
    - Bapr kapsayıcınızı 'ın GRPC iletişimini dinlediği bağlantı noktaları (varsayılan olarak 50001), aynı kişilerin birbirleriyle iletişim kurmasına izin vermek için gösterilmelidir.

1. Çözümü, beklendiği gibi çalıştığını doğrulamak için çalıştırın (<kbd>F5</kbd> veya <kbd>CTRL + F5</kbd>). Her şey doğru yapılandırılmışsa, hava durumu tahmin verilerini görmeniz gerekir:

    :::image type="content" source="./media/getting-started/multicontainer-result.png" alt-text="Hava durumu tahmin verilerinin gösterildiği son çözümün ekran görüntüsü":::

    Docker Compose ve Visual Studio 2019 ile yerel olarak çalışırken, kesme noktaları ve hata ayıklama işlemlerini uygulamaya ayarlayabilirsiniz. Üretim senaryolarında, uygulamanızın Kubernetes 'te barındırmasının yapılması önerilir. Bu kitap, Kubernetes 'e dağıtılacak betikleri içeren [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr)öğesine eşlik eden bir başvuru uygulaması içerir.

    Bu kılavuzda kullanılan Davpr hizmet çağrısı yapı taşı hakkında daha fazla bilgi edinmek için [Bölüm 6](service-invocation.md)' ya başvurun.

## <a name="summary"></a>Özet

Bu bölümde, dadpr *sürücüsünü test* etme fırsatınız vardı. Davpr .NET SDK 'yı kullanarak, Davpr 'nin .NET uygulama platformu ile nasıl tümleştiğini gördünüz.

İlk örnek, Davpr durum yönetimi oluşturma bloğunu kullanan basit ve durum bilgisi olan bir .NET konsol uygulamasıdır.

İkinci örnek, Docker 'da çalışan çok kapsayıcılı bir uygulama ile ilgilidir. Visual Studio 'Yu Docker Compose kullanarak tüm .NET uygulamalarında sunulan tanıdık *F5 hata ayıklama deneyimiyle* karşılaşmış olursunuz.

Ayrıca, Bapr bileşen yapılandırma dosyalarına daha yakından bakalım. Bunlar, Davpr yapı taşları tarafından kullanılan gerçek altyapı uygulamasını yapılandırır. Belirli ortamlara ve uygulamalara bileşen erişimini kısıtlamak için ad alanlarını ve kapsamları kullanabilirsiniz.

Yaklaşan bölümlerde, Davpr tarafından sunulan yapı taşları hakkında ayrıntılı bilgi edineceksiniz.

### <a name="references"></a>Başvurular

- [Davpr belgeleri-Başlarken](https://docs.dapr.io/getting-started)
- [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr)

> [!div class="step-by-step"]
> [Önceki](dapr-at-20000-feet.md) 
>  [Sonraki](reference-application.md)
