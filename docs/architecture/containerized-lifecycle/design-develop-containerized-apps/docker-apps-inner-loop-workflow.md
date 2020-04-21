---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamalarının geliştirilmesi için "iç döngü" iş akışını öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: bce047bd5ba75f9ef652a294ff6a15656fc5ac34
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738416"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker uygulamaları için iç döngü geliştirme iş akışı

Tüm DevOps döngüsünü kapsayan dış döngü iş akışını tetiklemeden önce, her geliştiricinin makinesinde başlar, uygulamanın kendisini kodlar, tercih ettikleri dilleri veya platformları kullanır ve yerel olarak test eder (Şekil 4-21). Ancak her durumda, hangi dili, çerçeveyi veya platformları seçerseniz seçin, ortak önemli bir noktanız olacak. Bu özel iş akışında, Docker kapsayıcılarını her zaman yerel olarak geliştiriyor ve test ediyorsunuz.

![Bir iç döngü dev ortam kavramını gösteren diyagram.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Şekil 4-21**. İç-döngü geliştirme bağlamı

Docker görüntüsünün kapsayıcısı veya örneği şu bileşenleri içerir:

- İşletim sistemi seçimi (örneğin, Bir Linux dağıtımı veya Windows)

- Geliştirici tarafından eklenen dosyalar (örneğin, uygulama ikilileri)

- Yapılandırma (örneğin, ortam ayarları ve bağımlılıklar)

- Docker tarafından hangi süreçlerin yürütülacağına yönelik talimatlar

İşlem olarak Docker'ı kullanan iç döngü geliştirme iş akışını ayarlayabilirsiniz (sonraki bölümde açıklanmıştır). Ortamı ayarlamak için ilk adımların dahil olmadığını, çünkü yalnızca bir kez yapmanız gerektiğini göz önünde bulundurun.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code ve Docker CLI kullanarak Docker konteyneriçinde tek bir uygulama oluşturma

Uygulamalar kendi hizmetlerinizden ve ek kitaplıklardan (bağımlılıklar) oluşur.

Şekil 4-22, bir Docker uygulaması inşa ederken genellikle gerçekleştirmeniz gereken temel adımları ve ardından her adımın ayrıntılı açıklamalarını gösterir.

![Kapsayıcı bir uygulama oluşturmak için gereken yedi adımı gösteren diyagram.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Şekil 4-22**. Docker CLI kullanarak Docker konteyner uygulamaları için yaşam döngüsü için üst düzey iş akışı

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Adım 1: Visual Studio Code'da kodlamaya başlayın ve ilk uygulama/hizmet taban çizginizi oluşturun

Uygulamanızı geliştirme şekliniz Docker olmadan yaptığınız avekçe benzer. Aradaki fark, geliştirirken, uygulamanızı veya yerel ortamınıza yerleştirilen Docker kapsayıcıları içinde çalışan hizmetleri (Linux VM veya Windows gibi) dağıtıyor ve test ediyor olmasıdır.

**Yerel ortamınızı ayarlama**

Mac ve Windows için Docker'ın en son sürümleriyle Docker uygulamalarını geliştirmek her zamankinden daha kolay ve kurulum çok kolay.

> [!TIP]
> Windows için Docker'ı ayarlama yla <https://docs.docker.com/docker-for-windows/>ilgili talimatlar için .
>
>Mac için Docker kurma talimatları için, gidin. <https://docs.docker.com/docker-for-mac/>

Buna ek olarak, Docker CLI kullanırken uygulamanızı gerçekten geliştirebilmeniz için bir kod düzenleyicisine ihtiyacınız vardır.

Microsoft, Windows, Linux ve macOS'ta desteklenen hafif bir kod düzenleyicisi olan Visual Studio Code'u sağlar ve IntelliSense'e [birçok dil](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python ve en modern diller) desteği sağlar, [hata ayıklama,](https://code.visualstudio.com/Docs/editor/debugging)Git ve uzantıları [desteği](https://code.visualstudio.com/docs/extensions/overview) [ile tümleştirme](https://code.visualstudio.com/Docs/editor/versioncontrol) sağlar. Bu editör macOS ve Linux geliştiricileri için harika bir uyum. Windows'da Visual Studio'u da kullanabilirsiniz.

> [!TIP]
> Windows, Linux veya macOS için Visual Studio Kodu <https://code.visualstudio.com/docs/setup/setup-overview/>yükleme yönergeleri için.
>
> Mac için Docker kurma talimatları için, gidin. <https://docs.docker.com/docker-for-mac/>

Docker CLI ile çalışabilir ve herhangi bir kod düzenleyicisini kullanarak kodunuzu yazabilirsiniz, ancak `Dockerfile` `docker-compose.yml` Docker uzantısı ile Visual Studio Code'u kullanmak çalışma alanınızda yazmanızı ve dosyaları kolayca yazmayı kolaylaştırır. Ayrıca, altında Docker CLI kullanarak Docker komutlarını yürütmek için Visual Studio Code IDE'den görevleri ve komut ları çalıştırabilirsiniz.

VS Code için Docker uzantısı aşağıdaki özellikleri sağlar:

- Otomatik `Dockerfile` `docker-compose.yml` ve dosya oluşturma

- Sözdizimi vurgulama ve gezinme `docker-compose.yml` `Dockerfile` ipuçları ve dosyalar

- IntelliSense (tamamlamalar) `Dockerfile` `docker-compose.yml` için ve dosyalar

- Dosyalar için `Dockerfile` linting (hatalar ve uyarılar)

- En yaygın Docker komutları için Komut Paleti (F1) tümleştirmesi

- Görüntüleri ve Kapsayıcıları yönetmek için Explorer tümleştirmesi

- DockerHub ve Azure Konteyner Kayıt Şirketlerinden görüntüleri Azure Uygulama Hizmetine dağıtma

Docker uzantısını yüklemek için Ctrl+Shift+P `ext install`tuşuna basın, ardından Market uzantı listesini açmak için Uzantıyı Yükle komutunu çalıştırın. Ardından, sonuçları filtrelemek için **docker** yazın ve ardından Şekil 4-23'te belirtildiği gibi Docker Destek uzantısını seçin.

![VS Kodu için Docker uzantısıgörünümü.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Şekil 4-23**. Docker Uzantısının Visual Studio Koduna Yüklenmesi

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Adım 2: Varolan bir görüntüyle ilgili bir DockerFile oluşturun (.NET Core, Node.js ve Ruby gibi düz işletim sistemi veya dev ortamlar)

Oluşturulacak özel `DockerFile` görüntü başına ve dağıtılmak üzere konteyner başına bir görüntü gerekir. Uygulamanız tek bir özel hizmetten oluşuyorsa, tek `DockerFile`bir özel hizmete ihtiyacınız vardır. Ancak uygulamanız birden çok hizmet (mikro hizmetler mimarisinde olduğu gibi) oluşuyorsa, her hizmet için bir hizmete `Dockerfile` ihtiyacınız vardır.

Uygulama `DockerFile` veya hizmetin kök klasörüne sık sık yerleştirilir ve Docker'ın bu uygulamayı veya hizmeti nasıl kurup çalıştırılabildiğini bilmesi için gerekli komutları içerir. Kodunuzu (node.js, .NET Core, vb.) birlikte oluşturabilir `DockerFile` ve projenize ekleyebilirsiniz veya çevreye yeniyseniz aşağıdaki İpucu'na göz atabilirsiniz.

> [!TIP]
> Docker kapsayıcılarınızla ilgili `Dockerfile` dosyaları ve dosyaları `docker-compose.yml` kullanırken size rehberlik etmek için Docker uzantısını kullanabilirsiniz. Sonunda, muhtemelen bu araç olmadan bu tür dosyaları yazacağım, ancak Docker uzantısı kullanarak öğrenme eğrisi hızlandıracak iyi bir başlangıç noktasıdır.

Şekil 4-24'te, VS Kodu için Docker Uzantısı kullanılarak docker-compose dosyasının nasıl eklendirilebildiğini görebilirsiniz.

![VS Code için Docker uzantısı konsol görünümü.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Şekil 4-24**. **Docker dosyaları Çalışma Alanı komutuna Docker dosyaları ekle** kullanılarak eklendi

DockerFile eklediğinizde, hangi temel Docker görüntüsünü kullanacağınızı (kullanmak `FROM mcr.microsoft.com/dotnet/core/aspnet`gibi) belirtirsiniz. Özel resminizi genellikle [Docker Hub kayıt defterindeki](https://hub.docker.com/) herhangi bir resmi depodan aldığınız temel görüntünün üzerine [(.NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) veya [Node.js](https://hub.docker.com/_/node/)için bir resim gibi) oluşturursunuz.

***Mevcut resmi Docker resmini kullanma***

Sürüm numarası olan bir dil yığınının resmi deposunun kullanılması, aynı dil özelliklerinin tüm makinelerde (geliştirme, test ve üretim dahil) kullanılabilmesini sağlar.

Aşağıda bir .NET Core kapsayıcı için örnek DockerFile:

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

Bu durumda, görüntü sürüm `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`2.2 resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok kemer) satırına göre dayanmaktadır. (Bu konu hakkında daha fazla bilgi için, [ASP.NET Core Docker Resim](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sayfasına ve [.NET Core Docker Resim](https://hub.docker.com/_/microsoft-dotnet-core/) sayfasına bakın).

DockerFile'da, Docker'a çalışma zamanında kullanacağınız TCP bağlantı noktasını (bağlantı noktası 80 gibi) dinlemesi için talimat verebilirsiniz.

Kullandığınız dile ve çerçeveye bağlı olarak Dockerfile'da ek yapılandırma ayarları belirtebilirsiniz. Örneğin, `ENTRYPOINT` satır Docker'a `["dotnet", "MySingleContainerWebApp.dll"]` bir .NET Core uygulaması çalıştırmasını söyler. .NET uygulamasını oluşturmak ve çalıştırmak için SDK`dotnet CLI`ve .NET Core CLI () kullanıyorsanız, bu ayar farklı olacaktır. Burada önemli nokta, ENTRYPOINT satırı ve diğer ayarların uygulamanız için seçtiğiniz dile ve platforma bağlı olmasıdır.

> [!TIP]
> .NET Core uygulamaları için Docker görüntüleri oluşturma hakkında <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>daha fazla bilgi için .
>
> Kendi resimlerinizi oluşturma hakkında daha <https://docs.docker.com/engine/tutorials/dockerimages/>fazla bilgi edinmek için.

**Çok kemerli görüntü depolarını kullanma**

Repo'daki tek bir görüntü adı, Linux görüntüsü ve Windows görüntüsü gibi platform türevleri içerebilir. Bu özellik, Microsoft (temel görüntü oluşturucular) gibi satıcıların birden çok platformu (linux ve Windows) kapsayacak şekilde tek bir repo oluşturmasına olanak tanır. Örneğin, Docker Hub kayıt defterinde bulunan [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) deposu, linux ve Windows Nano Server için aynı görüntü adını kullanarak destek sağlar.

Bir Windows ana bilgisayardan [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) görüntüsünü çekmek Windows varyantını çekerken, linux ana bilgisayardan aynı görüntü adını çekmek Linux varyantını çeker.

***Temel resminizi sıfırdan oluşturun***

Docker'ın bu [makalesinde](https://docs.docker.com/engine/userguide/eng-image/baseimages/) açıklandığı gibi kendi Docker taban resminizi sıfırdan oluşturabilirsiniz. Docker ile yeni başlıyorsanız, bu senaryo sizin için en iyisi değildir, ancak kendi temel görüntünüzün belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Adım 3: Özel Docker resimlerinizi oluşturun ve hizmetinizi bu görüntülere katıştırma

Uygulamanızı oluşturan her özel hizmet için ilgili bir resim oluşturmanız gerekir. Uygulamanız tek bir hizmet veya web uygulamasından oluşuyorsa, tek bir görüntüye ihtiyacınız vardır.

> [!NOTE]
> "Dış döngü DevOps iş akışı" dikkate alınarak, kaynak kodunuzu bir Git deposuna (Sürekli Tümleştirme) itdiğinizde görüntüler otomatik bir yapı işlemi tarafından oluşturulur, böylece görüntüler kaynak kodunuzdan bu küresel ortamda oluşturulur.
>
> Ancak bu dış döngü rotasına gitmeyi düşünmeden önce, Docker uygulamasının kaynak kontrol sistemine (Git, vb.) düzgün çalışmayan kodu itmemeleri için doğru çalıştığından emin olmalıyız.
>
> Bu nedenle, her geliştiricinin önce yerel olarak test etmek ve tam bir özelliği zorlamak veya kaynak denetim sistemine değiştirmek isteyene kadar geliştirmeye devam etmek için tüm iç döngü işlemini yapması gerekir.

Yerel ortamınızda ve DockerFile'ı kullanmak için Şekil 4-25'te gösterildiği gibi docker build komutunu `docker-compose up --build` kullanabilirsiniz (çeşitli kapsayıcılar/hizmetlerden oluşan uygulamalar için de çalıştırabilirsiniz).

![Docker build komutunun konsol çıktısını gösteren ekran görüntüsü.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Şekil 4-25**. Çalışan docker yapı

İsteğe bağlı olarak, `docker build` doğrudan proje klasöründen çalışan yerine, önce çalıştır `dotnet publish` komutunu kullanarak gereken .NET `docker build`kitaplıkları ile dağıtılabilir bir klasör oluşturabilir ve sonra çalıştırabilirsiniz.

Bu örnek, adında `cesardl/netcore-webapi-microservice-docker:first` bir Docker`:first` görüntüsü oluşturur (belirli bir sürüm gibi bir etikettir). Birkaç kapsayıcı ile oluşan Docker uygulaması için oluşturmanız gereken her özel görüntü için bu adımı atabilirsiniz.

Mevcut görüntüleri Şekil 4-26'da gösterildiği gibi docker görüntüleri komutunu kullanarak yerel deponuzda (geliştirme makinenizde) bulabilirsiniz.

![Varolan görüntüleri gösteren komut docker görüntüleri konsol çıkışı.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Şekil 4-26**. Docker görüntülerini kullanarak mevcut görüntüleri görüntüleme

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Adım 4: Birden fazla hizmetiçeren oluşturulmuş bir Docker uygulaması oluştururken servislerinizi docker-compose.yml olarak tanımlayın

Dosyayla, `docker-compose.yml` bir sonraki adım bölümünde açıklanan dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak ilgili hizmetler kümesini tanımlayabilirsiniz.

Bu dosyayı ana veya kök çözüm klasörünüzde oluşturun; bu `docker-compose.yml` dosyada gösterilenbenzer içeriğe sahip olmalıdır:

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

Bu özel durumda, bu dosya iki hizmeti tanımlar: web hizmeti (özel hizmetiniz) ve redis hizmeti (popüler bir önbellek hizmeti). Her hizmet bir konteyner olarak dağıtılacak, bu yüzden her biri için bir beton Docker görüntü kullanmanız gerekir. Bu özel web hizmeti için, görüntüaşağıdakileri yapmanız gerekir:

- Geçerli dizindeki DockerFile'dan yapı

- Konteynerüzerindeki açık port 80'i ana makinedeki 81 portuna iletin

- Proje dizinini kapsayıcının içindeki /koda ana bilgisayara monte ederek görüntüyü yeniden oluşturmanıza gerek kalmadan kodu değiştirmenizi mümkün kılar

- Redis hizmetine web hizmetini bağla

Redis hizmeti, Docker Hub kayıt defterinden çıkarılan [en son genel redis görüntüsünü](https://hub.docker.com/_/redis/) kullanır. [redis](https://redis.io/) sunucu tarafı uygulamaları için popüler bir önbellek sistemidir.

### <a name="step-5-build-and-run-your-docker-app"></a>Adım 5: Docker uygulamanızı oluşturun ve çalıştırın

Uygulamanızda yalnızca tek bir kapsayıcı varsa, yalnızca Docker Host'unuza (VM veya fiziksel sunucu) dağıtarak uygulamanızı çalıştırmanız gerekir. Ancak, uygulamanız birden çok hizmetten oluşuyorsa, uygulamayı da *oluşturmanız*gerekir. Farklı seçenekleri görelim.

***Seçenek A: Tek bir kapsayıcı veya hizmet çalıştırma***

Docker çalışmasını kullanarak Docker görüntüsünü burada gösterildiği gibi çalıştırabilirsiniz:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Bu özel dağıtım için, 80 bağlantı noktasına gönderilen istekleri iç bağlantı noktası 5000'e yönlendireceğiz. Şimdi uygulama ana bilgisayar düzeyinde dış bağlantı noktası 80 dinliyor.

***Seçenek B: Çoklu kapsayıcı uygulaması oluşturma ve çalıştırma***

Çoğu kurumsal senaryoda, Docker uygulaması birden çok hizmetlerden oluşur. Bu gibi durumlarda, daha `docker-compose up` önce oluşturmuş olabileceğiniz docker-compose.yml dosyasını kullanan komutu (Şekil 4-27) çalıştırabilirsiniz. Bu komutu çalıştıran tüm ilgili kapsayıcıları içeren oluşan bir uygulama dağıtır.

![Docker-comto komutundan konsol çıkışı.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Şekil 4-27**. "Docker-comto up" komutunu çalıştırmanın sonuçları

Çalıştırdıktan `docker-compose up`sonra, başvurunuzu ve ilgili konteyner(ler)i Şekil 4-28'de gösterildiği gibi, VM gösteriminde gösterildiği gibi Docker Host'unuza dağıtırsınız.

![VM çok konteyner uygulamaları çalıştırıyor.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Şekil 4-28**. Docker konteynerleri dağıtılan VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Adım 6: Docker uygulamanızı test edin (yerel olarak, yerel CD VM'nizde)

Bu adım, uygulamanızın ne yaptığına bağlı olarak değişir.

Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web API "Hello World"de, DockerFile'da belirtilen TCP bağlantı noktasını sağlayarak hizmete erişmeniz gerekir.

Localhost açık değilse, hizmetinize gitmek için, bu komutu kullanarak makinenin IP adresini bulun:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Docker ana bilgisayarda bir tarayıcı açın ve bu siteye gidin; Şekil 4-29'da gösterildiği gibi uygulamanızın/hizmetin izinin çalıştığını görmeniz gerekir.

![Localhost/API/values'ten gelen yanıtın tarayıcı görünümü.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Şekil 4-29**. Docker uygulamanızı localhost kullanarak yerel olarak test etme

Port 80'i kullandığını, ancak dahili olarak 5000 portuna yönlendirildiğini unutmayın, çünkü daha önce `docker run`açıklandığı gibi bu şekilde dağıtıldı.

Bunu terminalden CURL kullanarak test edebilirsiniz. Windows'daki Docker yüklemesinde, varsayılan IP Şekil 4-30'da belirtildiği gibi 10.0.75.1'dir.

![Kıvrılma http://10.0.75.1/API/values ile elde konsol çıkışı](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Şekil 4-30**. CURL kullanarak docker uygulamasını yerel olarak test etme

**Docker üzerinde çalışan bir konteyner hata ayıklama**

Visual Studio Code, Node.js ve .NET Core kapsayıcıları gibi diğer platformları kullanıyorsanız Docker hata ayıklama destekler.

Bir sonraki bölümde açıklandığı gibi Windows veya Mac için Visual Studio'yu kullanırken Docker'da .NET Core veya .NET Framework kapsayıcılarını hata ayıklayabilirsiniz.

> [!TIP]
> Node.js Docker konteynerlerini hata ayıklama hakkında <https://blog.docker.com/2016/07/live-debugging-docker/> <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>daha fazla bilgi için bkz.

>[!div class="step-by-step"]
>[Önceki](docker-apps-development-environment.md)
>[Sonraki](visual-studio-tools-for-docker.md)
