---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamaları için "Inner-loop" geliştirme iş akışı hakkında bilgi edinin.
ms.date: 08/06/2020
ms.openlocfilehash: 071e16afede91f4cfd6cbe8662fa68814ffdcdd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539768"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker uygulamaları için iç döngü geliştirme iş akışı

Tüm DevOps döngüsünü kapsayan dış döngü iş akışını tetiklemeden önce, hepsi her bir geliştirici makinesinde başlar, tercih edilen dillerini veya platformları kullanarak uygulamanın kendisini kodlayıp yerel olarak test edin (Şekil 4-21). Ancak her durumda, sizin seçtiğiniz dil, çerçeve veya platformlardan bağımsız olarak, genel olarak önemli bir noktaya sahip olacaksınız. Bu belirli iş akışında, Docker kapsayıcılarını her zaman başka bir ortamda geliştirmekte ve test eteceğiz, ancak yerel olarak.

![Bir iç döngü geliştirme ortamı kavramını gösteren diyagram.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Şekil 4-21**. İç döngü geliştirme bağlamı

Bir Docker görüntüsünün kapsayıcısı veya örneği şu bileşenleri içerir:

- Bir işletim sistemi seçimi (örneğin, bir Linux dağıtımı veya Windows)

- Geliştirici tarafından eklenen dosyalar (örneğin, uygulama ikilileri)

- Yapılandırma (örneğin, ortam ayarları ve bağımlılıklar)

- Docker tarafından hangi işlemlerin çalıştırılacağını gösteren yönergeler

İşlem olarak Docker kullanan iç döngü geliştirme iş akışını (sonraki bölümde açıklanmıştır) ayarlayabilirsiniz. Yalnızca bir kez yapmanız gerektiğinden, ortamı ayarlamaya yönelik ilk adımların dahil edilmediğini göz önünde bulundurun.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code ve Docker CLı kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma

Uygulamalar, kendi hizmetinizden ve ek kitaplıklardan (bağımlılıklar) oluşur.

Şekil 4-22, genellikle bir Docker uygulaması oluştururken gerçekleştirmeniz gereken temel adımları gösterir ve ardından her adımın ayrıntılı açıklamalarını izler.

![Kapsayıcılı bir uygulama oluşturmak için gereken yedi adımı gösteren diyagram.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Şekil 4-22**. Docker CLı kullanan Docker Kapsayıcılı uygulamalar için yaşam döngüsü için üst düzey iş akışı

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>1. Adım: Visual Studio Code kodlama başlatın ve ilk uygulamanızı/hizmet temelinizi oluşturun

Uygulamanızı geliştirme yönteminiz, Docker olmadan yaptığınız yönteme benzerdir. Bu fark, geliştirme sırasında uygulamanızı veya hizmetlerinizi yerel ortamınıza (Linux VM veya Windows gibi) yerleştirilmiş olan Docker Kapsayıcıları içinde çalışan, dağıtmanıza ve test etdiğinize göre yapılır.

**Yerel ortamınızı ayarlama**

Mac ve Windows için Docker Desktop 'ın en son sürümlerinde, Docker uygulamalarının geliştirilmesi her zamankinden daha kolay olur ve Kurulum basittir.

> [!TIP]
> Windows için Docker Desktop 'ı ayarlamaya ilişkin yönergeler için adresine gidin <https://docs.docker.com/docker-for-windows/> .
>
> Mac için Docker Desktop 'ı ayarlamaya ilişkin yönergeler için adresine gidin <https://docs.docker.com/docker-for-mac/> .

Ayrıca, Docker CLı kullanırken uygulamanızı geliştirebilmeniz için bir kod düzenleyicisine gerek duyarsınız.

Microsoft, Windows, Linux ve macOS 'ta desteklenen bir basit kod Düzenleyicisi olan Visual Studio Code sağlar ve IntelliSense 'i [birçok dil](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .net, Go, Java, Ruby, Python ve en modern diller), [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [Uzantılar desteğiyle tümleştirme desteği](https://code.visualstudio.com/docs/extensions/overview)sunan bir şekilde sunar. Bu düzenleyici macOS ve Linux geliştiricileri için harika bir uyum. Windows 'da, Visual Studio 'Yu da kullanabilirsiniz.

> [!TIP]
> Windows, Linux veya macOS için Visual Studio Code yükleme yönergeleri için adresine gidin <https://code.visualstudio.com/docs/setup/setup-overview/> .
>
> Mac için Docker 'ı ayarlamaya ilişkin yönergeler için adresine gidin <https://docs.docker.com/docker-for-mac/> .

Docker CLı ile çalışabilir ve herhangi bir kod Düzenleyicisi kullanarak kodunuzu yazabilirsiniz, ancak Docker uzantısıyla Visual Studio Code kullanmak, `Dockerfile` çalışma alanınızdaki yazma ve dosyaları daha kolay hale getirir `docker-compose.yml` . Ayrıca, altındaki Docker CLı kullanarak Docker komutlarını yürütmek için Visual Studio Code IDE 'den görevler ve betikler çalıştırabilirsiniz.

VS Code için Docker uzantısı aşağıdaki özellikleri sağlar:

- Otomatik `Dockerfile` ve `docker-compose.yml` dosya oluşturma

- `docker-compose.yml`Ve dosyaları için sözdizimi vurgulama ve üzerine gelme ipuçları `Dockerfile`

- `Dockerfile`Ve dosyaları Için IntelliSense (tamamlama `docker-compose.yml` )

- Dosyalar için linme (hatalar ve uyarılar) `Dockerfile`

- En yaygın Docker komutları için komut paleti (F1) Tümleştirmesi

- Görüntüleri ve kapsayıcıları yönetmek için Gezgin tümleştirmesi

- DockerHub ve Azure Container kayıt defterlerinden görüntüleri Azure App Service için dağıtma

Docker uzantısını yüklemek için CTRL + SHIFT + P tuşlarına basın, yazın `ext install` ve sonra da Market uzantı listesini açmak Için uzantı Install komutunu çalıştırın. Sonra, sonuçları filtrelemek için **Docker** yazın ve Şekil 4-23 ' de gösterildiği gibi Docker destek uzantısını seçin.

![VS Code için Docker uzantısının görünümü.](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Şekil 4-23**. Visual Studio Code Docker uzantısını yükleme

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>2. Adım: var olan bir görüntüyle ilgili bir DockerFile oluşturma (.NET Core, Node.js ve Ruby gibi basit işletim sistemleri veya geliştirme ortamları)

Dağıtılması için bir `DockerFile` özel görüntü ve dağıtılacak kapsayıcı başına ihtiyacınız vardır. Uygulamanız tek bir özel hizmetten yapılırsa, tek yapmanız gerekir `DockerFile` . Ancak uygulamanız birden çok hizmetten oluşuyorsa (bir mikro hizmet mimarisinde olduğu gibi), hizmet başına bir tane gerekir `Dockerfile` .

`DockerFile`Genellikle uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir ve Docker 'ın o uygulamayı veya hizmeti nasıl ayarlayacağını ve çalıştıracağını bilmesi için gerekli komutları içerir. Kodunuzu oluşturup `DockerFile` projenize (node.js, .NET Core vb.) birlikte ekleyebilirsiniz, ya da ortama yeni başladıysanız aşağıdaki ipucuna göz atın.

> [!TIP]
> Docker `Dockerfile` kapsayıcılarınız ile ilgili ve dosyalarını kullanırken size rehberlik etmek Için Docker uzantısını kullanabilirsiniz `docker-compose.yml` . Sonuç olarak, bu tür dosyaları bu araç olmadan yazarsınız, ancak Docker uzantısının kullanılması, öğrenme eğinizi hızlandırmaya yönelik iyi bir başlangıç noktasıdır.

Şekil 4-24 ' de Docker dosyalarını bir projeye ekleme adımlarını VS Code için Docker uzantısını kullanarak görebilirsiniz:

1. Komut paletini açın, "**Docker**" yazın ve "**çalışma alanına Docker dosyaları Ekle**" seçeneğini belirleyin.
2. Uygulama platformunu seçin (ASP.NET Core)
3. Işletim sistemini seçin (Linux)
4. İsteğe bağlı Docker Compose dosyaları Ekle
5. Yayımlanacak bağlantı noktalarını girin (80, 443)
6. Projeyi seçin

![Docker uzantılı Docker dosyaları ekleme adımları](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Şekil 4-24**. **Çalışma alanına Docker dosyaları Ekle** komutu kullanılarak Docker dosyaları eklendi

Bir DockerFile eklediğinizde, kullanacağınız temel Docker görüntüsünü (kullanma gibi `FROM mcr.microsoft.com/dotnet/core/aspnet` ) belirtirsiniz. Genellikle, [Docker Hub kayıt defterinde](https://hub.docker.com/) ( [.NET Core için bir görüntü](https://hub.docker.com/_/microsoft-dotnet-core/) veya [Node.jsiçin ](https://hub.docker.com/_/node/)bir görüntü gibi) herhangi bir resmi depodan aldığınız bir temel görüntünün en üstünde özel görüntünüzü oluşturacaksınız.

> [!TIP]
> Uygulamanızdaki her proje için bu yordamı tekrarlamanız gerekir. Ancak, uzantı ilk kez oluşturulan Docker-Compose dosyasını geçersiz kılacak. Üzerine yazılmaması gerekir, bu nedenle uzantı, Docker-Compose çalıştırmadan önce el ile birleştirebilmeniz için ayrı Docker-Compose dosyaları oluşturur.

**_Mevcut bir resmi Docker görüntüsünü kullanma_**

Sürüm numarasına sahip bir dil yığınının resmi deposunu kullanmak, tüm makinelerde (geliştirme, test ve üretim dahil) aynı dil özelliklerinin kullanılabilir olmasını sağlar.

Aşağıda .NET Core kapsayıcısı için örnek bir DockerFile verilmiştir:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

Bu durumda, görüntü, satıra göre resmi ASP.NET Core Docker görüntüsünün 3,1 sürümünü (Linux ve Windows için çoklu mimari) temel alır `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` . (Bu konu hakkında daha fazla bilgi için, [ASP.NET Core Docker görüntü](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sayfasına ve [.NET Core Docker görüntü](https://hub.docker.com/_/microsoft-dotnet-core/) sayfasına bakın).

DockerFile 'da, Docker 'ın çalışma zamanında kullanacağınız TCP bağlantı noktasını (bağlantı noktası 80 veya 443) dinleyebildiğini da söyleyebilirsiniz.

Kullanmakta olduğunuz dile ve çerçeveye bağlı olarak Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz. Örneğin, çizgi, `ENTRYPOINT` `["dotnet", "WebMvcApplication.dll"]` Docker 'A .NET Core uygulaması çalıştırmasını söyler. `dotnet CLI`.NET uygulamasını derlemek ve çalıştırmak IÇIN SDK ve .NET Core CLI () kullanıyorsanız, bu ayar farklı olur. Buradaki anahtar noktası, GIRIŞ noktası satırı ve diğer ayarların, uygulamanız için seçtiğiniz dile ve platforma bağlı olmasına bağlıdır.

> [!TIP]
> .NET Core uygulamaları için Docker görüntüleri oluşturma hakkında daha fazla bilgi için adresine gidin <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images> .
>
> Kendi görüntülerinizi oluşturma hakkında daha fazla bilgi edinmek için adresine gidin <https://docs.docker.com/engine/tutorials/dockerimages/> .

**Çoklu mimari görüntü depoları kullanma**

Depodaki tek bir görüntü adı, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir. Bu özellik, Microsoft (temel görüntü oluşturucuları) gibi satıcıların birden çok platformu (yani, Linux ve Windows) kapsayacak şekilde tek bir depo oluşturmasını sağlar. Örneğin, Docker Hub kayıt defterinde bulunan [DotNet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) deposu, aynı görüntü adı kullanılarak Linux ve Windows nano Server için destek sağlar.

Bir Windows ana bilgisayarının [DotNet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) görüntüsünü çekmek, Windows türevini çeker, ancak aynı görüntü adının bir Linux ana bilgisayardan çekmesinde Linux varyantı çekilir.

**_Sıfırdan taban görüntünüzü oluşturma_**

Docker 'daki bu [makalede](https://docs.docker.com/engine/userguide/eng-image/baseimages/) açıklandığı gibi, kendi Docker temel görüntünüzü sıfırdan oluşturabilirsiniz. Bu senaryo muhtemelen yalnızca Docker ile başlıyorsanız sizin için en iyi yöntem değildir, ancak kendi temel görüntünüzün belirli bitlerini ayarlamak istiyorsanız bunu yapabilirsiniz.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>3. Adım: hizmetinizi katıştırma özel Docker görüntülerinizi oluşturma

Uygulamanızı içeren her bir özel hizmet için ilgili bir görüntü oluşturmanız gerekir. Uygulamanız tek bir hizmetten veya Web uygulamasından yapılırsa yalnızca tek bir görüntüye ihtiyacınız vardır.

> [!NOTE]
> "Dış döngü DevOps iş akışını" hesaba katdığınızda,, kaynak kodunuzu bir git deposuna (sürekli tümleştirme) gönderdiğinizde görüntüler otomatik derleme işlemi tarafından oluşturulur. bu nedenle, görüntüler kaynak kodunuzla ilgili genel ortamda oluşturulur.
>
> Ancak, bu dış döngü yoluna gitmeden önce, Docker uygulamasının doğru şekilde çalıştığından emin olmanız gerekir. böylece, kaynak denetim sistemine (git, vb.) düzgün çalışmayan bir kod gönderemeyecektir.
>
> Bu nedenle, her geliştiricinin ilk olarak yerel olarak test etmesi için tüm iç döngü sürecini yapması ve tam bir özellik göndermek veya kaynak denetim sistemine geçiş yapmak istemeleriyle geliştirmeye devam etmesi gerekir.

Yerel ortamınızda bir görüntü oluşturmak ve DockerFile 'ı kullanmak için, Şekil 4-25 ' de gösterildiği gibi Docker Build komutunu kullanabilirsiniz. Bu, resmi sizin için etiketleyen ve basit bir komutla uygulamadaki tüm hizmetlere ait görüntüleri derlemedir.

![Docker-Compose derleme komutunun konsol çıkışını gösteren ekran görüntüsü.](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Şekil 4-25**. Docker derlemesini çalıştırma

İsteğe bağlı olarak, proje klasöründen doğrudan çalıştırmak yerine `docker build` , Çalıştır komutunu kullanarak gerekli .NET kitaplıkları ile dağıtılabilir bir klasör oluşturabilir `dotnet publish` ve sonra öğesini çalıştırabilirsiniz `docker build` .

Bu örnek, adıyla bir Docker görüntüsü oluşturur `explore-docker-vscode/webapi:latest` ( `:latest` belirli bir sürüm gibi bir etikettir). Bu adımı, çeşitli kapsayıcılarla oluşturulmuş Docker uygulamanız için oluşturmanız gereken her özel görüntü için gerçekleştirebilirsiniz. Bununla birlikte, bunu kullanarak bunu daha kolay bir şekilde yapacağız `docker-compose` .

Mevcut görüntüleri, `docker images` şekil 4-26 ' de gösterildiği gibi, komutunu kullanarak yerel deponuzda (geliştirme makineniz) bulabilirsiniz.

![Mevcut görüntüleri gösteren komut Docker görüntülerinin konsol çıktısı.](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Şekil 4-26**. Docker görüntülerini kullanarak mevcut görüntüleri görüntüleme

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>4. Adım: birden çok hizmet ile oluşturulmuş bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yml 'de tanımlama

Dosyası ile `docker-compose.yml` , bir sonraki adım bölümünde açıklanan dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak bir dizi ilgili hizmet tanımlayabilirsiniz.

Ana veya kök çözüm klasörünüzde bu dosyayı oluşturun; Bu dosyada gösterilene benzer içeriğe sahip olmalıdır `docker-compose.yml` :

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

Bu durumda, bu dosya üç hizmeti tanımlar: Web API hizmeti (özel hizmetiniz), bir Web uygulaması ve Redsıs hizmeti (popüler önbellek hizmeti). Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her biri için somut bir Docker görüntüsü kullanmanız gerekir. Bu uygulama için:

- Web API hizmeti, dizindeki DockerFile dosyasından oluşturulur `src/WebApi/Dockerfile` .

- 51080 ana bilgisayar bağlantı noktası, kapsayıcıda bulunan 80 numaralı bağlantı noktasına iletilir `webapi` .

- Web API hizmeti Redsıs hizmetine bağlıdır

- Web uygulaması, iç adresini kullanarak Web API hizmetine erişir: `http://webapi` .

- Redsıs hizmeti, Docker Hub kayıt defterinden çekilen [en son ortak redo görüntüsünü](https://hub.docker.com/_/redis/) kullanır. [Redsıs](https://redis.io/) , sunucu tarafı uygulamalar için popüler bir önbellek sistemidir.

### <a name="step-5-build-and-run-your-docker-app"></a>5. Adım: Docker uygulamanızı derleme ve çalıştırma

Uygulamanızda yalnızca tek bir kapsayıcı varsa, bunu yalnızca Docker konağına (VM veya fiziksel sunucu) dağıtarak çalıştırmanız gerekir. Ancak, uygulamanız birden çok hizmetten yapılırsa, _bunu_da oluşturmanız gerekir. Farklı seçenekleri görelim.

**_Seçenek A: tek bir kapsayıcı veya hizmet çalıştırma_**

Docker görüntüsünü, burada gösterildiği gibi Docker Run komutunu kullanarak çalıştırabilirsiniz:

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

Bu dağıtım için, ana bilgisayarda 50080 numaralı bağlantı noktasına gönderilen istekleri iç bağlantı noktası 80 ' e yeniden yönlentireceğiz.

**_Seçenek B: çok kapsayıcılı bir uygulama oluşturma ve çalıştırma_**

Çoğu kurumsal senaryoda, bir Docker uygulaması birden çok hizmetten oluşur. Bu gibi durumlarda, `docker-compose up` daha önce oluşturduğunuz Docker-Compose. yıml dosyasını kullanacak olan komutunu (şekil 4-27) çalıştırabilirsiniz. Bu komutu çalıştırmak tüm özel görüntüleri oluşturur ve tüm ilgili kapsayıcılarıyla birlikte oluşturulan uygulamayı dağıtır.

![Docker-Compose up komutuyla konsol çıktısı.](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Şekil 4-27**. "Docker-Compose up" komutunun çalıştırılmasının sonuçları

Çalıştırdıktan sonra `docker-compose up` , uygulamanızı ve ilgili kapsayıcınızı, şekil 4-28 ' de gösterildiği gibi, sanal makine gösteriminde, Docker ana bilgisayarınıza dağıtırsınız.

![Çok Kapsayıcılı uygulamaları çalıştıran VM.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Şekil 4-28**. Docker Kapsayıcıları dağıtılan VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>6. Adım: Docker uygulamanızı test etme (yerel CD sanal makinenizde yerel olarak)

Bu adım, uygulamanızın yaptığına bağlı olarak farklılık gösterir.

Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web API 'SI "Merhaba Dünya", yalnızca DockerFile içinde belirtilen TCP bağlantı noktasını sağlayarak hizmete erişmeniz gerekir.

Docker konağında bir tarayıcı açın ve bu siteye gidin; Şekil 4-29 ' de gösterildiği gibi, uygulamanızı/hizmetinizi çalışır durumda görmeniz gerekir.

![Localhost/API/değerlerden alınan yanıtın tarayıcı görünümü.](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Şekil 4-29**. Tarayıcı kullanarak Docker uygulamanızı yerel olarak test etme

50080 numaralı bağlantı noktasını kullandığını unutmayın, ancak `docker compose` daha önce açıklandığı gibi, ile birlikte dağıtılmakta olduğu gibi, dahili olarak bu bağlantı noktası 80 ' e yönlendirilmekte.

Bunu, Şekil 4-30 ' de gösterildiği gibi terminalden KıVARAK tarayıcıyı kullanarak test edebilirsiniz.

![Şu kaynaktan alınan kıvır sonucu http://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Şekil 4-30**. KıVRıMLı kullanarak Docker uygulamasını yerel olarak test etme

**Docker üzerinde çalışan bir kapsayıcıda hata ayıklama**

Visual Studio Code, Node.js ve .NET Core kapsayıcıları gibi diğer platformları kullanıyorsanız Docker hatalarını ayıklamayı destekler.

Ayrıca, sonraki bölümde açıklandığı gibi Windows veya Mac için Visual Studio 'Yu kullanırken Docker 'daki .NET Core veya .NET Framework kapsayıcılarında hata ayıklaması yapabilirsiniz.

> [!TIP]
> Docker Kapsayıcıları Node.js hata ayıklama hakkında daha fazla bilgi için <https://blog.docker.com/2016/07/live-debugging-docker/> bkz <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> . ve.

> [!div class="step-by-step"]
> [Önceki](docker-apps-development-environment.md) 
>  [Sonraki](visual-studio-tools-for-docker.md)
