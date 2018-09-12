---
title: Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/10/2018
ms.openlocfilehash: a03853a508cfb3d5dd5fbfe66e4ef484b685faaa
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511727"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker uygulaması için dış döngü DevOps iş akışındaki adımlar

Şekil 5-1 bir uçtan uca gösterimi DevOps dış döngü iş akışı oluşturan adımları sunar.

![](./media/image1.png)

Şekil 5-1: DevOps dış döngü Microsoft araçları ile Docker uygulamaları için iş akışı

Şimdi daha ayrıntılı bu adımların her birini inceleyelim.

## <a name="step-1-inner-loop-development-workflow"></a>1. adım: İç döngü geliştirme iş akışı

Bu adım ayrıntılı bölüm 4'te açıklanan ancak özeti için işte dış döngü, CI işlem hattı eylemleri başlatma kodunu (Git gibi) kaynak denetimi yönetim sistemine hangi geliştirici gönderim şu başladığı.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>2. adım: Kaynak kodu denetimi tümleştirme ve Azure DevOps Services ve Git ile yönetim

Bu adımda, birleştirilmiş bir takım farklı geliştiricilerden gelen kod sürümünü toplamak için bir sürüm denetimi sistemi olması gerekir.

Kaynak kodu denetimi (SCC) ve kaynak kodu Yönetimi yapısı ikinci geçiş için çoğu geliştirici, bir DevOps yaşam Docker uygulamaları oluştururken görünebilir olsa da, uygulama ile Docker görüntüleri göndermeniz gerekir değil, vurgulamak için kritik doğrudan genel Docker kayıt defterine (Azure Container Registry veya Docker hub'ı gibi) geliştiricinin makinesinden. Tam, genel derleme ya da CI işlem hattı, kaynak kodu deposu (Git gibi) temel tümleştiriliyor yalnızca kaynak kod üzerinde Docker görüntüleri yayımladı ve üretim ortamlarına dağıtılan oluşturulmalıdır.

Kendi makinelerde test ederken, geliştiriciler tarafından oluşturulan bir yerel görüntülere geliştiriciler tarafından kullanılmalıdır. SCC koddan etkinleştirilmiş DevOps işlem hattı için kritik nedeni budur.

Azure DevOps Hizmetleri ve Team Foundation Server Git ve Team Foundation sürüm denetimi destekler. Bunlar arasında seçin ve bir uçtan uca Microsoft deneyimi için kullanın. Kodunuzu dış depolardaki (örneğin, GitHub, Git depoları şirket içi veya Subversion gibi) ancak de yönetebilirsiniz ve yine de bağlanabilir ve DevOps CI işlem hattınızı için başlangıç noktası olarak kodu alma mümkün olmayacaktır.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>3. adım: Derleme, CI, tümleştirme ve Test ile Azure DevOps Hizmetleri ve Docker

CI, modern yazılım test etme ve teslim için standart olarak belirlendi. Docker çözümü, bir görev ayrımı nettir geliştirme ve operasyon ekipleri arasında tutar. Docker görüntülerinin değiştirilemezlik ne olan geliştirilen, CI aracılığıyla test ve üretim ortamında çalışması arasında tekrarlanabilir bir dağıtım sağlar. Docker altyapısı Geliştirici dizüstü bilgisayarlar arasında dağıtılmış ve test altyapısı kapsayıcıları ortamlar genelinde taşınabilir hale getirir.

Bu noktada, gönderilen doğru kodu ile bir sürüm denetimi sistemi sonra gereksinim duyduğunuz bir *derleme hizmeti* kod çekme ve genel derleme ve testleri çalıştırın.

Yapı sunucunuz (Azure DevOps Hizmetleri), Docker altyapısı ve bir Docker kayıt defteri, kod deposu (Git, vb.) oluşan bir CI işlem hattı hakkında (CI, derleme, test) Bu adım için iç iş akışı yapısıdır.

Azure DevOps Hizmetleri temel olarak uygulamalarınızı oluşturmaya ve CI işlem hattınızı ayarlama ve derlenen "yapıtları" yayımlama ", bir sonraki adımda açıklanan yapıt deposu," için kullanabilirsiniz.

Docker dağıtımı için "son yapıtların" kullanıldığında dağıtılacak Docker görüntüleri uygulama veya hizmetlerle içine katıştırılır. Bu görüntüleri atıldığında veya yayımlanan bir *Docker kayıt defteri* (Azure Container Registry'de sahip olanları ya da ortak bir resmi temel görüntüleri için yaygın olarak kullanılan Docker Hub kayıt gibi gibi özel bir depo).

Temel kavramlar şu şekildedir: CI işlem hattı devreye girdi dışı bir SCC depoya Git gibi bir işleme tarafından olacaktır. İşleme, Şekil 5-2'de gösterildiği gibi bir Docker kapsayıcısı içinde bir derleme işi çalıştırın ve bu işi işlemin başarıyla tamamlanmasından sonra bir Docker görüntüsü Docker kayıt defterine itme, Azure DevOps Hizmetleri neden olur.

![](./media/image2.png)

Şekil 5-2: CI'da yer alan adımların

Docker ve Azure DevOps hizmetleriyle temel CI iş akışı adımlar şunlardır:

1.  Geliştirici (Git/Azure DevOps Services, GitHub, vb.) bir SCC depoya bir yürütme iter.

2.  Azure DevOps Services veya Git kullanıyorsanız, CI, Azure DevOps Hizmetleri onay kutusunu seçmek kadar kolay olduğunu gösterir, oluşturulmuştur. Bir dış SCC (örneğin GitHub) kullanıyorsanız, bir *Web kancası* Azure DevOps Hizmetleri güncelleştirmesi bildirmek veya Git/GitHub gönderin.

3.  Azure DevOps hizmetleriyle görüntünün yanı sıra uygulama ve test kodu açıklayan DockerFile dahil olmak üzere SCC depoyu çeker.

4.  Azure DevOps hizmetleriyle bir Docker görüntüsü derler ve derleme numarasıyla etiketler.

5.  Azure DevOps hizmetleriyle sağlanan bir Docker konağı içinde Docker kapsayıcısı başlatır ve uygun testleri çalıştırır.

6.  Testler başarılı olursa, "en derleme" olduğunu öğrenmek için görüntüyü önce anlamlı bir ad relabeled (gibi "/ 1.0.0" veya herhangi bir etiketi) ve ardından Docker kayıt defterinize (Docker Hub, Azure Container Registry, DTR, vb.) gönderdiniz

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Azure DevOps hizmetler için CI işlem hattı Azure DevOps Hizmetleri ve Docker uzantısını uygulamak

[Azure DevOps Hizmetleri Docker uzantısını](https://aka.ms/vstsdockerextension) CI işlem hattınızda ile Docker görüntülerinizi oluşturmak, kimliği doğrulanmış bir Docker kayıt defterine Docker görüntüleri gönderin, Docker görüntülerini çalıştırmak veya yapabilirsiniz Docker tarafından sunulan diğer işlemleri çalıştırmak için bir görev ekler. CLI. Ayrıca, oluşturun, gönderin ve çok kapsayıcılı Docker uygulamaları çalıştırma veya Şekil 5-3'te gösterildiği gibi Docker Compose CLI tarafından sunulan diğer işlemleri çalıştırmak için kullanabileceğiniz bir Docker Compose görev ekler.

![](./media/image3.png)

Şekil 5-3: Docker CI işlem hattı, Azure DevOps Hizmetleri

Docker uzantısını hizmet uç noktaları, kapsayıcı ya da görüntü kayıt defterleri ve Docker ana bilgisayarları için kullanabilirsiniz. Yerel bir Docker konağı varsa (Bu şu anda özel bir Azure DevOps Hizmetleri Aracısı gerektirir); görevleri varsayılan Aksi takdirde, bunlar bir Docker konağı bağlantı verdiğiniz gerektirir. Bir Docker kayıt defteri bağlantısı sağlayan bir görüntü gönderme gibi bir Docker kayıt defteri ile kimlik doğrulaması üzerinde bağlı eylemler gerektirir.

Azure DevOps Hizmetleri Docker uzantısını Azure DevOps Services hesabınızda aşağıdaki bileşenleri yükler:

-   Bir Docker kayıt defterine bağlanmak için hizmet uç noktası

-   Bir Docker kapsayıcısı ana bilgisayarına bağlanmak için hizmet uç noktası

-   Aşağıdakileri yapmak için bir Docker görevi:

-   Bir görüntü oluşturun

-   Bir kayıt defterine iletin, bir resim veya bir depo

-   Bir kapsayıcıdaki bir görüntü çalıştırma

-   Docker komutu çalıştırın

-   Bir Docker Compose komutu çalıştırmak için bir Docker Compose görevi

Azure DevOps Hizmetleri bu görevleri, bir derleme Linux Docker konak/VM Azure'da sağlanan ve tercih edilen Docker kayıt defterinizin (Azure Container Registry, Docker Hub, özel Docker DTR veya herhangi bir Docker kayıt), Docker sürekli tümleştirme işlem hattında birleştirebilirsiniz bir çok tutarlı bir yol.

***Gereksinimler:***

-   Azure DevOps hizmetlerine veya şirket içi yüklemeler, Team Foundation Server 2015 güncelleştirme 3 veya sonraki sürümü için.

-   Docker ikili dosyaları içeren bir Azure DevOps Hizmetleri Aracısı.

Bunlardan birini oluşturmak kolay bir yolu, Azure DevOps Hizmetleri Aracısı Docker görüntü temel alan bir kapsayıcı çalıştırmak için Docker kullanmaktır.

**Daha fazla bilgi** Azure DevOps Hizmetleri Docker CI birleştirme hakkında daha fazla işlem hattı ve izlenecek yollar, görüntülemek için aşağıdaki siteleri ziyaret edin:

Azure DevOps Hizmetleri aracıyı çalıştıran bir Docker kapsayıcısı: [ https://hub.docker.com/r/\ microsoft/vsts-agent /](https://hub.docker.com/r/microsoft/vsts-agent/)

Azure DevOps Hizmetleri Docker uzantısı: <https://aka.ms/vstsdockerextension>

Azure DevOps hizmetleriyle .NET Core Linux Docker görüntüleri oluşturma: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Docker desteği içeren Visual Studio Team Service Linux tabanlı yapı makinesini oluşturma: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Tümleştirme, test etme ve çok kapsayıcılı Docker uygulamaları doğrula

Çoğu Docker uygulamalar genellikle birden çok kapsayıcı bir çoklu kapsayıcı yerine oluşur. Mikro hizmet başına bir kapsayıcı olurdu ve mikro hizmet odaklı bir uygulama buna iyi bir örnektir. Ancak, hatta kesinlikle mikro hizmetler yaklaşımı düzenleri olmadan, çok olası Docker uygulamanız birden çok kapsayıcı veya hizmet olarak sahipliğindeki.

Bu nedenle, uygulama kapsayıcıları CI işlem hattının oluşturduktan sonra ayrıca bir tümleştirme Docker konağı veya kümesine kapsayıcıları olduğu bile bir test kapsayıcılarında tüm bir bütün olarak uygulamadan test dağıtma ve tümleştirme gerekir Dağıtılmış.

Tek bir ana bilgisayar kullanıyorsanız, docker gibi Docker komutlarını kullanabilirsiniz-compose oluşturun ve ilgili kapsayıcıları tek bir VM Docker ortamında test edin ve dağıtın. Ancak, DC/OS, Kubernetes ve Docker Swarm gibi bir orchestrator kümesi ile çalışıyorsanız, farklı mekanizma veya seçili küme/scheduler bağlı olarak, orchestrator ile kapsayıcılarınızı dağıtmanız gerekebilir.

Docker kapsayıcıları karşı çalıştırabileceğiniz testleri çeşitli türleri şunlardır:

-   Docker kapsayıcıları için birim testleri

-   Test grupları birbiriyle uygulamaların veya mikro hizmetler

-   Üretim ve "kanarya" sürümlerde test

Tümleştirme ve işlevsel testleri çalıştırırken, kapsayıcıların dışında gelen bu testlerin çalıştırılması gereken önemli noktasıdır. Testleri değil tanımlanmalı ve kapsayıcılar, üretime dağıtma gibi tam olarak olması gereken statik görüntüler tabanlı olduğundan, dağıttığınız kapsayıcılara çalıştırın.

Birkaç kümelerini (küme, küme hazırlama ve üretim kümesi test) test gibi daha gelişmiş senaryoları test ederken çok uygun bir seçenek çeşitli kümelerinde test etmek için bir kayıt defterine görüntü yayımlamaktır.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Özel uygulama Docker görüntüsünü, genel Docker kayıt defterine gönderme

Docker görüntülerini test ve doğrulanmış sonra etiketleyebilir ve bunları Docker kayıt defterinize yayımlama isteyebilirsiniz. QA ve üretim ortamlarına dağıtılacak özel test (diğer adıyla "en görüntüleri") depoladığınız merkezi bir yerde olduğu için Docker kayıt defteri Docker uygulaması yaşam döngüsü içinde bir kritik hissettiğimiz parçaymış.

(Git, vb.) SCC deponuzda saklanan uygulama kodu, "gerçeklik kaynağı" nasıl olduğunu, Docker kayıt defteri, "gerçeklik kaynağı" ikili uygulamanızı veya BITS QA ya da üretim ortamı için dağıtılması için benzer.

Genellikle, Azure Container Registry veya Docker Trusted Registry gibi bir şirket içi kayıt defteri veya bir genel bulut kayıt defteri (gibi kısıtlı erişim için kendi özel görüntülerinizi özel depolarınızı ya da özel bir depoya sahip olmak isteyebilirsiniz Docker Hub), açık kaynak kodunuzu değilse, bu durumda son olsa da satıcının güvenlik güvenmesi gerekir. Her iki durumda da, bunu Şekil 5-4'te gösterildiği gibi docker itme komut sonuçta dayalı ve oldukça benzer yöntemidir.

![](./media/image4.png)

Şekil 5-4: özel görüntüleri Docker kayıt defterine yayımlama

Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, Quay kayıt defteri ve benzeri gibi bulut satıcılarının Docker kayıt defterleri birden çok tekliflerin vardır.

Azure DevOps Hizmetleri Docker uzantısını kullanarak, Şekil 5-5'te gösterildiği gibi hizmet görüntüleri kimliği doğrulanmış bir Docker kayıt defterine (Azure Container Registry) gibi birden çok etiketi ile bir docker-compose.yml dosyası tarafından tanımlanan bir dizi gönderebilirsiniz.

![](./media/image5.png)

Şekil 5-5: bir Docker kayıt defterine yayımlama özel görüntüleri için Azure DevOps Hizmetleri kullanma

**Daha fazla bilgi** daha fazla bilgi için Azure DevOps Services için Docker uzantısını hakkında Git <https://aka.ms/vstsdockerextension>. Azure Container Registry hakkında daha fazla bilgi için şuraya gidin <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>4. adım: CD dağıtma

Docker görüntülerinin değiştirilemezlik ne geliştirilen, CI aracılığıyla test ve üretim ortamında çalışması tekrarlanabilir bir dağıtım sağlar. Docker kayıt defterinizde (özel veya genel) yayımlanmış uygulama Docker görüntüleri oluşturduktan sonra bunları sahip olabileceğiniz birden fazla ortam dağıtabilirsiniz (üretim, QA, hazırlama, vb.) gelen Azure DevOps hizmetlerini kullanarak CD işlem hattı işlem hattı görevler veya Azure DevOps Services Release Management.

Ancak, bu noktada, dağıttığınız ne tür bir Docker uygulaması üzerinde bağlıdır. Basit bir uygulaması (açısından bir oluşturma ve dağıtma) gibi bir tek parçalı birkaç kapsayıcılar veya hizmetler oluşturan uygulama ve dağıtılan birkaç sunucular veya VM'ler dağıtma gibi daha karmaşık bir uygulama dağıtmanızı çok farklı bir mikro hizmet tabanlı uygulama hiper ölçekli özelliklere sahip. Bu iki senaryo aşağıdaki bölümlerde açıklanmıştır.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Docker uygulamaları için birden fazla Docker ortamlarını oluşan dağıtma

Az karmaşık senaryo ilk bakalım: Basit Docker ana bilgisayarları (VM'ler veya sunucular) tek bir ortam ya da birden çok ortama dağıtma (QA, hazırlık ve üretim). Bu senaryoda, dahili olarak docker CD işlem hattınızı kullanabilirsiniz-Şekil 5-6'da gösterildiği gibi kapsayıcılar ve hizmetler, ilgili alt kümesi ile Docker uygulamalarını dağıtma (Azure DevOps Hizmetleri dağıtım görevlerinizi) oluşturun.

![](./media/image6.png)

Şekil 5-6: Basit Docker konağı ortamları kayıt defterine uygulama kapsayıcıları dağıtma

Şekil 5-7, nasıl yapı CI QA ve test ortamları Azure DevOps hizmetleriyle Docker Compose Görev Ekle iletişim kutusuna tıklayarak bağlanabilirsiniz vurgular. Ancak, hazırlama veya üretim ortamlarına dağıtıldığında, genellikle birden çok ortama işleme Release Management özellikleri kullanmanız gerekir (ister QA, hazırlık ve üretim). Tek Docker ana bilgisayarlara dağıtıyorsanız, Azure DevOps hizmetlerin kullandığı "Docker Compose" Görev (docker çağırma-başlık altında komut oluşturmanıza). Azure Container Service'e dağıtıyorsanız, aşağıdaki bölümde açıklandığı gibi Docker dağıtım görevini kullanır.

![](./media/image7.png)

Şekil 5-7: bir hizmetlerinize DevOps işlem hattı, bir Docker Compose görev ekleme

Azure DevOps Hizmetleri'nde bir yayın oluştururken, giriş yapıtları kümesini alır. Bunlar birden çok ortamda sürüm kullanım ömrü boyunca sabit olması amaçlanır. Kapsayıcıları yapılırsa, giriş yapıları dağıtmak için bir kayıt defterindeki görüntüleri belirleyin. Nasıl bunlar tanımlanır bağlı olarak, bunlar "myimage:latest" docker-compose dosyasından başvurduğunuzda olan en bariz örnek yayın süresi boyunca aynı kalması garanti edilmez.

Azure DevOps Services için Docker uzantısını, belirli kayıt defteri görüntü içeren derleme yapıtları oluşturma yeteneği özetleyen ikili aynı görüntü benzersiz olarak tanımlanabilmesi için garanti sunar. Gerçekten bir yayın için giriş olarak kullanmak istediklerinizi şunlardır.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Azure DevOps Services Release Management'ı kullanarak sürümleri için Docker ortamlarını yönetme

Azure DevOps Hizmetleri uzantıları, yeni bir görüntü oluşturun, bir Docker kayıt defterine yayımlama, Linux veya Windows konaklarda çalıştırın ve docker gibi komutları kullanın-tüm uygulama, Azure DevOps bakmalıyım olarak birden çok kapsayıcı dağıtmak için oluşturma Release Management özellikleri, birden çok ortam için hedeflenen Şekil 5-8'de gösterildiği gibi hizmetler.

![](./media/image8.png)

Azure DevOps Services Release Management Azure DevOps Hizmetleri Docker Compose görevlerden Şekil 5-8: yapılandırma

Ancak, Şekil 5-6'daki ve uygulanan Şekil 5-8'de senaryo (Basit Docker ana bilgisayarları ve Vm'leri dağıtma ve tek kapsayıcı ya da örnek başına görüntü olacaktır) oldukça basittir ve yalnızca geliştirme veya test sc için büyük olasılıkla kullanılması gerektiğini göz önünde bulundurun enarios. Çoğu Kurumsal üretim senaryosunda, yüksek kullanılabilirlik (HA) sahip istiyorsunuz ve birden çok düğüm, sunucuları ve Vm'leri artı "akıllı yük devretmeleri" arasında bu nedenle, bir sunucu veya düğüm Yük Dengeleme tarafından yönetilmesi kolay ölçeklenebilirlik başarısız olursa, hizmetlerinin ve kapsayıcılar, başka bir ana bilgisayar sunucusuna veya VM taşınır. Bu durumda, kapsayıcı kümeleri ve düzenleyicileri zamanlayıcılar gibi daha gelişmiş teknolojilerden gerekir. Bu nedenle, bu kümeye dağıtmak için tam olarak sonraki bölümde açıklanan Gelişmiş senaryolar aracılığıyla yoludur.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Docker kümeleri (DC/OS, Kubernetes ve Docker Swarm) karmaşık Docker uygulamalarını dağıtma

Dağıtılmış uygulamalar doğasını da dağıtılmış işlem kaynakları gerektirir. HA havuza alınmış kaynaklar temelinde ve üretim ölçeği-özelliklerini kullanabilmek için yüksek ölçeklenebilirlik sağlayan özellikleri kümeleme olması gerekir.

Kapsayıcıları el ile bu kümeye CLI aracından Docker Swarm gibi dağıtabilirsiniz (kullanma gibi [docker hizmeti oluşturulur](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) veya bir web kullanıcı Arabirimi gibi [Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) kümeleri, ancak DC/OS için gerekir. Bu, yalnızca punctual dağıtımı test etmek veya ölçeklendirme genişletme veya izleme amacıyla gibi yönetim amacıyla saklı tutarız.

Özellikle, bir CD açısından ve Azure DevOps Hizmetleri kapsayıcıya alınmış uygulamalarınızı kapsayıcı dağıtılmış kümelerini dağıtır, Azure DevOps Services Release Management ortamlarından özel yapılan dağıtım görevlerini çalıştırabilirsiniz Şekil 5-9'da gösterildiği gibi hizmet.

![](./media/image9.png)

Şekil 5-9: dağıtılmış uygulamaları Container Service'e dağıtma

Başlangıçta, belirli bir küme veya düzenleyicileri dağıtırken, geleneksel olarak belirli bir dağıtım betikleri ve mekanizmalarına göre her bir orchestrator (diğer bir deyişle, Mesosphere DC/OS veya Kubernetes, Docker ve Docker değerinden farklı dağıtım mekanizmalarına sahip kullanmanız gerekir Yerine swarm) daha basit ve kullanımı kolay docker-docker-compose.yml tanımı dosyasını temel alan bir aracı oluşturun. Ancak, Şekil 5-10'da gösterilen Microsoft Azure DevOps Hizmetleri Docker dağıtımı görev sayesinde artık da DC/OS için Microsoft, "çeviri" sizin için gerçekleştirdiğinden yalnızca bilinen docker-compose.yml dosyanız kullanarak dağıtabilirsiniz (gelen, DC/OS tarafından gereken diğer biçimlere docker-compose.yml dosyası).

![](./media/image10.png)

Şekil 5-10: Docker dağıtma görevi için ortam RM ekleme

Şekil 5-11 Docker dağıtma görevi düzenleyin ve hedef türünü (Azure Container Service DC/OS, bu durumda), Docker Compose dosyası ve Docker kayıt defteri bağlantıya (ör. Azure Container Registry veya Docker hub'ı) nasıl gösterir. Görevin DC/OS kümesindeki kapsayıcılar olarak dağıtılması için kullanıma hazır özel Docker görüntülerinizi burada alır budur.

![](./media/image11.png)

Şekil 5-11: Docker dağıtma görev tanımını Azure Container Service DC/OS için dağıtma

**Daha fazla bilgi** daha fazla bilgi için CD işlem hattının hakkında Azure DevOps Hizmetleri ve Docker ile aşağıdaki siteleri ziyaret edin:

Docker ve Azure Container Service için Azure DevOps Hizmetleri uzantısı: [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Azure kapsayıcı hizmeti: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>5. adım: Çalıştırma ve yönetme

Çalıştıran ve uygulamaları yönetmek için Kurumsal üretim sırasında önemli bir konu içinde ve kendisinin ve işlemleri türü nedeniyle düzeyidir ve bu alan büyük kapsamını yanı sıra bu düzeyde (BT işlemleri) çalışan kişiler, biz tüm sonraki HARCANMIŞTIR Bunu açıklayan için bölüm.

## <a name="step-6-monitor-and-diagnose"></a>6. adım: İzleme ve tanılama

Bu konuda, üretim sistemleri BT işlemleri gerçekleştiren görevler bir parçası olarak bir sonraki bölümde de ele alınmıştır; Bununla birlikte, uygulamayı sürekli olarak geliştirilir, bu adımda elde edilen içgörüleri Geliştirme takımına geri besleme gerekir vurgulamak önemlidir. Görevleri ve işlemleri genellikle tarafından gerçekleştirilen olsa da bu açısından bakıldığında, ayrıca DevOps, parçasıdır BT.

Yalnızca izleme ve tanılama DevOps bölge içinde yüzde 100 olduğunda izleme işlemleri ve test veya beta ortamları karşı geliştirme ekibi tarafından gerçekleştirilen analiz olan. Bu, yük testi yapma veya yalnızca beta veya beta test uzmanlarına yeni sürümleri nereden çalışıyorsunuz, QA ortamları izleme tarafından gerçekleştirilir.

>[!div class="step-by-step"]
[Önceki](index.md)
[İleri](../run-manage-monitor-docker-environments/index.md)
