---
title: Kapsayıcı uygulamaları için Microsoft platformu ve araçlarına giriş
description: Docker uygulamalarının yaşam döngüsünü desteklemek için Microsoft'un tekliflerini tanıyın.
ms.date: 02/15/2019
ms.openlocfilehash: 8cb7870035003e956ee57684a2a2528732849379
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738454"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Kapsayıcı uygulamaları için Microsoft platformu ve araçlarına giriş

*Vizyon: Geliştirme, BT işlemleri ve üretim yönetiminizi kapsayan uyarlanabilir, kurumsal sınıf, kapsayıcı bir uygulama yaşam döngüsü oluşturun.*

Şekil 3-1, birden fazla ekip tarafından sunulan iş türüne (uygulama geliştirme, DevOps altyapı süreçleri ve BT yönetimi ve operasyonları) göre sınıflandırılan Docker uygulamalarının yaşam döngüsündeki ana direkleri gösterir. Genellikle, kuruluşta, her alandan sorumlu "persona" profilleri farklıdır. Yetenekleri de öyle.

:::image type="complex" source="./media/index/microsoft-tools-contanerized-docker-app.png" alt-text="Docker uygulamalarını korumak için gereken Microsoft araçlarını gösteren diyagram.":::
Microsoft araçları. Geliştirme/Tasarım iş yükü için: Windows için Docker motoru, VS ve VS Kodu, .NET Core, Azure Kubernetes Hizmeti. Yapı/Test/Gemi iş yükü için: Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes Hizmeti. Çalıştır/İzle/Yönet iş yükü için: Azure Monitor, Azure Portal Azure Kubernetes Hizmetleri, Hizmet Kumaşı ve diğer orkestratörler.
:::image-end:::

**Şekil 3-1.** Microsoft platformu ve araçları ile konteynerdocker uygulamaları için yaşam döngüsünde ana direkleri

Konteynerleştirilmiş Docker yaşam döngüsü iş akışı başlangıçta "varsayılan ürün seçeneklerine" dayalı olarak önceden yazılabilir ve bu da geliştiricilerin daha hızlı başlamasını kolaylaştırır, ancak kaputun altında her kuruluş veya kuruluştan farklı bağlamlara uyum sağlayabilen esnek bir iş akışı olması için açık bir çerçeve olması temel dir. İş akışı altyapısı (bileşenler ve ürünler), geliştirme veya DevOps ürünlerini başkalarıyla değiştirebilme yeteneğine sahip olsa lar bile, her şirketin gelecekte sahip olacağı ortamı kapsayacak kadar esnek olmalıdır. Bu esneklik, açıklık ve platform ve altyapıdaki geniş teknoloji seçenekleri, takip eden bölümlerde açıklandığı gibi, konteynerleştirilmiş Docker uygulamaları için Microsoft öncelikleridir.

Tablo 3-1, kapsayıcı Docker uygulamaları için Microsoft DevOps'lerin amacının, her aşama için hangi ürünlerin kullanılacağını seçebilmeniz için açık bir DevOps iş akışı sağlamak olduğunu ve "varsayılan olarak bağlı ürünler" sağlayan basitleştirilmiş bir iş akışı sağlamak olduğunu göstermektedir; böylece Docker uygulamaları için kurumsal düzeydeki DevOps iş akışınıza hızla başlayabilirsiniz.

**Tablo 3-1.** DevOps iş akışları, her teknolojiye açık

| Ana bilgisayar | Microsoft teknolojileri | Üçüncü taraf—Azure takılabilir |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker uygulamaları için platform   | • Microsoft Visual Studio ve Visual Studio Kodu<br /> • .NET<br /> • Microsoft Azure Kubernetes Hizmeti (AKS)<br /> • Azure Servis Kumaşı<br /> • Azure Konteyner Kayıt Defteri<br /> | • Herhangi bir kod düzenleyicisi (örneğin, Sublime)<br /> • Herhangi bir dil (Node.js, Java, Go, vb.)<br /> • Herhangi bir orkestratör ve zamanlayıcı<br /> • Herhangi bir Docker kayıt defteri<br /> |
| Docker uygulamaları için DevOps     | • Azure Devops Hizmetleri<br /> • Microsoft Team Foundation Server<br /> • Azure Kubernetes Servisi (AKS)<br /> • Azure Servis Kumaşı<br /> | • GitHub, Git, Subversion, vb.<br /> • Jenkins, Şef, Kukla, Hız, CircleCI, TravisCI, vb.<br /> • Şirket içi Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes, vb.<br /> |
| Yönetim ve izleme  | • Azure Monitör | • Maraton, Chronos, vb.<br />|

Tablo 3-1'de tanımlandığı gibi kapsayıcı Docker uygulamaları için Microsoft platformu ve araçları aşağıdaki bileşenleri içerir:

- **Docker Apps geliştirme platformu** Bir hizmetin geliştirilmesi veya bir "uygulama" oluşturan hizmetlerin toplanması. Geliştirme platformu, geliştiricilerin kodlarını paylaşılan bir kod deposuna itmeden önce ihtiyaç duyduğu tüm işleri sağlar. Kapsayıcı olarak dağıtılan hizmetlerin geliştirilmesi, Docker olmadan aynı uygulamaların veya hizmetlerin geliştirilmesine benzer. Tercih ettiğiniz dili (.NET, Node.js, Go, vb.) ve Visual Studio veya Visual Studio Code gibi tercih edilen editör veya IDE'yi kullanmaya devam emebilirsiniz. Ancak, Docker'ı dağıtım hedefi olarak değerlendirmek yerine, hizmetlerinizi Docker ortamında geliştirirsiniz. Kodunuzu yerel olarak kapsayıcılarda oluşturup çalıştırAr, sınayın ve hata ayıklayarak geliştirme zamanında hedef ortamı sağlarsınız. Docker konteynerleri, varış noktasını yerel olarak sağlayarak DevOps yaşam döngünüzü geliştirmenize büyük ölçüde yardımcı olacak bir ortam kurar. Visual Studio ve Visual Studio Code geliştirme süreciiçinde Docker konteyner entegre uzantıları vardır.

- **Docker Uygulamaları için DevOps** Docker uygulamaları oluşturan geliştiriciler, kapsamlı bir otomatik uygulama yaşam döngüsü yönetimi (ALM) oluşturmak için [Azure DevOps Hizmetlerini](https://azure.microsoft.com/services/devops/) veya Jenkins gibi diğer üçüncü taraf ürünleri kullanabilir.

  Azure DevOps Hizmetleri ile geliştiriciler, kaynak kodu denetimini her yerden (Azure DevOps Services-Git, Git Hub, herhangi bir uzaktan Git deposu veya Subversion), Sürekli Tümleştirme (CI), dahili birim testleri, kapsayıcılar arası/hizmet tümleştirme testleri, Sürekli Teslim (CD) ve sürüm yönetimi (RM) kapsayan hızlı ve yinelemeli bir işlem için kapsayıcı odaklı DevOps oluşturabilir. Geliştiriciler ayrıca Docker uygulama sürümlerini geliştirmeden evreleme ve üretim ortamlarına kadar Azure Kubernetes Hizmeti 'nde (AKS) otomatikleştirebilir.

- **Yönetim ve İzleme** BT, üretim uygulamalarını ve hizmetlerini çeşitli şekillerde yönetebilir ve izleyebilir ve her iki perspektifi de konsolide bir deneyime entegre edebilir.

  - **Azure portalı** Açık kaynak kodlu orkestratörler, Azure Kubernetes Hizmeti (AKS), Service Fabric ve diğer orkestratörler kullanıyorsanız Docker ortamlarınızı kurmanıza ve korumanıza yardımcı olur. Azure Hizmet Kumaşı kullanıyorsanız, Service Fabric Explorer aracı kümenizi görselleştirmenizi ve yapılandırmanızı mümkün kılar.

  - **Docker araçları** Kabı uygulamalarınızı tanıdık araçları kullanarak yönetebilirsiniz. Konteyner iş yüklerini buluta taşımak için mevcut Docker yönetim uygulamalarınızı değiştirmenize gerek yoktur. Zaten aşina olduğunuz uygulama yönetimi araçlarını kullanın ve seçtiğiniz orkestratör için standart API uç noktaları üzerinden bağlanın. Docker Datacenter ve hatta CLI Docker araçları gibi Docker uygulamalarınızı yönetmek için diğer üçüncü taraf araçlarını da kullanabilirsiniz.

    Linux komutlarını biliyor sanız bile, bu Linux Alt Sistemi özelliğiyle çalışan microsoft Windows ve PowerShell'i kullanarak konteyner uygulamalarınızı linux alt sistem komut satırı ve ürünleri (Docker, Kubernetes...) istemcileriyle yönetebilirsiniz. Bu kitapta en sevdiğiniz Microsoft Windows OS'yi kullanarak Linux Alt Sistemi altında bu araçları kullanma hakkında daha fazla bilgi edineceksiniz.

  - **Açık kaynak araçları** AKS orkestrasyon motoru için standart API uç noktalarını ortaya çıkardığı için, en popüler araçlar AKS ile uyumludur ve çoğu durumda, görselleştiriciler, izleme, komut satırı araçları ve hatta gelecekteki araçlar da dahil olmak üzere kutunun dışında çalışır.

  - **Azure Monitör** Azure'un çözüm, üretim ortamınızın her açısını izlemektir. Uygulamalardan sistem tarafından oluşturulan günlük verilerini alabilmeniz için sdk'sını hizmetlerinize kurarak üretim Docker uygulamalarını izleyebilirsiniz.

Böylece, Microsoft uç-to-uç konteyner Docker uygulama yaşam döngüsü için tam bir temel sunuyor. Ancak, *isteğe bağlı olarak mevcut araçları ve süreçleri seçmenize ve bu işlemlerle tümleştirmenize olanak tanıyan bir ürün ve teknoloji koleksiyonu.* Geniş bir yaklaşımdaki esneklik ve yeteneklerin derinliğindeki güç, Microsoft'u konteynerleştirilmiş Docker uygulaması geliştirme için güçlü bir konuma yerleştirilmesidir.

>[!div class="step-by-step"]
>[Önceki](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[Sonraki](../design-develop-containerized-apps/index.md)
