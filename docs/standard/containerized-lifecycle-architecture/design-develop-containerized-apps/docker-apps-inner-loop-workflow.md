---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamaları geliştirmek için "İç döngü" iş akışı öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 03eb4662e55551678105fa9ef25b42cc05c132a5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219094"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker uygulamaları için iç döngü geliştirme iş akışı

Tüm DevOps kapsayan dış döngü iş akışı tetiklemeden önce döngüsü, tüm uygulama kodlama, kullanıcılarınızın tercih edilen diller veya platformlar ve yerel olarak test her geliştiricinin makine üzerinde (Şekil 4-14) başlar. Ancak her durumda çok önemli bir nokta ortak hangi dil, çerçeve veya platformlar, seçtiğiniz ne olursa olsun gerekir. Bu belirli bir iş akışında, her zaman geliştirdiğiniz ve Docker kapsayıcıları, ancak yerel olarak test etme.

![](./media/image18.png)

Şekil 4-14: İç döngü geliştirme bağlamı

Bu bileşenler kapsayıcı veya bir Docker görüntüsü örneğini içerir:

-   Bir işletim sistemi seçimi (örneğin, bir Linux dağıtımı veya Windows)

-   Geliştirici (örneğin, uygulama ikili değerleri) tarafından eklenen dosyaları

-   (Örneğin, ortam ayarlarını ve bağımlılıklarını) yapılandırma

-   Docker ile çalıştırmak için hangi işlemleri için yönergeler

(Sonraki bölümde açıklanmıştır) işlem olarak Docker kullanan iç döngü geliştirme iş akışı ayarlayabilirsiniz. Bu yalnızca bir kez yapmanız gerektiğinden ortamı ayarlamak için ilk adımlarında olmadığını dahil dikkate alın.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code ve Docker CLI'yı kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma

Uygulamaları, kendi Hizmetleri artı ek kitaplıklar (bağımlılıklar) oluşur.

Şekil 4-15, genellikle her adımın ayrıntılı açıklamaları tarafından izlenen bir Docker uygulaması derlerken, gerçekleştirmesi gereken temel adımları gösterir.

![](./media/image19.png)

Şekil 4-15: Docker CLI'yı kullanarak kapsayıcılı Docker uygulamaları için yaşam döngüsü için üst düzey iş akışı

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>1. Adım: Visual Studio Code'da kodlamaya başlayın ve ilk uygulama/hizmet temel oluşturma

Uygulamanızı geliştirdiğiniz biçimini, Docker yaptığınız gibi oldukça benzerdir. Geliştirmeye devam ederken, dağıtan ve uygulamanızı veya yerel ortamınızda (örneğin, bir Linux VM veya Windows) yerleştirilen Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.

**Yerel ortamınızda ayarlama**

Mac ve Windows için Docker'ın en son sürümleri, Docker uygulamaları geliştirmek için hiç olmadığı kadar kolay ve kurulumu basittir.

**Daha fazla bilgi** için Docker Windows ayarlama hakkında yönergeler için Git [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).

Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.

Ayrıca, Docker CLI'yı kullanırken uygulamanızı aslında geliştirebilmeniz bir kod düzenleyicisi gerekir.

Microsoft, Mac, Windows ve Linux üzerinde desteklenir ve IntelliSense ile sağlayan bir basit Kod Düzenleyicisi Visual Studio Code sağlar [birçok dil için destek](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python ve çoğu Modern dilleri) [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git tümleştirmesiyle](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [uzantıları desteğiyle](https://code.visualstudio.com/docs/extensions/overview). Bu düzenleyici Mac ve Linux geliştiriciler için harika bir çözümdür. Windows tam Visual Studio uygulamasını kullanabilirsiniz.

**Daha fazla bilgi** Visual Studio için Windows, Mac veya Linux yükleme ile ilgili yönergeler için Git <https://code.visualstudio.com/docs/setup/setup-overview/>.

Docker CLI ile çalışır ve herhangi bir kod Düzenleyicisi'ni kullanarak kodunuzu yazın, ancak Visual Studio Code kullanıyorsanız, bunu Dockerfile yazar için kolay ve docker-compose.yml dosyaları çalışma alanınızda kolaylaştırır. Ayrıca, altında Docker CLI'yı kullanarak ayrıntılandırılmış işlemleri çalışması gereken betikleri ister IDE üzerinden Visual Studio Code görevler çalıştırabilirsiniz.

Visual Studio Code'u yüklemek için ihtiyacınız uzantı tarafından sağlanır. Bunu tuşuna Ctrl + Shift + P yapmak için yazın **ext yükleme**, ve Uzantıları'nı çalıştırın: Market uzantısı listesini getirmek için komut uzantısı yükleyin. Sonra aşağıdakileri yazın **docker** sonuçları filtreleyin ve ardından Dockerfile ve Docker Compose dosyası (yml) destek uzantısı, Şekil 4-16 gösterildiği şekilde seçin.

![](./media/image20.png)

Şekil 4-16: Visual Studio Code'da Docker uzantısını yükleme

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>2. Adım: Mevcut bir görüntüyü (düz işletim sistemi veya geliştirme ortamları .NET Core, Node.js ve Ruby gibi) ilgili bir DockerFile'ı oluşturma

Kapsayıcısını, dağıtılmasını ve oluşturulacak özel görüntü başına bir DockerFile gerekir, bu nedenle, uygulamanız tek bir özel hizmet yapılırsa, tek bir DockerFile gerekir. Ancak, uygulamanız birden çok hizmeti (olduğu gibi bir mikro hizmetler mimarisinde) oluşan, hizmet başına bir Dockerfile gerekir.

DockerFile, uygulamanızı veya hizmetinizi kök klasörü içinde genellikle yerleştirilir ve Docker nasıl ayarlanacağını ve söz konusu uygulamayı veya hizmeti çalıştırılacağını bilmesi gereken komutları içerir. DockerFile'ı oluşturabilir ve kodunuzun yanı sıra projenize ekleyin (node.js, .NET Core, vb.), veya ortama yeni başladıysanız, aşağıdaki ipucu göz atın.

> [!TIP]
> Adlı bir komut satırı aracını kullanabilirsiniz [yo docker](https://github.com/Microsoft/generator-docker), iskele oluşturulduğunu hangi dosyaların projenizden dili seçin ve gerekli Docker yapılandırma dosyaları ekler. Temelde, kullanmaya başlayan geliştiriciler yardımcı olmak için ilgili DockerFile oluşturduğu docker-compose.yml ve ilişkili diğer komut oluşturun ve Docker kapsayıcılarınızı çalıştırır. Bu yeoman oluşturucuyu birkaç soruyu soran seçili geliştirme dil ve hedef kapsayıcı konağı, ister.

![yo docker](./media/image21.png)

Örneğin, Şekil 4-17 Windows ve Mac'te yo çalışmak üzere önceden yapılandırılmış örnek kod projeleri (şu anda .NET Core, Golang ve desteklenen dilleri olarak Node.js) oluşturacak docker, çalıştırma, her iki durumda da iki ekran görüntüleri terminaller gösterir Docker'ın üstünde.

![](./media/image22.PNG)  ![](./media/image23.png)

Şekil 4-17: yo docker komut aracını (solda) Windows ve Mac'te

Şekil 4-18 iskelesi oluşturulmuş için var olan bir .NET Core projesi oluşturduktan sonra yo docker kullanan bir örnek gösterir.

![](./media/image24.PNG)

Şekil 4-18: yo docker ile var olan bir .NET Core proje bir yerde

DockerFile ("microsoft/dotnet:1.0.0-core" kullanma gibi) kullanacaksınız hangi temel Docker görüntüsünü belirtin. Özel görüntünüzü herhangi bir resmi deponun sayfasından edinebilirsiniz bir temel görüntünün üstüne genellikle oluşturacağınız [Docker Hub kayıt defterinde](https://hub.docker.com/) (gibi bir [.NET Core için görüntü](https://hub.docker.com/r/microsoft/dotnet/) veya bir [Node.jsiçin](https://hub.docker.com/_/node/)).

***Seçenek A: Var olan resmi bir Docker görüntüsü kullanma***

Bir sürüm numarasına sahip bir resmi bir dil yığını depoyu kullanarak, aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.

DockerFile'bir .NET Core kapsayıcı için bir örnek aşağıda verilmiştir:

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Bu durumda, bunu microsoft/aspnetcore:1.0.1 adlı Linux için resmi ASP.NET Core Docker görüntüsünü 1.0.1 sürümü kullanıyor. Daha fazla ayrıntı için başvurun [ASP.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/aspnetcore/) ve [.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/dotnet/). Düğüm: 4 gibi başka bir karşılaştırılabilir görüntü kullanabilecek-Node.js veya diğer önceden yapılandırılmış birçok görüntüler bulabileceğiniz geliştirme diller için onbuıld [Docker Hub](https://hub.docker.com/explore/).

DockerFile içinde ayrıca isteyin (örneğin, bağlantı noktası 80) çalışma zamanında kullanacağınız TCP bağlantı noktasını dinlemek için Docker gerekir.

Docker, uygulamayı çalıştırmak nasıl olduğunu bilmesi için kullanmakta olduğunuz dil/framework bağlı olarak DockerFile içinde ekleyebilirsiniz yapılandırmanın diğer satırlar var. ENTRYPOINT satırla örneği için ihtiyacınız \["dotnet", "MyCustomMicroservice.dll"\] oluşturup hizmetinizi çalıştırmak için bir yaklaşım bağlı olarak birden çok çeşitleri olabilir ancak bir .NET Core uygulamasını çalıştırmak için. .NET uygulaması derleyebilir ve için SDK'sı ve dotnet CLI kullanıyorsanız, biraz farklı olacaktır. ENTRYPOINT satırı artı ek satırlar, uygulamanız için seçtiğiniz dil/platforma bağlı olarak farklı olacaktır alt çizgidir.

**Daha fazla bilgi** .NET Core uygulamaları için Docker görüntüleri oluşturma hakkında daha fazla bilgi için Git <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.

Kendi görüntülerinizi oluşturma hakkında daha fazla bilgi edinmek için Git [ https://docs.docker.com/engine/\ öğreticiler/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Çok platformlu görüntü depolar**

Windows kapsayıcıları daha yaygın hale geldikçe, tek bir depoda bir Linux ve Windows görüntüsü gibi platformu çeşitleri içerebilir. Bu, tek bir depo gibi birden çok platform karşılamak üzere kullanılacak satıcılar için mümkün kılan docker'da kullanıma sunulacak yeni bir özelliktir [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) DockerHub kayıt defterinde kullanılabilir olan depo. Bir özellik Canlı gelir gibi görüntü adının aynısını, bir Linux ana bilgisayarından alınan Linux değişken çeker ise Windows konaktan bu görüntüyü çekmeyi Windows değişken çeker.

***Seçenek B: Temel görüntünüzü sıfırdan oluşturma***

Bu konuda açıklandığı gibi sıfırdan kendi Docker temel görüntüsünde oluşturabilirsiniz [makale](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker. Bu, Docker ile yeni başlıyorsanız, sizin için en büyük olasılıkla bir senaryodur ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>3. Adım: Hizmetinizi katıştırarak, özel Docker görüntüleri oluşturma

Uygulamanızı oluşturan özel her hizmet için ilgili bir görüntü oluşturmak gerekir. Tek bir hizmeti veya web uygulaması, uygulamanızı oluşuyorsa, yalnızca tek bir görüntü gerekir.

> [!NOTE]
> Görüntüler genel bir ortamda oluşturulur böylece, kaynak kodunuzda bir Git deposuna (sürekli tümleştirme) gönderdiğinizde "dış döngü DevOps iş akışı" dikkate alarak, görüntüleri bir otomatik yapı işlemi tarafından gelen oluşturulur, Kaynak kodu.

Ancak Biz bu dış döngü rota giderek göz önünde bulundurun önce kaynak denetim sistemine (Git, vb.) düzgün çalışmayabilir kod itme yoktur, böylece Docker uygulaması aslında düzgün çalıştığından emin olmak gerekiyor.

Bu nedenle, her geliştirici, yerel olarak test etmek ve tam bir özelliği bildirme veya kaynak denetim sistemine değiştirmek istedikleri kadar geliştirmeye devam etmek için tüm iç döngü işlem yapmak öncelikle gerekir.

Yerel ortamınıza ve DockerFile'ı kullanarak bir görüntü oluşturmak için docker oluşturma komutu, Şekil 4-19'gösterildiği gibi kullanabilirsiniz (da çalıştırabilirsiniz docker-compose--'kurmak birkaç kapsayıcılar/Hizmetleri tarafından oluşturulan uygulamalar için derleme).

![](./media/image25.png)

Şekil 4-19: Çalışan docker derleme

İsteğe bağlı olarak, doğrudan docker çalıştırmak yerine Proje klasöründen yapı, ilk çalıştırma dotnet kullanarak yayımlama komutu ve docker derleme çalıştırın gerekli .NET kitaplıklarıyla dağıtılabilir bir klasör oluşturabilirsiniz.

Bu örnekte, bu bir Docker görüntüsü cesardl/netcore-webapı-mikro adı ile oluşturur-docker: ilk (: önce belirli bir sürümü gibi bir etiketi olan). Bu adım birkaç kapsayıcılar ile oluşturulmuş Docker uygulamanızı oluşturmak için ihtiyacınız olan her bir özel görüntüsünün alabilir.

Var olan görüntülerden yerel deponuzda (geliştirme makinenize) docker'ı kullanarak görüntü komutu, Şekil 4-20'de gösterildiği gibi bulabilirsiniz.

![](./media/image26.png)

Şekil 4-20: Docker görüntüleri kullanarak var olan görüntüleri görüntüleme

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>4. Adım: (İsteğe bağlı) Birden çok hizmeti ile oluşturulmuş bir Docker uygulaması derlerken, hizmetlerinizi docker-compose.yml tanımlayın

Docker-compose.yml dosyasıyla, bir dizi adım bir sonraki bölümde açıklanan dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili hizmetler tanımlayabilirsiniz.

Bu ana dosyasında veya kök Çözüm klasörü oluşturmanız gerekir; Aşağıdaki docker-compose.yml dosyasına benzer içeriğe sahip olmalıdır:

```yml
version: '2'
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

-   DockerFile geçerli dizinde yapıdan

-   Konak makinedeki 81 numaralı bağlantı noktasına kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletme

-   Proje dizini görüntüsünü yeniden oluşturmak zorunda kalmadan kodu değiştirmeniz edinerek /code kapsayıcı içindeki konağa üzerinde bağlama

-   Redis hizmetine web hizmetine bağlama

Redis hizmeti kullandığı [en son genel redis görüntüsünü](https://hub.docker.com/_/redis/) Docker Hub kayıt defterinden çekilir. [redis](https://redis.io/) sunucu tarafı uygulamalar için çok popüler önbellek sistemidir.

### <a name="step-5-build-and-run-your-docker-app"></a>5. Adım: Derleme ve Docker uygulamanızı çalıştırma

Yalnızca tek bir kapsayıcı uygulamanız varsa, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırmak yeterlidir. Uygulamanızı birden çok hizmetlerini yapılırsa, ancak yapmanız *onu oluşturan*, çok. Farklı seçenekler görelim.

***Seçenek A: Tek kapsayıcı ya da hizmet çalıştırma***

Burada gösterildiği gibi komutu çalıştırın: docker kullanarak Docker görüntüsünü çalıştırabilirsiniz:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Bu belirli dağıtım için biz 5000 iç bağlantı noktası için 80 numaralı bağlantı noktasına gönderilen istekleri yönlendirme, unutmayın. Artık, uygulamanın dış konak düzeyinde 80 numaralı bağlantı noktasında dinliyor.

***Seçenek B: Oluşturma ve birden çok kapsayıcılı bir uygulama çalıştırma***

Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok hizmetlerini oluşacaktır. Bu durumlarda komutunu çalıştırabilirsiniz docker-compose (Şekil 4-21 ayarlama), hangi daha önce oluşturmuş olabileceğiniz docker-compose.yml dosyasını kullanır. Bu komutu çalıştırarak tüm ilgili kapsayıcılarında oluşan bir uygulama dağıtır.

![](./media/image27.png)

Şekil 4-21: "Docker compose up" komutunu çalıştırma sonuçları

Docker'ı çalıştırdıktan sonra-oluşturmanıza, uygulamanız ve onun ilişkili kapsayıcılar, Docker konağı VM gösteriminde Şekil 4-22'de gösterildiği gibi dağıtın.

![](./media/image28.png)

Şekil 4-22: Dağıtılmış Docker kapsayıcıları ile VM

Not docker-compose ayarlama ve docker run kapsayıcılarınızı geliştirme ortamınızda test etmek için yeterli olmayabilir. ancak, bunları Docker kümeleriyle çalışmak görmeyi ve Docker Swarm, Mesosphere DC/OS veya Kubernetes düzenleyicileri gibi kullanmamak ölçeği artırma oluşturabilmek. Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) (Docker için Windows ve Mac sürümünden itibaren kullanılabilir sürüm 1.12), dağıtın ve docker hizmeti oluşturmak için tek Hizmetleri gibi ya da işiniz ek komutlar ile test için ihtiyacınız birden çok kapsayıcılardan oluşan bir uygulama dağıtma, paket oluşturma kullanarak docker ve docker dağıtma myBundleFile, makalesinde açıklandığı gibi bir yığın oluşturulmuş uygulama dağıtarak [dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) docker.

İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) farklı dağıtım komutları ve komut dosyaları, de kullanmanız gerekir.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>6. Adım: (Yerel olarak, yerel CD sanal makinenizin) Docker uygulamanızı test edin

Bu adım, uygulamanızı yapmak bağlı olarak değişir.

Bir çok basit .NET Core Web API'si "Hello tek kapsayıcı veya hizmet olarak dağıtılan World", yalnızca Dockerfile'da belirtilen TCP bağlantı noktası sağlayarak hizmete erişmeniz gerekecektir.

Localhost, hizmetinize gidin açık değilse şu komutu kullanarak makine için IP adresini bulun:

docker-machine IP *your-container-name*

Docker konağı, bir tarayıcı açın ve o siteye gidin; Şekil 4-23'te gösterildiği gibi uygulama/hizmet çalışıyorsa, görmeniz gerekir.

![](./media/image29.png)

Şekil 4-23: Docker uygulamanızı yerel olarak localhost kullanarak test etme

Nasıl bunu çalıştırmak, docker ile daha önce açıklandığı gibi dağıtılmış olduğu için 80 numaralı bağlantı noktasını kullanıyor, ancak dahili olarak, bağlantı noktası 5000 yönlendirilen unutmayın.

Bu terminalde CURL kullanarak test edebilirsiniz. Windows üzerindeki Docker yüklemede varsayılan IP 10.0.75.1, Şekil 4-24 gösterilen aynıdır.

![](./media/image30.png)

Şekil 4-24: Docker uygulaması'nın CURL kullanarak yerel olarak test etme

**Docker üzerinde çalışan bir kapsayıcısında hata ayıklama**

Node.js ve .NET Core kapsayıcıları gibi diğer platformlarda kullanıyorsanız, visual Studio Code hata ayıklama Docker destekler.

Ayrıca Docker kapsayıcılarında .NET Core Visual Studio kullanarak, sonraki bölümde açıklandığı gibi ayıklayabilirsiniz.

**Daha fazla bilgi:** Node.js Docker kapsayıcılarında hata ayıklama hakkında daha fazla bilgi için şuraya gidin <https://blog.docker.com/2016/07/live-debugging-docker/> ve [ https://blogs.msdn.microsoft.com/\ kullanıcı\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-Big-Debugging-Updates-Rich-Object-hover-Conditional-Breakpoints-node-js-Mono-More/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).

>[!div class="step-by-step"]
>[Önceki](docker-apps-development-environment.md)
>[İleri](visual-studio-tools-for-docker.md)