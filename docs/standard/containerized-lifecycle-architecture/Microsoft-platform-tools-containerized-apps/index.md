---
title: Kapsayıcı uygulamaları için Microsoft platformu ve araçlarına giriş
description: Docker uygulama yaşam döngüsü desteklemek için Microsoft'un teklifleri tanışın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: cdaac06ffd907783c7ebe9b62ecd726158a02484
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664389"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Microsoft Platformu ve araçları kapsayıcılı uygulamalar için giriş

*İşleme: Uyarlanabilir, Kurumsal kapsayıcılı hale sınıf, oluşturma, geliştirme, BT işlemleri ve üretim Yönetimi yayılan bir uygulama yaşam döngüsü.*

Şekil 3-1 temel yapı taşları birden çok takımı tarafından (uygulama geliştirme, DevOps altyapı işlemlerini ve BT yönetim ve işlemler) teslim iş türüne göre sınıflandırılmış Docker uygulama yaşam döngüsünü gösterir. Genellikle, kuruluştaki, "kişi" profiller farklı her alan için sorumlu. Bu nedenle becerilerini var.

![Microsoft araçları. Geliştirme/tasarım iş yükü için: Windows, VS ve VS Code, .NET Core, Azure Kubernetes Service için docker altyapısı. Test/derleme/sevk iş yükü için: Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes hizmeti. İzleyici/Çalıştır/Yönet iş yükü için: Azure İzleyici, Azure portalında Azure Kubernetes hizmeti, Service Fabric, diğer düzenleyiciler.](./media/image1.png)

**Şekil 3-1.** Yaşam döngüsünde Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulamaları için temel yapı taşları

"Varsayılan olarak ürün seçenekleri daha hızlı kullanmaya başlamak, geliştiriciler için kolaylaştıran," temel kapsayıcılı Docker yaşam döngüsü iş akışı başlangıçta öngörücü olabilir ancak başlık altında olması gerektiğini bir açık çerçeve olacaktır, böylece temel bir Esnek iş akışı farklı Bağlamlar için her kuruluş ya da enterprise ayarlama yeteneği. (Bileşenlerin ve ürünlerin) iş akışı altyapısı, her şirket, gelecekte bile geliştirme veya diğer ürünleri DevOps değiştirme özelliğine sahip olması gerekir bu ortamda kapsayacak şekilde esnek olması gerekir. Bu esneklik, açıklık ve altyapı ve platform teknolojilerini geniş seçimi tam olarak Microsoft kapsayıcılı Docker uygulamaları için aşağıdaki bölümlerde açıklandığı gibi aralığındadır.

Tablo 3-1 kapsayıcılı Docker uygulamaları için Microsoft DevOps amacınıza her aşamada (Microsoft veya üçüncü taraf) kullanmak için hangi ürünleri seçebilmeniz açık bir DevOps iş akışı sağlamak için basitleştirilmiş bir iş akışı sağlarken olduğunu gösterir. "tarafından varsayılan-ürün" zaten bağlı sağlayan; Bu nedenle, size hızlıca Docker uygulamaları için kurumsal düzeyde DevOps iş akışınızla başlayabilirsiniz.

**Tablo 3-1.** DevOps iş akışları, herhangi bir teknoloji için Aç

| Ana bilgisayar | Microsoft teknolojileri | Üçüncü taraf: Azure eklenebilir |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker uygulamaları için Platform   | • Microsoft Visual Studio ve Visual Studio Code<br /> • .NET<br /> • Microsoft Azure kapsayıcı hizmeti<br /> • Azure Service Fabric<br /> • Azure kapsayıcı kayıt defteri<br /> | • Herhangi bir kod Düzenleyicisi (örneğin, Sublime)<br /> • Herhangi bir dile (Node.js, Java, Go, vb.)<br /> • Herhangi bir orchestrator ve Zamanlayıcı<br /> • Any Docker registry<br /> |
| Docker uygulamaları için DevOps     | • Azure DevOps Hizmetleri<br /> • Microsoft Team Foundation Server<br /> • Azure kapsayıcı hizmeti<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion, vs.<br /> • Jenkins, Chef, Puppet, hız, CircleCI, Travis CI, vs.<br /> • Şirket içi Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes, vs.<br /> |
| Yönetim ve izleme  | • Azure izleme | • Marathon, Chronos, vb.<br />|

Microsoft Platformu ve kapsayıcılı Docker uygulamaları için Araçlar Tablo 3-1'de tanımlandığı gibi aşağıdaki bileşenler oluşturan:

- **Docker uygulamaları geliştirme platformu** geliştirmeye yönelik bir hizmet veya bir "uygulamayı oluşturan." Hizmetler koleksiyonu Tüm iş geliştiricilerin gerektirir kodlarını bir paylaşılan kod deposuna göndermeden önce geliştirme platformu sağlar. Kapsayıcıları olarak, Dağıtılmış Geliştirme Hizmetleri, aynı uygulamalar veya hizmetler olmadan Docker geliştirme benzerdir. Tercih edilen dili (.NET, Node.js, Go, vb.) ve tercih edilen Düzenleyici ya da Visual Studio veya Visual Studio Code gibi IDE kullanmaya devam edersiniz. Ancak, dağıtım hedef Docker göz önünde bulundurun yerine Docker ortamında hizmetlerinizi geliştirin. Yapı, çalıştırın, test ve geliştirme zamanında hedef ortamı sağlayan kapsayıcıları yerel olarak kodunuzda hata ayıklama. Yerel olarak hedef ortam sağlayarak, Docker kapsayıcıları ne önemli ölçüde, DevOps yaşam döngüsü geliştirmenize yardımcı olacak yukarı ayarlayın. Visual Studio ve Visual Studio Code Uzantıları Geliştirme sürecinizin içinde Docker kapsayıcıları tümleştirmek için var.

- **Docker uygulamaları için DevOps** Docker uygulama oluşturan geliştiricilere kullanabileceğiniz [Azure DevOps Hizmetleri](https://azure.microsoft.com/services/devops/) ya da başka üçüncü taraf bir ürün, bir kapsamlı otomatik uygulama yaşam döngüsü oluşturmak için Jenkins gibi Yönetimi (ALM).

  Azure DevOps hizmetleriyle kapsayıcı odaklı geliştiriciler oluşturabilir, kaynak kodu kapsayan hızlı, yinelemeli bir işlem için DevOps denetim her yerden (Azure DevOps Hizmetleri-Gıt, GitHub, herhangi bir uzak Git deposu veya Subversion) sürekli tümleştirme (CI) , iç birim testleri, arası container/hizmet tümleştirme testleri, sürekli teslim (CD) ve sürüm Yönetimi'ni (RM). Geliştiricilerin kendi Docker uygulama sürümlerin içindeki Azure Container Service, geliştirme, hazırlama ve üretim ortamları için de otomatik hale getirebilirsiniz.

- **Yönetim ve izleme** BT yönetebilir ve üretim uygulamalarınızda ve hizmetlerinizde birleştirilmiş bir deneyim hem açılardan tümleştirme çeşitli şekillerde izleyebilirsiniz.

  - **Azure portalında** açık kaynak düzenleyicileri kullanıyorsanız, Azure Kubernetes Service (AKS), Service Fabric ve diğer düzenleyiciler ayarlamak ve Docker ortamlarınızı korumak için yardımcı. Azure Service Fabric kullanıyorsanız, Service Fabric Explorer aracını, görselleştirin ve kümenizi yapılandırma için mümkün kılar.

  - **Docker Araçları** alışık olduğunuz araçları kullanarak kapsayıcı uygulamalarınızı yönetebilirsiniz. Kapsayıcı iş yüklerini buluta taşımak için mevcut Docker yönetim uygulamalarınızı değiştirmenize gerek yoktur. Alışık olduğunuz ve tercih ettiğiniz orchestrator için standart API uç noktaları aracılığıyla bağlanma uygulama yönetimi araçlarını kullanın. Docker Datacenter veya hatta Docker CLI araçları gibi Docker uygulamalarınızı yönetmek için diğer üçüncü taraf araçları da kullanabilirsiniz. 

    Linux komutları ile tanıdık olsa bile, bir Linux alt komut satırı ve ürünlerle (Docker, Kubernetes...) bu Linux alt özellik üzerinde çalışan istemciler Microsoft Windows ve PowerShell kullanarak kapsayıcı uygulamalarınızı yönetebilirsiniz. Ayrıca, Linux en sevdiğiniz Microsoft Windows işletim bu kitap kullanarak alt altında bu araçları kullanma hakkında daha fazla öğreneceksiniz.

  - **Açık kaynak Araçları** nedeniyle AKS düzenleme altyapısı için standart API uç noktalarını kullanıma sunar, en popüler araçların AKS ile uyumludur ve çoğu durumda kullanıma hazır olarak çalışır; görselleştiriciler, izleme, dahil olmak üzere komut satırı araçları ve kullanıma sunuldukça hatta gelecekte kullanıma sunulacak araçlar.

  - **Azure İzleyici** olan Azure'nın çözüm, üretim ortamınızın her açıdan ele izlemek için. Sistem tarafından oluşturulan günlük verileri uygulamalardan alabilmesi yalnızca kendi SDK hizmetlerinizi içine ayarlayarak üretim Docker uygulamalarını izleyebilirsiniz.

Bu nedenle, Microsoft, bir uçtan uca kapsayıcı Docker uygulaması yaşam döngüsü için tam bir temel sunar. Ancak, *koleksiyonu ürünleri ve isteğe bağlı olarak seçin ve var olan tümleştirme olanak tanıyan teknolojileri, araçları ve işler*. Özelliklerin ayrıntılı gücü ile birlikte geniş bir yaklaşım esneklik, kapsayıcılı Docker uygulama geliştirme için güçlü bir konumda Microsoft yerleştirin.

>[!div class="step-by-step"]
>[Önceki](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[İleri](../design-develop-containerized-apps/index.md)
