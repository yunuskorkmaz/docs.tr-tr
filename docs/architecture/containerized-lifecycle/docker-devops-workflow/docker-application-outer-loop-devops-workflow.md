---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: DevOps iş akışının "dış döngü" adımlarını öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: 44bd73bf88a743e5350e422d3ea000ca075f7383
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021295"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar

Şekil 5-1, DevOps dış döngü iş akışını içeren adımların uçtan uca bir tasvirini sunar. DevOps'un "dış halkasını" gösterir. Kod repo'ya itildiğinde, bir CI ardışık hattı başlatılır ve ardından uygulamanın dağıtıldığı CD ardışık Dağıtılan uygulamalardan toplanan ölçümler, "iç döngü"nün oluştuğu geliştirme iş yüküne geri beslenir, bu nedenle geliştirme ekipleri kullanıcı ve iş gereksinimlerine yanıt vermek için gerçek verilere sahiptir.

![DevOps dış döngü iş akışının 6 adımını gösteren diyagram.](./media/docker-application-outer-loop-devops-workflow/overview-dev-ops-outter-loop-workflow.png)

**Şekil 5-1**. Microsoft araçları yla Docker uygulamaları için DevOps dış döngü iş akışı

Şimdi, bu adımların her birini daha ayrıntılı olarak inceleyelim.

## <a name="step-1-inner-loop-development-workflow"></a>Adım 1: İç-döngü geliştirme iş akışı

Bu adım Bölüm 4'te ayrıntılı olarak açıklanmıştır, ancak özetlemek gerekirse, burada dış döngü nün başladığı yer, bir geliştiricinin KODU KAYNAK Denetim Yönetim Sistemi'ne (Git gibi) ittiği an, CI boru hattı eylemlerini başlatMıştır.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Adım 2: Azure DevOps Hizmetleri ve Git ile Kaynak Kod Denetimi entegrasyonu ve yönetimi

Bu adımda, takımdaki farklı geliştiricilerden gelen tüm kodun birleştirilmiş sürümünü toplamak için bir sürüm denetim sistemine sahip olmanız gerekir.

Kaynak kodu denetimi (SCC) ve kaynak kodu yönetimi çoğu geliştirici için ikinci doğa gibi görünse de, DevOps yaşam döngüsünde Docker uygulamaları oluştururken, uygulamayla birlikte Docker görüntülerini doğrudan geliştiricinin makinesinden küresel Docker Registry'ye (Azure Konteyner Kayıt Defteri veya Docker Hub gibi) göndermemeniz gerektiğini vurgulamak önemlidir. Tam tersine, piyasaya sürülecek ve üretim ortamlarına dağıtılacak Docker görüntüleri, yalnızca kaynak kod deponuza (Git gibi) dayalı olarak küresel yapınıza veya CI ardışık hattınıza entegre edilen kaynak kodunda oluşturulmalıdır.

Geliştiriciler tarafından oluşturulan yerel görüntüler, sadece kendi makineleri içinde test ederken onlar tarafından kullanılmalıdır. Bu yüzden DevOps boru hattının SCC kodundan aktif hale getirilmiş olması çok önemlidir.

Azure DevOps Hizmetleri ve Team Foundation Server, Git ve Team Foundation Sürüm Denetimini destekler. Aralarında seçim yapabilir ve uça bir Microsoft deneyimi için kullanabilirsiniz. Ancak, kodunuzu harici depolarda (GitHub, şirket içi Git depoları veya Subversion gibi) yönetebilir ve yine de bu depoya bağlanabilir ve Kodu DevOps CI ardışık ardınız için başlangıç noktası olarak alabilirsiniz.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Adım 3: Azure DevOps Hizmetleri ve Docker ile Oluşturma, CI, Tümleştirme ve Test

CI modern yazılım testi ve teslimat için bir standart olarak ortaya çıkmıştır. Docker çözümü, geliştirme ve operasyon ekipleri arasındaki endişeleri net bir şekilde birbirinden korur. Docker görüntülerinin değişmezliği, geliştirilen, CI aracılığıyla test edilen ve üretimde çalışan arasında tekrarlanabilir bir dağıtım sağlar. Docker Engine geliştirici dizüstü bilgisayarlar ve test altyapısı arasında dağıtılan kapsayıcılar ortamlar arasında taşınabilir hale getirir.

Bu noktada, gönderilen doğru kodu içeren bir sürüm denetim sistemine sahip olduktan sonra, kodu almak ve genel yapı ve testleri çalıştırmak için bir *yapı hizmetine* ihtiyacınız vardır.

Bu adımiçin dahili iş akışı (CI, inşa, test) kod deponuz (Git, vb.), yapı sunucunuz (Azure DevOps Hizmetleri), Docker Engine ve Docker Registry'nizden oluşan bir CI ardışık hattının inşası ile ilgilidir.

Azure DevOps Hizmetlerini, uygulamalarınızı oluşturmak ve CI ardınızı ayarlamak ve inşa edilen "yapıları" bir sonraki adımda açıklanan bir "yapı deposuna" yayımlamak için temel olarak kullanabilirsiniz.

Dağıtım için Docker'ı kullanırken, dağıtılacak "son yapılar" uygulamanızın veya hizmetlerinizin içinde gömülü olduğu Docker görüntüleridir. Bu görüntüler, Docker *Registry'ye* (Azure Konteyner Kayıt Defteri'nde sahip olabileceğiniz özel bir depo veya resmi temel resimler için yaygın olarak kullanılan Docker Hub Kayıt Defteri gibi herkese açık bir depo) itilir veya yayımlanır.

Burada temel kavram: CI boru hattı git gibi bir SCC deposu na taahhüt tarafından başladı olacak. Taahhüt, Azure DevOps Hizmetlerinin bir Docker kapsayıcısı içinde bir yapı işi çalıştırmasını ve bu işi başarıyla tamamladıktan sonra Şekil 5-2'de gösterildiği gibi Docker görüntüsünü Docker Registry'ye itmesine neden olur. Dış döngünün ilk bölümü, kod, çalıştır, hata ayıklama ve doğrulama, ardından kod repo'su oluşturma ve test CI adımına kadar 1'den 3'e kadar olan adımları içerir.

![CI iş akışında yer alan üç adımı gösteren diyagram.](./media/docker-application-outer-loop-devops-workflow/continuous-integration-steps.png)

**Şekil 5-2**. CI dahil adımlar

Docker ve Azure DevOps Hizmetleri ile temel CI iş akışı adımları şunlardır:

1. Geliştirici bir SCC deposuna (Git/Azure DevOps Hizmetleri, GitHub, vb.) taahhüt eder.

2. Azure DevOps Services veya Git kullanıyorsanız, CI yerleşiktir, bu da Azure DevOps Hizmetlerinde onay kutusu seçmek kadar basit olduğu anlamına gelir. Harici bir SCC kullanıyorsanız (GitHub gibi), azure `webhook` DevOps Hizmetlerini güncelleştirmehakkında bilgilendirecek veya Git/GitHub'a itecektir.

3. Azure DevOps Hizmetleri, görüntüyü açıklayan Dockerfile'ın yanı sıra uygulama ve test kodu da dahil olmak üzere SCC deposunu çeker.

4. Azure DevOps Hizmetleri bir Docker görüntüsü oluşturur ve bir yapı numarasıyla etiketler.

5. Azure DevOps Hizmetleri, Docker konteynerini sağlanan Docker Host'ta anında kullanır ve uygun testleri çalıştırır.

6. Testler başarılı olursa, görüntü önce anlamlı bir ada yeniden etiketlenir, böylece "kutsanmış yapı" ("/1.0.0" veya başka bir etiket gibi) olduğunu bilmeniz ve ardından Docker Registry'nize (Docker Hub, Azure Konteyner Kayıt Defteri, DTR, vb.) itilir.

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Azure DevOps Hizmetleri ve Azure DevOps Hizmetleri için Docker uzantısı ile CI ardışık hattını uygulama

Visual Studio Azure DevOps Hizmetleri, Docker görüntüleri oluşturabileceğiniz, Docker görüntülerini kimlik doğrulanmış docker kayıt defterine taşıyabileceğiniz, Docker görüntülerini çalıştırabileceğiniz veya Docker CLI tarafından sunulan diğer işlemleri çalıştırabileceğiniz CI/CD ardışık ardışık ardışık ardışık ardışık ardışık ğınızda kullanabileceğiniz Yapı & Sürüm Şablonları içerir. Ayrıca, şekil 5-3'te gösterildiği gibi, çok kapsayıcı Docker uygulamalarını oluşturmak, itmek ve çalıştırmak veya Docker Compose CLI tarafından sunulan diğer işlemleri çalıştırmak için kullanabileceğiniz bir Docker Compose görevi de ekler.

![Azure DevOps'taki Docker CI boru hattının ekran görüntüsü.](./media/docker-application-outer-loop-devops-workflow/docker-ci-pipeline-azure-devops.png)

**Şekil 5-3**. Yapı & Sürüm Şablonları ve ilişkili görevler de dahil olmak üzere Azure DevOps Hizmetlerinde Docker CI ardışık hattı.

Bu şablonları ve görevleri, Azure Hizmet Kumaşı, Azure Kubernetes Hizmeti ve benzeri teklifleroluşturmak/ test etmek ve dağıtmak için CI/CD yapılarınızı oluşturmak için kullanabilirsiniz.

Bu Visual Studio Takım Hizmetleri görevleri, Azure'da sağlanan bir Linux-Docker Host/VM ve tercih ettiğiniz Docker kayıt defteri (Azure Konteyner Kayıt Defteri, Docker Hub, özel Docker DTR veya diğer Docker kayıt defteri) ile Docker CI boru hattınızı çok tutarlı bir şekilde monte edebilirsiniz.

***Gereksinim -leri:***

- Azure DevOps Hizmetleri veya şirket içi yüklemeler için Team Foundation Server 2015 Update 3 veya sonraki.

- Docker ikililerine sahip bir Azure DevOps Hizmetleri aracısı.

  Bu aracılardan birini oluşturmanın kolay bir yolu, Azure DevOps Hizmetleri aracısı Docker görüntüsünü temel alan bir kapsayıcıyı çalıştırmak için Docker'ı kullanmaktır.

> [! BİlGİ: Azure DevOps Services Docker CI ardışık hattını birleştirme hakkında daha fazla bilgi almak ve iz geçitleri görüntülemek için aşağıdaki siteleri ziyaret edin:
>
> - Docker konteyneri olarak Visual Studio Takım Hizmetleri (Şimdi Azure DevOps Hizmetleri) aracısı çalıştırma: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Azure DevOps Hizmetleri ile .NET Core Linux Docker görüntüleri oluşturma: \
>   <https://docs.microsoft.com/archive/blogs/stevelasker/building-net-core-linux-docker-images-with-visual-studio-team-services>
>
> - Docker desteği ile Linux tabanlı Visual Studio Team Service inşa makinesi oluşturma: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Çoklu kapsayıcı Docker uygulamalarını tümleştirin, test edin ve doğrulayın

Genellikle, çoğu Docker uygulamaları tek bir kapsayıcı yerine birden çok kapsayıcıoluşur. İyi bir örnek, mikrohizmet başına bir konteyner olurdu için mikro hizmetler odaklı bir uygulamadır. Ancak, mikro hizmetler yaklaşım modellerini kesinlikle takip etmeden bile Docker uygulamanızın birden fazla kapsayıcı veya hizmetten oluşması olasıdır.

Bu nedenle, CI ardışık boru hattında uygulama kapsayıcıları inşa ettikten sonra, aynı zamanda dağıtmak gerekir, entegre, ve bir entegrasyon Docker ana bilgisayar içinde tüm kapları ile bir bütün olarak uygulama entegre ve hatta konteyner dağıtılır bir test kümesi içine.

Tek bir ana bilgisayar kullanıyorsanız, docker-compose gibi Docker komutlarını kullanarak ilgili kapsayıcıları tek bir VM'de Docker ortamını test etmek ve doğrulamak için dağıtabilirsiniz. Ancak, DC/OS, Kubernetes veya Docker Swarm gibi bir orkestratör kümesiyle çalışıyorsanız, seçtiğiniz küme/zamanlayıcıya bağlı olarak kapsayıcılarınızı farklı bir mekanizma veya orkestratör aracılığıyla dağıtmanız gerekir.

Docker kapsayıcılarına karşı çalıştırabileceğiniz çeşitli test türleri şunlardır:

- Docker konteynerleri için birim testleri

- Birbiriyle ilişkili uygulamaların veya mikro hizmetlerin test grupları

- Üretim testi ve "kanarya" bültenleri

Önemli nokta, tümleştirme ve işlevsel testleri çalıştırırken, bu testleri kapsayıcıların dışından çalıştırmanız gerektiğidir. Kapsayıcılar, üretime dağıtacağınız kaplara tam olarak benzeyen statik görüntülere dayandığından, testler içermez veya dağıtacağınız kapsayıcılarda çalıştırılamaz.

Birkaç küme (test kümesi, hazırlama kümesi ve üretim kümesi) gibi daha gelişmiş senaryoları sınarken pratik bir seçenek, görüntüleri bir kayıt defterine yayımlamaktır, böylece çeşitli kümelerde sınanabilir.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Özel uygulama Docker imajını küresel Docker Registry'nize itin

Docker görüntüleri test edildikten ve doğrulandıktan sonra, bunları etiketlemek ve Docker kayıt defterinize yayınlamak isteyeceksiniz. Docker kayıt defteri Docker uygulama yaşam döngüsünde kritik bir parçadır, çünkü ÖZEL TESTINIZI ("kutsanmış görüntüler" olarak da bilinir) QA ve üretim ortamlarına dağıtılmak üzere depoladığınız merkezi yerdir.

SCC deponuzda (Git, vb.) depolanan uygulama kodunun sizin "doğruluk kaynağınız" olması gibi, Docker kayıt defteri de ikili uygulamanız veya bitlerinizin QA veya üretim ortamlarına dağıtılması için "doğruluk kaynağınız"dır.

Tipik olarak, özel görüntüleriniz için özel depolarınızı Azure Kapsayıcı Kayıt Defteri'ndeki özel bir depoda veya Docker Trusted Registry gibi bir şirket içi kayıt defterinde veya sınırlı erişime sahip bir genel bulut kayıt defterinde (Docker Hub gibi) sahip olmak isteyebilirsiniz, ancak bu son durumda kodunuz açık kaynak değilse satıcının güvenliğine güvenmeniz gerekir. Her iki durumda da, kullandığınız yöntem benzerdir ve Şekil 5-4'te gösterildiği gibi komutu `docker push` temel alabilirsiniz.

![Özel görüntülerin bir kapsayıcı kayıt defterine itmesini gösteren diyagram.](./media/docker-application-outer-loop-devops-workflow/docker-push-custom-images.png)

**Şekil 5-4**. Docker Registry'ye özel görüntüler yayınlama

3. adımda, bina tümleştirmesi ve sınama (CI) için ortaya çıkan docker görüntülerini özel veya genel kayıt defterine yayımlayabilirsiniz. Azure Konteyner Kayıt Defteri, Amazon Web Hizmetleri Konteyner Kayıt Defteri, Google Konteyner Kayıt Defteri, Quay Registry gibi bulut satıcılarından birden fazla Docker kayıt şirketi teklifi vardır.

Docker görevlerini kullanarak, bir `docker-compose.yml` dosya tarafından tanımlanan ve birden çok etiketiçeren bir hizmet görsel kümesini Şekil 5-5'te gösterildiği gibi kimlik doğrulaması alınmış docker kayıt defterine (Azure Konteyner Kayıt Defteri gibi) taşıyabilirsiniz.

![Görüntüleri kayıt defterine yayımlama adımını gösteren ekran görüntüsü.](./media/docker-application-outer-loop-devops-workflow/publish-custom-image-to-docker-registry.png)

**Şekil 5-5**. Docker Kayıt Defterine özel görüntüler yayınlamak için Azure DevOps Hizmetlerini kullanma

> [! BİlGİ: Azure Kapsayıcı Kayıt Defteri <https://aka.ms/azurecontainerregistry>hakkında daha fazla bilgi için bkz.

## <a name="step-4-cd-deploy"></a>Adım 4: CD, Dağıtım

Docker görüntülerinin değişmezliği, geliştirilen, CI aracılığıyla test edilen ve üretimde çalışan larla tekrarlanabilir bir dağıtım sağlar. Docker kayıt defterinizde yayınlanan uygulama Docker görüntülerini (özel veya herkese açık) yayımladıktan sonra, bunları Azure DevOps Hizmetleri boru hattı görevlerini veya Azure DevOps Hizmetleri Yayın Yönetimi'ni kullanarak CD ardınızdan sahip olabileceğiniz çeşitli ortamlara (üretim, QA, evreleme, vb.) dağıtabilirsiniz.

Ancak, bu noktada bu, ne tür Docker uygulaması dağıttığınız için bağlıdır. Birkaç kapsayıcı veya hizmetten oluşan ve birkaç sunucuya veya VM'ye dağıtılan yekpare bir uygulama gibi basit bir uygulamayı (kompozisyon ve dağıtım açısından) dağıtmak, hiper ölçek özelliklerine sahip mikro hizmet odaklı bir uygulama gibi daha karmaşık bir uygulamayı dağıtmaktan farklıdır. Bu iki senaryo aşağıdaki bölümlerde açıklanmıştır.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Oluşan Docker uygulamalarını birden çok Docker ortamına dağıtma

Önce daha az karmaşık olan senaryoya bakalım: basit Docker ana bilgisayarlarına (VM'ler veya sunucular) tek bir ortamda veya birden çok ortamda (QA, evreleme ve üretim) dağıtım. Bu senaryoda, CD ardınız, Şekil 5-6'da gösterildiği gibi Docker uygulamalarını ilgili kapsayıcı veya hizmet kümesiyle dağıtmak için docker-compose'i (Azure DevOps Hizmetleri dağıtım görevlerinizden) kullanabilir.

![Üç ortama dağıtılabasma adımını gösteren CD diyagramı.](./media/docker-application-outer-loop-devops-workflow/deploy-app-containers-to-docker-host-environments.png)

**Şekil 5-6**. Uygulama kaplarını basit Docker ana bilgisayar ortamları kayıt defterine dağıtma

Şekil 5-7, Görev Ekle iletişim kutusunda Docker Oluştur'u tıklatarak yapı CI'nizi Azure DevOps Hizmetleri aracılığıyla QA/test ortamlarına nasıl bağleyebileceğinizin altını çiziyor. Ancak, evreleme veya üretim ortamlarına dağıtılırken, genellikle birden çok ortamı (QA, evreleme ve üretim gibi) işleyen Sürüm Yönetimi özelliklerini kullanırsınız. Tek Docker ana bilgisayarlarına dağıtım yapıyorsanız, Azure DevOps Hizmetleri "Docker Compose" görevini kullanıyor `docker-compose up` (başlık altındaki komutu çağırmaktır). Azure Kubernetes Hizmeti'ne (AKS) dağıtım yapıyorsanız, aşağıdaki bölümde açıklandığı gibi Docker Dağıtım görevini kullanır.

![Docker Compose görevinin görev ekle iletişim kutusunu gösteren ekran görüntüsü.](./media/docker-application-outer-loop-devops-workflow/add-tasks-docker-compose.png)

**Şekil 5-7**. Azure DevOps Hizmetleri boru hattında Docker Oluşturma görevi ekleme

Azure DevOps Hizmetleri'nde bir sürüm oluşturduğunuzda, bir dizi giriş yapıları alır. Bu eserler, tüm ortamlarda, sürüm ömrü için değişmez olması amaçlanmıştır. Kapsayıcıları tanıttığınızda, giriş yapıları dağıtmak için bir kayıt defterindeki görüntüleri tanımlar. Bu görüntülerin nasıl tanımlandığına bağlı olarak, bu görüntülerin sürüm süresi boyunca aynı kalacağı garanti edilmez, `myimage:latest` en `docker-compose` belirgin durum bir dosyadan referans aldığınızda olur.

Azure DevOps Hizmetleri şablonları, aynı görüntü ikilisini benzersiz olarak tanımlamayı garanti eden belirli kayıt defteri görüntü özetleri içeren yapı yapıları oluşturma olanağı sağlar. Bunlar gerçekten bir sürüm giriş olarak kullanmak istediğiniz şeylerdir.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Azure DevOps Hizmetleri Yayın Yönetimi'ni kullanarak Docker ortamlarına sürüm leri yönetme

Azure DevOps Hizmetleri şablonları aracılığıyla, yeni bir resim oluşturabilir, Docker kayıt defterinde yayımlayabilir, Linux veya Windows `docker-compose` ana bilgisayarlarında çalıştırabilir ve Şekil 5-8'de gösterildiği gibi birden çok ortama yönelik Azure DevOps Hizmetleri Yayın Yönetimi özellikleri aracılığıyla birden çok kapsayıcıyı tüm uygulama olarak dağıtmak gibi komutlar kullanabilirsiniz.

![Docker oluşturma sürümlerinin yapılandırmasını gösteren ekran görüntüsü.](./media/docker-application-outer-loop-devops-workflow/configure-docker-compose-release.png)

**Şekil 5-8**. Azure DevOps Hizmetlerinin Yapılandırılması Azure DevOps Hizmetleri Yayın Yönetimi'nden görevler oluşturun

Ancak, Şekil 5-6'da gösterilen ve Şekil 5-8'de uygulanan senaryonun basit bir senaryo olduğunu (tek Docker ana bilgisayarlarına ve VM'lere dağıtılacak ve görüntü başına tek bir kapsayıcı veya örnek olacak) ve büyük olasılıkla yalnızca geliştirme veya test senaryoları için kullanılması gerektiğini unutmayın. Çoğu kurumsal üretim senaryosunda, birden çok düğüm, sunucu ve VM arasında yük dengelemesi ve sunucu veya düğüm başarısız olursa, hizmetleri ve kapsayıcıları başka bir ana bilgisayar sunucusuna veya VM'ye taşınacak şekilde "akıllı arızalar" yaparak Yüksek Kullanılabilirlik (HA) ve kolay yönetilebilirlik olmasını isteyebilirsiniz. Bu durumda, konteyner kümeleri, orkestratörler ve zamanlayıcılar gibi daha gelişmiş teknolojilere ihtiyacınız vardır. Bu nedenle, bu kümelere dağıtmanın yolu, bir sonraki bölümde açıklanan gelişmiş senaryoları işlemektir.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Docker uygulamalarını Docker kümelerine dağıtma

Dağıtılmış uygulamaların niteliği, dağıtılan bilgi işlem kaynaklarını da gerektirir. Üretim ölçeğinde yeteneklere sahip olmak için, birleştirilmiş kaynaklara dayalı olarak yüksek ölçeklenebilirlik ve yüksek kullanılabilirlik sağlayan kümeleme özelliklerine sahip olmanız gerekir.

Kapsayıcıları bir CLI aracından veya web Kullanıcı Arabirimi'nden bu kümelere el ile dağıtabilirsiniz, ancak dağıtım sınama veya ölçeklendirme veya izleme gibi yönetim amaçlarını tespit etmek için bu tür el ile çalışmayı rezerve etmelisiniz.

CD bakış açısından ve Azure DevOps Hizmetleri özellikle, Azure DevOps Hizmetleri Yayın Yönetimi ortamlarınızdan, kapsayıcı uygulamalarınızı Şekil 5-9'da gösterildiği gibi Kapsayıcı Hizmeti'ndeki dağıtılmış kümelere dağıtacak özel olarak hazırlanmış dağıtım görevlerini çalıştırabilirsiniz.

![CD'nin orkestratörlere dağıtıla adım dağıtan adımını gösteren diyagram.](./media/docker-application-outer-loop-devops-workflow/cd-deploy-to-orchestrators.png)

**Şekil 5-9**. Dağıtılmış uygulamaları Konteyner Hizmetine dağıtma

Başlangıçta, belirli kümelere veya orkestratörlere dağıtılırken, `docker-compose` `docker-compose.yml` tanım dosyasına dayalı daha basit ve kullanımı kolay araç yerine geleneksel olarak her orchestrator (diğer bir şekilde Kubernetes ve Hizmet Dokusu farklı dağıtım mekanizmalarına sahiptir) başına belirli dağıtım komut dosyalarını ve mekanizmalarını kullanırsınız. Ancak, Şekil 5-10'da gösterilen Azure DevOps Hizmetleri Docker Dağıtma görevi sayesinde, artık yalnızca tanıdık `docker-compose.yml` dosyanızı kullanarak desteklenen orkestratörlere dağıtabilirsiniz, çünkü `docker-compose.yml` araç sizin için bu "çeviri"yi gerçekleştirir (dosyanızdan orkestratörün ihtiyaç duyduğu biçime kadar).

![Kubernetes'e Dağıt görevini gösteren ekran görüntüsü.](./media/docker-application-outer-loop-devops-workflow/add-deploy-to-kubernetes-task.png)

**Şekil 5-10**. Kubernetes'e Dağıtma görevini Ortamınıza Ekleme

Şekil 5-11, yapılandırma için kullanılabilir bölümlerle Kubernetes'e Dağıt görevini nasıl ayarlayabileceğinizi gösterir. Bu, kümede kapsayıcı olarak dağıtılacak kullanıma hazır özel Docker görüntülerinizi alacak görevdir.

![Kubernetes görev yapılandırmasına Dağıt'ı gösteren ekran görüntüsü.](./media/docker-application-outer-loop-devops-workflow/edit-deploy-to-kubernetes-task.png)

**Şekil 5-11**. ACS DC/OS'ye dağıtım görevi tanımını dağıtan Docker Deploy

> [! BİlGİ: Azure DevOps Hizmetleri ve Docker ile CD boru hattı hakkında daha fazla bilgi için,<https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Adım 5: Çalıştır ın ve yönetin

Uygulamaları işletme-üretim düzeyinde çalıştırmak ve yönetmek başlı başına önemli bir konu olduğundan ve bu düzeyde çalışan operasyonların ve çalışan kişilerin (BT işlemleri) yanı sıra bu alanın geniş kapsamı nedeniyle, bir sonraki bölümün tamamı bunu açıklamaya ayrılmıştır.

## <a name="step-6-monitor-and-diagnose"></a>Adım 6: İzleme ve tanılama

Bu konu, BT'nin üretim sistemlerinde gerçekleştirdiği görevlerin bir parçası olarak bir sonraki bölümde de ele alınmıştır; ancak, bu adımda elde edilen öngörülerin, uygulamanın sürekli olarak geliştirilen şekilde geliştirme ekibine geri beslemesi gerektiğini vurgulamak önemlidir. Bu açıdan bakıldığında, görevler ve işlemler genellikle BT tarafından gerçekleştirilse de, DevOps'lerin de bir parçasıdır.

Sadece izleme ve tanılama DevOps alanı içinde% 100 olduğunda test veya beta ortamlarına karşı geliştirme ekibi tarafından gerçekleştirilen izleme süreçleri ve analitik vardır. Bu, yük testi yaparak veya beta test edicilerin yeni sürümleri denedikleri beta veya QA ortamlarını izleyerek yapılır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
