---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: DevOps iş akışının "dıştaki döngüsü" adımlarını öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e7a82d2e5a5d503e5efbe9ac8242b163baab1286
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295759"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar

Şekil 5-1, DevOps dış döngüsü iş akışından oluşan adımların uçtan uca bir listesini sunar.

![Bu diyagramda DevOps 'ın "dıştaki döngüsü" gösterilmektedir. Kod depoya gönderildiğinde, bir CI işlem hattı başlatılır, sonra uygulamanın dağıtıldığı CD işlem hattı başlar. Dağıtılan uygulamalardan toplanan ölçümler, "iç döngü" gerçekleştiği geliştirme iş yüküne geri gönderilir, böylece geliştirme ekipleri Kullanıcı ve iş ihtiyaçlarına yanıt vermeye yönelik gerçek verilere sahip olur.](./media/image1.png)

**Şekil 5-1**. Microsoft araçları ile Docker uygulamaları için DevOps dış döngüsü iş akışı

Şimdi bu adımların her birini daha ayrıntılı olarak inceleyelim.

## <a name="step-1-inner-loop-development-workflow"></a>1\. Adım: İç döngü geliştirme iş akışı

Bu adım, Bölüm 4 ' te ayrıntılı olarak açıklanmıştır, ancak bir üst sınır, bir geliştiricinin CI ardışık düzen eylemlerini Başlatan kaynak denetimi yönetim sistemine (git gibi) kod iletmesinin ne kadar olduğunu burada bulabilirsiniz.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>2\. Adım: Azure DevOps Services ve git ile kaynak kodu denetimi tümleştirmesi ve yönetimi

Bu adımda, ekipteki farklı geliştiricilerden gelen tüm kodun birleştirilmiş bir sürümünü toplamak için bir sürüm denetimi sistemine sahip olmanız gerekir.

Kaynak kodu denetimi (SCC) ve kaynak kodu yönetimi çoğu geliştiricilerin ikinci doğası olmasına rağmen bir DevOps yaşam döngüsü içinde Docker uygulamaları oluştururken, Docker görüntülerini uygulamayla birlikte göndermemeye ihtiyacınız olduğunu vurgulamak önemlidir. Geliştiricinin makinesinden doğrudan genel Docker kayıt defterine (Azure Container Registry veya Docker Hub gibi). Aynı şekilde, yayımlanacak ve üretim ortamlarına dağıtılacak Docker görüntülerinin yalnızca kaynak kodu deponuza (git gibi) bağlı olarak genel derleme veya CI işlem hattınızda tümleştirilebilen kaynak kodunda oluşturulması gerekir.

Geliştiriciler tarafından oluşturulan yerel görüntüler, yalnızca kendi makineleri içinde test edilirken kullanılmalıdır. Bu nedenle, DevOps ardışık düzeninin SCC kodundan etkinleştirilmesi çok önemlidir.

Azure DevOps Services ve Team Foundation Server git ve Team Foundation Sürüm Denetimi desteği. Bunlarla arasında seçim yapabilir ve uçtan uca bir Microsoft deneyimi için kullanabilirsiniz. Ancak, kodunuzu dış depolarda (GitHub, şirket içi Git depoları veya alt sürüm gibi) yönetebilir ve yine de bu koda bağlanarak DevOps CI işlem hattınızı başlangıç noktası olarak alabilirsiniz.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>3\. Adım: Azure DevOps Services ve Docker ile derleme, CI, tümleştirme ve test etme

CI, modern yazılım testi ve teslimi için standart olarak ortaya çıktı. Docker çözümü, geliştirme ve operasyon takımları arasındaki kaygılara açık bir ayrım sağlar. Docker görüntülerinin imlebilirliği, geliştirildiği, CI üzerinden test edilen ve üretimde çalışan arasında tekrarlanabilir bir dağıtım sağlar. Geliştirici dizüstü bilgisayarları ve test altyapısı arasında dağıtılan Docker altyapısı, kapsayıcıları ortamlar arasında taşınabilir hale getirir.

Bu noktada, doğru koda sahip bir sürüm denetimi sistemine sahip olduktan sonra, kodu seçmek ve genel derlemeyi ve testleri çalıştırmak için bir *Yapı hizmetine* ihtiyacınız vardır.

Bu adım için iç iş akışı (CI, yapı, test), kod deponuzdan (git, vb.), Yapı sunucunuza (Azure DevOps Services), Docker altyapısından ve bir Docker kayıt defteriyle oluşan bir CI işlem hattının oluşturulmasını yaklaşık olarak oluşturur.

Uygulamalarınızı oluşturmak ve CI işlem hattınızı ayarlamak ve oluşturulan "yapıtları" bir sonraki adımda açıklanan "yapıt deposuna" yayımlamak için temel olarak Azure DevOps Services kullanabilirsiniz.

Dağıtım için Docker kullanırken, dağıtılacak "son yapıtlar", uygulama veya hizmetlerinizin içine gömülü olan Docker görüntüleridir. Bu görüntüler, bir *Docker kayıt defterine* gönderilir veya yayımlanır (Azure Container Registry sahip olduklarınızı gibi özel bir depo veya resmi temel görüntülerde yaygın olarak kullanılan Docker Hub kayıt defteri gibi).

Temel kavram aşağıda verilmiştir: CI işlem hattı git gibi bir SCC deposuna yapılan bir işleme tarafından açılır. Bu işlem, Azure DevOps Services bir Docker kapsayıcısında derleme işi çalıştırmasına ve bu işin başarıyla tamamlanmasıyla, Şekil 5-2 ' de gösterildiği gibi Docker kayıt defterine bir Docker görüntüsü göndermesine neden olur.

![Dış döngünün ilk bölümü, 1 ile 3 arasındaki adımları, koddan, çalıştırmayı, hata ayıklamayı ve doğrulamayı, sonra derleme ve test CI adımına kadar kod depoyu içerir](./media/image2.png)

**Şekil 5-2**. CI 'da yer alan adımlar

Docker ve Azure DevOps Services ile ilgili temel CI iş akışı adımları aşağıda verilmiştir:

1. Geliştirici bir SCC deposuna (git/Azure DevOps Services, GitHub, vb.) bir işlemeye gönderim sağlar.

2. Azure DevOps Services veya git kullanıyorsanız, CI içinde yerleşik olarak bulunur, bu da Azure DevOps Services bir onay kutusu seçmenin basit olduğu anlamına gelir. Bir dış SCC (GitHub gibi) kullanıyorsanız, güncelleştirme Azure DevOps Services veya git `webhook` /GitHub ' a gönderim yapılır.

3. Azure DevOps Services, resmi açıklayan Dockerfile ve uygulama ve test kodu da dahil olmak üzere SCC deposunu çeker.

4. Azure DevOps Services bir Docker görüntüsü oluşturur ve bir yapı numarasıyla etiketleyebilir.

5. Azure DevOps Services sağlanan Docker Konağı içindeki Docker kapsayıcısını başlatır ve uygun testleri çalıştırır.

6. Testler başarılı olursa görüntü, "Blessed" ("/1.0.0" gibi) ve ardından Docker Kayıt defterinize (Docker Hub, Azure Container Registry, DTR vb.) itilmesi için ilk olarak anlamlı bir ada yol açmıştır.

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Azure DevOps Services için Azure DevOps Services ve Docker uzantısıyla CI işlem hattını uygulama

Visual Studio Azure DevOps Services,, Docker görüntülerini oluşturabileceğiniz, Docker görüntülerini kimliği doğrulanmış bir Docker kayıt defterine gönderebilen, Docker görüntülerini çalıştıran veya tarafından sunulan diğer işlemleri çalıştıran, CI/CD işlem hattınızda kullanabileceğiniz derleme & sürüm şablonları içerir. Docker CLı. Ayrıca, Şekil 5-3 ' de gösterildiği gibi, çok Kapsayıcılı Docker uygulamaları oluşturmak, göndermek ve çalıştırmak için kullanabileceğiniz bir Docker Compose görevi ekler veya Docker Compose CLı tarafından sunulan diğer işlemleri çalıştırabilirsiniz.

![Azure DevOps 'da Docker CI işlem hattının tarayıcı görünümü](./media/image3.png)

**Şekil 5-3**. Yapı & sürüm şablonları ve ilişkili görevler de dahil olmak üzere Azure DevOps Services Docker CI işlem hattı.

Azure Service Fabric, Azure Kubernetes hizmeti ve benzer tekliflerde derleme/test ve dağıtım yapmak üzere CI/CD yapılarınızı oluşturmak için bu şablonları ve görevleri kullanabilirsiniz.

Bu Visual Studio Team Services görevlerle, Azure 'da sağlanan bir Linux-Docker Konağı/VM ve tercih ettiğiniz Docker kayıt defteri (Azure Container Registry, Docker Hub, özel Docker DTR veya başka bir Docker kayıt defteri) ile Docker CI işlem hattınızı bir ile birleştirebilirsiniz. çok tutarlı bir yoldur.

***Gereksinimler:***

- Azure DevOps Services veya şirket içi yüklemeler için, Team Foundation Server 2015 güncelleştirme 3 veya sonraki bir sürümü.

- Docker ikililerini içeren bir Azure DevOps Services Aracısı.

  Bu aracılardan birini oluşturmanın kolay bir yolu, Azure DevOps Services Agent Docker görüntüsünü temel alan bir kapsayıcı çalıştırmak için Docker kullanmaktır.

> [! BILGI] Azure DevOps Services Docker CI işlem hattı oluşturma ve izlenecek yolları görüntüleme hakkında daha fazla bilgi edinmek Için şu siteleri ziyaret edin:
>
> - Bir Visual Studio Team Services (Şimdi Azure DevOps Services) aracı bir Docker kapsayıcısı olarak çalıştırılıyor: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Azure DevOps Services .NET Core Linux Docker görüntüleri derleniyor: \
>   <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>
>
> - Docker desteğiyle Linux tabanlı bir Visual Studio Team Service derleme makinesi oluşturma: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Çok Kapsayıcılı Docker uygulamalarını tümleştirin, test edin ve doğrulayın

Genellikle, çoğu Docker uygulaması tek bir kapsayıcı yerine birden çok kapsayıcıdan oluşur. İyi bir örnek, mikro hizmet başına bir kapsayıcıya sahip olduğunuz mikro hizmetlere dayalı bir uygulamadır. Ancak, mikro hizmetler yaklaşım desenlerinin kesinlikle takip etmeksizin bile, Docker uygulamanızın birden çok kapsayıcı veya hizmetten oluşması olasıdır.

Bu nedenle, CI işlem hattında uygulama kapsayıcıları oluşturulduktan sonra, bir tümleştirme Docker ana bilgisayarı içindeki kapsayıcılarından veya hatta kapsayıcılarınızın bulunduğu bir test kümesine bir bütün olarak uygulamayı dağıtmanız, tümleştirmeniz ve test etmeniz gerekir Dağıtılmış.

Tek bir konak kullanıyorsanız, tek bir VM 'de Docker ortamını test etmek ve doğrulamak üzere ilgili kapsayıcıları derlemek ve dağıtmak için Docker-Compose gibi Docker komutlarını kullanabilirsiniz. Ancak, DC/OS, Kubernetes veya Docker Sısınma gibi bir Orchestrator kümesiyle çalışıyorsanız, seçili kümenize/zamanlayıcıya bağlı olarak Kapsayıcılarınızı farklı bir mekanizma veya Orchestrator aracılığıyla dağıtmanız gerekir.

Docker kapsayıcılarına karşı çalıştırabileceğiniz birçok test türü aşağıda verilmiştir:

- Docker kapsayıcıları için birim testleri

- İlişkili uygulamaların veya mikro hizmetlerin gruplarını test etme

- Üretimde ve "Canary" sürümlerindeki test

Önemli nokta, tümleştirme ve işlevsel testleri çalıştırırken, bu testleri kapsayıcılar dışından çalıştırmanız gerekir. Kapsayıcılar, üretim ortamına dağıtabilediklerinizle aynı olması gereken statik görüntüleri temel aldığı için, dağıtmakta olduğunuz kapsayıcılarda testler dahil değildir veya çalıştırılmaz.

Çeşitli kümeler (test kümesi, hazırlama kümesi ve üretim kümesi) gibi daha gelişmiş senaryolar test edilirken, görüntüleri bir kayıt defterine yayımlamada pratik bir seçenek, bu sayede çeşitli kümelerde test edilebilir.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Özel uygulama Docker görüntüsünü küresel Docker Kayıt defterinize gönderme

Docker görüntüleri test edildikten ve doğrulandıktan sonra, bunları Docker kayıt defterinizde etiketlemek ve yayımlamak isteyeceksiniz. Docker kayıt defteri, özel testinizi ("küçük resimler" olarak da bilinir), QA ve üretim ortamlarına dağıtmak üzere depoladığınız merkezi bir yerdir çünkü Docker uygulama yaşam döngüsünün önemli bir parçasıdır.

(Git, vb.), SCC deponuzda (git, vb.) depolanan uygulama kodunun "Truth kaynağı", ikili uygulamanız veya bitlerin QA veya üretim ortamlarına dağıtılması için "gerçeği kaynağıdır".

Genellikle, özel görüntüleriniz için Azure Container Registry ya da Docker güvenilen kayıt defteri gibi bir şirket içi kayıt defterinde veya kısıtlanmış erişimi olan bir ortak bulut kayıt defterinde (örneğin, Docker Hub), ancak kodunuzun açık kaynak olmaması durumunda satıcının güvenliğine güvenmeniz gerekir. Her iki durumda da, kullandığınız yöntem benzerdir ve Şekil 5-4 ' de gösterildiği `docker push` gibi komuta dayalıdır.

![Adım 3 ' te, tümleştirme ve test (CI) oluşturmak için, elde edilen Docker görüntülerini özel veya ortak bir kayıt defterine yayımlayabilirsiniz.](./media/image4.png)

**Şekil 5-4**. Docker kayıt defterine özel görüntüler Yayımlama

Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, Quay kayıt defteri vb. gibi bulut satıcılarından çok sayıda Docker kayıt defteri teklifi vardır.

Docker görevlerini kullanarak, Şekil 5-5 ' de gösterildiği gibi, birden çok etiketli bir `docker-compose.yml` dosya tarafından tanımlanan bir dizi hizmet görüntüsünü, kimliği doğrulanmış bir Docker kayıt defterine (Azure Container Registry gibi) gönderebilirsiniz.

![Azure DevOps 'daki bir kayıt defterine görüntü yayımlama adımının tarayıcı görünümü.](./media/image5.png)

**Şekil 5-5**. Özel görüntüleri bir Docker kayıt defterine yayımlamak için Azure DevOps Services kullanma

> [! BILGI] Azure Container Registry hakkında daha fazla bilgi Için bkz <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>4\. Adım: CD, dağıtma

Docker görüntülerinin imlebilirliği, geliştirildiği, CI üzerinden test edilen ve üretimde çalışan, tekrarlanabilir bir dağıtım sağlar. Docker kayıt defterinizde (özel veya ortak) uygulama Docker görüntülerini yayımladıktan sonra, Azure DevOps Services kullanarak CD işlem hattınızdan (üretim, QA, hazırlama, vb.) sahip olabileceğiniz çeşitli ortamlara dağıtabilirsiniz. işlem hattı görevleri veya Azure DevOps Services Release Management.

Ancak, bu noktada dağıtmakta olduğunuz Docker uygulamasının türüne bağlıdır. Birkaç kapsayıcıyı veya hizmeti kapsayan ve birkaç sunucuya veya VM 'ye dağıtılan tek parçalı bir uygulama gibi basit bir uygulamayı (bir bileşim ve dağıtım noktasından) dağıtmak, hiper ölçekli özelliklerine sahip mikro hizmetlere dayalı uygulama. Bu iki senaryo aşağıdaki bölümlerde açıklanmıştır.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Oluşturulan Docker uygulamalarını birden çok Docker ortamına dağıtma

Daha az karmaşık senaryoya ilk göz atalım: tek bir ortamda veya birden çok ortamda basit Docker konaklarına (VM 'Ler veya sunucular) dağıtım (QA, hazırlama ve üretim). Bu senaryoda, dahili olarak CD işlem hattı, Şekil 5-6 ' de gösterildiği gibi, Docker uygulamalarını ilgili kapsayıcı veya hizmet kümesiyle birlikte dağıtmak için Docker-Compose ' u (Azure DevOps Services dağıtım görevleriniz) kullanabilir.

![CD dağıtım adımı (#4), q & a, hazırlama ve üretim gibi farklı ortamlarda yayımlayabilir.](./media/image6.png)

**Şekil 5-6**. Uygulama kapsayıcılarını basit Docker ana bilgisayar ortamları kayıt defterine dağıtma

Şekil 5-7 Görev Ekle iletişim kutusunda Docker Compose ' a tıklayarak yapı CI 'nizi Azure DevOps Services aracılığıyla QA/test ortamlarına nasıl bağlayabileceğinizi vurgular. Ancak, hazırlama veya üretim ortamlarına dağıtım yaparken, genellikle birden çok ortamı (QA, hazırlama ve üretim gibi) işleyen Release Management özellikleri kullanırsınız. Tek Docker konaklarına dağıtıyorsanız, bu, Azure DevOps Services "Docker Compose" görevini kullanıyor (Bu `docker-compose up` komut, alt ' ın altındaki komutu çağırır). Azure Kubernetes Service 'e (AKS) dağıtım yapıyorsanız, aşağıdaki bölümde açıklandığı gibi Docker dağıtım görevini kullanır.

![Docker Compose görevi ekleme tarayıcı görünümü.](./media/image7.png)

**Şekil 5-7**. Bir Azure DevOps Services işlem hattına Docker Compose görevi ekleme

Azure DevOps Services ' de bir yayın oluşturduğunuzda, bir giriş yapıtları kümesi alır. Bu yapıtlar, tüm ortamlarda yayının kullanım ömrü boyunca sabit olmak üzere tasarlanmıştır. Kapsayıcıları belirttiğinizde, giriş yapıtları dağıtılacak bir kayıt defterindeki görüntüleri belirler. Bu görüntülerin nasıl tanımlandığına bağlı olarak, yayının süresi boyunca aynı kalmaları garanti edilmez, bu da bir `myimage:latest` `docker-compose` dosyadan başvuru yaparken en belirgin durumdur.

Azure DevOps Services şablonlar, aynı görüntü ikilisini benzersiz şekilde tanımlamak için garanti edilen belirli bir kayıt defteri görüntüsü olan yapı yapıtları oluşturma olanağı sağlar. Bunlar, gerçekten bir yayına giriş olarak kullanmak istediğiniz şeydir.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Azure DevOps Services kullanarak, Docker ortamlarında yayınları yönetme Release Management

Azure DevOps Services şablonları aracılığıyla yeni bir görüntü oluşturabilir, bunu bir Docker kayıt defterine yayımlayabilir, Linux veya Windows konakları üzerinde çalıştırabilir ve tüm uygulama olarak birden çok kapsayıcı dağıtmak için, tüm `docker-compose` Azure DevOps aracılığıyla gibi komutları kullanabilirsiniz. Hizmetler, Şekil 5-8 ' de gösterildiği gibi birden çok ortam için tasarlanan yetenekler Release Management.

![Docker Compose sürümlerini yapılandıran Azure DevOps tarayıcı görünümü.](./media/image8.png)

**Şekil 5-8**. Azure DevOps Services Azure DevOps Services Docker Compose görevlerini yapılandırma Release Management

Bununla birlikte, Şekil 5-6 ' de gösterilen ve Şekil 5-8 ' de uygulanan senaryonun basit bir işlemdir (tek Docker konaklarına ve sanal makinelere dağıtılıyor ve tek bir kapsayıcı veya görüntü başına bir örnek olacaktır) ve muhtemelen yalnızca geliştirme veya test SCE için kullanılmalıdır narios. Çoğu kurumsal üretim senaryosunda, yüksek kullanılabilirlik (HA) ve birden çok düğüm, sunucu ve VM genelinde yük dengelemeye ve ayrıca "akıllı yük devretme", bir sunucu veya düğüm başarısız olursa, hizmetleri ve kapsayıcıları başka bir konak sunucusuna veya VM 'ye taşınacak. Bu durumda, kapsayıcı kümeleri, düzenleyiciler ve zamanlayıcılar gibi daha gelişmiş teknolojilerin olması gerekir. Bu nedenle, bu kümelere dağıtmanın yolu, sonraki bölümde açıklanan gelişmiş senaryoları işlemeklerdir.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Docker uygulamalarını Docker kümelerine dağıtma

Dağıtılmış uygulamaların doğası de dağıtılan işlem kaynaklarını gerektirir. Üretim ölçeğinde yetenekler sağlamak için, havuza alınmış kaynaklara göre yüksek ölçeklenebilirlik ve yüksek kullanılabilirlik sağlayan kümeleme özelliklerine sahip olmanız gerekir.

Bir CLı aracından veya Web kullanıcı arabiriminden bu kümelerdeki kapsayıcıları el ile dağıtabilirsiniz, ancak bu tür bir el ile çalışma türünü, genişleme veya izleme gibi yönetim amaçlarını veya bunları belirlemek için ayırmanız gerekir.

Bir CD görünümü ve Azure DevOps Services özel olarak, Kapsayıcılı uygulamalarınızı kapsayıcıda dağıtılmış kümelere dağıtan Azure DevOps Services Release Management ortamlarınızdan özel olarak hazırlanmış dağıtım görevlerini çalıştırabilirsiniz Service, Şekil 5-9 ' de gösterildiği gibi.

![CD dağıtım adımı (#4), kümeler aracılığıyla kümelere da yayımlayabilir.](./media/image9.png)

**Şekil 5-9**. Dağıtılmış uygulamaları kapsayıcı hizmetine dağıtma

Başlangıçta, belirli kümelere veya düzenleyicilerine dağıtım yaparken, her Orchestrator için (yani, Kubernetes ve Service Fabric farklı dağıtım mekanizmalarına sahip olan) geleneksel olarak belirli dağıtım betikleri ve mekanizmaları kullanacaksınız ve `docker-compose.yml` tanım dosyasını temel alan kullanımı `docker-compose` kolay araç. Ancak, Şekil 5-10 ' de gösterilen Azure DevOps Services Docker Deploy görevi sayesinde, araç artık sizin için "Çeviri" gerçekleştirtiğinden tanıdık `docker-compose.yml` dosyayı kullanarak desteklenen düzenleyicilerine de dağıtabilirsiniz ( `docker-compose.yml`Orchestrator tarafından gereken biçime dosya).

![Azure DevOps 'da, Kubernetes 'e dağıt görevini gösteren tarayıcı görünümü.](./media/add-deploy-to-kubernetes-task.png)

**Şekil 5-10**. Ortamınıza Kubernetes görevine dağıtım ekleme

Şekil 5-11 ' da, Kubernetes ile yapılandırma için kullanılabilir olan bölümleri nasıl düzenleyebileceğinizi gösterir. Bu, kümedeki kapsayıcılar olarak dağıtılacak, kullanıma yönelik özel Docker görüntülerini alacak olan görevdir.

![Azure DevOps tarayıcı görünümü, Kubernetes görev tanımına dağıtın.](./media/edit-deploy-to-kubernetes-task.png)

**Şekil 5-11**. Docker dağıtım görev tanımı, ACS DC/OS 'ye dağıtılıyor

> [! BILGI] Azure DevOps Services ve Docker ile CD işlem hattı hakkında daha fazla bılgı edinmek Için şu adresi ziyaret edin<https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>5\. Adım: Çalıştır ve Yönet

Kurumsal üretim düzeyinde uygulama çalıştırmak ve yönetmek için ve tek başına ve bu düzeyde (BT işlemleri) çalışan işlem ve kişilerin türü ve bu alanın büyük kapsamı nedeniyle, bir sonraki bölümün tamamının Bunu açıklayarak.

## <a name="step-6-monitor-and-diagnose"></a>6\. Adım: İzleme ve tanılama

Bu konu ayrıca, üretim sistemlerinde gerçekleştirdiği görevlerin bir parçası olarak sonraki bölümde ele alınmıştır. Bununla birlikte, uygulamanın sürekli geliştirilmesi için bu adımda elde edilen öngörülerin geliştirme ekibine geri akışı gerektiğini vurgulamak önemlidir. Bu görünüm noktasından de DevOps 'un bir parçası olsa da, görevler ve işlemler yaygın olarak gerçekleştirilir.

Yalnızca izleme ve tanılama, DevOps bölgesi kapsamında% 100 olduğunda, geliştirme ekibi tarafından test veya beta ortamlarına karşı gerçekleştirilen izleme işlemleri ve analizlerdir. Bu işlem, yük testi gerçekleştirerek veya Beta Test edicilerin yeni sürümleri çalıştığı Beta ya da QA ortamlarını izleyerek yapılır.

>[!div class="step-by-step"]
>[Önceki](index.md)İleri
>[](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
