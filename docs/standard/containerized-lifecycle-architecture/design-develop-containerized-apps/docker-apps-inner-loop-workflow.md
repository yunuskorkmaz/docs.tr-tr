---
title: "Docker uygulamaları için iç döngü geliştirme iş akışı"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3605a6cd53db695de3af015a777e3c1a0e92af58
ms.sourcegitcommit: 672c9cd122c13c9813f57f022c86ebdf6dd69b4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker uygulamaları için iç döngü geliştirme iş akışı

Tüm DevOps kapsayıcı döngü dış iş akışı tetiklemeden döngüsü, tüm uygulama kodlama, kendi tercih edilen dil ya da platformlar kullanarak ve yerel olarak test her geliştiricinin makinesinde (Şekil 4-14) başlar. Ancak her durumda, çok önemli bir nokta ortak hangi dil, framework ya da platformlar seçtiğiniz olsun gerekir. Bu belirli iş akışındaki her zaman geliştirdiğiniz ve Docker kapsayıcıları, ancak yerel olarak test etme.

![](./media/image18.png)

Şekil 4-14: iç döngü geliştirme bağlamı

Kapsayıcı veya bir Docker görüntüsü örneği şu bileşenleri içerir:

-   Bir işletim sistemi seçim (örneğin, bir Linux dağıtım veya Windows)

-   (Örneğin, uygulama ikili dosyaları) geliştirici tarafından eklenen dosyalar

-   Yapılandırma (örneğin, ortam ayarlarını ve bağımlılıklarını)

-   Docker tarafından çalıştırmak için hangi işlemleri için yönergeler

Docker (sonraki bölümde açıklanan) bir işlem olarak kullanan iç döngü geliştirme iş akışı ayarlayabilirsiniz. Yalnızca bir kez yapmanız gerektiğinden ilk ortamını ayarlama adımlarını olmadığını dahil dikkate alın.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code ve Docker CLI kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma

Uygulamaları, kendi Hizmetleri artı ek kitaplıkları (bağımlılıklar) yapılır.

Şekil 4-15 genellikle her bir adımın ayrıntılı açıklamaları tarafından izlenen bir Docker uygulaması oluştururken gerçekleştirmesi gereken temel adımlarda gösterir.

![](./media/image19.png)

Şekil 4-15: Docker CLI kullanarak kapsayıcılı Docker uygulama yaşam döngüsü için üst düzey iş akışı

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>1. adım: Visual Studio kodda kodlama başlatmak ve ilk uygulama/hizmet taban çizgisi oluşturma

Uygulamanızı geliştirme oldukça benzer Docker yapmak şekilde yoludur. Geliştirme sırasında dağıtma ve uygulama veya Docker kapsayıcıları (örneğin, bir Linux VM veya Windows), yerel ortamınızda yerleştirilen içinde çalışan hizmetler sınama olduğundan farktır.

**Yerel ortamını ayarlama**

Mac ve Windows için Docker en son sürümleri, Docker uygulamaları geliştirmek için her zamankinden daha kolay ve Kurulum basittir.

**Daha fazla bilgi** Docker Windows için ayarlama hakkında yönergeler için Git [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).

Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.

Ayrıca, Docker CLI kullanırken, uygulamanızın gerçekte geliştirebilirsiniz böylece bir kod düzenleyicisinde gerekir.

Microsoft, Mac, Windows ve Linux desteklenir ve IntelliSense ile sağlayan bir basit bir kod düzenleyicisidir Visual Studio Code sağlar [desteklemek için çok sayıda dilleri](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Git, Java, Ruby, Python ve çoğu Modern dilleri), [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git ile tümleştirme](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [Uzantıları desteği](https://code.visualstudio.com/docs/extensions/overview). Mac ve Linux geliştiricileri için harika bir sığdırma düzenleyicisidir. Windows, tam Visual Studio uygulama de kullanabilirsiniz.

**Daha fazla bilgi** Windows için Visual Studio, Mac veya Linux yükleme ile ilgili yönergeler için Git [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).

Docker CLI ile çalışır ve herhangi bir kod düzenleyicisini kullanarak kodunuzu yazma, ancak Visual Studio Code kullanırsanız, yazar Dockerfile kolay ve docker-compose.yml dosyaları çalışma alanınızda kolaylaştırır. Ayrıca, Docker CLI altında kullanarak ayrıntılandırılmış işlemleri çalıştıran komut dosyaları ister IDE gelen Visual Studio Code görevleri çalıştırabilir.

Visual Studio Code yüklemeniz gerekir bir uzantı tarafından sağlanır. Tuşuna Ctrl + Shift + P, bunun için türü **ext yüklemek**, ve Uzantıları'nı çalıştırın: Market uzantısı listesini getirmek için yükleme uzantısını komutu. Sonra aşağıdakileri yazın **docker** sonuçlara filtre uygulamak ve ardından Dockerfile ve Docker oluşturan dosyasını (yml) destek uzantısı, Şekil 4-16'gösterildiği gibi seçin.

![](./media/image20.png)

Şekil 4-16: Visual Studio kodda Docker uzantı yükleme

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>2. adım: var olan bir görüntüsünü (düz işletim sistemi veya geliştirme ortamları .NET Core, Node.js ve Ruby gibi) ilgili bir DockerFile oluşturma

Uygulamanız, tek bir özel hizmet yapılırsa, bu nedenle, tek bir DockerFile gerekir, bir DockerFile dağıtılacak kapsayıcı ve oluşturulacak özel görüntü başına gerekir. Ancak, uygulamanız (örneğin, bir mikro mimarisi) birden çok hizmet oluşan bir Dockerfile hizmeti başına ihtiyacınız vardır.

DockerFile genellikle uygulama veya hizmet kök klasörü içinde yerleştirilir ve bu Docker ayarlamak ve bu uygulamayı veya hizmeti çalıştırmak nasıl bilmesi için gerekli komutları içerir. DockerFile oluşturabilir ve kodunuzun yanı sıra projenize ekleyin (node.js, .NET Core, vb.), ya da ortama yeniyseniz, aşağıdaki ipucu göz atın.

> [!TIP]
> Adlı bir komut satırı aracını kullanabilirsiniz [yo docker](https://github.com/Microsoft/generator-docker), hangi dosyaların projenizden dili seçin ve gerekli Docker yapılandırma dosyaları ekler iskelesini kurar. Temel olarak, geliştiricilerin Başlarken yardımcı olmak için uygun DockerFile oluşturduğu docker-compose.yml ve diğer ilişkili betikler oluşturun ve Docker kapsayıcılarınızı çalıştırın. Bu yeoman oluşturucunun seçili geliştirme dilini ve hedef kapsayıcı konak isteyen birkaç soruyla ister.

![yo docker](./media/image21.png)

Örneğin, Şekil 4-17 Windows ve Mac'te yo çalışmak üzere önceden yapılandırılmış örnek kodu projeleri (şu anda .NET Core, Golang ve desteklenen diller olarak Node.js) oluşturacak docker çalıştıran, her iki durumda da Terminal gelen iki ekran görüntüleri gösterir Docker üstündeki.

![](./media/image22.PNG)  ![](./media/image23.png)

Şekil 4-17: yo docker komut aracını (soldaki) Windows ve Mac'te

Şekil 4-18 iskele kurulmuş yerinde varolan bir .NET Core projesi oluşturduktan sonra yo docker kullanarak bir örnek sunulmaktadır.

![](./media/image24.PNG)

Şekil 4-18: yo docker varolan bir .NET Core ile proje bir yerde

DockerFile ("microsoft/dotnet:1.0.0-core" kullanarak gibi) kullanacaksınız temel hangi Docker görüntüsü belirtin. Genellikle resmi herhangi depodan alabilirsiniz temel bir görüntü üstünde özel görüntünüzü oluşturacaksınız [Docker hub'a kayıt defteri](https://hub.docker.com/) (gibi bir [.NET Core için görüntü](https://hub.docker.com/r/microsoft/dotnet/) veya bir [Node.jsiçin](https://hub.docker.com/_/node/)).

***Seçenek A: kullanımı var olan bir resmi Docker görüntüsünü***

Sürüm numarası olan bir dil yığınının resmi bir depo kullanarak (geliştirme, test ve üretim dahil) tüm makinelerde aynı dil özellikleri kullanılabilir olmasını sağlar.

.NET Core kapsayıcı için bir örnek DockerFile aşağıdadır:

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

Bu durumda, onu microsoft/aspnetcore:1.0.1 adlı Linux için resmi ASP.NET Core Docker görüntüsünün 1.0.1 sürümü kullanıyor. Daha fazla ayrıntı için başvurun [ASP.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/aspnetcore/) ve [.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/dotnet/). Düğüm: 4 gibi başka bir karşılaştırılabilir görüntü ayrıca kullanıyor-Node.js veya diğer önceden yapılandırılmış birçok görüntüleri kullanılabilir geliştirme diller için onbuild [Docker hub'a](https://hub.docker.com/explore/).

DockerFile içinde de (örneğin, bağlantı noktası 80) çalışma zamanında kullanacağı TCP bağlantı noktasını dinlemek için Docker istemeniz gerekir.

Uygulamayı çalıştırmak nasıl Docker bilmesi için kullanmakta olduğunuz dil/framework bağlı olarak DockerFile ekleyebilirsiniz yapılandırmasının diğer satırlar vardır. ENTRYPOINT satırıyla örneği için ihtiyacınız \["dotnet", "MyCustomMicroservice.dll"\] oluşturup, hizmetinizi çalıştırmak için bir yaklaşım bağlı olarak birden çok çeşitleri sahip olabilirsiniz, ancak bir .NET Core uygulamayı çalıştırmak için. Derleme ve çalıştırma .NET uygulaması için SDK ve dotnet CLI kullanıyorsanız, biraz farklı olacaktır. ENTRYPOINT satır yanı sıra ek satırlar, uygulamanız için seçtiğiniz dil/platforma bağlı olarak farklı olacaktır alt çizgidir.

**Daha fazla bilgi** .NET Core uygulamaları için Docker görüntülerinizi oluşturmak hakkında daha fazla bilgi için Git <https://docs.microsoft.com/dotnet/articles/core/docker/building-net-docker-images>.

Kendi görüntüleri oluşturma hakkında daha fazla bilgi için şuraya gidin [https://docs.docker.com/engine/ \öğreticileri/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Birden çok platform görüntüsü depoları**

Windows kapsayıcıları daha yaygın hale gibi tek bir depo Linux ve Windows görüntüsü gibi platform çeşitleri içerebilir. Bu, birden çok platformu gibi karşılamak üzere tek bir depoyu kullanacak şekilde satıcılar için mümkün kılar Docker gelen yeni bir özelliktir [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) DockerHub kayıt kullanılabilir deposu. Özellik Canlı geldiğinde aynı görüntü adı Linux ana bilgisayardan çekme Linux değişken çeker ancak bu görüntüyü Windows ana bilgisayardan çekme Windows değişken çeker.

***Temel görüntünüzde sıfırdan seçenek B: oluşturma***

Bu konuda açıklandığı gibi sıfırdan kendi Docker temel görüntü oluşturabilir [makale](https://docs.docker.com/engine/userguide/eng-image/baseimages/) Docker gelen. Bu Docker ile yeni başlıyorsanız, sizin için en iyi şekilde büyük olasılıkla bir senaryodur, ancak temel görüntünüzün belirli BITS ayarlamak istiyorsanız, bunu yapabilirsiniz.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>3. adım: özel Docker görüntülerinizi hizmetinizi katıştırmak oluşturma

Uygulamanızı oluşur her özel hizmeti için ilgili görüntü oluşturmanız gerekir. Uygulamanızı bir tek hizmeti veya web uygulaması oluşuyorsa, yalnızca tek bir görüntü gerekir.

> [!NOTE]
> Görüntüleri genel ortamında oluşturulmayacak bir Git deposu (sürekli tümleştirme), kaynak kodunuzu itme her "dış döngü DevOps iş akışı" dikkate alarak, görüntüleri otomatik derleme süreci tarafından oluşturulur, Kaynak kodu.

Ancak Biz bu dış döngü rota gitmeyi göz önünde bulundurun önce kaynak denetim sistemi (Git, vb.) düzgün çalışmayabilir kod itme yok böylece Docker uygulama gerçekte düzgün çalıştığından emin olmak gerekiyor.

Bu nedenle, her geliştirici, yerel olarak test ve bunlar tam bir özelliği bildirme veya kaynak denetim sistemi değiştirmek istediğiniz kadar geliştirmeye devam etmek için tüm iç döngüsü işlemi yapmak öncelikle gerekir.

Yerel ortamınıza ve DockerFile kullanarak bir görüntü oluşturmak için docker yapı komutu, Şekil 4-19'gösterildiği gibi kullanabilirsiniz (de çalıştırabilirsiniz docker compose'u birkaç kapsayıcıları/Hizmetleri tarafından oluşturulmuş uygulamalar için yukarı--yapı).

![](./media/image25.png)

Şekil 4-19: çalışan docker derleme

İsteğe bağlı olarak, doğrudan docker çalıştırmak yerine projenin klasöründen derleme, ilk çalıştırma dotnet kullanarak komut yayımlamak ve docker yapı çalıştırmak gerekli .NET kitaplıklarıyla dağıtılabilir bir klasör oluşturabilirsiniz.

Bu örnekte, bu bir Docker görüntü cesardl/netcore-webapı-mikro adı ile oluşturur-docker: ilk (: önce belirli bir sürümü gibi bir etiketi olan). Bu adım birkaç kapsayıcıları ile oluşan Docker uygulamanızı oluşturmak için gereken her özel görüntü için alabilir.

Var olan görüntüleri, yerel depoda (geliştirme makinenizi) docker kullanarak görüntüleri komutu, Şekil 4-20'de gösterildiği gibi bulabilirsiniz.

![](./media/image26.png)

Şekil 4-20: docker görüntüleri kullanarak var olan görüntüleri görüntüleme

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>4. adım: (İsteğe bağlı) tanımlama docker-compose.yml birden çok hizmetleriyle oluşan bir Docker uygulaması oluştururken, hizmetleri

Docker-compose.yml dosyası ile oluşturulmuş bir uygulama olarak bir sonraki adım bölümde açıklanan dağıtım komutlarla dağıtılması için ilgili hizmetler kümesini tanımlayabilir.

Bu, ana dosyasında veya kök çözüm klasör oluşturmanız gerekir. Aşağıdaki docker-compose.yml dosyası benzer içeriğe sahip olmalıdır:

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

Bu örnekte, bu dosya, iki hizmet tanımlar: web hizmeti (özel hizmeti) ve redis hizmeti (popüler önbellek hizmeti). Somut bir Docker görüntü her biri için kullanılacak ihtiyacımız şekilde her bir hizmet bir kapsayıcı olarak dağıtılır. Bu belirli web hizmeti için görüntü aşağıdakileri yapmanız gerekir:

-   DockerFile geçerli dizinde gelen derleme

-   Kullanıma sunulan bağlantı noktası 80 konak makinedeki 81 numaralı bağlantı noktasına kapsayıcısı üzerinde ilet

-   Konaktaki görüntüsünü yeniden oluşturmak zorunda kalmadan kodu değiştirmeniz edinerek kapsayıcı içindeki /code için proje bağlama

-   Web hizmeti redis hizmetine bağlama

Redis hizmet kullandığı [son ortak redis görüntü](https://hub.docker.com/_/redis/) Docker hub'a kayıt defterinden çekilen. [redis](http://redis.io/) sunucu tarafı uygulamalar için çok popüler önbellek sistemidir.

### <a name="step-5-build-and-run-your-docker-app"></a>5. adım: Derleme ve Docker uygulamanızı çalıştırma

Yalnızca tek bir kapsayıcı uygulamanız varsa, yalnızca, Docker ana (VM veya fiziksel sunucu) dağıtarak çalıştırmak yeterlidir. Uygulamanız birden çok hizmetlerini yapılırsa, ancak yapmanız *onu oluşturan*, çok. Farklı seçenekler görelim.

***Y: Çalıştır tek bir kapsayıcı veya hizmet seçeneği***

Aşağıda gösterildiği gibi komutu çalıştırmak docker kullanarak Docker görüntünün çalıştırabilirsiniz:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Bu belirli dağıtım için biz 5000 iç bağlantı noktası 80 numaralı bağlantı noktasına gönderilen istekleri yönlendirme olduğunu unutmayın. Şimdi, uygulama dış ana bilgisayar düzeyinde 80 numaralı bağlantı noktasında dinliyor.

***Seçenek B: oluşturma ve çalıştırma birden çok kapsayıcı uygulama***

Çoğu Kurumsal senaryoda, Docker uygulama birden çok hizmetlerinden oluşur. Bu durumlarda, komutunu çalıştırabilirsiniz docker compose'u (Şekil 4-21 yukarı), hangi daha önce oluşturmuş olabileceğiniz docker-compose.yml dosyası kullanır. Bu komutu çalıştırmak, tüm ilgili kapsayıcılarında oluşan bir uygulamayla dağıtır.

![](./media/image27.png)

Şekil 4-21: "docker-oluşturmanıza" komutunu çalıştırarak sonuçları

Docker çalıştırdıktan sonra-oluşturmanıza, uygulamanızı ve ilgili kaldırıldığından, Docker ana bilgisayara VM gösterimi Şekil 4-22'de gösterildiği gibi dağıttığınız.

![](./media/image28.png)

Şekil 4-22: VM ile dağıtılan Docker kapsayıcıları

Not docker-oluşturan ayarlama ve çalıştırma docker kapsayıcılarınızı geliştirme ortamında test etmek için yeterli olabilir, ancak, bunları hiç Docker kümeleriyle çalışmak beklediğiniz ve Docker Swarm, Mesosphere DC/OS veya Kubernetes orchestrators gibi kullanamayabilir ölçeği oluşturabilmek. Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) dağıtmak ve docker hizmet oluşturmak için tek Hizmetleri gibi ya da bunu olduğunuzda ek komutları ile test gerek (Docker için Windows ve Mac sürümünden itibaren kullanılabilir sürüm 1.12), birkaç kapsayıcıları için oluşan bir uygulama dağıtımı, paket oluşturma docker kullanarak ve docker makalesinde açıklandığı gibi bir yığın oluşturulmuş uygulama dağıtarak myBundleFile, dağıtma [dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) Docker gelen.

İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) farklı dağıtım komutlarını ve komut dosyaları da kullanırsınız.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>6. adım: Docker uygulamanızda (yerel olarak yerel CD VM) Test

Bu adımı uygulamanız yapılması bağlı olarak değişir.

Bir çok basit .NET Core Web API'si "Merhaba tek kapsayıcısı veya hizmet dağıtılan World", yalnızca DockerFile belirtilen TCP bağlantı noktası sağlayarak hizmete erişmek gerekir.

Localhost üzerinde hizmetinize gitmek için açık değilse IP adresi makine için bu komutu kullanarak bulun:

docker Makine IP *kapsayıcı adı bilgisayarınızı*

Docker ana bilgisayarında, bir tarayıcı açın ve o siteye gidin; Şekil 4-23'te gösterildiği gibi çalışır, uygulama/hizmet görmeniz gerekir.

![](./media/image29.png)

Şekil 4-23: localhost kullanarak yerel olarak Docker uygulamanızı test etme

Nasıl bunu çalıştırmak, docker ile daha önce açıklandığı gibi dağıtılmış olduğu için 80 numaralı bağlantı noktasını kullanıyor, ancak dahili olarak, bağlantı noktası 5000 yönlendirildi unutmayın.

Bu terminal durumundan CURL kullanarak test edebilirsiniz. Windows Docker yüklemede varsayılan IP 10.0.75.1, Şekil 4-24'de gösterilen aynıdır.

![](./media/image30.png)

Şekil 4-24: CURL kullanarak yerel olarak Docker uygulamayı test etme

**Docker üzerinde çalışan bir kapsayıcı hata ayıklama**

Node.js ve .NET Core kapsayıcıları gibi diğer platformlarda kullanıyorsanız, visual Studio Code hata ayıklama Docker destekler.

Ayrıca Docker .NET Core kapsayıcılarında Visual Studio kullanırken bir sonraki bölümde açıklandığı gibi ayıklayabilirsiniz.

**Daha fazla bilgi:** Node.js Docker kapsayıcılarında hata ayıklama hakkında daha fazla bilgi için şuraya gidin <https://blog.docker.com/2016/07/live-debugging-docker/> ve [https://blogs.msdn.microsoft.com/ \ kullanıcı\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).


>[!div class="step-by-step"]
[Önceki] (docker-apps-development-environment.md) [sonraki] (visual-studio-araçları-için-docker.md)
