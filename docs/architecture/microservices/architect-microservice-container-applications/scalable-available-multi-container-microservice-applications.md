---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Kubernetes uygulama yaşam döngüsünü geliştirirken yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok konteyner li uygulamaları ve Azure Dev Spaces olanaklarını düzenleme seçeneklerini keşfedin.
ms.date: 01/30/2020
ms.openlocfilehash: 8a67235109bed806caa7d9caa2bc26fd4fe9daca
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988914"
---
# <a name="orchestrate-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme

Uygulamanız mikro hizmetlere dayanıyorsa veya birden fazla kapsayıcıya bölünmüşse, üretime hazır uygulamalar için orkestratörlerin kullanılması esastır. Daha önce de tanıtılan, mikrohizmet tabanlı bir yaklaşımda, her microservice bir geliştirme ve dağıtım bakış açısından özerk olacak şekilde kendi modeli ve veri sahibi. Ancak birden çok hizmetten (SOA gibi) oluşan daha geleneksel bir uygulamanız olsa bile, dağıtılmış bir sistem olarak dağıtılması gereken tek bir iş uygulamasından oluşan birden çok kapsayıcınız veya hizmetiniz de olacaktır. Bu tür sistemler ölçeklendirmek ve yönetmek için karmaşıktır; bu nedenle, üretime hazır ve ölçeklenebilir çok konteyner uygulaması na sahip olmak istiyorsanız kesinlikle bir orkestratöre ihtiyacınız vardır.

Şekil 4-23, birden çok mikro hizmet (kapsayıcı) oluşan bir uygulama kümesine dağıtım göstermektedir.

![Kümedeki Oluşan Docker uygulamalarını gösteren diyagram.](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Şekil 4-23**. Bir kapsayıcı kümesi

Her hizmet örneği için bir kapsayıcı kullanırsınız. Docker kapsayıcıları "dağıtım birimleri" ve bir kapsayıcı docker örneğidir. Ana bilgisayar birçok kapsayıcıyı işler. Mantıklı bir yaklaşım gibi görünüyor. Ama nasıl yük dengeleme, yönlendirme ve bu bestelenmiş uygulamaları düzenleyen ele alıyormusunuz?

Tek Docker ana bilgisayarlarındaki düz Docker Engine, tek bir ana bilgisayarda tek görüntü örneklerini yönetme gereksinimlerini karşılar, ancak daha karmaşık dağıtılmış uygulamalar için birden fazla ana bilgisayarda dağıtılan birden çok kapsayıcıyı yönetme konusunda yetersiz kalır. Çoğu durumda, kapsayıcıları otomatik olarak başlatacak, kapsayıcıları görüntü başına birden çok örneği olan ölçeklendirecek, askıya alacak veya gerektiğinde kapatacak ve ideal olarak ağ ve veri depolama gibi kaynaklara nasıl erişeceklerini de denetleyecek bir yönetim platformuna ihtiyacınız vardır.

Tek tek kapsayıcıların veya çok basit bestelenmiş uygulamaların yönetiminin ötesine geçmek ve mikro hizmetlerle daha büyük kurumsal uygulamalara yönelmek için, düzenleme ve kümeleme platformlarına yönelmeniz gerekir.

Mimari ve geliştirme açısından, mikro hizmetlere dayalı uygulamalardan oluşan büyük bir kuruluş oluşturuyorsanız, gelişmiş senaryoları destekleyen aşağıdaki platformları ve ürünleri anlamak önemlidir:

**Kümeler ve orkestrasyoncular.** Uygulamaları birçok Docker ana bilgisayararasında ölçeklendirmeniz gerektiğinde, büyük bir mikrohizmet tabanlı uygulamada olduğu gibi, temel platformun karmaşıklığını soyutlayarak tüm bu ana bilgisayarları tek bir küme olarak yönetebilmeniz çok önemlidir. Konteyner kümeleri ve orkestratörleri bunu sağlıyor. Kubernetes bir orkestratör örneğidir ve Azure Kubernetes Hizmeti aracılığıyla Azure'da kullanılabilir.

**Schedulers.** *Zamanlama,* bir yöneticinin kapsayıcıları kümede başlatabilmesi anlamına gelir, böylece aynı zamanda bir ui sağlarlar. Küme zamanlayıcısının çeşitli sorumlulukları vardır: kümenin kaynaklarını verimli bir şekilde kullanmak, kullanıcı tarafından sağlanan kısıtlamaları ayarlamak, düğümler veya ana bilgisayarlar arasında denge kapları verimli bir şekilde yüklemek ve yüksek kullanılabilirlik sağlarken hatalara karşı sağlam olmak.

Küme ve zamanlayıcı kavramları yakından ilişkilidir, bu nedenle farklı satıcılar tarafından sağlanan ürünler genellikle her iki yetenek kümesini de sağlar. Aşağıdaki liste, kümeler ve zamanlayıcılar için sahip olduğunuz en önemli platform ve yazılım seçeneklerini gösterir. Bu orkestratörler genellikle Azure gibi genel bulutlarda sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Konteyner kümeleme, düzenleme ve zamanlama için yazılım platformları

|     |   |
|:---:|---|
| **Kubernetes** <br> ![Kubernetes logosunun bir resmi.](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes,*](https://kubernetes.io/) küme altyapısı ve konteyner planlamasından düzenleme özelliklerine kadar değişen işlevsellik sağlayan açık kaynaklı bir üründür. Uygulama kapsayıcılarının dağıtımını, ölçeklemesini ve işlemlerini ana bilgisayar kümeleri arasında otomatikleştirmenizi sağlar. <br><br> *Kubernetes,* uygulama kapsayıcılarını kolay yönetim ve keşif için mantıksal birimlere gruplandıran konteyner merkezli bir altyapı sağlar. <br><br> *Kubernetes* Linux'ta olgun, Windows'ta daha az olgun. |
| **Azure Kubernetes Hizmeti (AKS)** <br> ![Azure Kubernetes Hizmet logosunun bir görüntüsü.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [AKS,](https://azure.microsoft.com/services/kubernetes-service/) Azure'da Kubernetes kümesinin yönetimini, dağıtımını ve işlemlerini kolaylaştıran yönetilen bir Kubernetes konteyner düzenleme hizmetidir. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Microsoft Azure'da kapsayıcı tabanlı orkestratörleri kullanma

Birçok bulut satıcısı Docker konteyner desteğinin yanı sıra Microsoft Azure, Amazon EC2 Konteyner Hizmeti ve Google Konteyner Motoru da dahil olmak üzere Docker kümeleri ve orkestrasyon desteği sunar. Microsoft Azure, Azure Kubernetes Hizmeti (AKS) aracılığıyla Docker kümesi ve orkestratör desteği sağlar.

## <a name="using-azure-kubernetes-service"></a>Azure Kubernetes Hizmetini Kullanma

Bir Kubernetes kümesi birden çok Docker ana bilgisayarını bir araya getirerek bunları tek bir sanal Docker ana bilgisayar olarak ortaya çıkarır, böylece kümeye birden fazla kapsayıcı dağıtabilir ve istediğiniz sayıda kapsayıcı örneğiyle ölçeklendirebilirsiniz. Küme ölçeklenebilirlik, sağlık ve benzeri gibi tüm karmaşık yönetim sıhhi tesisat ele alacaktır.

AKS, Azure'da kapsayıcı uygulamaları çalıştırmak için önceden yapılandırılmış bir sanal makine kümesinin oluşturulmasını, yapılandırmasını ve yönetimini basitleştirmenin bir yolunu sağlar. Popüler açık kaynak zamanlama ve düzenleme araçlarının optimize edilmiş yapılandırmasını kullanan AKS, Microsoft Azure'da kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için mevcut becerilerinizi kullanmanıza veya büyük ve büyüyen bir topluluk uzmanlığından yararlanmanıza olanak tanır.

Azure Kubernetes Hizmeti, azure için özel olarak popüler Docker kümeleme açık kaynak araçları nın ve teknolojilerinin yapılandırmasını optimize eder. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan açık bir çözüm elabilirsiniz. Boyutu, ana bilgisayar sayısını ve orkestratör araçlarını seçersiniz ve AKS diğer her şeyi işler.

![Bir Kubernetes küme yapısını gösteren diyagram.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Şekil 4-24**. Kubernetes kümesinin basitleştirilmiş yapısı ve topolojisi

Şekil 4-24'te bir Ana düğümün (VM) kümenin koordinasyonunun çoğunu kontrol ettiği bir Kubernetes kümesinin yapısını görebilir ve uygulama açısından tek bir havuz olarak yönetilen ve binlerce hatta on binlerce kapsayıcıya ölçeklendirmenize olanak tanıyan düğümlerin geri kalanına kapsayıcılar dağıtabilirsiniz.

## <a name="development-environment-for-kubernetes"></a>Kubernetes için geliştirme ortamı

Geliştirme [ortamında, Docker Temmuz 2018'de](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) Kubernetes'in sadece [Docker Desktop'ı](https://docs.docker.com/install/)yükleyerek tek bir geliştirme makinesinde (Windows 10 veya macOS) çalıştırabileceğini duyurdu. Daha sonra şekil 4-25'te gösterildiği gibi daha fazla tümleştirme testleri için buluta (AKS) dağıtabilirsiniz.

![Bir dev makinede Kubernetes gösteren diyagram sonra AKS dağıtılan](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Şekil 4-25**. Dev makine ve bulut kubernetes çalışan

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Azure Kubernetes Hizmeti (AKS) ile başlarken

AKS kullanmaya başlamak için, Azure portalından veya CLI'yi kullanarak bir AKS kümesi dağıtırsınız. Azure'da bir Kubernetes kümesini dağıtma hakkında daha fazla bilgi [için](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)bkz.

AKS'nin bir parçası olarak varsayılan olarak yüklenen yazılımların herhangi biri için herhangi bir ücret yoktur. Tüm varsayılan seçenekler açık kaynak yazılımla uygulanır. AKS, Azure'da birden fazla sanal makine için kullanılabilir. Yalnızca seçtiğiniz işlem örneklerinin yanı sıra depolama ve ağ gibi tüketilen diğer temel altyapı kaynakları için ücretlendirilirsiniz. AKS kendisi için artımlı ücret yoktur.

Kubernetes için varsayılan üretim dağıtım seçeneği, bir sonraki bölümde tanıtılan Miğfer grafiklerini kullanmaktır.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Miğfer grafikleri ile Kubernetes kümelerine dağıtın

Bir Uygulamayı Bir Kubernetes kümesine dağıtırken, önceki bölümde belirtildiği gibi, özgün kubectl.exe CLI aracını, önceki bölümde belirtildiği gibi, yerel biçime (.yaml dosyaları) dayalı dağıtım dosyalarını kullanarak kullanabilirsiniz. Ancak, karmaşık mikrohizmet tabanlı uygulamalar dağıtılırken olduğu gibi daha karmaşık Kubernetes uygulamaları [için, Helm](https://helm.sh/)kullanılması önerilir.

Miğfer Grafikleri, en karmaşık Kubernetes uygulamasını bile tanımlamanıza, sürüm kurmanıza, yüklemenize, paylaşmanıza, yükseltmenize veya geri almanıza yardımcı olur.

Daha da ileri giderek, [Azure'daki Azure Dev Alanları](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) gibi ek Kubernetes ortamları da Miğfer grafiklerini temel aldığı için Mik kullanımı önerilir.

Helm, Microsoft, Google, Bitnami ve Helm katılımcısı topluluğu ile işbirliği içinde [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) tarafından sürdürülmektedir.

Miğfer grafikleri ve Kubernetes hakkında daha fazla uygulama bilgisi için, [aks gönderisine eShopOnContainers dağıtmak için Miğfer Şemaları Kullanma'ya](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)) bakın.

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Kubernetes uygulama yaşam döngüsünüz için Azure Geliştirme Alanları'nı kullanın

[Azure Dev Spaces,](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) takımlar için hızlı, yinelemeli Kubernetes geliştirme deneyimi sağlar. Minimum geliştirme makinesi kurulumu ile, doğrudan Azure Kubernetes Service (AKS) içinde yinelemeli olarak kapsayıcıları çalıştırabilir ve kapsayıcıların hatasını ayıklayabilirsiniz. Windows, Mac veya Linux’ta, Visual Studio, Visual Studio Code veya komut satırı gibi bilindik araçları kullanarak geliştirme gerçekleştirin.

Belirtildiği gibi, Azure Dev Spaces kapsayıcı tabanlı uygulamaları dağıtırken Miğfer grafiklerini kullanır.

Azure Dev Spaces, Visual Studio 2019 veya Visual Studio Code'u kullanarak Azure'daki global Kubernetes kümesinde kodu hızla yineleyip hata ayıklamanızı sağladığı ndan, geliştirme ekiplerinin Kubernetes'te daha üretken olmasına yardımcı olur. Azure'daki Kubernetes kümesi paylaşılan yönetilen bir Kubernetes kümesidir, böylece ekibiniz birlikte çalışabilir. Kodunuzu yalıtılmış olarak geliştirebilir, ardından genel kümeye dağıtabilir ve bağımlılıkları çoğaltmadan veya alay etmeden diğer bileşenlerle uç-uç sınama yapabilirsiniz.

Şekil 4-26'da gösterildiği gibi, Azure Dev Spaces'teki en diferansiyel özellik, kümedeki genel dağıtımın geri kalanına entegre çalıştırabilen 'boşluklar' oluşturma yeteneğidir.

![Azure Dev Spaces'te birden çok boşluk kullanımını gösteren diyagram.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Şekil 4-26**. Azure Geliştirme Alanlarında birden çok boşluk kullanma

Temel olarak Azure'da paylaşılan bir geliştirme alanı ayarlayabilirsiniz. Her geliştirici, uygulamanın yalnızca kendisine ayrılan kısmıyla ilgilenebilir ve senaryolarının bağımlı olduğu diğer tüm hizmetleri ve bulut kaynaklarını barındırmakta olan bir geliştirme alanında yinelemeli olarak yürütme öncesi kod geliştirebilir. Bağımlılıklar her zaman günceldir ve geliştiriciler üretimi yansıtan bir şekilde çalışır.

Azure Dev Spaces, göreceli yalıtımda ve ekibinizin çalışmasını bozma korkusu olmadan çalışmanızı sağlayan bir alan konsepti sağlar. Her dev alanı, "üst" ana dev alanından, devam eden iş microservice ile bir microservice (veya çok) geçersiz kılmak için izin veren hiyerarşik bir yapının bir parçasıdır.

Bu özellik URL öneklerine dayanır, bu nedenle url'deki herhangi bir dev alanı önekini kullanırken, dev alanında varsa hedef mikrohizmetten bir istek sunulur, aksi takdirde hiyerarşide bulunan hedef mikrohizmetin ilk örneğine kadar iletilir ve sonunda en üstteki ana dev alanına gider.

Somut bir örnekte pratik bir görünüm elde etmek için [Azure Dev Spaces'teki eShopOnContainers wiki sayfasına](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)bakın.

Daha fazla bilgi için [Azure Dev Spaces ile Takım Geliştirme](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore)makalesini kontrol edin.

## <a name="additional-resources"></a>Ek kaynaklar

- **Azure Kubernetes Hizmeti (AKS) ile başlarken** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Alanları** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** Resmi site. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Önceki](resilient-high-availability-microservices.md)
>[Sonraki](../docker-application-development-process/index.md)
