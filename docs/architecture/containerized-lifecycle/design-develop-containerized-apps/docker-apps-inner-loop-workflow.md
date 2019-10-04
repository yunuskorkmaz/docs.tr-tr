---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamalarının geliştirilmesi için "Inner loop" iş akışını öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 565852511f3a837066d5da5cf0e3ab0a902dd7da
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956539"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker uygulamaları için iç döngü geliştirme iş akışı

Tüm DevOps döngüsünü kapsayan dış döngü iş akışını tetiklemeden önce, hepsi her bir geliştirici makinesinde başlar, tercih edilen dillerini veya platformları kullanarak uygulamanın kendisini kodlayıp yerel olarak test edin (Şekil 4-21). Ancak her durumda, sizin seçtiğiniz dil, çerçeve veya platformlardan bağımsız olarak, genel olarak önemli bir noktaya sahip olacaksınız. Bu belirli iş akışında, her zaman Docker kapsayıcılarını geliştirmekte ve test eteceğiz, ancak yerel olarak.

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

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>1\. Adım: Visual Studio Code kodlama başlatın ve ilk uygulamanızı/hizmet temelinizi oluşturun

Uygulamanızı geliştirme yönteminiz, Docker olmadan yaptığınız yönteme benzerdir. Bu fark, geliştirme sırasında uygulamanızı veya hizmetlerinizi yerel ortamınıza (Linux VM veya Windows gibi) yerleştirilmiş olan Docker Kapsayıcıları içinde çalışan, dağıtmanıza ve test etdiğinize göre yapılır.

**Yerel ortamınızı ayarlama**

Mac ve Windows için Docker 'ın en son sürümlerinde, Docker uygulamalarının geliştirilmesi her zamankinden daha kolay olur ve Kurulum basittir.

> [!TIP]
> Docker for Windows ayarlama yönergeleri için <https://docs.docker.com/docker-for-windows/> ' a gidin.
>
>Mac için Docker 'ı ayarlamaya ilişkin yönergeler için <https://docs.docker.com/docker-for-mac/> ' a gidin.

Ayrıca, Docker CLı kullanırken uygulamanızı geliştirebilmeniz için bir kod düzenleyicisine gerek duyarsınız.

Microsoft, Windows, Linux ve macOS 'ta desteklenen bir basit kod Düzenleyicisi olan Visual Studio Code sağlar ve IntelliSense 'i birçok dil (JavaScript, .NET, Go, Java, Ruby, Python ve en modern diller) [için destek](https://code.visualstudio.com/docs/languages/overview) sağlar. [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), git ve uzantılar [ile tümleştirme](https://code.visualstudio.com/Docs/editor/versioncontrol) [desteği](https://code.visualstudio.com/docs/extensions/overview). Bu düzenleyici macOS ve Linux geliştiricileri için harika bir uyum. Windows 'da, Visual Studio 'Yu da kullanabilirsiniz.

> [!TIP]
> Windows, Linux veya macOS için Visual Studio Code yükleme yönergeleri için <https://code.visualstudio.com/docs/setup/setup-overview/> ' a gidin.
>
> Mac için Docker 'ı ayarlamaya ilişkin yönergeler için <https://docs.docker.com/docker-for-mac/> ' a gidin.

Docker CLı ile çalışabilir ve herhangi bir kod Düzenleyicisi kullanarak kodunuzu yazabilirsiniz, ancak Docker uzantısıyla Visual Studio Code kullanmak, `Dockerfile` ve `docker-compose.yml` dosyalarını çalışma alanınızda yazmayı kolaylaştırır. Ayrıca, altındaki Docker CLı kullanarak Docker komutlarını yürütmek için Visual Studio Code IDE 'den görevler ve betikler çalıştırabilirsiniz.

VS Code için Docker uzantısı aşağıdaki özellikleri sağlar:

- Otomatik `Dockerfile` ve `docker-compose.yml` dosya oluşturma

- @No__t-0 ve `Dockerfile` dosyaları için sözdizimi vurgulama ve üzerine gelme ipuçları

- @No__t-0 ve `docker-compose.yml` dosyaları için IntelliSense (tamamlama)

- @No__t-0 dosyaları için (hatalar ve uyarılar)

- En yaygın Docker komutları için komut paleti (F1) Tümleştirmesi

- Görüntüleri ve kapsayıcıları yönetmek için Gezgin tümleştirmesi

- DockerHub ve Azure Container kayıt defterlerinden görüntüleri Azure App Service için dağıtma

Docker uzantısını yüklemek için CTRL + SHIFT + P tuşlarına basın, `ext install` yazın ve sonra da Market uzantı listesini açmak için uzantıyı Install komutunu çalıştırın. Sonra, sonuçları filtrelemek için **Docker** yazın ve Şekil 4-23 ' de gösterildiği gibi Docker destek uzantısını seçin.

![VS Code için Docker uzantısının görünümü.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Şekil 4-23**. Visual Studio Code Docker uzantısını yükleme

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>2\. Adım: var olan bir görüntüyle ilgili bir DockerFile oluşturma (.NET Core, Node. js ve Ruby gibi basit işletim sistemleri veya geliştirme ortamları)

Dağıtılacak ve kapsayıcı başına her özel görüntü için bir `DockerFile` gerekir. Uygulamanız tek bir özel hizmetten yapılırsa, tek bir @no__t gerekir-0. Ancak uygulamanız birden çok hizmetten oluşuyorsa (bir mikro hizmet mimarisinde olduğu gibi), hizmet başına bir `Dockerfile` gerekir.

@No__t-0 genellikle uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir ve Docker 'ın o uygulamayı veya hizmeti nasıl ayarlayacağını ve çalıştıracağını bilmesi için gerekli komutları içerir. @No__t-0 ' ı oluşturabilir ve kodunuza (node. js, .NET Core vb.) birlikte projenize ekleyebilirsiniz, ya da ortama yeni başladıysanız aşağıdaki Ipucuna göz atın.

> [!TIP]
> Docker uzantısını kullanarak, Docker kapsayıcılarınız ile ilgili `Dockerfile` ve `docker-compose.yml` dosyalarını kullanırken size rehberlik edebilirsiniz. Sonuç olarak, bu tür dosyaları bu araç olmadan yazarsınız, ancak Docker uzantısının kullanılması, öğrenme eğinizi hızlandırmaya yönelik iyi bir başlangıç noktasıdır.

Şekil 4-24 ' de, bir Docker-Compose dosyasının VS Code için Docker uzantısını kullanarak nasıl eklendiğini görebilirsiniz.

![VS Code için Docker uzantısının konsol görünümü.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Şekil 4-24**. **Çalışma alanına Docker dosyaları Ekle komutu** kullanılarak Docker dosyaları eklendi

Bir DockerFile eklediğinizde, hangi temel Docker görüntüsünü kullanacağınız (`FROM mcr.microsoft.com/dotnet/core/aspnet` kullanarak) belirtin. Genellikle, [Docker Hub kayıt defterindeki](https://hub.docker.com/) ( [.NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) veya [Node. js için](https://hub.docker.com/_/node/)bir görüntü gibi) herhangi bir resmi depodan aldığınız bir temel görüntünün en üstünde özel görüntünüzü oluşturacaksınız.

***Mevcut bir resmi Docker görüntüsünü kullanma***

Sürüm numarasına sahip bir dil yığınının resmi deposunu kullanmak, tüm makinelerde (geliştirme, test ve üretim dahil) aynı dil özelliklerinin kullanılabilir olmasını sağlar.

Aşağıda .NET Core kapsayıcısı için örnek bir DockerFile verilmiştir:

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Bu durumda, görüntü, `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` satırına göre resmi ASP.NET Core Docker görüntüsünün 2,2 sürümünü (Linux ve Windows için çoklu mimari) temel alır. (Bu konu hakkında daha fazla bilgi için, [ASP.NET Core Docker görüntü](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sayfasına ve [.NET Core Docker görüntü](https://hub.docker.com/_/microsoft-dotnet-core/) sayfasına bakın).

DockerFile 'da, Docker 'ı çalışma zamanında kullanacağınız (bağlantı noktası 80 gibi) TCP bağlantı noktasını dinlemek için de talimat verebilirsiniz.

Kullanmakta olduğunuz dile ve çerçeveye bağlı olarak Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz. Örneğin, `["dotnet", "MySingleContainerWebApp.dll"]` içeren `ENTRYPOINT` satırı, Docker 'ın bir .NET Core uygulaması çalıştırmasını söyler. .NET uygulamasını derlemek ve çalıştırmak için SDK ve .NET Core CLI (`dotnet CLI`) kullanıyorsanız, bu ayar farklı olur. Buradaki anahtar noktası, GIRIŞ noktası satırı ve diğer ayarların, uygulamanız için seçtiğiniz dile ve platforma bağlı olmasına bağlıdır.

> [!TIP]
> .NET Core uygulamaları için Docker görüntüleri oluşturma hakkında daha fazla bilgi için <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images> ' a gidin.
>
> Kendi görüntülerinizi oluşturma hakkında daha fazla bilgi edinmek için <https://docs.docker.com/engine/tutorials/dockerimages/> ' a gidin.

**Çoklu mimari görüntü depoları kullanma**

Depodaki tek bir görüntü adı, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir. Bu özellik, Microsoft (temel görüntü oluşturucuları) gibi satıcıların birden çok platformu (yani, Linux ve Windows) kapsayacak şekilde tek bir depo oluşturmasını sağlar. Örneğin, Docker Hub kayıt defterinde bulunan [DotNet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) deposu, aynı görüntü adı kullanılarak Linux ve Windows nano Server için destek sağlar.

Bir Windows ana bilgisayarının [DotNet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) görüntüsünü çekmek, Windows türevini çeker, ancak aynı görüntü adının bir Linux ana bilgisayardan çekmesinde Linux varyantı çekilir.

***Sıfırdan taban görüntünüzü oluşturma***

Docker 'daki bu [makalede](https://docs.docker.com/engine/userguide/eng-image/baseimages/) açıklandığı gibi, kendi Docker temel görüntünüzü sıfırdan oluşturabilirsiniz. Bu senaryo muhtemelen yalnızca Docker ile başlıyorsanız sizin için en iyi yöntem değildir, ancak kendi temel görüntünüzün belirli bitlerini ayarlamak istiyorsanız bunu yapabilirsiniz.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>3\. Adım: hizmetinizi katıştırma özel Docker görüntülerinizi oluşturma

Uygulamanızı içeren her bir özel hizmet için ilgili bir görüntü oluşturmanız gerekir. Uygulamanız tek bir hizmetten veya Web uygulamasından yapılırsa yalnızca tek bir görüntüye ihtiyacınız vardır.

> [!NOTE]
> "Dış döngü DevOps iş akışını" hesaba katdığınızda,, kaynak kodunuzu bir git deposuna (sürekli tümleştirme) gönderdiğinizde görüntüler otomatik bir yapı işlemi tarafından oluşturulur ve bu sayede, görüntüler bu genel ortamda şu şekilde oluşturulur. kaynak kodu.
>
> Ancak, bu dış döngü rotasına gitmeden önce, Docker uygulamasının doğru şekilde çalıştığından emin olunması gerekir, böylece kaynak denetim sistemine (git, vb.) düzgün çalışmayan bir kod göndermezsiniz.
>
> Bu nedenle, her geliştiricinin ilk olarak yerel olarak test etmesi için tüm iç döngü sürecini yapması ve tam bir özellik göndermek veya kaynak denetim sistemine geçiş yapmak istemeleriyle geliştirmeye devam etmesi gerekir.

Yerel ortamınızda bir görüntü oluşturmak ve DockerFile 'ı kullanmak için, Şekil 4-25 ' de gösterildiği gibi Docker Build komutunu kullanabilirsiniz (Ayrıca birkaç kapsayıcı/hizmet tarafından oluşturulan uygulamalar için `docker-compose up --build` ' ı çalıştırabilirsiniz).

![Docker Build komutunun konsol çıkışını gösteren ekran görüntüsü.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Şekil 4-25**. Docker derlemesini çalıştırma

İsteğe bağlı olarak, proje klasöründen `docker build` ' ı doğrudan çalıştırmak yerine, önce `dotnet publish` Çalıştır komutunu kullanarak gerekli .NET kitaplıkları olan dağıtılabilir bir klasör oluşturabilir ve sonra da `docker build` ' yi çalıştırabilirsiniz.

Bu örnek `cesardl/netcore-webapi-microservice-docker:first` adıyla bir Docker görüntüsü oluşturur (`:first`, belirli bir sürüm gibi bir etikettir). Bu adımı, çeşitli kapsayıcılarla oluşturulmuş Docker uygulamanız için oluşturmanız gereken her özel görüntü için gerçekleştirebilirsiniz.

Şekil 4-26 ' de gösterildiği gibi, Docker görüntüleri komutunu kullanarak yerel deponuzda (geliştirme makineniz) mevcut görüntüleri bulabilirsiniz.

![Mevcut görüntüleri gösteren komut Docker görüntülerinin konsol çıktısı.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Şekil 4-26**. Docker görüntülerini kullanarak mevcut görüntüleri görüntüleme

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>4\. Adım: birden çok hizmet ile oluşturulmuş bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yml 'de tanımlama

@No__t-0 dosyası ile, bir sonraki adım bölümünde açıklanan dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak bir dizi ilgili hizmet tanımlayabilirsiniz.

Ana veya kök çözüm klasörünüzde bu dosyayı oluşturun; Bu `docker-compose.yml` dosyasında gösterilenle benzer içeriğe sahip olmalıdır:

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

Bu örnekte bu dosya iki hizmeti tanımlar: Web hizmeti (özel hizmetiniz) ve redsıs hizmeti (popüler önbellek hizmeti). Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her biri için somut bir Docker görüntüsü kullanmanız gerekir. Bu özel Web hizmeti için, görüntünün aşağıdakileri yapması gerekir:

- Geçerli dizindeki DockerFile dosyasından derleme

- Kapsayıcıda açığa çıkarılan 80 numaralı bağlantı noktasını ana makinedeki 81 numaralı bağlantı noktasına iletin

- Ana bilgisayardaki proje dizinini kapsayıcıda/Code dizinine bağlayın ve görüntüyü yeniden derlemek zorunda kalmadan kodu değiştirmenize olanak sağlar

- Web hizmetini redsıs hizmetine bağlama

Redsıs hizmeti, Docker Hub kayıt defterinden çekilen [en son ortak redo görüntüsünü](https://hub.docker.com/_/redis/) kullanır. [redsıs](https://redis.io/) , sunucu tarafı uygulamalar için popüler bir önbellek sistemidir.

### <a name="step-5-build-and-run-your-docker-app"></a>5\. Adım: Docker uygulamanızı derleme ve çalıştırma

Uygulamanızda yalnızca tek bir kapsayıcı varsa, bunu yalnızca Docker konağına (VM veya fiziksel sunucu) dağıtarak çalıştırmanız gerekir. Ancak, uygulamanız birden çok hizmetten yapılırsa, *bunu*da oluşturmanız gerekir. Farklı seçenekleri görelim.

***Seçenek A: tek bir kapsayıcı veya hizmet çalıştırma***

Docker görüntüsünü, burada gösterildiği gibi Docker Run komutunu kullanarak çalıştırabilirsiniz:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Bu dağıtım için 80 numaralı bağlantı noktasına gönderilen istekleri iç bağlantı noktası 5000 ' e yönlentireceğiz. Uygulama artık ana bilgisayar düzeyindeki 80 numaralı dış bağlantı noktasını dinliyor.

***Seçenek B: çok kapsayıcılı bir uygulama oluşturma ve çalıştırma***

Çoğu kurumsal senaryoda, bir Docker uygulaması birden çok hizmetten oluşur. Bu gibi durumlarda, daha önce oluşturmuş olabileceğiniz Docker-Compose. yıml dosyasını kullanacak olan `docker-compose up` komutunu (Şekil 4-27) çalıştırabilirsiniz. Bu komutun çalıştırılması, tüm ilişkili kapsayıcılarıyla oluşturulmuş bir uygulamayı dağıtır.

![Docker-Compose up komutuyla konsol çıktısı.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Şekil 4-27**. "Docker-Compose up" komutunun çalıştırılmasının sonuçları

@No__t-0 ' ı çalıştırdıktan sonra, sanal makine temsilinde Şekil 4-28 ' de gösterildiği gibi, uygulamanızı ve ilgili kapsayıcınızı Docker ana bilgisayarınıza dağıtırsınız.

![Çok Kapsayıcılı uygulamaları çalıştıran VM.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Şekil 4-28**. Docker Kapsayıcıları dağıtılan VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>6\. Adım: Docker uygulamanızı test etme (yerel CD sanal makinenizde yerel olarak)

Bu adım, uygulamanızın yaptığına bağlı olarak farklılık gösterir.

Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web API 'SI "Merhaba Dünya", yalnızca DockerFile içinde belirtilen TCP bağlantı noktasını sağlayarak hizmete erişmeniz gerekir.

Localhost açık değilse, hizmetinize gitmek için şu komutu kullanarak makinenin IP adresini bulun:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Docker konağında bir tarayıcı açın ve bu siteye gidin; Şekil 4-29 ' de gösterildiği gibi, uygulamanızı/hizmetinizi çalışır durumda görmeniz gerekir.

![Localhost/API/değerlerden alınan yanıtın tarayıcı görünümü.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Şekil 4-29**. Localhost kullanarak Docker uygulamanızı yerel olarak test etme

80 numaralı bağlantı noktasını kullandığına, ancak daha önce açıklandığı gibi `docker run` ile dağıtıldığına yönelik olarak, BT 'nin 5000 numaralı bağlantı noktasına yönlendirildiğini unutmayın.

Bunu terminalden KıVRıMLı kullanarak test edebilirsiniz. Windows 'daki bir Docker yüklemesinde, Şekil 4-30 ' de gösterildiği gibi varsayılan IP 10.0.75.1 ' dir.

![@No__t-0 ' ı kıvarak konsol çıkışı](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Şekil 4-30**. KıVRıMLı kullanarak Docker uygulamasını yerel olarak test etme

**Docker üzerinde çalışan bir kapsayıcıda hata ayıklama**

, Node. js ve .NET Core kapsayıcıları gibi diğer platformları kullanıyorsanız Docker hata ayıklamayı destekler Visual Studio Code.

Ayrıca, sonraki bölümde açıklandığı gibi Windows veya Mac için Visual Studio 'Yu kullanırken Docker 'daki .NET Core veya .NET Framework kapsayıcılarında hata ayıklaması yapabilirsiniz.

> [!TIP]
> Node. js Docker kapsayıcılarında hata ayıklama hakkında daha fazla bilgi edinmek Için bkz. <https://blog.docker.com/2016/07/live-debugging-docker/> ve <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.

>[!div class="step-by-step"]
>[Önceki](docker-apps-development-environment.md)
>[İleri](visual-studio-tools-for-docker.md)
