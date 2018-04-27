---
title: Docker uygulama için dış döngü DevOps iş akışı adımları
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7a85f42969a3bc1476367203415eb6898641e33a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker uygulama için dış döngü DevOps iş akışı adımları

Şekil 5-1 bir uçtan uca gösterimi DevOps döngü dış iş akışı kapsayan adımları gösterir.

![](./media/image1.png)

Şekil 5-1: DevOps dış döngü Microsoft araçları ile Docker uygulamaları için iş akışı

Şimdi, her bu adımların daha ayrıntılı inceleyelim.

## <a name="step-1-inner-loop-development-workflow"></a>1. adım: İç döngü geliştirme iş akışı

Bu adım ayrıntılı bölüm 4'te açıklandığı ancak olduðunu için İşte burada dış-döngü, hangi geliştirici CI ardışık düzen Eylemler başlatan kodu kaynak denetimi yönetim sistemine (ör. Gıt) iter şu anda başlar.

## <a name="step-2-source-code-control-integration-and-management-with-visual-studio-team-services-and-git"></a>2. adım: Kaynak kodu denetimi tümleştirmesinin ve Visual Studio Team Services ve Git ile Yönetimi

Bu adımda, Ekipteki farklı geliştiriciler'ten gelen tüm kodunun birleştirilmiş bir sürümünü toplamak için bir sürüm denetimi sistemi olması gerekir.

Kaynak kodu denetimi (SCC) ve kaynak kodu Yönetimi ikinci yapısı için çoğu geliştirici, Docker uygulamaları DevOps hayatta oluştururken döngüsü görünebilir olsa bile, uygulama Docker görüntülerle göndermelisiniz değil, vurgulamak için kritik öneme sahiptir doğrudan genel Docker kayıt defterine (gibi Azure kapsayıcı kayıt defteri veya Docker hub'a) Geliştirici makineden. Tersine, serbest ve üretim ortamlarına dağıtılır için Docker görüntüleri yalnızca tümleştirilmiş kaynak kodu üzerinde genel derleme veya kaynak kod deponuza (ör. Gıt) temel CI ardışık oluşturulması gerekir.

Geliştiriciler tarafından oluşturulan yerel görüntüleri, kendi makinelerine içinde test edilirken geliştiriciler tarafından kullanılmalıdır. SCC koddan etkinleştirilmiş DevOps ardışık düzen olması önemlidir nedeni budur.

Visual Studio Team Services ve Team Foundation Server Git ve Team Foundation sürüm denetimi destekler. Aralarında seçin ve bir uçtan uca Microsoft deneyimi için kullanın. Ancak, ayrıca (örneğin, GitHub, şirket içi Git depoları veya alt sürüme) dış depoları kodunuzda yönetebilir ve hala kendisine bağlanıp kodu, DevOps CI ardışık düzeni için başlangıç noktası olarak alın.

## <a name="step-3-build-ci-integrate-and-test-with-visual-studio-team-services-and-docker"></a>3. adım: Derleme, CI, tümleştirme ve Visual Studio Team Services ve Docker ile Test

CI modern yazılım testi ve teslimat için bir standart olarak ortaya çıktı. Docker çözüm geliştirme ve işlemleri ekipleri arasında sorunları açıkça ayrılması tutar. Docker görüntüleri girişi ne geliştirilen CI test ve üretim ortamında çalışması arasında tekrarlanabilir bir dağıtım sağlar. Docker altyapısına Geliştirici dizüstü bilgisayarlar arasında dağıtılır ve test altyapısını kapsayıcıları ortamlar genelinde taşınabilir hale getirir.

Bu noktada, gönderilen doğru koduyla bir sürüm denetim sisteminiz varsa sonra gereken bir *yapı hizmeti* kodu çek ve genel derleme ve testleri çalıştırın.

İç iş akışı (CI, derleme, test) Bu adım için kod deponuza (Git, vb.) yapı sunucunuz (Visual Studio Team Services), Docker altyapısına ve Docker kayıt defteri oluşan bir CI ardışık hakkında bir yapıdır.

Visual Studio Team Services temel olarak uygulamalarınızı geliştirmek ve CI hattınızı ayarlama ve yerleşik "yapıları" yayımlama ", sonraki adımda açıklandığı bir yapıları havuzu" için kullanabilirsiniz.

Docker dağıtımı için "son yapıları" kullanırken dağıtılacak uygulama veya hizmetlerle Docker görüntüleri içine katıştırılır. Bu görüntüleri gönderilen veya yayımlanan bir *Docker kayıt defteri* (Azure kapsayıcı kayıt defterinde sahip olanları veya ortak bir resmi temel görüntüleri için yaygın olarak kullanılan Docker Hub kayıt gibi gibi özel bir depo).

Temel kavramlar şöyledir: CI ardışık düzen başlayacağı zamana dışı SCC deponuza Git gibi bir yürütme tarafından olacaktır. Yürütme Şekil 5-2'de gösterildiği gibi Visual Studio Team Docker kapsayıcısı içinde derleme işi çalıştırmak ve bu iş başarıyla tamamlandıktan sonra Docker görüntü Docker kayıt defterine itme Services neden olur.

![](./media/image2.png)

Şekil 5-2: adımlarını CI'da

Docker ve Visual Studio Team Services ile temel CI iş akışı adımlar şunlardır:

1.  Geliştirici (Git/Visual Studio Team Services, GitHub, vb.) bir SCC depoya bir yürütme iter.

2.  Visual Studio Team Services veya Git kullanıyorsanız, CI bir onay kutusu Visual Studio Team Services içinde işaretlemektir anlamına gelir, oluşturulmuştur. Bir dış SCC (ör. GitHub) kullanıyorsanız, bir *Web kancası* Visual Studio Team Services güncelleştirmesi bildir veya itme Git/GitHub için.

3.  Visual Studio Team Services görüntü ve bunun yanı sıra uygulama ve test kodu açıklayan DockerFile dahil olmak üzere SCC depo çeker.

4.  Visual Studio Team Services Docker görüntüsünü oluşturur ve bir yapı numarası ile etiketler.

5.  Visual Studio Team Services Docker kapsayıcısı içinde sağlanan Docker ana bilgisayar oluşturur ve uygun testleri çalıştırır.

6.  Testleri başarılı olursa, "en derleme" olduğunu bilmesi görüntünün ilk anlamlı bir ad ile relabeled (gibi "/ 1.0.0" veya diğer bir etiketi) ve Docker kayıt (Docker hub'a, Azure kapsayıcı kayıt defteri, DTR, vb.) için gönderilen

### <a name="implementing-the-ci-pipeline-with-visual-studio-team-services-and-the-docker-extension-for-visual-studio-team-services"></a>Visual Studio Team Services için Visual Studio Team Services ve Docker uzantısı ile CI ardışık düzeni uygulama

[Visual Studio Team Services Docker uzantısı](https://aka.ms/vstsdockerextension) CI hattınızı ile Docker görüntüleri oluşturmak, kimliği doğrulanmış bir Docker kayıt defterine Docker görüntüleri itme, Docker görüntüsünü çalıştırın veya için tarafından sunulan diğer işlemlerini çalıştırmak için bir görev ekler Docker CLI. Ayrıca, yapı, bildirme ve multicontainer Docker uygulamaları çalıştırmak veya oluşturma Docker CLI tarafından sunulan diğer işlemleri Şekil 5-3'te gösterildiği gibi çalıştırmak için kullanabileceğiniz bir Docker Compose görev ekler.

![](./media/image3.png)

Şekil 5-3: Docker CI ardışık düzeninde Visual Studio Team Services

Docker uzantısı hizmet uç noktaları ve kapsayıcı veya görüntü kayıt defterleri Docker ana bilgisayarları için kullanabilirsiniz. Görevler varsayılan olarak yerel bir Docker ana varsa (Bu şu anda özel bir Visual Studio Team Services Aracısı gerektirir); Aksi takdirde, bunlar Docker ana bilgisayar bağlantı sağlamanızı gerektirir. Bir görüntü gönderilmesi gibi bir Docker kayıt defteri ile kimlik doğrulaması üzerinde bağlı Eylemler, kayıt defteri bağlantı bir Docker sağlamanızı gerektirir.

Visual Studio Team Services Docker uzantısı Visual Studio Team Services hesabınızı aşağıdaki bileşenleri yükler:

-   Docker kayıt defterine bağlanma için bir hizmet uç noktası

-   Docker kapsayıcısı ana bilgisayara bağlanmak için bir hizmet uç noktası

-   Aşağıdakileri yapmak için bir Docker görevi:

-   Bir görüntü oluşturma

-   Bir görüntüsünü veya bir havuz için bir kayıt defteri itme

-   Görüntüyü bir kapsayıcıda çalıştırın

-   Docker komutunu çalıştırın

-   Docker Compose komutu çalıştırmak için bir Docker Compose görevi

Bu Visual Studio Team Services görevleri, bir derleme Linux Docker ana bilgisayar/VM Azure'da sağlanan ve tercih edilen Docker kaydınız (Azure kapsayıcı kayıt defteri, Docker hub'a, özel Docker DTR veya başka bir Docker kayıt) Docker CI hattınızı toplayabilir bir çok tutarlı bir yol.

***Gereksinimleri:***

-   Visual Studio Team Services veya şirket içi yüklemeleri, Team Foundation Server 2015 güncelleştirme 3 veya sonraki sürümü için.

-   Docker ikili dosyaları sahip bir Visual Studio Team Services Aracısı.

Bunlardan birini oluşturmak için kolay bir yol, Visual Studio Team Services Aracısı Docker görüntüyü temel alarak bir kapsayıcı çalıştırmak için Docker kullanmaktır.

**Daha fazla bilgi** okuyan bir Visual Studio Team Services Docker CI birleştirme hakkında daha fazla kanal ve incelemeleri görüntülemek için aşağıdaki siteleri ziyaret edin:

Docker kapsayıcısı Visual Studio Team Services aracısını çalıştıran: [ https://hub.docker.com/r/\ vsts/microsoft-agent /](https://hub.docker.com/r/microsoft/vsts-agent/)

VSTS Docker uzantısı: <https://aka.ms/vstsdockerextension>

Visual Studio Team Services ile .NET Core Linux Docker görüntülerinizi oluşturmak: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Linux tabanlı Visual Studio Team hizmeti yapı makinesi Docker desteğiyle oluşturma: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Tümleştirme, test ve multicontainer Docker uygulamaları doğrula

Genellikle, çoğu Docker uygulamaları tek bir kapsayıcı yerine birden çok kapsayıcı oluşur. Mikro hizmet başına bir kapsayıcı olurdu mikro odaklı bir uygulama buna iyi bir örnektir. Ancak, hatta kesinlikle mikro yaklaşım desenleri uymadan, Docker uygulamanız birden çok kapsayıcı veya services oluşan, çok olası değil.

Bu nedenle, uygulama kapsayıcıları CI ardışık düzeninde oluşturduktan sonra dağıtma, tümleştirme ve tüm kapsayıcılarında tümleştirme Docker ana bilgisayarı veya bile kapsayıcılarınızı olan bir test kümesinde bir bütün olarak uygulamadan test etmeniz Dağıtılmış.

Tek bir ana bilgisayar kullanıyorsanız, docker gibi Docker komutlarını kullanabilirsiniz-oluşturmak ve sınamak ve tek bir VM'ye Docker ortamında doğrulamak için ilgili kapsayıcıları dağıtmak için oluşturun. Ancak, DC/OS, Kubernetes veya Docker Swarm gibi bir orchestrator küme ile çalışıyorsanız, kapsayıcılarınızı farklı mekanizması veya seçili, küme/Zamanlayıcı bağlı olarak orchestrator üzerinden dağıtmak gerekir.

Docker kapsayıcıları karşı çalıştırabilirsiniz testleri çeşitli türleri şunlardır:

-   Docker kapsayıcıları için birim testleri

-   Birbiriyle ilişkili uygulamalar veya mikro test grupları

-   Üretim ve "canary" sürümlerde test

Tümleştirme ve işlevsel testleri çalıştırırken bu testlerden kapsayıcıların dışında çalıştırmalısınız önemli noktasıdır. Testleri gerekir değil tanımlanabilir ve kapsayıcılar tam olarak üretim ortamına dağıtma olanlar gibi olmalıdır statik görüntü tabanlı olduğundan, dağıttığınız kapsayıcılara çalıştırın.

(Küme, küme hazırlama ve üretim kümesi test) birkaç kümeleri sınama gibi daha Gelişmiş senaryolar sınarken çok uygun bir seçenek görüntüleri çeşitli kümelerde test etmek için bir kayıt defteri yayımlamaktır.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Genel, Docker kayıt defterine özel uygulama Docker görüntüsü bildirme

Docker görüntüleri doğrulandı ve sınanmış sonra etiketi ve Docker kaydınız yayımlama istersiniz. QA ve üretim ortamlarına dağıtılacak özel testinizi (diğer adıyla "en görüntüleri") depoladığınız merkezi konum olduğundan Docker kayıt defteri bir kritik Docker uygulama yaşam döngüsü parçasıdır.

Benzer şekilde nasıl SCC deponuza (Git, vb.) içinde depolanan uygulama kodu, "gerçekte" kaynağıdır, Docker kayıt defteri, "gerçekte" ikili uygulamanızı veya BITS QA veya üretim ortamları için dağıtılması için kaynağıdır.

Genellikle, özel depoları için kendi özel görüntülerinizi ya da özel bir depo Azure kapsayıcı kayıt defteri veya Docker güvenilen kayıt defteri gibi bir şirket içi kayıt defteri veya genel bulut kayıt defteri (gibi kısıtlı erişime sahip olmasını isteyebilirsiniz Docker hub'a), kodunuzu açık kaynak değilse bu son durumda olsa da satıcının güvenlik güvenmesi gerekir. Her iki durumda da, bunu Şekil 5-4'te gösterildiği gibi oldukça benzer ve docker anında iletme komutu, sonuçta göre yöntemidir.

![](./media/image4.png)

Şekil 5-4: Docker kayıt defterine özel resimler yayımlama

Azure kapsayıcı kayıt defteri, Amazon Web Hizmetleri kapsayıcı kayıt defteri, Google kapsayıcı kayıt defteri, Quay kayıt defteri vb. gibi bulut satıcılardan Docker kayıt defterleri, birden çok teklifleri vardır.

Visual Studio Team Services Docker uzantısını kullanarak, Şekil 5-5'te gösterildiği gibi bir hizmet görüntü kimliği doğrulanmış bir Docker kayıt defterine (gibi Azure kapsayıcı kayıt defteri), birden çok etiketlerle bir docker-compose.yml dosyası tarafından tanımlanan kümesi gönderebilir.

![](./media/image5.png)

Şekil 5-5: Docker kayıt defteri yayımlama özel görüntüleri için Visual Studio Team Services kullanma

**Daha fazla bilgi** daha fazla bilgi için Visual Studio Team Services için Docker uzantı hakkında Git <https://aka.ms/vstsdockerextension>. Azure kapsayıcı kayıt hakkında daha fazla bilgi için şuraya gidin <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>4. adım: CD dağıtma

Docker görüntüleri girişi ne geliştirilen CI test ve üretim ortamında çalışması ile tekrarlanabilir bir dağıtım sağlar. Docker kayıt defterinizde (özel veya genel) yayımlanan uygulama Docker görüntüleri oluşturduktan sonra bunları sahip olabileceğiniz çeşitli ortamlar için dağıtabilirsiniz (üretim, QA, hazırlama, vb.) Visual Studio Team Services kullanarak CD düzenindeki Ardışık Düzen görevler veya Visual Studio Team Services yayın yönetimi.

Ancak, bu noktada, dağıttığınız ne tür bir Docker uygulama üzerinde bağlıdır. Basit bir uygulaması (açısından bir oluşturma ve dağıtma) gibi bir tek yapılı birkaç kapsayıcıları veya hizmetleri kapsayan uygulama ve dağıtılan birkaç sunucular veya VM'ler için dağıtma gibi daha karmaşık bir uygulama dağıtımı çok farklı bir mikro odaklı uygulama ölçekte özelliklerine sahip. Bu iki senaryo aşağıdaki bölümlerde açıklanmıştır.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Docker uygulamaları birden çok Docker ortamlara oluşan dağıtma

Az karmaşık senaryo ilk bakalım: Basit Docker veya ana bilgisayar (VM'ler veya sunucular) bir ortamda birden çok ortamları dağıtma (QA hazırlama ve üretim). Bu senaryoda, dahili olarak docker CD hattınızı kullanabilirsiniz-Şekil 5-6'gösterildiği gibi kapsayıcıları veya hizmetlerin, ilgili kümesi ile Docker uygulamaları dağıtmak için (Visual Studio Team Services dağıtım görevlerinizi) oluşturun.

![](./media/image6.png)

Şekil 5-6: Basit Docker ana bilgisayar ortamları kayıt defterine uygulama kapsayıcıları dağıtma

Şekil 5-7 nasıl yapı CI Visual Studio Team Services aracılığıyla QA ve test ortamları için Docker Compose'u Görev Ekle iletişim kutusuna tıklayarak bağlayabileceğiniz vurgular. Ancak, hazırlık veya üretim ortamları için dağıtırken, genellikle birden çok ortamları işleme yayın yönetimi özellikleri kullanırsınız (ister QA hazırlama ve üretim). Tek Docker ana bilgisayarlara dağıtıyorsanız, Visual Studio Team Services kullanıyor "Docker Compose" Görev (docker çağırma-başlık altında komut oluşturma). Azure kapsayıcı hizmeti dağıtıyorsanız, aşağıdaki bölümde açıklandığı gibi Docker dağıtım görev kullanır.

![](./media/image7.png)

Şekil 5-7: Visual Studio Team Services ardışık düzeninde bir Docker Compose görev ekleme

Visual Studio Team Services içinde bir yayın oluşturduğunuzda, giriş yapıları kümesini alır. Bu, birden çok ortamlar genelinde yayın yaşam süresi sabit olacak şekilde tasarlanmıştır. Kapsayıcıları aldığımızda giriş yapıları dağıtmak için bir kayıt defteri görüntülerinde tanımlayın. Nasıl bunlar tanımlanır bağlı olarak, bunlar aynı sürüm, "myimage:latest" docker-compose dosyasından başvurduğunuzda olan en bariz örnek süresi boyunca kalmasına garanti edilmez.

Visual Studio Team Services Docker uzantısı, belirli kayıt defteri görüntü içeren derleme yapıları oluşturma yeteneği özetleyen, ikili aynı görüntü benzersiz şekilde tanımlamak için garanti sağlar. Ne gerçekten yayın giriş olarak kullanmak istediğiniz bunlar.

### <a name="managing-releases-to-docker-environments-by-using-visual-studio-team-services-release-management"></a>Sürümleri Docker ortamlar için Visual Studio Team Services sürüm Yönetimi'ni kullanarak yönetme

Visual Studio Team Services uzantıları yeni bir görüntü oluşturmak, onu bir Docker kayıt defterine yayımlayabilir, Linux veya Windows ana bilgisayarda çalıştırmak ve docker gibi komutları kullanın-birden çok kapsayıcı görsel all through tüm bir uygulamayı olarak dağıtmak için oluşturma Şekil 5-8'de gösterildiği gibi birden çok ortamları için hedeflenen studio Team Services yayın yönetimi yetenekleri.

![](./media/image8.png)

Şekil 5-8: Visual Studio Team Services yayın yönetimi görevleri Visual Studio Team Services Docker Compose yapılandırma

Ancak, Şekil 5-6'da gösterilen ve Şekil 5-8'de uygulanan senaryo (Basit Docker ana bilgisayarları ve sanal makineleri dağıtma ve tek kapsayıcı veya görüntü başına örnek olacaktır) oldukça basittir ve yalnızca geliştirme veya test sc için büyük olasılıkla kullanılması gerektiğini göz önünde bulundurun enarios. Çoğu Kurumsal üretim senaryoda, yüksek kullanılabilirlik (HA) sahip istersiniz ve yönetilmesi kolay ölçeklenebilirlik birden çok düğümleri, sunucuları ve VM'ler artı "Akıllı yerine" Bu nedenle, sunucu ya da düğümü Yük Dengeleme tarafından başarısız, hizmetlerinin ve kapsayıcılar, başka bir ana bilgisayar sunucusu veya VM taşınır. Bu durumda, kapsayıcı kümeleri, orchestrators ve zamanlayıcılar gibi daha gelişmiş teknolojiler gerekir. Bu nedenle, bu kümeler dağıtmak için tam olarak bir sonraki bölümde açıklanan Gelişmiş senaryolar üzerinden yoludur.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Docker kümeleri (DC/OS, Kubernetes ve Docker Swarm) karmaşık Docker uygulamalarını dağıtma

Dağıtılmış uygulamalar yapısını da dağıtılmış işlem kaynaklarını gerektirir. HA havuza alınmış kaynaklara bağlı ve üretim ölçeği yetenekleri sağlamak için yüksek ölçeklenebilirlik sağlamak yetenekleri kümeleme olması gerekir.

Kapsayıcıları el ile bu kümelere Docker Swarm gibi CLI aracından dağıttığınız (kullanarak gibi [docker hizmet oluşturma](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) veya bir web kullanıcı Arabirimi gibi [Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) DC/OS için kümeleri, ancak gerekir Bu, yalnızca punctual dağıtımını test etmek için veya ölçeklendirme veya izleme amacıyla gibi yönetim amacıyla ayırın.

Özellikle, bir CD bakış açısı ve Visual Studio Team Services kapsayıcılı uygulamalarınıza dağıtılmış kümelerde dağıtacağınız, Visual Studio Team Services yayın Yönetimi ortamlarından özel yapılan dağıtım görevlerini çalıştırabilirsiniz Şekil 5-9'da gösterildiği gibi kapsayıcı hizmeti.

![](./media/image9.png)

Şekil 5-9: kapsayıcı hizmeti dağıtılmış uygulama dağıtma

Başlangıçta, belirli kümeleri veya orchestrators dağıtırken, geleneksel belirli dağıtım betikleri ve her orchestrator (diğer bir deyişle, Mesosphere DC/OS veya Docker ve Docker'den farklı dağıtım mekanizmaları Kubernetes başına mekanizmaları kullanır Yerine swarm) daha basit ve kullanımı kolay docker-docker-compose.yml tanımı dosyasına dayalı aracı oluşturun. Ancak, Şekil 5-10'da gösterilen Microsoft Visual Studio Team Services Docker dağıtımı görev sayesinde artık da DC/OS için Microsoft sizin için bu "çeviri" gerçekleştirdiğinden yalnızca bilinen docker-compose.yml dosyası kullanarak dağıtabilirsiniz (gelen, DC/OS tarafından gereken diğer biçimlere docker-compose.yml dosyası).

![](./media/image10.png)

Şekil 5-10: Docker dağıtım görevi, ortam RM ekleme

Şekil 5-11 Docker dağıtma görevi düzenleyin ve hedef türü (Azure kapsayıcı hizmeti DC/OS, bu durumda), Docker oluşturan dosyanızı ve Docker kayıt defteri bağlantısı (örneğin, Azure kapsayıcı kayıt defteri veya Docker hub'a) belirtin nasıl gösterir. Görevin DC/OS kümesine kapsayıcıları olarak dağıtılması için kullanıma hazır özel Docker görüntülerinizi burada alacak budur.

![](./media/image11.png)

Şekil 5-11: Docker dağıtma görev tanımını Azure kapsayıcı hizmeti DC/OS için dağıtma

**Daha fazla bilgi** daha fazla bilgi için Visual Studio Team Services ve Docker CD kanalı hakkında aşağıdaki siteleri ziyaret edin:

Docker ve Azure kapsayıcı hizmeti için Visual Studio Team Services uzantısı: [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Azure kapsayıcı hizmeti: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>5. adım: Çalıştırma ve yönetme

Çalıştıran ve uygulamaları yönetmek için Kurumsal üretim sırasında önemli bir konu ve kendisinin ve işlemleri türü nedeniyle düzeyidir ve bu alanda büyük kapsamını yanı sıra (BT işlemleri) düzeyde çalışan kişilerin, biz tüm sonraki ayrılan Bunu açıklayan için bölüm.

## <a name="step-6-monitor-and-diagnose"></a>6. adım: İzleme ve tanılama

Bu konuda, BT işlemleri gerçekleştirir üretim sistemleri görevleri bir parçası olarak bir sonraki bölümde ayrıca ele alınmıştır; Bununla birlikte, böylece uygulamanın sürekli geliştirilmiş Bu adımda elde edilen Öngörüler Geliştirme ekibine akış gerekir vurgulamak önemlidir. Görevleri ve işlemleri genellikle tarafından gerçekleştirilen rağmen bu açısından bakıldığında, ayrıca DevOps, parçasıdır BT.

Yalnızca izleme ve tanılama DevOps bölge içindeki yüzde 100 olduğunda izleme işlemleri ve test etme veya beta ortamlar karşı geliştirme ekibi tarafından gerçekleştirilen analytics değildir. Bu yük testi gerçekleştirmek veya yalnızca beta veya beta Test edenlere yeni sürümler burada çalıştığınız QA ortamları izleme tarafından gerçekleştirilir.

>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (.. /Run-Manage-Monitor-docker-Environments/index.MD)
