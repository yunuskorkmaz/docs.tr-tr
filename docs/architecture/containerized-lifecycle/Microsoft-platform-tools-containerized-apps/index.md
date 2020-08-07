---
title: Kapsayıcı uygulamaları için Microsoft platformu ve araçlarına giriş
description: Microsoft 'un Docker uygulamalarının yaşam döngüsünü desteklemeye yönelik tekliflerini öğrenin.
ms.date: 08/06/2020
ms.openlocfilehash: 72b98f945494936b7775a525297a17c5ce72c69a
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916054"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Kapsayıcı uygulamaları için Microsoft platformu ve araçlarına giriş

*Vizyon: geliştirme, BT işlemleri ve üretim yönetiminden yayılan uyarlanabilir tablo, kurumsal düzeyde, kapsayıcılı bir uygulama yaşam döngüsü oluşturun.*

Şekil 3-1, birden fazla ekip tarafından sunulan iş türüne göre sınıflandırılan Docker uygulamalarının yaşam döngüsünde ana pillerini gösterir (uygulama geliştirme, DevOps altyapı işlemleri ve BT yönetimi ve işlemler). Genellikle, kuruluşta, her alandan sorumlu olan "kişi" profilleri farklıdır. Bu nedenle becerileri.

![Visual Studio 'da ASP.NET Core Web uygulaması ' nı seçerek yeni proje penceresi ekleyin.](media/index/microsoft-tools-contanerized-docker-app.png)

**Şekil 3-1.** Microsoft platformu ve araçları ile Kapsayıcılı Docker uygulamalarına yönelik yaşam döngüsünde ana sütunlar

Kapsayıcılı bir Docker yaşam döngüsü iş akışı, başlangıçta "varsayılan ürün seçenekleri" temelinde görünür, ancak geliştiricilerin daha hızlı bir şekilde başlatılmasını kolaylaştırır, ancak açık bir çerçeve olması gerekir, böylece her bir kuruluşun veya kuruluşun farklı bağlamlarına yönelik esnek bir iş akışı olacaktır. İş akışı altyapısının (bileşenler ve ürünler), geliştirme veya DevOps ürünlerini başkalarına değiştirme yeteneğine sahip olacak şekilde, her şirketin gelecekte sahip olacağı ortamı kapsayacak kadar esnek olması gerekir. Bu esneklik, openlik ve teknoloji ve altyapıdaki geniş kapsamlı teknolojiler, izleyen bölümlerde açıklandığı gibi Kapsayıcılı Docker uygulamalarına yönelik Microsoft önceliklerdir.

Tablo 3-1, Kapsayıcılı Docker uygulamaları için Azure DevOps 'un bir açık DevOps iş akışı sağladığını gösterir. böylece, "varsayılan olarak ürünler" zaten bağlı olan basitleştirilmiş bir iş akışı sağlarken her aşamada (Microsoft veya üçüncü taraf) hangi ürünleri kullanacağınızı seçebiliriz. Bu nedenle, Docker uygulamalarına yönelik kurumsal düzeyde DevOps iş akışınızı hızlıca kullanmaya başlayın.

**Tablo 3-1.** Azure DevOps iş akışları, herhangi bir teknolojiye açık

| Konak | Microsoft teknolojileri | Üçüncü taraf (Azure takılabilir) |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker uygulamaları için platform   | • Microsoft Visual Studio ve Visual Studio Code<br /> • .NET<br /> • Kubernetes hizmeti (AKS) Microsoft Azure<br /> • Azure Container Registry<br /> | • Herhangi bir kod Düzenleyicisi (örneğin, alt limon)<br /> • Herhangi bir dil (Node.js, Java, go vb.)<br /> • Herhangi bir Orchestrator ve Scheduler<br />  • Herhangi bir Docker kayıt defteri<br /> |
| Docker uygulamaları için DevOps     | • Azure DevOps Services<br /> • Microsoft Team Foundation Server<br /> • Azure Kubernetes hizmeti (AKS)<br /> | • GitHub, git, alt sürüm, vb.<br /> • Jenkins, Chef, Pupevcil hayvan, hız, CircleCI, Traviscı vb.<br /> • Şirket içi Docker Datacenter, Kubernetes, Mesos DC/OS vb.<br /> |
| Yönetim ve izleme  | • Azure Izleyici | • Marathon, zaman hatası, vb.<br />|

Kapsayıcılı Docker uygulamalarına yönelik Microsoft platformu ve araçları, tablo 3-1 ' de tanımlandığı şekilde aşağıdaki bileşenleri içerir:

- **Docker uygulamaları geliştirme platformu** Bir hizmetin geliştirilmesi veya bir "uygulama" oluşturan hizmet koleksiyonu. Geliştirme platformu, kendi kodlarını paylaşılan bir kod deposuna dağıtmadan önce tüm iş geliştiricilerinin gerekli olmasını sağlar. Kapsayıcılar olarak dağıtılan hizmetlerin geliştirilmesi, Docker olmadan aynı uygulamaların veya hizmetlerin geliştirilmesine benzer. Tercih ettiğiniz dili (.NET, Node.js, Go, vb.) ve tercih edilen düzenleyiciyi veya Visual Studio veya Visual Studio Code gibi IDE 'yi kullanmaya devam edersiniz. Bununla birlikte, bir dağıtım hedefini Docker 'a göz önünde bulundurmanız yerine, hizmetlerinizi Docker ortamında geliştirirsiniz. Hedef ortamı geliştirme zamanında sağlayarak yerel olarak kapsayıcılardaki kodunuzu oluşturur, çalıştırır, test edin ve hatalarını ayıklayın. Hedef ortamı yerel olarak sağlayarak Docker kapsayıcıları, DevOps yaşam döngünüzü iyileştirmenize büyük ölçüde yardımcı olur. Visual Studio ve Visual Studio Code, geliştirme süreciniz dahilinde Docker kapsayıcılarını tümleştirme uzantılarına sahiptir.

- **Docker uygulamaları Için DevOps** Docker uygulamaları oluşturan geliştiriciler, kapsamlı bir otomatik uygulama yaşam döngüsü yönetimi (ALM) oluşturmak için [Azure DevOps](https://azure.microsoft.com/services/devops/) veya Jenkins gibi başka bir üçüncü taraf ürünü kullanabilir.

  Azure DevOps sayesinde geliştiriciler, kaynak kodu denetimini her yerden (Azure DevOps-git, GitHub, herhangi bir uzak Git deposu veya alt sürüm), sürekli tümleştirme (CI), iç birim testleri, kapsayıcı/hizmet tümleştirme testleri, sürekli teslim (CD) ve Release Management (RM) içeren hızlı, yinelemeli bir işlem için kapsayıcı odaklı DevOps oluşturabilir. Geliştiriciler ayrıca, Azure Kubernetes Service (AKS) ile Docker uygulama sürümlerini, geliştirmeden hazırlama ve üretim ortamlarına otomatik hale getirebilir.

- **Yönetim ve izleme** Üretim uygulamalarını ve hizmetlerini çeşitli yollarla yönetebilir ve izleyebilir ve her iki perspektifi birleştirilmiş bir deneyimde tümleştirirler.

  - **Azure Portal**   Azure Kubernetes hizmeti (AKS), Docker ortamlarınızı ayarlamanıza ve bakımını yapmanıza yardımcı olur. Kümenizi görselleştirmek ve yapılandırmak için diğer düzenlemeleri de kullanabilirsiniz.

  - **Docker Araçları**   Tanıdık araçları kullanarak kapsayıcı uygulamalarınızı yönetebilirsiniz. Kapsayıcı iş yüklerini buluta taşımak için mevcut Docker yönetim uygulamalarınızı değiştirmeniz gerekmez. Zaten bildiğiniz uygulama yönetimi araçlarını kullanın ve seçtiğiniz Orchestrator için Standart API uç noktaları aracılığıyla bağlanın. Ayrıca, Docker uygulamalarınızı veya hatta CLı Docker araçlarını yönetmek için diğer üçüncü taraf araçları da kullanabilirsiniz.

    Linux komutlarına alışkın olsanız bile, bu Linux alt sistemi özelliği üzerinde çalışan bir Linux alt sistemi komut satırı ve Products (Docker, Kubernetes...) istemcileri ile Microsoft Windows ve PowerShell 'i kullanarak kapsayıcı uygulamalarınızı yönetebilirsiniz. Bu kitabın devamındaki en sevdiğiniz Microsoft Windows işletim sistemini kullanarak Linux alt sistemi altında bu araçları kullanma hakkında daha fazla bilgi edineceksiniz.

  - **Açık kaynaklı araçlar**   AKS, düzenleme motoru için Standart API uç noktalarını kullanıma sunduğundan, en popüler araçlar AKS ile uyumludur ve çoğu durumda, kullanıma sunulan araçlar, izleme, komut satırı araçları ve hatta gelecek araçlar da dahil olmak üzere bu kutudan çıkar.

  - **Azure izleyici** , Azure 'un üretim ortamınızın her açısını izlemeye yönelik çözümüdür. Uygulamadan sistem tarafından oluşturulan günlük verilerini alabilmeniz için SDK 'sını hizmetlerinize ayarlayarak üretim Docker uygulamalarını izleyebilirsiniz.

Bu nedenle, Microsoft uçtan uca Kapsayıcılı Docker uygulaması yaşam döngüsü için tam bir temel sunar. Ancak, *isteğe bağlı olarak mevcut araçları ve süreçlerini seçip tümleştirmenize olanak tanıyan bir ürün ve teknoloji koleksiyonudur*. Becerinin derinlemesine bir yaklaşımla birlikte, Microsoft 'un Kapsayıcılı Docker uygulama geliştirme için güçlü bir konuma yerleştirilme esnekliği.

>[!div class="step-by-step"]
>[Önceki](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md) 
> [Sonraki](../design-develop-containerized-apps/index.md)
