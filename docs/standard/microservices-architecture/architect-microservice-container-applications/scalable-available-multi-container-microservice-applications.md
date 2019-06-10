---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Kubernetes uygulama yaşam döngüsü geliştirirken, mikro hizmetler ve çok kapsayıcılı uygulamalar için yüksek ölçeklenebilirlik ve kullanılabilirlik ve Azure Dev alanları olasılıklarını düzenlemek için seçenekleri keşfedin.
ms.date: 09/20/2018
ms.openlocfilehash: 76fa68cee41f8d1f34ec399c346f457efae57151
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815846"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme

Uygulamanız üzerinde mikro hizmet tabanlı ya da birden çok kapsayıcıda yalnızca bölme düzenleyicileri kullanarak üretime hazır uygulamalar için gereklidir. Böylece bir geliştirme ve dağıtım açısından otonom mikro hizmet tabanlı bir yaklaşım, daha önce tanıtılan her mikro hizmet kendi modeli ve veri sahibi. Ancak oluşan daha geleneksel bir uygulama (SOA gibi) birden çok Hizmetleri olsa da birden çok kapsayıcı veya hizmet dağıtılmış bir sistemde dağıtılması gereken bir tek iş uygulaması oluşturan olursunuz. Ölçeği genişletme ve yönetmek için bu tür sistemler karmaşıktır; Bu nedenle, üretime hazır ve ölçeklenebilir çok kapsayıcılı bir uygulama istiyorsanız kesinlikle bir orchestrator gerekir.

Şekil 4-23 (kapsayıcılar) birden çok mikro hizmetlerden bir uygulama kümesi dağıtmayı gösterir.

![Bir kümede oluşturulmuş Docker uygulamaları: Her bir hizmet örneği için bir kapsayıcı kullanırsınız. Docker kapsayıcıları "dağıtım" birimleridir ve çok sayıda kapsayıcı Docker.A ana bilgisayar örneği işleyen bir kapsayıcıdır](./media/image23.png)

**Şekil 4-23**. Kapsayıcıları kümesi

Mantıksal bir yaklaşım gibi görünüyor. Ancak uygulamaları oluşan işleme Yük Dengeleme, Yönlendirme ve bunlar işlemlerini nasılsın?

Tek bir Docker ana bilgisayarları düz Docker altyapısındaki bir konak üzerinde tek bir görüntü örneklerini yönetme gereksinimlerini karşılayan, ancak daha karmaşık dağıtılmış uygulamaların birden çok konak üzerinde dağıtılan birden çok kapsayıcı yönetmek için söz konusu olduğunda kısa döner. Çoğu durumda, otomatik olarak kapsayıcılar, görüntü başına birden çok örneği ölçeklendirme kapsayıcılarla başlayın, bunları askıya alma veya gerektiğinde Kapat ve ideal olarak ayrıca nasıl veri ve ağ gibi kaynaklara erişim denetimini bir yönetim platformunun gerekir depolama alanı.

Kapsayıcılara veya çok basit oluşturulmuş uygulamalar ve mikro Hizmetleri daha büyük kuruluş uygulamaları doğru taşıma yönetimini ötesine gitmek için düzenleme ve platformları kümeleme için etkinleştirmeniz gerekir.

Mikro hizmet tabanlı uygulamaları, oluşan büyük bir kurumsal oluşturuyorsanız bir mimari ve geliştirme açısından bakıldığında, aşağıdaki platformları ve Gelişmiş senaryolar destekleyen ürünleri anlamak önemlidir:

**Kümeler ve düzenleyiciler.** Büyük bir mikro hizmet tabanlı uygulama, bu konak tarafından temel platform karmaşıklığını özetleyen tek bir küme halinde yönetmek için kritik olduğu gibi birçok Docker konakları arasında uygulamalarının ölçeğini gerektiğinde. Neler kapsayıcı kümeleri ve düzenleyicileri sağlar olmasıdır. Kubernetes orchestrator bir örnektir ve azure'da Azure Kubernetes hizmeti aracılığıyla kullanılabilir.

**Zamanlayıcılar.** *Zamanlama* özelliğine de bir kullanıcı Arabirimi sağlar, böylece bir kümedeki kapsayıcıları başlatmak bir yöneticinin anlamına gelir. Bir küme Zamanlayıcı çeşitli sorumlulukları vardır: küme kaynaklarını verimli bir şekilde kullanmak için verimli bir şekilde düğümleri veya konaklar arasında Yük Dengeleme kapsayıcıları için kullanıcı tarafından sağlanan kısıtlamaları ayarlamak ve yüksek sağlarken hatalarına karşı güçlü Kullanılabilirlik.

Genellikle farklı satıcılar tarafından sağlanan ürün iki yetenekleri sağlamak için bir küme ve bir zamanlayıcı yakından ilişkilidir. Aşağıdaki listede, yazılım seçenek kümeleri ve zamanlayıcılar olması ve en önemli platform gösterir. Bu düzenleyiciler, Azure gibi genel bulutlarda genel kullanıma sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Yazılım platformlarının kümeleme kapsayıcı, düzenleme ve zamanlama için

### <a name="kubernetes"></a>Kubernetes

![Kubernetes logosu](./media/image24.png)

> [*Kubernetes* ](https://kubernetes.io/) küme altyapısı ve kapsayıcı özelliklerini düzenlemek için zamanlama aralıkları işlevselliği sağlayan bir açık kaynaklı üründür. Bu ana bilgisayar kümeleri arasında dağıtım, ölçeklendirme ve uygulama kapsayıcıların işlemlerini otomatikleştirmenizi sağlar.
>
> *Kubernetes* uygulama kapsayıcıları kolay yönetim ve bulma için mantıksal birimler halinde gruplandırır kapsayıcı merkezli bir altyapı sağlar.
>
> *Kubernetes* Linux'ta, Windows daha az olgun olgun olduğu.

### <a name="azure-kubernetes-service-aks"></a>Azure Kubernetes Service'i (AKS)

![Azure Kubernetes hizmeti logosu](./media/image41.png)

> [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) olduğu yönetilen bir Kubernetes kapsayıcı düzenleme hizmeti azure'da Kubernetes küme yönetimi, dağıtımı ve işlemleri basitleştirir.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Microsoft Azure'daki kapsayıcı tabanlı düzenleyicileri kullanarak

Docker kapsayıcıları desteği yanı sıra Docker kümeler ve düzenleme desteği, Microsoft Azure, Amazon EC2 Container Service ve Google Container altyapısı dahil olmak üzere birden fazla bulut satıcılarına sunar. Microsoft Azure desteği aracılığıyla Azure Kubernetes Service (AKS) kümesi ve orchestrator Docker sağlar.

## <a name="using-azure-kubernetes-service"></a>Azure Kubernetes hizmetini kullanarak

Bir Kubernetes kümesi havuzları birden çok Docker konakları ve küme ve herhangi bir sayıda container Instances ile ölçek genişletme birden çok kapsayıcı dağıtmak için bunları bir tek sanal Docker konağı olarak kullanıma sunar. Küme ölçeklenebilirliği, sistem durumu ve benzeri gibi tüm karmaşık yönetim ayarlamaları, işler.

AKS, oluşturma, yapılandırma ve kapsayıcılı uygulamaları çalıştırmak için önceden yapılandırılmış sanal makinelerin azure'da bir küme yönetimi basitleştirmek için bir yol sağlar. Popüler açık kaynak planlama ve düzenleme araçlarının iyileştirilmiş yapılandırmalarını kullanarak AKS mevcut becerilerinizi kullanabilir veya Microsoft azure'daki kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için topluluk uzmanlığından geniş ve büyüyen bir gövdesi üzerinde çizim yapmanızı sağlar .

Azure Kubernetes hizmeti popüler Docker kümeleme açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure'a yönelik en iyi duruma getirir. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz. Boyutu, konak sayısını ve düzenleyici araçlarını seçmeniz ve diğer her şey AKS işler.

![Kubernetes kümesi yapısı: DNS, Zamanlayıcı, proxy vb. işleyen bir ana düğümü ve kapsayıcıları barındıran birden çok çalışan düğümü yoktur.](media/image36.png)

**Şekil 4-24**. Kubernetes küme Basitleştirilmiş yapısı ve topolojisi

Şekil 4-24 burada küme eşgüdümüyle çoğunu bir ana düğüm (VM) denetler ve bir uygulama açısından tek bir havuz olarak yönetilir ve y sağlar düğümler geri kalanı için kapsayıcılar dağıtabilir, bir Kubernetes kümesi yapısını görebilirsiniz binlerce veya on binlerce kapsayıcının ölçeklendirmek için ou'ı tıklatın.

## <a name="development-environment-for-kubernetes"></a>Kubernetes için geliştirme ortamı

Geliştirme ortamındaki [Temmuz 2018'de duyurulan Docker](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) Kubernetes ayrıca bir tek bir geliştirme makinesinde (Windows 10 veya macOS) yalnızca yükleyerek çalışabilen [Docker Masaüstü](https://docs.docker.com/install/). Daha sonra işlenmek üzere buluta (AKS) daha ayrıntılı tümleştirme testleri, 4-25 gösterildiği gibi dağıtabilirsiniz.

![Docker üzerinde Temmuz ' 2018 ile Docker masaüstü geliştirme makine desteği Kubernetes kümeleri için duyurdu.](media/image37.png) 

**Şekil 4-25**. Kubernetes geliştirme makinesi ve bulutta çalışan

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) ile çalışmaya başlama 

AKS'ı kullanmaya başlamak için Azure portalından veya CLI kullanarak bir AKS kümesi dağıtın. Azure'da bir Kubernetes kümesi dağıtma hakkında daha fazla bilgi için bkz. [Azure Kubernetes Service (AKS) kümesini dağıtma](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Herhangi birini varsayılan olarak, AKS bir parçası olarak yüklenen yazılım için herhangi bir ücret yoktur. Tüm varsayılan seçenekleri ile açık kaynaklı yazılım uygulanır. AKS, azure'da birden çok sanal makine için kullanılabilir. Yalnızca seçtiğiniz işlem örnekleri yanı sıra, depolama ve ağ gibi kullanılan temel altyapı kaynakları için ücret ödersiniz. AKS kendisi için artımlı ücretlendirme yoktur.

Kubectl ve özgün .yaml dosyaları daha fazla bağlı Kubernetes dağıtımda uygulama bilgi için posta atın [hizmetine (Azure Kubernetes hizmeti) AKS'de ayarlama](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploying-with-helm-charts-into-kubernetes-clusters"></a>Kubernetes küme halinde ile Helm grafikleri dağıtma

Bir Kubernetes kümesine uygulama dağıtma, dağıtım dosyaları gibi zaten önceki bölümde belirtilen yerel biçimi (.yaml dosyaları), temel kullanarak özgün kubectl.exe CLI aracını kullanabilirsiniz. Ancak, daha karmaşık Kubernetes uygulamaları için gibi karmaşık mikro hizmet tabanlı uygulamaları dağıtırken kullanılacak önerilir [Helm](https://helm.sh/).

Helm grafikleri sürümü, yükleme, paylaşım, yükseltme veya geri alma bile en karmaşık Kubernetes uygulamasını tanımlamanıza yardımcı olur.

Daha fazla devam, Helm kullanımı da önerilir çünkü Azure, ek Kubernetes ortamlarda gibi [Azure geliştirme alanları](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) de Helm grafikleri üzerinde temel alır.

Helm tarafından korunduğu [bulut yerel bilgisayar Foundation (CNCF)](https://www.cncf.io/) - Microsoft, Google, Bitnami ve Helm katkıda bulunan topluluğu ile yaptığı işbirliği.

Daha fazla uygulama için Helm grafikleri ve Kubernetes hakkında bilgi denetimini post [hizmetine AKS'ye dağıtma için Helm grafikleri kullanarak](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Azure geliştirme alanları Kubernetes uygulama yaşam döngünüz için kullanın.

[Azure geliştirme alanları](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) takımlar için hızlı, yinelemeli bir Kubernetes geliştirme deneyimi sağlar. En az bir geliştirme makinesi kuruluma yinelemeli olarak çalıştırın ve doğrudan Azure Kubernetes Service (AKS) kapsayıcıları hata ayıklama. Windows, Mac veya Linux Visual Studio, Visual Studio Code veya komut satırı gibi alışık olduğunuz araçları kullanarak geliştirin.

Belirtildiği gibi Azure geliştirme alanları Helm grafikleri kapsayıcı tabanlı uygulamaları dağıtırken kullanır.

Azure geliştirme alanları geliştirme ekipleri, hızla yineleyin ve yalnızca Visual Studio 2017 veya Visual Studio Code kullanarak azure'da genel bir Kubernetes kümesi doğrudan kodda hata ayıklama izin verdiğinden, Kubernetes üzerinde daha üretken olmanıza yardımcı olur. Azure'da Kubernetes kümesi paylaşılan olduğunu, takımınızın işbirliği içinde birlikte çalışabilmesi için Kubernetes kümesi yönetilen. Yalıtım, kodunuzda geliştirin sonra genel kümeye dağıtın ve uçtan uca çoğaltmak veya bağımlılıkları sahte işlem olmadan diğer bileşenlerle testi gerçekleştirin.

4-26, şekilde gösterildiği gibi en fark Azure geliştirme alanları 'geri kalanı kümedeki genel dağıtımı için tümleşik çalıştırabilirsiniz alanları' oluşturma yeteneği özelliğidir.

![Azure geliştirme alanları, saydam karıştırın ve yeni sürümlerini test etmeye kolaylaştırmak için geliştirme kapsayıcı örneği, üretim mikro hizmetler eşleştirin.](media/image38.png)

**Şekil 4-26**. Azure geliştirme alanlarında birden çok alanları kullanma

Temel bir paylaşılan geliştirme alanında Azure ayarlayabilirsiniz. Her geliştirici yalnızca uygulama kendi parçası üzerinde odaklanın yinelemeli olarak tüm diğer hizmetler içeren bir geliştirme alanında ön işleme kod geliştirme ve bulut kendi senaryoları bağımlı kaynakları. Bağımlılıkları her zaman güncel olduğundan ve geliştiricilerin üretim yansıtan bir şekilde çalışıyoruz.

Azure geliştirme alanları göreli yalıtım ve takımınızın iş bozucu ödemeden olmadan çalışmanıza olanak sağlayan bir alanı kavramını sunar. Her geliştirme alan bir mikro hizmet (ya da birden çok), geçersiz kılmanıza da olanak tanıyan bir hiyerarşik yapının "top" ana geliştirme alanından kendi iş ilerleme-mikro hizmet ile parçasıdır.

Bu özellik temel geliştirme alanında varsa herhangi bir geliştirme alanı önek URL'de kullanırken, bir istek hedef mikro hizmet sunulur için URL ön ekleri üzerinde Aksi takdirde ilk hiyerarşi içinde bulunan hedef mikro hizmet örneğinin kadar iletilir , en üstte ana geliştirme alanına sonunda alınıyor.

Gördüğünüz [hizmetine wiki sayfasında Azure geliştirme alanları](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Using-Azure-Dev-Spaces-and-AKS), somut örneği pratik bir görünüm elde edin.

Daha fazla bilgi için makaleyi kontrol [Azure geliştirme alanları ile takım geliştirme](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Ek kaynaklar

- **Azure Kubernetes Service (AKS) ile çalışmaya başlama** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure geliştirme alanları** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** resmi sitesi. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Önceki](resilient-high-availability-microservices.md)
>[İleri](../docker-application-development-process/index.md)
