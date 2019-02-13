---
title: Microsoft Platformu ve araçları kapsayıcılı uygulamalar için giriş
description: Docker uygulama yaşam döngüsü desteklemek için Microsoft'un teklifleri tanışın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 0e883041624f99d51b49994f02f3a42fc945a96d
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219587"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Microsoft Platformu ve araçları kapsayıcılı uygulamalar için giriş


Şekil 3-1 temel yapı taşları birden çok takımı tarafından (uygulama geliştirme, DevOps altyapı işlemlerini ve BT yönetim ve işlemler) teslim iş türüne göre sınıflandırılmış Docker uygulama yaşam döngüsünü gösterir. Genellikle, kuruluştaki, "kişi" profiller farklı her alan için sorumlu. Bu nedenle becerilerini var.

![](./media/image1.png)

Şekil 3-1: Yaşam döngüsünde Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulamaları için temel yapı taşları

Bir yaşam döngüsü iş akışı başlangıçta öngörücü "varsayılan olarak ürün seçenekleri daha hızlı kullanmaya başlamak, geliştiriciler için kolaylaştıran," temel Docker kapsayıcıya alınmış ancak başlık altında olması gerektiğini bir açık çerçeve olacaktır, böylece temel bir Esnek iş akışı farklı Bağlamlar için her kuruluş ya da enterprise ayarlama yeteneği. (Bileşenlerin ve ürünlerin) iş akışı altyapısı, her şirket, gelecekte bile geliştirme veya diğer ürünleri DevOps değiştirme özelliğine sahip olması gerekir bu ortamda kapsayacak şekilde esnek olması gerekir. Bu esneklik, açıklık ve altyapı ve platform teknolojilerini geniş seçimi tam olarak Microsoft kapsayıcılı Docker uygulamaları için aşağıdaki bölümlerde açıklandığı gibi aralığındadır.

Tablo 3-1 kapsayıcılı Docker uygulamaları için Microsoft DevOps amacınıza her aşamada (Microsoft veya üçüncü taraf) kullanmak için hangi ürünleri seçebilmeniz açık bir DevOps iş akışı sağlamak için basitleştirilmiş bir iş akışı sağlarken olduğunu gösterir. "tarafından varsayılan-ürün" zaten bağlı sağlayan; Bu nedenle, size hızlıca Docker uygulamaları için kurumsal düzeyde DevOps iş akışınızla başlayabilirsiniz.

Tablo 3-1: Herhangi bir teknoloji için DevOps iş akışı Aç

| Ana bilgisayar | Microsoft teknolojileri | Üçüncü taraf: Azure eklenebilir |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker uygulamaları için Platform   | • Microsoft Visual Studio ve Visual Studio Code<br /> • .NET<br /> • Microsoft Azure kapsayıcı hizmeti<br /> • Azure Service Fabric<br /> • Azure kapsayıcı kayıt defteri<br /> | • Herhangi bir kod Düzenleyicisi (örneğin, Sublime)<br /> • Herhangi bir dile (Node.js, Java, Go, vb.)<br /> • Herhangi bir orchestrator ve Zamanlayıcı<br /> • Any Docker registry<br /> |
| Docker uygulamaları için DevOps     | • Azure DevOps Hizmetleri<br /> • Microsoft Team Foundation Server<br /> • Azure kapsayıcı hizmeti<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion, vs.<br /> • Jenkins, Chef, Puppet, hız, CircleCI, Travis CI, vs.<br /> • Şirket içi Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes, vs.<br /> |
| Yönetim ve izleme  | • Operations Management Suite<br /> • Uygulama öngörüleri<br /> | • Marathon, Chronos, vb.<br />

Microsoft Platformu ve kapsayıcılı Docker uygulamaları için Araçlar Tablo 3-1'de tanımlandığı gibi aşağıdaki bileşenler oluşturan:

-   **Docker uygulamaları geliştirme platformu** geliştirmeye yönelik bir hizmet veya bir "uygulamayı oluşturan." Hizmetler koleksiyonu Tüm iş geliştiricilerin gerektirir kodlarını bir paylaşılan kod deposuna göndermeden önce geliştirme platformu sağlar. Kapsayıcıları olarak, Dağıtılmış Geliştirme Hizmetleri, aynı uygulamalar veya hizmetler olmadan Docker geliştirme oldukça benzerdir. Tercih edilen dili (.NET, Node.js, Go, vb.) ve tercih edilen Düzenleyici ya da Visual Studio veya Visual Studio Code gibi IDE kullanmaya devam edersiniz. Ancak, dağıtım hedef Docker göz önünde bulundurun yerine Docker ortamında hizmetlerinizi geliştirin. Yapı, çalıştırın, test ve geliştirme zamanında hedef ortamı sağlayan kapsayıcıları yerel olarak kodunuzda hata ayıklama. Yerel olarak hedef ortam sağlayarak, Docker kapsayıcıları ne önemli ölçüde, DevOps yaşam döngüsü geliştirmenize yardımcı olacak yukarı ayarlayın. Visual Studio ve Visual Studio Code Uzantıları Geliştirme sürecinizin içinde Docker kapsayıcıları tümleştirmek için var.

-   **Docker uygulamaları için DevOps** Docker uygulama oluşturan geliştiricilere, Azure DevOps Hizmetleri ya da başka üçüncü taraf bir ürün, Jenkins gibi kullanabileceğiniz, kapsamlı bir oluşturmak için uygulama yaşam döngüsü yönetimi (ALM) otomatik.

Azure DevOps hizmetleriyle kapsayıcı odaklı geliştiriciler oluşturabilir, kaynak kodu kapsayan hızlı, yinelemeli bir işlem için DevOps denetim her yerden (Azure DevOps Hizmetleri-Gıt, GitHub, herhangi bir uzak Git deposu veya Subversion) sürekli tümleştirme (CI) , iç birim testleri, arası kapsayıcı/hizmet tümleştirme testleri, sürekli teslim (CD) ve sürüm Yönetimi'ni (RM). Geliştiricilerin kendi Docker uygulama sürümlerin içindeki Azure Container Service, geliştirme, hazırlama ve üretim ortamları için de otomatik hale getirebilirsiniz.
 
-   BT üretim yönetim ve izleme.

**Yönetim** BT üretim uygulamalarınızda ve hizmetlerinizde birkaç yolla yönetebilir:

-   **Azure portalında** açık kaynak düzenleyicileri, Azure Container Service (ACS) kullanıyorsanız artı kümesi yönetim araçları gibi Docker Datacenter ve Mesosphere Marathon, ayarlamak ve Docker ortamlarınızı korumak için yardımcı olur. Azure Service Fabric kullanıyorsanız, Service Fabric Explorer aracını, görselleştirin ve kümenizi yapılandırma için mümkün kılar.

-   **Docker Araçları** alışık olduğunuz araçları kullanarak kapsayıcı uygulamalarınızı yönetebilirsiniz. Kapsayıcı iş yüklerini buluta taşımak için mevcut Docker yönetim uygulamalarınızı değiştirmenize gerek yoktur. Alışık olduğunuz ve tercih ettiğiniz orchestrator için standart API uç noktaları aracılığıyla bağlanma uygulama yönetimi araçlarını kullanın. Docker Datacenter veya hatta Docker CLI araçları gibi Docker uygulamalarınızı yönetmek için diğer üçüncü taraf araçları da kullanabilirsiniz.

-   **Açık kaynak Araçları** çünkü ACS düzenleme altyapısı için standart API uç noktalarını kullanıma sunar, en popüler araçların ACS ile uyumludur ve çoğu durumda kullanıma hazır olarak çalışır; görselleştiriciler, izleme, dahil olmak üzere komut satırı araçları ve kullanıma sunuldukça hatta gelecekte kullanıma sunulacak araçlar.

**İzleme** üretim ortamlarında çalışırken, size her açıdan ele aşağıdaki kullanarak izleyebilirsiniz:

-   **Operations Management Suite (OMS)** "OMS kapsayıcı çözümünü" yönetebilir ve kapsayıcılar ve kapsayıcı konağında olduğu hakkında bilgi göstererek Docker ana bilgisayarları ve kapsayıcıları izleme çalışan ya da başarısız, kapsayıcıları ve Docker daemon ve kapsayıcı günlüklerini. Ayrıca CPU, bellek, ağ ve depolama kapsayıcısı ve sorun giderme ve gürültülü komşu kapsayıcıları bulmanıza yardımcı olması için ana bilgisayarları gibi performans ölçümlerini gösterir.

-   **Application Insights** uygulamalardan telemetri verilerini alabilmesi yalnızca kendi SDK hizmetlerinizi içine ayarlayarak üretim Docker uygulamalarını izleyebilirsiniz.

Bu nedenle, Microsoft, bir uçtan uca kapsayıcı Docker uygulaması yaşam döngüsü için tam bir temel sunar. Ancak, *koleksiyonu ürünleri ve isteğe bağlı olarak seçin ve var olan tümleştirme olanak tanıyan teknolojileri, araçları ve işler*. Özelliklerin ayrıntılı gücü ile birlikte geniş bir yaklaşım esneklik, kapsayıcılı Docker uygulama geliştirme için güçlü bir konumda Microsoft yerleştirin.

>[!div class="step-by-step"]
>[Önceki](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[İleri](../design-develop-containerized-apps/index.md)