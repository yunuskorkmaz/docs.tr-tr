---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamaları geliştirmek için "İç döngü" iş akışı öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 36fcf5769376375854c2a2631e26e8b136df0de6
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920915"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker uygulamaları için iç döngü geliştirme iş akışı

Tüm DevOps kapsayan dış döngü iş akışı tetiklemeden önce döngüsü, tüm uygulama kodlama, kullanıcılarınızın tercih edilen diller veya platformlar ve yerel olarak test her geliştiricinin makine üzerinde (Şekil 4-21) başlar. Ancak her durumda, önemli bir nokta ortak hangi dil, çerçeve veya platformlar, seçtiğiniz ne olursa olsun sahip olacaksınız. Bu belirli bir iş akışında, her zaman geliştirirken ve Docker kapsayıcıları, ancak yerel olarak test etme.

![Adım 1 - kod/Çalıştır/Hata Ayıkla](./media/image18.png)

**Şekil 4-21**. İç döngü geliştirme bağlamı

Bu bileşenler kapsayıcı veya bir Docker görüntüsü örneğini içerir:

-   Bir işletim sistemi seçimi (örneğin, bir Linux dağıtımı veya Windows)

- Geliştirici (örneğin, uygulama ikili değerleri) tarafından eklenen dosyaları

-   (Örneğin, ortam ayarlarını ve bağımlılıklarını) yapılandırma

- Docker ile çalıştırmak için hangi işlemleri için yönergeler

(Sonraki bölümde açıklanmıştır) işlem olarak Docker kullanan iç döngü geliştirme iş akışı ayarlayabilirsiniz. Yalnızca bir kez yapmanız gerektiğinden ortamı ayarlamak için ilk adımları dahil olmadığını göz önünde bulundurun.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code ve Docker CLI'yı kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma

Uygulamaları, kendi Hizmetleri artı ek kitaplıklar (bağımlılıklar) oluşur.

Şekil 4-22, genellikle her adımın ayrıntılı açıklamaları tarafından izlenen bir Docker uygulaması derlerken, gerçekleştirmesi gereken temel adımları gösterir.

![İş akışı genel bakış: Adım 1 - kod, 2. adım - dockerfile'ları, 3. adım - yazma dockerfile'ları ile 4. adımda tanımlanan görüntüleri oluşturma - 5. adım - Çalıştır kapsayıcıları docker-compose dosya ile hizmetleri tanımlamak veya dış döngü (CI/CD işlem hatları) başlayamaz veya de devam etmek için oluşturulan uygulamalar, adım 6 - Test uygulamaları, 7. adım - gönderin veloping.](./media/image19.png)

**Şekil 4-22**. Docker CLI'yı kullanarak kapsayıcılı Docker uygulamaları için yaşam döngüsü için üst düzey iş akışı

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>1. Adım: Visual Studio Code'da kodlamaya başlayın ve ilk uygulama/hizmet temel oluşturma

Uygulamanızı geliştirdiğiniz yolu Docker yaptığınız gibi benzer. Geliştirmeye devam ederken, dağıtma ve uygulama veya yerel ortamınızda (örneğin, bir Linux VM veya Windows) yerleştirilen Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.

**Yerel ortamınızda ayarlama**

Mac ve Windows için Docker'ın en son sürümleri, Docker uygulamaları geliştirmek için hiç olmadığı kadar kolay ve kurulumu basittir.

> [! BİLGİLERİ]
>
> Docker için Windows ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-windows/>.
>
>Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.

Ayrıca, Docker CLI'yı kullanırken uygulamanızı aslında geliştirebilmeniz bir kod düzenleyicisi gerekir.

Microsoft, Mac, Windows ve Linux üzerinde desteklenir ve IntelliSense ile sağlayan bir basit Kod Düzenleyicisi Visual Studio Code sağlar [birçok dil için destek](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python ve çoğu Modern dilleri) [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git tümleştirmesiyle](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [uzantıları desteğiyle](https://code.visualstudio.com/docs/extensions/overview). Bu düzenleyici Mac ve Linux geliştiriciler için harika bir çözümdür. Windows tam Visual Studio uygulamasını kullanabilirsiniz.

> [! BİLGİLERİ]
>
> Visual Studio Code için Windows, Mac veya Linux yükleme ile ilgili yönergeler için Git <https://code.visualstudio.com/docs/setup/setup-overview/>.
>
> Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.

Docker CLI ile çalışır ve herhangi bir kod Düzenleyicisi'ni kullanarak kodunuzu yazın, ancak Visual Studio Code ile Docker uzantısını kullanarak kolaylaştırır Yazar `Dockerfile` ve `docker-compose.yml` çalışma alanınızdaki dosyaları. Visual Studio IDE'den kod altında Docker CLI'yı kullanarak Docker komutları yürütmek için görevleri ve betikler çalıştırabilirsiniz.

VS Code için Docker uzantısını aşağıdaki özellikleri sağlar:

- Otomatik `Dockerfile` ve `docker-compose.yml` dosya oluşturma

- Söz dizimi vurgulama ve vurgulu ipuçları `docker-compose.yml` ve `Dockerfile` dosyaları

- (Tamamlamalar) için IntelliSense `Dockerfile` ve `docker-compose.yml` dosyaları

- Linting (hatalar ve uyarılar) için `Dockerfile` dosyaları

- En yaygın Docker komutları için komut paleti (F1) Tümleştirmesi

- Görüntüleri ve kapsayıcılar yönetmek için Gezgini tümleştirmesi

- DockerHub ve Azure kapsayıcı kayıt defterleri görüntülerinden Azure App Service'e dağıtma

Docker uzantısını yüklemek için Ctrl + Shift + P tuşlarına basın yazın `ext install`, ve ardından Market uzantısı listesini getirmek için uzantı yükleme komutu çalıştırın. Sonra aşağıdakileri yazın **docker** sonuçları filtrelemek ve ardından, Şekil 4-23'te gösterildiği gibi Docker desteği uzantısı seçin.

![VS Code için Docker uzantısını görünümü.](./media/image20.png)

**Şekil 4-23**. Visual Studio Code'da Docker uzantısını yükleme

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>2. Adım: Mevcut bir görüntüyü (düz işletim sistemi veya geliştirme ortamları .NET Core, Node.js ve Ruby gibi) ilgili bir DockerFile'ı oluşturma

İhtiyacınız olacak bir `DockerFile` ve dağıtılması için kapsayıcı başına oluşturulacak özel görüntü. Uygulamanızı tek bir özel hizmet yapılırsa, tek bir gerekir `DockerFile`. Ancak uygulamanız birden çok hizmetlerinin (olduğu gibi bir mikro hizmetler mimarisinde) oluşuyorsa, tane gerekecektir `Dockerfile` hizmet başına.

`DockerFile` Uygulamanızı veya hizmetinizi kök klasöründe bulunan yaygın olarak yerleştirilir ve Docker nasıl ayarlanacağını ve söz konusu uygulamayı veya hizmeti çalıştırılacağını bilmesi gereken komutları içerir. Oluşturabileceğiniz, `DockerFile` ve kodunuzu birlikte projenize ekleyin (node.js, .NET Core, vb.), veya ortama yeni başladıysanız, aşağıdaki ipucu göz atın.

> [!TIP]
>
> Docker uzantısını kullanırken yol göstermesi için kullanabileceğiniz `Dockerfile` ve `docker-compose.yml` Docker kapsayıcıları için ilgili dosyaları. Sonuç olarak, bu tür dosyaları bu aracı olmadan büyük olasılıkla yazacaksınız, ancak Docker uzantısını kullanmaktır, öğrenme eğrisi hızlandıracaktır iyi bir başlangıç noktası.

Şekil 4-24'te bir docker nasıl görebilirsiniz-compose dosyası, VS Code için Docker uzantısını kullanarak eklenir.

![VS Code için Docker uzantısını konsol görünümü.](./media/image24.png)

**Şekil 4-24**. Docker dosyaları kullanılarak eklenen **çalışma komut Docker ekleme dosyaları**

Bir DockerFile eklediğinizde, kullanıyor hangi temel Docker görüntüsüne belirtin (kullanma gibi `FROM mcr.microsoft.com/dotnet/core/aspnet`). Özel görüntünüzü herhangi bir resmi deponun aldığınız bir temel görüntünün üstüne genellikle oluşturacaksınız [Docker Hub kayıt defterinde](https://hub.docker.com/) (gibi bir [.NET Core için görüntü](https://hub.docker.com/_/microsoft-dotnet-core/) veya [Node.jsiçin](https://hub.docker.com/_/node/)).

***Var olan resmi bir Docker görüntüsü kullanma***

Bir sürüm numarasına sahip bir resmi bir dil yığını depoyu kullanarak, aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.

DockerFile'bir .NET Core kapsayıcı için bir örnek verilmiştir:

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Bu durumda, görüntü resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch), satır başına 2.1 sürümünü dayalı `FROM mcr.microsoft.com/dotnet/core/aspnet:2.1`. (Bu konu hakkında daha fazla bilgi için bkz. [ASP.NET Core, Docker görüntüsü](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sayfası ve [.NET Core, Docker görüntüsü](https://hub.docker.com/_/microsoft-dotnet-core/) sayfası).

DockerFile içinde Docker çalışma zamanında (örneğin, bağlantı noktası 80) kullanan TCP bağlantı noktası dinleyecek şekilde bildirebilirsiniz.

Dil ve çerçeve kullanmakta olduğunuz bağlı olarak bir Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz. Örneğin, `ENTRYPOINT` ile satır `["dotnet", "MySingleContainerWebApp.dll"]` .NET Core uygulamasını çalıştırmak için Docker söyler. SDK ve .NET Core CLI'yı kullanıyorsanız (`dotnet CLI`) .NET uygulaması derleme ve çalıştırma için bu ayarı farklı olacaktır. Burada temel nokta ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dil ve platform bağımlı olduğunu ' dir.

> [! BİLGİLERİ]
>
> .NET Core uygulamaları için Docker görüntüleri oluşturma hakkında daha fazla bilgi için Git <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Kendi görüntülerinizi oluşturma hakkında daha fazla bilgi edinmek için Git <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Çok yay görüntü depolar**

Bir tek bir görüntü adı bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir. Bu özellik, birden çok Platformu (diğer bir deyişle, Linux ve Windows) karşılamak için tek bir depo oluşturmak Microsoft (temel Görüntü Oluşturucu) gibi satıcıları sağlar. Örneğin, [dotnet/çekirdek/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) Docker Hub kayıt defterinde depo, görüntü adının aynısını kullanarak Linux ve Windows Nano sunucu için destek sağlar.

Çekme [dotnet/çekirdek/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) Windows konaktan görüntüyü, Linux değişken aynı görüntü adı, bir Linux ana bilgisayarından alınan çeker ise Windows değişken çeker.

***Temel görüntünüzü sıfırdan oluşturma***

Bu konuda açıklandığı gibi sıfırdan kendi Docker temel görüntüsünde oluşturabilirsiniz [makale](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker. Bu senaryo sizin için en iyi Docker ile yeni başlıyor ister, ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz, büyük olasılıkla değil.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>3. Adım: Hizmetinizi katıştırarak, özel Docker görüntüleri oluşturma

Uygulamanızı oluşturan özel her hizmet için ilgili bir görüntü oluşturmak gerekir. Tek bir hizmeti veya web uygulaması, uygulamanızı oluşuyorsa, yalnızca tek bir görüntü gerekir.

> [!NOTE]
>
> Görüntüler genel bir ortamda oluşturulur böylece, kaynak kodunuzu Git deposuna (sürekli tümleştirme) öğesinden gönderdiğinizde "dış döngü DevOps iş akışı" dikkate alarak, görüntüleri bir otomatik yapı işlemi tarafından oluşturulur, Kaynak kodu.
>
> Ancak Biz bu dış döngü rota giderek düşünmeden önce kaynak denetim sistemine (Git, vb.) düzgün çalışmayabilir kod itme yoktur, böylece Docker uygulaması aslında düzgün çalıştığından emin olmak oluşturmamız gerekir.
>
> Bu nedenle, her geliştirici, yerel olarak test etmek ve tam bir özelliği bildirme veya kaynak denetim sistemine değiştirmek istedikleri kadar geliştirmeye devam etmek için tüm iç döngü işlem yapmak öncelikle gerekir.

Yerel ortamınıza ve DockerFile'ı kullanarak bir görüntü oluşturmak için docker oluşturma komutu, Şekil 4-25 gösterildiği gibi kullanabilirsiniz (da çalıştırabilirsiniz `docker-compose up --build` birkaç kapsayıcılar/Hizmetleri tarafından oluşturulan uygulamalar için).

![İlerleme durumunu indirme görüntüleri gösteren docker-compose derleme, konsol çıktısı.](./media/image25.png)

**Şekil 4-25**. Çalışan docker derleme

İsteğe bağlı olarak, doğrudan çalıştırmak yerine `docker build` proje klasöründen, ilk dağıtılabilir bir klasör Çalıştır'ı kullanarak gerekli .NET kitaplıkları oluşturabilirsiniz `dotnet publish` komutunu ve ardından çalıştırın `docker build`.

Bu örnek adıyla bir Docker görüntüsü oluşturur `cesardl/netcore-webapi-microservice-docker:first` (`:first` belirli bir sürümü gibi bir etiket). Bu adım birkaç kapsayıcılar ile oluşturulmuş Docker uygulamanızı oluşturmak için ihtiyacınız olan her bir özel görüntüsünün alabilir.

Var olan görüntülerden yerel deponuzda (geliştirme makinenize) docker'ı kullanarak görüntü komutu, Şekil 4-26 gösterildiği şekilde bulabilirsiniz.

![Konsol, var olan görüntülerden gösteren komut docker görüntülerinden çıktısı.](./media/image26.png)

**Şekil 4-26**. Docker görüntüleri kullanarak var olan görüntüleri görüntüleme

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>4. Adım: Birden çok hizmeti ile oluşturulmuş bir Docker uygulaması derlerken, hizmetlerinizi docker-compose.yml tanımlayın

İle `docker-compose.yml` dosyası, bir dizi adım bir sonraki bölümde açıklanan dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili hizmetler tanımlayabilirsiniz.

Bu ana dosyasında veya kök Çözüm klasörü oluşturmak; benzer şekilde, bu konuda gösterilen içeriği olması gereken `docker-compose.yml` dosyası:

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

Bu durumda, bu dosya, iki hizmet tanımlar: web hizmeti (özel hizmeti) ve redis hizmetinin (popüler önbellek hizmeti). Yüzden somut bir Docker görüntüsü her biri için kullanılacak her bir hizmet bir kapsayıcı olarak dağıtılır. Bu belirli bir web hizmeti için görüntüyü şunları yapmanız gerekir:

- DockerFile geçerli dizinde yapıdan

- Konak makinedeki 81 numaralı bağlantı noktasına kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletme

- Proje dizini görüntüsünü yeniden oluşturmak zorunda kalmadan kodu değiştirmeniz edinerek /code kapsayıcı içindeki konağa üzerinde bağlama

- Redis hizmetine web hizmetine bağlama

Redis hizmeti kullandığı [en son genel redis görüntüsünü](https://hub.docker.com/_/redis/) Docker Hub kayıt defterinden çekilir. [redis](https://redis.io/) sunucu tarafı uygulamalar için yaygın olarak kullanılan önbellek sistemidir.

### <a name="step-5-build-and-run-your-docker-app"></a>5. Adım: Derleme ve Docker uygulamanızı çalıştırma

Yalnızca tek bir kapsayıcı uygulamanız varsa, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırmak yeterlidir. Uygulamanızı birden çok hizmetlerini yapılırsa, ancak yapmanız *onu oluşturan*, çok. Farklı seçenekler görelim.

***Seçenek A: Tek kapsayıcı ya da hizmet çalıştırma***

Burada gösterildiği gibi komutu çalıştırın: docker kullanarak Docker görüntüsünü çalıştırabilirsiniz:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Bu belirli dağıtım için biz 5000 iç bağlantı noktası için 80 numaralı bağlantı noktasına gönderilen istekleri yönlendirme. Şimdi uygulamayı dış konak düzeyinde 80 numaralı bağlantı noktasında dinliyor.

***Seçenek B: Oluşturma ve birden çok kapsayıcılı bir uygulama çalıştırma***

Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok hizmetlerini oluşacaktır. Bu durumlarda çalıştırabileceğiniz `docker-compose up` daha önce oluşturmuş olabileceğiniz docker-compose.yml dosyasını kullanır (Şekil 4-27), komutu. Bu komutu çalıştırarak tüm ilgili kapsayıcılarında oluşan bir uygulama dağıtır.

![Konsol çıktısı docker-compose komutu.](./media/image27.png)

**Şekil 4-27**. "Docker compose up" komutunu çalıştırma sonuçları

Çalıştırdıktan sonra `docker-compose up`, uygulamanız ve onun ilişkili kapsayıcılar, Docker konağı VM gösteriminde Şekil 4-28'de gösterildiği gibi dağıttığınız.

![Çok kapsayıcılı uygulamalar çalıştıran VM.](./media/image28.png)

**Şekil 4-28**. Dağıtılmış Docker kapsayıcıları ile VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>6. Adım: (Yerel olarak, yerel CD sanal makinenizin) Docker uygulamanızı test edin

Bu adım, uygulamanızı yapmak bağlı olarak değişir.

Bir basit'de .NET Core Web API'si "Hello tek kapsayıcı veya hizmet olarak dağıtılan World", yalnızca Dockerfile'da belirtilen TCP bağlantı noktası sağlayarak hizmete erişmeniz gerekecektir.

Localhost, hizmetinize gidin açık değilse şu komutu kullanarak makine için IP adresini bulun:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Docker konağı, bir tarayıcı açın ve o siteye gidin; Şekil 4-29 gösterildiği gibi uygulama/hizmet çalışıyorsa, görmeniz gerekir.

![API/localhost/değerleri yanıt tarayıcı görünümü.](./media/image29.png)

**Şekil 4-29**. Docker uygulamanızı yerel olarak localhost kullanarak test etme

80 numaralı bağlantı noktasını kullanıyor, ancak bağlantı noktası 5000 dahili olarak yönlendiriliyor nasıl ile dağıtıldığı olduğu için Not `docker run`, daha önce açıklandığı gibi.

Bu terminalde CURL kullanarak test edebilirsiniz. Windows üzerindeki Docker yüklemede varsayılan IP 10.0.75.1, Şekil 4-30 gösterilen aynıdır.

![Konsol çıktısı geçmesini http://10.0.75.1/API/values curl ile](./media/image30.png)

**Şekil 4-30**. Docker uygulaması'nın CURL kullanarak yerel olarak test etme

**Docker üzerinde çalışan bir kapsayıcısında hata ayıklama**

Node.js ve .NET Core kapsayıcıları gibi diğer platformlarda kullanıyorsanız, visual Studio Code hata ayıklama Docker destekler.

Ayrıca .NET Core veya .NET Framework Docker kapsayıcılarında kullanırken Windows için Visual Studio veya Mac, sonraki bölümde açıklandığı gibi ayıklayabilirsiniz.

> [! BİLGİLERİ]
>
> Node.js Docker kapsayıcılarında hata ayıklama hakkında daha fazla bilgi için şuraya gidin <https://blog.docker.com/2016/07/live-debugging-docker/> ve <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.

>[!div class="step-by-step"]
>[Önceki](docker-apps-development-environment.md)
>[İleri](visual-studio-tools-for-docker.md)
