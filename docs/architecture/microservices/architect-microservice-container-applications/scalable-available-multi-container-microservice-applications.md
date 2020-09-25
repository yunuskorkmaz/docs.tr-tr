---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok Kapsayıcılı uygulamaları düzenleme seçeneklerini ve Kubernetes uygulama yaşam döngüsünü geliştirirken Azure Dev Spaces olasılıklarını öğrenin.
ms.date: 01/30/2020
ms.openlocfilehash: a61e883ab0d27300e00b177c2621c6521e85ac84
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172508"
---
# <a name="orchestrate-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme

Uygulamanız mikro hizmetleri temel alıyorsa veya yalnızca birden çok kapsayıcıyı ayırmak için, üretime yönelik uygulamalar için düzenleyiciler kullanmak gereklidir. Daha önce belirtildiği gibi, mikro hizmet tabanlı bir yaklaşımda, her mikro hizmet modelin ve verilerinin sahibi olur, böylece bir geliştirme ve dağıtım noktasından otonom hale gelir. Ancak, birden çok hizmetten (SOA gibi) oluşan daha geleneksel bir uygulamanız olsa da, dağıtılmış bir sistem olarak dağıtılması gereken tek bir iş uygulamasının bulunduğu birden fazla kapsayıcıyla veya hizmete sahip olursunuz. Bu tür sistemler, ölçeği genişletmek ve yönetmek için karmaşıktır; Bu nedenle, üretime hazırlı ve ölçeklenebilir çok kapsayıcılı bir uygulamaya sahip olmak istiyorsanız kesinlikle bir Orchestrator gerekir.

Şekil 4-23, birden fazla mikro hizmetten (kapsayıcılardan) oluşan bir uygulama kümesine dağıtımı gösterir.

![Bir kümede oluşturulan Docker uygulamalarını gösteren diyagram.](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Şekil 4-23**. Kapsayıcılar kümesi

Her hizmet örneği için bir kapsayıcı kullanırsınız. Docker Kapsayıcıları "dağıtım birimleri" ve bir kapsayıcı bir Docker örneğidir. Bir konak birçok kapsayıcıyı işler. Mantıksal bir yaklaşım gibi görünüyor. Ancak yük dengelemeyi nasıl ele alırken, yönlendirirsiniz ve bu oluşturulan uygulamalar nasıl düzenlenir?

Tek Docker konaklarındaki düz Docker altyapısı, tek bir konaktaki tek görüntü örneklerinin yönetilmesi ihtiyaçlarını karşılar, ancak daha karmaşık dağıtılmış uygulamalar için birden fazla konakta dağıtılan birden çok kapsayıcıyı yönetmek için olduğunda kısa sürer. Çoğu durumda, kapsayıcıları otomatik olarak başlatacak bir yönetim platformuna ihtiyacınız vardır, görüntü başına birden çok örnek içeren kapsayıcılar, genişleme kapsayıcıları, gerektiğinde askıya alır veya onları kapatabilir ve ayrıca, ağ ve veri depolama gibi kaynaklara nasıl erişebilecekleri de kontrol edersiniz.

Tek tek kapsayıcıların veya basit oluşturulmuş uygulamaların yönetimini ötesinde ve mikro hizmetlerle daha büyük kurumsal uygulamalarda gezinmek için, düzenleme ve kümeleme platformları ' nı açmanız gerekir.

Bir mimaride ve geliştirme noktasından, mikro hizmet tabanlı uygulamalardan oluşan büyük bir kuruluş oluşturuyorsanız, gelişmiş senaryoları destekleyen aşağıdaki platformların ve ürünlerin anlaşılması önemlidir:

**Kümeler ve düzenleyiciler.** Büyük bir mikro hizmet tabanlı uygulama gibi birçok Docker ana bilgisayarı genelinde uygulama ölçeklendirmeniz gerektiğinde, temel alınan platformun karmaşıklığını soyutlayarak bu konakları tek bir küme olarak yönetebilmek önemlidir. Kapsayıcı kümelerinin ve düzenleyicilerinin sağladığı bu. Kubernetes, bir Orchestrator örneğidir ve Azure Kubernetes hizmeti aracılığıyla Azure 'da kullanılabilir.

**Zamanlayıcılar.** *Zamanlama* , bir yöneticinin, BIR kullanıcı arabirimi sağlamak için bir kümedeki kapsayıcıları başlatma yeteneğinin olması anlamına gelir. Bir küme Zamanlayıcısı çeşitli sorumluluklara sahiptir: kümenin kaynaklarını verimli bir şekilde kullanmak, Kullanıcı tarafından sağlanan kısıtlamaları ayarlamak için, düğümler veya konaklardaki kapsayıcıları etkin bir şekilde dengelemek ve yüksek kullanılabilirlik sağlarken hatalara karşı dayanıklı olması gerekir.

Bir kümenin ve Scheduler 'ın kavramlarıyla ilgili olarak, farklı satıcılar tarafından sunulan ürünlerin çoğu özellik kümesini sağlaması çok benzer. Aşağıdaki listede, kümeler ve zamanlayıcılar için sahip olduğunuz en önemli platform ve yazılım seçimleri gösterilmektedir. Bu düzenleyiciler genellikle Azure gibi genel bulutlarda sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Kapsayıcı Kümelemesi, düzenleme ve zamanlama için yazılım platformları

|     |   |
|:---:|---|
| **Kubernetes** <br> ![Kubernetes logosunun bir görüntüsü.](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) , özellikleri düzenlemek için küme altyapısı ve kapsayıcı zamanlamalarından değişen işlevselliği sağlayan açık kaynaklı bir üründür. Ana bilgisayar kümelerinde uygulama kapsayıcılarının dağıtım, ölçeklendirme ve işlemlerini otomatikleştirmenizi sağlar. <br><br> *Kubernetes* , kolay yönetim ve bulma için uygulama kapsayıcılarını mantıksal birimlere gruplandıran kapsayıcı merkezli bir altyapı sağlar. <br><br> *Kubernetes* , Linux 'Ta, Windows 'da daha az olgun bir yerde. |
| **Azure Kubernetes Service (AKS)** <br> ![Azure Kubernetes hizmet logosunun bir görüntüsü.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [Aks](https://azure.microsoft.com/services/kubernetes-service/) , Azure 'Da Kubernetes kümesinin yönetimini, dağıtımını ve işlemlerini kolaylaştıran yönetilen bir Kubernetes kapsayıcı düzenleme hizmetidir. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Microsoft Azure içinde kapsayıcı tabanlı düzenleyiciler kullanma

Çeşitli bulut satıcıları, Microsoft Azure, Amazon EC2 kapsayıcı hizmeti ve Google Container Engine dahil olmak üzere Docker kapsayıcıları ve düzenleme desteğini sunmaktadır. Microsoft Azure Azure Kubernetes Service (AKS) aracılığıyla Docker kümesi ve Orchestrator desteği sağlar.

## <a name="using-azure-kubernetes-service"></a>Azure Kubernetes hizmetini kullanma

Bir Kubernetes kümesi, birden çok Docker barındırır ve bunları tek bir sanal Docker Konağı olarak kullanıma sunar, böylece kümeye birden çok kapsayıcı dağıtabilir ve istediğiniz sayıda kapsayıcı örneğiyle ölçeği değiştirebilirsiniz. Küme, ölçeklenebilirlik, sağlık ve benzeri tüm karmaşık yönetim sıhhi kileri idare eder.

AKS, Azure 'da Kapsayıcılı uygulamaları çalıştırmak üzere önceden yapılandırılmış bir sanal makine kümesinin oluşturulmasını, yapılandırılmasını ve yönetimini basitleştirmek için bir yol sağlar. Popüler açık kaynak zamanlama ve düzenleme araçlarının iyileştirilmiş bir yapılandırmasını kullanarak, AKS, Microsoft Azure Kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için mevcut becerilerinizi kullanmanıza veya büyük ve büyüyen bir topluluk uzmanlığı üzerine çizmenize olanak sağlar.

Azure Kubernetes hizmeti, popüler Docker Kümelemesi açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure için iyileştirir. Kapsayıcılar ve uygulama yapılandırmanız için taşınabilirlik sağlayan bir açık çözüm alırsınız. Boyut, ana bilgisayar sayısı ve Orchestrator Araçları ' nı seçin ve AKS diğer her şeyi işler.

![Bir Kubernetes küme yapısını gösteren diyagram.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Şekil 4-24**. Kubernetes kümesinin Basitleştirilmiş yapısı ve topolojisi

Şekil 4-24 ' de, ana düğümün (VM) küme koordinasyonundan çoğunu denetlediği bir Kubernetes kümesinin yapısını görebilir ve bir uygulama görünümünden tek bir havuz olarak yönetilen düğümlerin geri kalanına kapsayıcı dağıtabilir ve binlerce kapsayıcının binlerce veya onlarca ölçeğini ölçeklendirmenize izin verebilirsiniz.

## <a name="development-environment-for-kubernetes"></a>Kubernetes için geliştirme ortamı

Geliştirme ortamında, Docker yalnızca [Docker Desktop](https://docs.docker.com/install/)'ı yükleyerek tek bir geliştirme makinesinde (Windows 10 veya MacOS) çalışan Kubernetes [2018 Temmuz 'da duyuruldu](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) . Şekil 4-25 ' de gösterildiği gibi daha sonra daha fazla tümleştirme testi için buluta dağıtabilirsiniz (AKS).

![Bir geliştirme makinesinde Kubernetes 'i gösteren ve daha sonra AKS 'e dağıtılan diyagram](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Şekil 4-25**. Geliştirme makinesi ve bulutu 'nda Kubernetes çalıştırma

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) ile çalışmaya başlama

AKS 'yi kullanmaya başlamak için Azure portal veya CLı kullanarak bir AKS kümesi dağıtırsınız. Azure 'da bir Kubernetes kümesi dağıtma hakkında daha fazla bilgi için bkz. [Azure Kubernetes Service (AKS) kümesi dağıtma](/azure/aks/kubernetes-walkthrough-portal).

Varsayılan olarak AKS 'nin bir parçası olarak yüklenen yazılımların herhangi bir ücreti yoktur. Tüm varsayılan seçenekler açık kaynaklı yazılımlarla uygulanır. AKS, Azure 'da birden çok sanal makine için kullanılabilir. Yalnızca seçtiğiniz işlem örnekleri için ücretlendirilirsiniz, Ayrıca, depolama ve ağ gibi diğer temel altyapı kaynakları kullanılır. AKS 'in kendisi için artımlı ücret alınmaz.

Kubernetes için varsayılan üretim dağıtım seçeneği, sonraki bölümde kullanıma sunulan helk grafiklerini kullanmaktır.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Kubernetes kümelerine helk grafiklerle dağıtım

Bir Kubernetes kümesine bir uygulama dağıttığınızda, önceki bölümde zaten bahsedildiği gibi, yerel biçimi (. YAML dosyaları) temel alınarak dağıtım dosyalarını kullanarak özgün kubectl.exe CLı aracını kullanabilirsiniz. Ancak, karmaşık mikro hizmet tabanlı uygulamalar dağıtımında olduğu gibi daha karmaşık Kubernetes uygulamaları için [Held](https://helm.sh/)kullanılması önerilir.

HELI grafikleri, en karmaşık Kubernetes uygulamasını bile tanımlamanızı, sürüm, yükleme, paylaşma, yükseltme veya geri alma yapmanıza yardımcı olur.

Ayrıca, [Azure dev SPACES](/azure/dev-spaces/azure-dev-spaces) gibi Azure 'Daki ek Kubernetes ortamları da HELI grafiklerini temel alan da, helk kullanımı da önerilir.

HELI, [bulut Yerel Bilgi Işlem altyapısı (CNCF)](https://www.cncf.io/) tarafından korunur. Microsoft, Google, BitNami ve helmkatkıda bulunan topluluğuyla işbirliği yapın.

Helk grafikleri ve Kubernetes hakkında daha fazla uygulama bilgisi için, [AKS gönderisini eShopOnContainers dağıtmak üzere helk grafiklerini kullanma](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)) konusuna bakın.

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Kubernetes uygulama yaşam döngünüz için Azure Dev Spaces kullanın

[Azure dev Spaces](/azure/dev-spaces/azure-dev-spaces) takımlar için hızlı, yinelemeli bir Kubernetes geliştirme deneyimi sağlar. Minimum geliştirme makinesi kurulumu ile, doğrudan Azure Kubernetes Service (AKS) içinde yinelemeli olarak kapsayıcıları çalıştırabilir ve kapsayıcıların hatasını ayıklayabilirsiniz. Windows, Mac veya Linux’ta, Visual Studio, Visual Studio Code veya komut satırı gibi bilindik araçları kullanarak geliştirme gerçekleştirin.

Belirtildiği gibi, kapsayıcı tabanlı uygulamaları dağıtmada Azure Dev Spaces HELI grafiklerini kullanır.

Azure Dev Spaces, Visual Studio 2019 veya Visual Studio Code kullanarak doğrudan Azure 'daki genel bir Kubernetes kümesinde kodu hızla yinelemenize ve hata ayıklamanıza olanak sağladığından geliştirme ekiplerinin Kubernetes üzerinde daha üretken olmasına yardımcı olur. Azure 'daki Kubernetes kümesi paylaşılan bir yönetilen Kubernetes kümesidir ve bu sayede ekibiniz birlikte çalışarak işbirliği yapabilir. Kodunuzu yalıtımlı olarak geliştirebilir, daha sonra genel kümeye dağıtabilir ve bağımlılıkları çoğaltmadan veya mocize etmeden diğer bileşenlerle uçtan uca test gerçekleştirebilirsiniz.

Şekil 4-26 ' de gösterildiği gibi, Azure Dev Spaces en yüksek fark özelliği, kümedeki genel dağıtımın geri kalanı ile tümleştirilen ' Spaces ' oluşturma yeteneğidir.

![Azure Dev Spaces birden çok boşluk kullanımını gösteren diyagram.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Şekil 4-26**. Azure Dev Spaces birden çok boşluk kullanma

Temel olarak Azure 'da paylaşılan bir geliştirme alanı ayarlayabilirsiniz. Her geliştirici, uygulamanın yalnızca kendisine ayrılan kısmıyla ilgilenebilir ve senaryolarının bağımlı olduğu diğer tüm hizmetleri ve bulut kaynaklarını barındırmakta olan bir geliştirme alanında yinelemeli olarak yürütme öncesi kod geliştirebilir. Bağımlılıklar her zaman günceldir ve geliştiriciler üretimi yansıtan bir şekilde çalışır.

Azure Dev Spaces, bir alan kavramı sağlar. Bu, göreli yalıtımda çalışmanıza ve takımınızın çalışmasını bozmadan korku etmenize olanak tanır. Her dev alanı, "en iyi" ana geliştirme alanındaki bir mikro hizmeti (veya daha fazla), kendi süren iş mikro hizmetinizdeki bir mikro hizmeti (veya çok sayıda) geçersiz kılmanızı sağlayan hiyerarşik bir yapının parçasıdır.

Bu özellik URL öneklerini temel alır. bu nedenle, URL 'de herhangi bir geliştirme alanı öneki kullanılırken, istek mikro hizmetinden geliştirme alanında varsa bir istek sunulur, aksi takdirde hiyerarşide bulunan hedef mikro hizmetin ilk örneğine iletilir ve sonunda en üstteki ana geliştirme alanına ulaşırsınız.

Somut bir örnek üzerinde pratik bir görünüm almak için [Azure dev Spaces üzerindeki Eshoponcontainers wiki sayfasına](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)bakın.

Daha fazla bilgi için [Azure dev Spaces Ile takım geliştirme](/azure/dev-spaces/team-development-netcore)makalesini inceleyin.

## <a name="additional-resources"></a>Ek kaynaklar

- **Azure Kubernetes Service (AKS) ile çalışmaya başlama** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** Resmi site. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Önceki](resilient-high-availability-microservices.md) 
> [Sonraki](../docker-application-development-process/index.md)
