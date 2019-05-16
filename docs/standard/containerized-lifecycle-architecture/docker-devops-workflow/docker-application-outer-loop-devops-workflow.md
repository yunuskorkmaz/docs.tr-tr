---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: "\"Dış döngü\" DevOps iş akışının adımları öğrenin"
ms.date: 02/15/2019
ms.openlocfilehash: 194786a90fc02801211c7614eb632392d67f0109
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641049"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar

Şekil 5-1 bir uçtan uca gösterimi DevOps dış döngü iş akışı oluşturan adımları sunar.

![Bu diyagramda devops'un "dış döngü" gösterilmektedir. Kod depoya gönderildiğinde bir CI işlem hattı başlatıldıktan sonra uygulamanın dağıtılacağı CD işlem hattı başlar. Geliştirme ekipleri için kullanıcı ve iş gereksinimlerinizi yanıt vermek için gerçek böylece "İç döngü" gerçekleştiği geri geliştirme iş yükü olarak, dağıtılmış uygulamalardan toplanan ölçümleri beslenir.](./media/image1.png)

**Şekil 5-1**. Docker uygulamaları Microsoft araçları ile DevOps dış döngü iş akışı

Şimdi daha ayrıntılı bu adımların her birini inceleyelim.

## <a name="step-1-inner-loop-development-workflow"></a>1. Adım: İç döngü geliştirme iş akışı

Bu adım ayrıntılı bölüm 4'te açıklanan ancak özeti için işte dış döngü, CI işlem hattı eylemleri başlatma kodunu (Git gibi) kaynak denetimi yönetim sistemine hangi geliştirici gönderim şu başladığı.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>2. Adım: Kaynak kodu denetimi tümleştirme ve Azure DevOps Services ve Git ile yönetim

Bu adımda, birleştirilmiş bir takım farklı geliştiricilerden gelen kod sürümünü toplamak için bir sürüm denetimi sistemi olması gerekir.

Kaynak kodu denetimi (SCC) ve kaynak kodu Yönetimi yapısı ikinci geçiş için çoğu geliştirici, bir DevOps yaşam Docker uygulamaları oluştururken görünebilir olsa da, uygulama ile Docker görüntüleri göndermeniz gerekir değil, vurgulamak için kritik doğrudan genel Docker kayıt defterine (Azure Container Registry veya Docker hub'ı gibi) geliştiricinin makinesinden. Tam, genel derleme ya da CI işlem hattı, kaynak kodu deposu (Git gibi) temel tümleştiriliyor yalnızca kaynak kod üzerinde Docker görüntüleri yayımladı ve üretim ortamlarına dağıtılan oluşturulmalıdır.

Geliştiriciler tarafından oluşturulan yerel görüntüler, yalnızca bunlara kendi makinelerde test ederken kullanılmalıdır. İşte bu SCC kodundan etkinleştirilmiş DevOps işlem hattı için önemlidir.

Azure DevOps Hizmetleri ve Team Foundation Server Git ve Team Foundation sürüm denetimi destekler. Bunlar arasında seçin ve bir uçtan uca Microsoft deneyimi için kullanın. Kodunuzu dış depolardaki (örneğin, GitHub, Git depoları şirket içi veya Subversion gibi) ancak de yönetebilirsiniz ve yine de bağlanabilir ve DevOps CI işlem hattınızı için başlangıç noktası olarak kodu alma mümkün olmayacaktır.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>3. Adım: Derleme, CI, tümleştirme ve Test ile Azure DevOps Hizmetleri ve Docker

CI, modern yazılım test etme ve teslim için standart olarak belirlendi. Docker çözümü, bir görev ayrımı nettir geliştirme ve operasyon ekipleri arasında tutar. Docker görüntülerinin değiştirilemezlik ne olan geliştirilen, CI aracılığıyla test ve üretim ortamında çalışması arasında tekrarlanabilir bir dağıtım sağlar. Docker altyapısı Geliştirici dizüstü bilgisayarlar arasında dağıtılmış ve test altyapısı kapsayıcıları ortamlar genelinde taşınabilir hale getirir.

Bu noktada, gönderilen doğru kodu ile bir sürüm denetimi sistemi sonra gereksinim duyduğunuz bir *derleme hizmeti* kod çekme ve genel derleme ve testleri çalıştırın.

Yapı sunucunuz (Azure DevOps Hizmetleri), Docker altyapısı ve bir Docker kayıt defteri, kod deposu (Git, vb.) oluşan bir CI işlem hattı hakkında (CI, derleme, test) Bu adım için iç iş akışı yapısıdır.

Azure DevOps Hizmetleri temel olarak uygulamalarınızı oluşturmaya ve CI işlem hattınızı ayarlama ve derlenen "yapıtları" yayımlama ", bir sonraki adımda açıklanan yapıt deposu," için kullanabilirsiniz.

Docker dağıtımı için "son yapıtların" kullanıldığında dağıtılacak Docker görüntüleri uygulama veya hizmetlerle içine katıştırılır. Bu görüntüleri atıldığında veya yayımlanan bir *Docker kayıt defteri* (Azure Container Registry'de sahip olanları ya da ortak bir resmi temel görüntüleri için yaygın olarak kullanılan Docker Hub kayıt gibi gibi özel bir depo).

Temel kavramlar aşağıda verilmiştir: CI işlem hattı devreye girdi dışı bir SCC depoya Git gibi bir işleme tarafından olacaktır. İşleme, Şekil 5-2'de gösterildiği gibi bir Docker kapsayıcısı içinde bir derleme işi çalıştırın ve bu işi işlemin başarıyla tamamlanmasından sonra bir Docker görüntüsü Docker kayıt defterine itme, Azure DevOps Hizmetleri neden olur.

![Çalıştırma adımları 1-3, koddan dış döngü ilk bölümünü içerir, hata ayıklama ve doğrulayın, ardından derleme ve test CI adım en fazla kod deposu](./media/image2.png)

**Şekil 5-2**. CI'da adımlar

Docker ve Azure DevOps hizmetleriyle temel CI iş akışı adımlar şunlardır:

1. Geliştirici (Git/Azure DevOps Services, GitHub, vb.) bir SCC depoya bir yürütme iter.

2. Azure DevOps Services veya Git kullanıyorsanız, CI, Azure DevOps Hizmetleri onay kutusunu seçmek kadar kolay olduğunu gösterir, oluşturulmuştur. Bir dış SCC (örneğin GitHub) kullanıyorsanız, bir `webhook` Azure DevOps Hizmetleri güncelleştirmesi bildirmek veya Git/GitHub gönderin.

3. Azure DevOps hizmetleriyle görüntünün yanı sıra uygulama ve test kodu açıklayan Dockerfile dahil olmak üzere SCC depoyu çeker.

4. Azure DevOps hizmetleriyle bir Docker görüntüsü derler ve derleme numarasıyla etiketler.

5. Azure DevOps hizmetleriyle sağlanan bir Docker konağı içinde Docker kapsayıcısı başlatır ve uygun testleri çalıştırır.

6. Testler başarılı olursa, "en derleme" olduğunu öğrenmek için görüntüyü önce anlamlı bir ad relabeled (gibi "/ 1.0.0" veya herhangi bir etiketi) ve ardından Docker kayıt defterinize (Docker Hub, Azure Container Registry, DTR, vb.) gönderdiniz

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Azure DevOps hizmetler için CI işlem hattı Azure DevOps Hizmetleri ve Docker uzantısını uygulamak

Visual Studio Azure DevOps Services derleme ve sürüm ile Docker görüntülerinizi oluşturmak, kimliği doğrulanmış bir Docker kayıt defterine Docker görüntüleri gönderin, Docker görüntülerini çalıştırmak veya yapabilirsiniz tarafından sunulan diğer işlemleri çalıştırma CI/CD işlem hattınızdaki kullanabileceğiniz şablonları içerir. Docker CLI. Ayrıca, oluşturun, gönderin ve çok kapsayıcılı Docker uygulamaları çalıştırmak veya Şekil 5-3'te gösterildiği gibi Docker Compose CLI tarafından sunulan diğer işlemleri çalıştırmak için kullanabileceğiniz bir Docker Compose görev ekler.

![Azure DevOps Docker CI işlem hattının tarayıcı görünümü](./media/image3.png)

**Şekil 5-3**. Azure DevOps Services derleme ve sürüm şablonları ve ilişkili görevleri dahil olmak üzere Docker CI işlem hattında.

Bu şablonları ve görevleri geliştirmek / test etmek ve dağıtmak için CI/CD yapıtlarınızı oluşturmak için kullanabileceğiniz Azure Service Fabric, Azure Kubernetes hizmeti ve benzer teklifleri.

Bu Visual Studio Team Services görevleri ile bir yapı Linux Docker konak/VM Azure'da sağlanan ve tercih edilen Docker kayıt defterinizin (Azure Container Registry, Docker Hub, özel Docker DTR veya herhangi bir Docker kayıt), Docker sürekli tümleştirme işlem hattında birleştirebilirsiniz bir çok tutarlı bir yol.

***Gereksinimler:***

- Azure DevOps hizmetlerine veya şirket içi yüklemeler, Team Foundation Server 2015 güncelleştirme 3 veya sonraki sürümü için.

- Docker ikili dosyaları içeren bir Azure DevOps Hizmetleri Aracısı.

  Bu aracıların oluşturmak kolay bir yolu, Azure DevOps Hizmetleri Aracısı Docker görüntü temel alan bir kapsayıcı çalıştırmak için Docker kullanmaktır.

> [! Bilgi] Azure DevOps Hizmetleri Docker CI birleştirme hakkında daha fazla işlem hattı ve izlenecek yollar görüntülemek için bu siteleri ziyaret edin:
>
> - Bir Docker kapsayıcısı bir Visual Studio Team Services (artık Azure DevOps Hizmetleri) aracısını çalıştıran: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Azure DevOps hizmetleriyle .NET Core Linux Docker görüntüleri oluşturma: \
>   <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>
>
> - Bir Linux tabanlı Visual Studio Team Service oluşturma, Docker desteği makineyle derleme: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Tümleştirme, test etme ve çok kapsayıcılı Docker uygulamaları doğrula

Çoğu Docker uygulamalar genellikle birden çok kapsayıcı bir çoklu kapsayıcı yerine oluşur. Mikro hizmet başına bir kapsayıcı olurdu ve mikro hizmet odaklı bir uygulama buna iyi bir örnektir. Ancak, hatta kesinlikle mikro hizmetler yaklaşımı düzenleri olmadan, olası Docker uygulamanız birden çok kapsayıcı veya hizmet olarak sahipliğindeki.

Bu nedenle, uygulama kapsayıcıları CI işlem hattının oluşturduktan sonra ayrıca bir tümleştirme Docker konağı veya kümesine kapsayıcıları olduğu bile bir test kapsayıcılarında tüm bir bütün olarak uygulamadan test dağıtma ve tümleştirme gerekir Dağıtılmış.

Tek bir ana bilgisayar kullanıyorsanız, docker gibi Docker komutlarını kullanabilirsiniz-compose oluşturun ve ilgili kapsayıcıları tek bir VM Docker ortamında test edin ve dağıtın. Ancak, DC/OS, Kubernetes ve Docker Swarm gibi bir orchestrator kümesi ile çalışıyorsanız, farklı mekanizma veya seçili küme/scheduler bağlı olarak, orchestrator ile kapsayıcılarınızı dağıtmanız gerekebilir.

Docker kapsayıcıları karşı çalıştırabileceğiniz testleri çeşitli türleri şunlardır:

- Docker kapsayıcıları için birim testleri

- Test grupları birbiriyle uygulamaların veya mikro hizmetler

- Üretim ve "kanarya" sürümlerde test

Tümleştirme ve işlevsel testleri çalıştırırken, kapsayıcıların dışında gelen bu testlerin çalıştırılması gereken önemli noktasıdır. Testleri değil yer alan veya Üretim dağıtımı olanlar gibi olması gereken statik görüntüler kapsayıcı tabanlı olduğundan dağıtıyorsanız, kapsayıcılarda çalıştırın.

Daha gelişmiş senaryoları gibi çeşitli kümelerini (küme, küme hazırlama ve üretim kümesi test) dahil olmak üzere test pratik bir seçenek çeşitli kümelerinde test edilmesi için bir kayıt defterine görüntüleri yayımlamaktır.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Özel uygulama Docker görüntüsünü, genel Docker kayıt defterine gönderme

Docker görüntülerini test ve doğrulanmış sonra etiketleyebilir ve bunları Docker kayıt defterinize yayımlama isteyebilirsiniz. QA ve üretim ortamlarına dağıtılacak özel test (diğer adıyla "en görüntüleri") depoladığınız merkezi bir yerde olduğu için Docker kayıt defteri Docker uygulaması yaşam döngüsü içinde bir kritik hissettiğimiz parçaymış.

(Git, vb.) SCC deponuzda saklanan uygulama kodu, "gerçeklik kaynağı" nasıl olduğunu, Docker kayıt defteri, "gerçeklik kaynağı" ikili uygulamanızı veya BITS QA ya da üretim ortamı için dağıtılması için benzer.

Genellikle, Azure Container Registry veya Docker Trusted Registry gibi bir şirket içi kayıt defteri veya bir genel bulut kayıt defteri (gibi kısıtlı erişim için kendi özel görüntülerinizi özel depolarınızı ya da özel bir depoya sahip olmak isteyebilirsiniz Docker Hub), açık kaynak kodunuzu değilse, bu durumda son olsa da satıcının güvenlik güvenmesi gerekir. Her iki durumda da, kullandığınız yönteme benzer ve dayanır `docker push` Şekil 5-4'te gösterildiği gibi komutu.

![3. adımda tümleştirme oluşturmak ve test etme (CI) için bir özel veya genel kayıt defterine elde edilen docker görüntüleri yayımlıyor olabilir.](./media/image4.png)

**Şekil 5-4**. Özel görüntüleri Docker kayıt defterine yayımlama

Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, Quay kayıt defteri ve benzeri gibi bulut satıcılarının Docker kayıt defterleri birden çok tekliflerin vardır.

Docker görevleri kullanarak hizmet görüntüleri tarafından tanımlanan bir dizi gönderebilmek için bir `docker-compose.yml` , kimliği doğrulanmış bir Docker kayıt defterine (Azure Container Registry) gibi birden çok etiketlerle Şekil 5-5'te gösterildiği gibi dosya.

![Görüntüleri, Azure DevOps bir kayıt defterine yayımlamak için adımın tarayıcı görünümü.](./media/image5.png)

**Şekil 5-5**. Bir Docker kayıt defterine yayımlama özel görüntüleri için Azure DevOps Hizmetleri kullanma

> [! Bilgi] Azure Container Registry hakkında daha fazla bilgi için bkz: <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>4. Adım: CD dağıtma

Docker görüntülerinin değiştirilemezlik ne geliştirilen, CI aracılığıyla test ve üretim ortamında çalışması tekrarlanabilir bir dağıtım sağlar. Docker kayıt defterinizde (özel veya genel) yayımlanmış uygulama Docker görüntüleri oluşturduktan sonra bunları sahip olabileceğiniz birden fazla ortam dağıtabilirsiniz (üretim, QA, hazırlama, vb.) gelen Azure DevOps hizmetlerini kullanarak CD işlem hattı işlem hattı görevler veya Azure DevOps Services Release Management.

Ancak, bu noktada, ne tür bir Docker uygulaması dağıtmakta üzerinde bağlıdır. Basit bir uygulaması (açısından bir oluşturma ve dağıtma) gibi bir tek parçalı birkaç kapsayıcılar veya hizmetler oluşturan uygulama ve dağıtılan birkaç sunucular veya VM'ler dağıtma gibi daha karmaşık bir uygulama dağıtması farklı bir mikro hizmet tabanlı uygulama hiper ölçekli özelliklere sahip. Bu iki senaryo aşağıdaki bölümlerde açıklanmıştır.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Docker uygulamaları için birden fazla Docker ortamlarını oluşan dağıtma

Az karmaşık senaryo ilk bakalım: Basit Docker ana bilgisayarları (VM'ler veya sunucular) tek bir ortam ya da birden çok ortama dağıtma (QA, hazırlık ve üretim). Bu senaryoda, dahili olarak docker CD işlem hattınızı kullanabilirsiniz-Şekil 5-6'da gösterildiği gibi kapsayıcılar ve hizmetler, ilgili alt kümesi ile Docker uygulamalarını dağıtma (Azure DevOps Hizmetleri dağıtım görevlerinizi) oluşturun.

![CD dağıtma adım (4) q gibi farklı ortamlarda yayımlayabilirsiniz & hazırlama ve üretim.](./media/image6.png)

**Şekil 5-6**. Basit Docker konağı ortamları kayıt defterine uygulama kapsayıcıları dağıtma

Şekil 5-7, nasıl yapı CI QA ve test ortamları Azure DevOps hizmetleriyle Docker Compose Görev Ekle iletişim kutusuna tıklayarak bağlanabilirsiniz vurgular. Ancak, hazırlama veya üretim ortamlarına dağıtıldığında, genellikle birden çok ortama işleme Release Management özellikleri kullanmanız gerekir (ister QA, hazırlık ve üretim). Tek bir Docker ana bilgisayarlara dağıtıyorsanız, Azure DevOps hizmetleri kullanıyor "Docker Compose" Görev (hangi çağırma `docker-compose up` komutunu başlık altında). Azure Container Service'e dağıtıyorsanız, aşağıdaki bölümde açıklandığı gibi Docker dağıtım görevini kullanır.

![Docker Compose bir görev ekleyerek, tarayıcı görünümü.](./media/image7.png)

**Şekil 5-7**. Bir Azure DevOps Hizmetleri işlem hattı, bir Docker Compose görev ekleme

Azure DevOps Hizmetleri'nde bir yayın oluştururken, giriş yapıtları kümesini alır. Bu yapılar, tüm ortamlarda yayının ömrü boyunca sabit olması amaçlanır. Kapsayıcıları yapılırsa, giriş yapıları dağıtmak için bir kayıt defterindeki görüntüleri belirleyin. Bu görüntüleri nasıl tanımlanır bağlı olarak bunlar başvuru olduğunda en belirgin büyük/küçük harf olan yayın süresi boyunca aynı kalması garanti edilmez `myimage:latest` gelen bir `docker-compose` dosya.

Azure DevOps Hizmetleri şablonları, belirli kayıt defteri görüntü içeren derleme yapıtları oluşturma yeteneği özetleyen ikili aynı görüntü benzersiz olarak tanımlanabilmesi için garanti verir. Gerçekten bir yayın için giriş olarak kullanmak istediklerinizi şunlardır.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Azure DevOps Services Release Management'ı kullanarak sürümleri için Docker ortamlarını yönetme

Azure DevOps Hizmetleri şablonları, yeni bir görüntü oluşturun, bir Docker kayıt defterine yayımlama, Linux veya Windows konaklarda çalıştırın ve gibi komutları kullanın `docker-compose` tüm uygulama, Azure DevOps bakmalıyım olarak birden çok kapsayıcı dağıtma Release Management özellikleri, birden çok ortam için hedeflenen Şekil 5-8'de gösterildiği gibi hizmetler.

![Azure DevOps, Docker'ı yapılandırma tarayıcı görünümü, yayınları oluşturun.](./media/image8.png)

**Şekil 5-8**. Azure DevOps Hizmetleri Docker Compose görevleri Azure DevOps Services Release Management'ı yapılandırma

Ancak, basit bir senaryoyu Şekil 5-6'daki ve uygulanan Şekil 5-8'de olduğunu aklınızda bulundurun (tek Docker ana bilgisayarları ve Vm'leri dağıtma ve tek kapsayıcı ya da örnek başına görüntü olacaktır) ve muhtemelen yalnızca geliştirme veya test sce kullanılmalıdır narios. Çoğu Kurumsal üretim senaryosunda, yüksek kullanılabilirlik (HA) ve yönetilmesi kolay ölçeklenebilirlik birden çok düğüm, sunucuları ve Vm'leri artı "akıllı yük devretmeleri" arasında yük dengelemeyi sahip istiyorsunuz bunu bir sunucu veya düğüm başarısız olursa, hizmetler ve kapsayıcılar başka bir ana bilgisayar sunucusuna veya VM taşınır. Bu durumda, kapsayıcı kümeleri ve düzenleyicileri zamanlayıcılar gibi daha gelişmiş teknolojilerden gerekir. Bu nedenle, bu kümeye dağıtma olanağı Gelişmiş senaryolar işleyerek sonraki bölümde açıklanmıştır.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Docker uygulamaları Docker kümelerine dağıtma

Dağıtılmış uygulamalar doğasını da dağıtılmış işlem kaynakları gerektirir. Üretim ölçeği-özelliklerini kullanabilmek için yüksek ölçeklenebilirlik ve havuza alınmış kaynaklar temelinde yüksek kullanılabilirlik sağlayan özellikler kümeleme olması gerekir.

Kapsayıcıları el ile bu kümeye CLI aracını veya bir web kullanıcı Arabirimi, dağıttığınız ancak ölçeklendirme genişletme veya izleme yönetim amaçları gibi veya nokta dağıtımını test etmek için el ile çalışma, bu tür ayırmanız gerekir.

Özellikle, bir CD açısından ve Azure DevOps Hizmetleri, kapsayıcıya alınmış uygulamalarınızı kapsayıcı dağıtılmış kümeleri dağıtan, Azure DevOps Services Release Management ortamlarından özel yapılan dağıtım görevlerini çalıştırabilirsiniz Şekil 5-9'da gösterildiği gibi hizmet.

![CD dağıtma adım (4) aracılığıyla düzenleyicileri kümelerine de yayımlayabilirsiniz.](./media/image9.png)

**Şekil 5-9**. Dağıtılmış uygulamalar Container Service'e dağıtma

Başlangıçta, belirli bir küme veya düzenleyicileri dağıtırken, geleneksel olarak belirli bir dağıtım betikleri ve her bir orchestrator (diğer bir deyişle, Kubernetes ve farklı dağıtım mekanizmalarına sahip Service Fabric) başına mekanizmaları yerine daha basit kullanmanız gerekir ve kullanımı kolay `docker-compose` tabanlı aracı `docker-compose.yml` tanım dosyası. Ancak, Şekil 5-10'da gösterilen Azure DevOps Hizmetleri Docker dağıtım görevi sayesinde artık ayrıca desteklenen düzenleyiciler için yalnızca, tanıdık kullanarak dağıtabilirsiniz `docker-compose.yml` aracı "çeviri" gerçekleştirdiğinden, dosya (sizin gelen`docker-compose.yml`orchestrator tarafından gerekli biçime dosyası).

![Görev Kataloğu'nda Azure DevOps, Docker gösteren tarayıcı görünümünü görev dağıtın.](./media/image10.png)

**Şekil 5-10**. Docker dağıtma görevi için ortam RM ekleme

Şekil 5-11 Docker dağıtma görevi düzenleyin ve hedef türünü (Azure Container Service DC/OS, bu durumda), Docker Compose dosyası ve Docker kayıt defteri bağlantıya (ör. Azure Container Registry veya Docker hub'ı) nasıl gösterir. Bu, kümedeki kapsayıcıları olarak dağıtılması için kullanıma hazır özel Docker görüntülerinizi alır görevdir.

![Azure DevOps, tarayıcı görünümünü orchestrator görev tanımına dağıtın.](./media/image11.png)

**Şekil 5-11**. Docker dağıtma görev tanımını Azure Container Service DC/OS için dağıtma

> [! Daha fazla bilgi] CD işlem hattının hakkında Azure DevOps Hizmetleri ve Docker'ı ziyaret edin <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>5. Adım: Çalıştırma ve yönetme

Çalıştıran ve uygulamaları yönetmek için Kurumsal üretim sırasında önemli bir konu içinde ve kendisinin ve işlemleri türü nedeniyle düzeyidir ve bu alanı büyük kapsamını yanı sıra bu (BT işlemleri) düzeyinde çalışan kişiler için tüm sonraki bölümde ayrılmıştır Bunu açıklayan.

## <a name="step-6-monitor-and-diagnose"></a>6. Adım: İzleme ve tanılama

Bu konu aynı zamanda sonraki kapsamında görevleri bir parçası olarak bölüm, BT gerçekleştirir; üretim sistemleri Bununla birlikte, uygulamayı sürekli olarak geliştirilir, bu adımda elde edilen içgörüleri Geliştirme takımına geri besleme gerekir vurgulamak önemlidir. Görevleri ve işlemleri sık gerçekleştirilir ancak bu açısından bakıldığında, ayrıca DevOps parçası BT.

Yalnızca, %100 devops'un bölge içindeki izleme ve tanılama olduğunda izleme işlemleri ve test veya beta ortamları karşı geliştirme ekibi tarafından gerçekleştirilen analiz olan. Bu, yük testi yapma veya beta veya beta test uzmanlarına yeni sürümleri nereden çalışıyorsunuz, QA ortamları izleme tarafından gerçekleştirilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
