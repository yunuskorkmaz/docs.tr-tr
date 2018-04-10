---
title: Microsoft Platformu ve araçları kapsayıcılı uygulamalar için giriş
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a24f57216130a42eb11ef44abe462d4955601fdb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-the-microsoft-platform-and-tools-for-containerized-apps"></a>Microsoft Platformu ve araçları kapsayıcılı uygulamalar için giriş


Şekil 3-1 ana ayaklar birden çok ekibin tarafından (uygulama geliştirme, DevOps altyapı işlemleri ve BT yönetimi ve işlemleri) teslim iş türüne göre sınıflandırılmış Docker uygulamaları yaşam döngüsünü gösterir. Genellikle, kuruluşta, "kişi" profilleri her alan için farklı sorumlu. Bu nedenle yeteneklerini var.

![](./media/image1.png)

Şekil 3-1: ana ayaklar Microsoft Platformu ve araçları kapsayıcılı Docker uygulamalarla yaşam döngüsündeki

A kapsayıcılı yaşam döngüsü iş akışı olabilir başlangıçta Düzenleyici "varsayılan olarak ürün seçimleri daha hızlı başlamak geliştiriciler için kolaylaştıran," temel Docker ancak bu başlık altında olması gerektiğini bir açık çerçeve olacak şekilde, temel bir Esnek iş akışı her bir kuruluş veya Kurumsal farklı bağlamdan ayarlama özelliğine sahip. İş akışı altyapısı (bileşenlerin ve ürünlerin) her şirket gelecekte bile geliştirme veya başkalarına DevOps ürünleri değiştirme yeteneğine sahip olması gerekir bu ortamda kapsayacak şekilde esnek olması gerekir. Bu esneklik, açıklık ve altyapı ve platform teknolojilerinin geniş seçim kapsayıcılı Docker uygulamaları için tam olarak Microsoft öncelikleri izleyen bölümlerde açıklandığı gibi ' dir.

Tablo 3-1 kapsayıcılı Docker uygulamalar için Microsoft DevOps amacı her aşama için (Microsoft veya üçüncü taraf) kullanmak için hangi ürünleri seçebilmeleri açık bir DevOps iş akışı sağlamak için basitleştirilmiş bir iş akışı sağlarken olduğunu gösterir "yan varsayılan-Ürünler" zaten bağlı sağlayan; Bu nedenle, hızlı bir şekilde Docker uygulamalar için kuruluş düzeyi DevOps iş akışını kullanmaya.

Tablo 3-1: açık DevOps iş akışına herhangi teknolojisi

| Ana bilgisayar | Microsoft teknolojileri | Üçüncü taraf — Azure eklenebilir |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker uygulamalar için Platform   | • Microsoft Visual Studio ve Visual Studio Code<br /> • .NET<br /> • Microsoft Azure kapsayıcı hizmeti<br /> • Azure Service Fabric<br /> • Azure kapsayıcı kayıt defteri<br /> | • (Örneğin, Sublime) herhangi bir kod Düzenleyicisi<br /> • Herhangi bir dil (Node.js, Java, Git, vb.)<br /> • Herhangi bir orchestrator ve Zamanlayıcı<br /> • Herhangi Docker kayıt defteri<br /> |
| DevOps Docker uygulamalar için     | • Visual Studio Team Services<br /> • Microsoft Team Foundation Server<br /> • Azure kapsayıcı hizmeti<br /> • Azure Service Fabric<br /> | • GitHub, Git, alt sürüme, vs.<br /> • Jenkins, Chef, Puppet, hız, CircleCI, TravisCI, vs.<br /> • Şirket içi Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes, vs.<br /> |
| Yönetim ve izleme  | • Operations Management Suite<br /> • Uygulamaları Öngörüler<br /> | • Marathon, Chronos, vb.<br />

Microsoft Platformu ve araçları kapsayıcılı Docker uygulamalar için Tablo 3-1'de tanımlandığı gibi aşağıdaki bileşenleri oluşturan:

-   **Docker uygulamaları geliştirme platformu** bir hizmeti veya bir "uygulaması." Hizmetler koleksiyonu geliştirme Tüm iş geliştiriciler gerektirir ve kodunu paylaşılan kod depoya Ftp'den önce geliştirme platformu sağlar. Kapsayıcılar olarak dağıtılan geliştirme hizmetler, aynı uygulamalar veya hizmetler Docker olmadan geliştirilmesi çok benzer. Tercih edilen dili (.NET, Node.js, Git, vb.) ve tercih edilen Düzenleyicisi'ni ya da Visual Studio veya Visual Studio Code gibi IDE kullanmaya devam edersiniz. Ancak, bir dağıtım hedef Docker göz önünde bulundurun yerine hizmetlerinizi Docker ortamında geliştirin. Derleme, çalıştırmak, test ve geliştirme anında hedef ortam sağlama kodunuzu kapsayıcılarında yerel olarak hata ayıklama. Yerel olarak hedef ortam sağlayarak, Docker kapsayıcıları ne büyük ölçüde DevOps yaşam döngüsü geliştirmenize yardımcı olacak yukarı ayarlayın. Visual Studio ve Visual Studio Code geliştirme sürecini Docker kapsayıcılara tümleştirmek için uzantılarına sahip.

-   **Docker uygulamalar için DevOps** Docker uygulamaları oluşturma geliştiricileri Visual Studio Team Services (VSTS) veya herhangi diğer üçüncü taraf ürün, Jenkins gibi kullanabilir, kapsamlı bir yapı için uygulama yaşam döngüsü yönetimi (ALM) otomatik.

VSTS ile geliştiriciler, kaynak kodu kapsayan hızlı ve yinelemeli bir işlem için kapsayıcı odaklı DevOps oluşturabilir yerden (VSTS Git, GitHub, uzak bir Git deposuna veya alt sürüme) sürekli tümleştirme (CI), iç birim testleri denetlemek, ağlar arası kapsayıcı/hizmet tümleştirme testleri, sürekli teslim (CD) ve yayın Yönetimi (RM). Geliştiriciler Ayrıca kendi Docker uygulama sürümlerden Azure kapsayıcı hizmeti içine geliştirme hazırlama ve üretim ortamları için otomatik hale getirebilirsiniz.

-   BT üretim yönetim ve izleme.

**Yönetim** BT üretim uygulamaları ve Hizmetleri birkaç yolla yönetebilir:

-   **Azure portal** açık kaynak orchestrators, Azure kapsayıcı Hizmeti'ni (ACS) kullanmakta olduğunuz artı Docker Datacenter ve Mesosphere Marathon ayarlamak ve Docker ortamınızı sürdürmek için yardımcı gibi kümesi Yönetim Araçları. Azure Service Fabric kullanıyorsanız, Service Fabric Explorer aracını, görselleştirin ve kümenizi yapılandırmak için mümkün kılar.

-   **Docker Araçları** kapsayıcı uygulamalarınızı tanıdık araçlar kullanarak yönetebilirsiniz. Kapsayıcı iş yüklerinin buluta taşımak için varolan Docker yönetim uygulamalarınızı değiştirmenize gerek yoktur. Zaten aşina ve tercih ettiğiniz orchestrator için standart API uç noktaları bağlanma uygulama yönetim araçlarını kullanın. Diğer üçüncü taraf araçları, Docker Datacenter veya hatta CLI Docker araçları gibi Docker uygulamalarınızı yönetmek için de kullanabilirsiniz.

-   **Açık kaynaklı Araçları** çünkü ACS sunan düzenleme altyapısı için standart API uç noktaları, en popüler araçları ACS ile uyumludur ve çoğu durumda, kutudan çıktığı çalışır — görselleştiriciler, izleme de dahil olmak üzere komut satırı araçları ve kullanılabilir olduklarında bile gelecekteki araçları.

**İzleme** üretim ortamlarında çalışırken, her açısı aşağıdaki kullanarak izleyebilirsiniz:

-   **Operations Management Suite (OMS)** "OMS kapsayıcı Çözüm" yönetme ve Docker ana bilgisayarları ve kapsayıcıları kapsayıcıları ve kapsayıcı konakları nerede hakkında bilgi göstererek izleme çalışan ya da başarısız, hangi kapsayıcıları ve Docker arka plan programı ve kapsayıcı günlükleri. Ayrıca, performans ölçümleri CPU, bellek, ağ ve depolama kapsayıcısı ve sorun giderme ve gürültülü komşu kapsayıcıları bulmanıza yardımcı olmak için ana bilgisayarların gibi gösterir.

-   **Application Insights** böylece uygulamalardan telemetri verileri alabilir şekilde kendi SDK hizmetlerinizi içine ayarlayarak üretim Docker uygulamalarını izleyebilirsiniz.

Bu nedenle, Microsoft, bir uçtan uca kapsayıcılı Docker uygulama yaşam döngüsü için tam bir temel sunar. Ancak, *ürünleri ve isteğe bağlı olarak seçin ve var olan tümleştirmenize olanak tanıyan teknolojileri koleksiyonu araçları ve işler*. Geniş bir yaklaşım yetenekleri derinlemesine gücü birlikte esneklik kapsayıcılı Docker uygulama geliştirme için güçlü bir konumda Microsoft yerleştirin.

>[!div class="step-by-step"]
[Önceki] (.. / Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md) [sonraki] (.. /Design-Develop-containerized-Apps/index.MD)
