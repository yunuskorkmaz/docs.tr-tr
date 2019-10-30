---
title: Kapsayıcı uygulamaları için Microsoft platformu ve araçlarına giriş
description: Microsoft 'un Docker uygulamalarının yaşam döngüsünü desteklemeye yönelik tekliflerini öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 1829ce1051f091065f543a6cadcf5d179a284834
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094463"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Kapsayıcılı uygulamalar için Microsoft platformu ve araçlarına giriş

*Vizyon: geliştirme, BT işlemleri ve üretim yönetiminden yayılan uyarlanabilir tablo, kurumsal düzeyde, kapsayıcılı bir uygulama yaşam döngüsü oluşturun.*

Şekil 3-1, birden fazla ekip tarafından sunulan iş türüne göre sınıflandırılan Docker uygulamalarının yaşam döngüsünde ana pillerini gösterir (uygulama geliştirme, DevOps altyapı işlemleri ve BT yönetimi ve işlemler). Genellikle, kuruluşta, her alandan sorumlu olan "kişi" profilleri farklıdır. Bu nedenle becerileri.

![Microsoft araçları. Geliştirme/tasarım iş yükü: Windows için Docker Engine, VS ve VS Code, .NET Core, Azure Kubernetes hizmeti. Derleme/test/teslim iş yükü için: Azure DevOps, Team Foundation Server, Docker CLı, Azure Kubernetes hizmeti. Çalıştırma/Izleme/yönetme iş yükü: Azure Izleyici, Azure portalı Azure Kubernetes Hizmetleri, Service Fabric, diğer düzenleyiciler.](./media/image1.png)

**Şekil 3-1.** Microsoft platformu ve araçları ile Kapsayıcılı Docker uygulamalarına yönelik yaşam döngüsünde ana sütunlar

Kapsayıcılı bir Docker yaşam döngüsü iş akışı, başlangıçta "varsayılan ürün seçenekleri" temelinde öngörüden yararlanarak geliştiricilerin daha hızlı bir şekilde başlatılmasını kolaylaştırır, ancak bir açık çerçeve olması gerekir, böylece Her bir kuruluştan veya kuruluştan farklı bağlamlara ayarlama yapabilen esnek iş akışı. İş akışı altyapısının (bileşenler ve ürünler), geliştirme veya DevOps ürünlerini başkalarına değiştirme yeteneğine sahip olacak şekilde, her şirketin gelecekte sahip olacağı ortamı kapsayacak kadar esnek olması gerekir. Platform ve altyapıda bu esneklik, openlik ve geniş kapsamlı teknolojiler, izleyen bölümlerde açıklandığı gibi Kapsayıcılı Docker uygulamalarına yönelik Microsoft önceliklerdir.

Tablo 3-1, Kapsayıcılı Docker uygulamaları için Microsoft DevOps 'un, Basitleştirilmiş bir iş akışı sağlarken her aşamada hangi ürünlerin kullanılacağını (Microsoft veya üçüncü taraf) seçebilmeniz için açık bir DevOps iş akışı sağlamaktır. Bu, "varsayılan olarak-ürünler" i zaten bağlı; Bu nedenle, Docker uygulamalarına yönelik kurumsal düzeyde DevOps iş akışınızı hızlıca kullanmaya başlayın.

**Tablo 3-1.** DevOps iş akışları, herhangi bir teknolojiye açık

| Ana bilgisayar | Microsoft teknolojileri | Üçüncü taraf — Azure takılabilir |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker uygulamaları için platform   | • Microsoft Visual Studio ve Visual Studio Code<br /> • .NET<br /> • Kubernetes hizmeti (AKS) Microsoft Azure<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • Herhangi bir kod Düzenleyicisi (örneğin, alt limon)<br /> • Herhangi bir dil (node. js, Java, go vb.)<br /> • Herhangi bir Orchestrator ve Scheduler<br /> • Herhangi bir Docker kayıt defteri<br /> |
| Docker uygulamaları için DevOps     | • Azure DevOps Services<br /> • Microsoft Team Foundation Server<br /> • Azure Kubernetes hizmeti (AKS)<br /> • Azure Service Fabric<br /> | • GitHub, git, alt sürüm, vb.<br /> • Jenkins, Chef, Pupevcil hayvan, hız, CircleCI, Traviscı vb.<br /> • Şirket içi Docker Datacenter, Docker Sısınma, Mesos DC/OS, Kubernetes, vb.<br /> |
| Yönetim ve izleme  | • Azure Izleyici | • Marathon, zaman hatası, vb.<br />|

Kapsayıcılı Docker uygulamalarına yönelik Microsoft platformu ve araçları, tablo 3-1 ' de tanımlandığı şekilde aşağıdaki bileşenleri içerir:

- **Docker uygulamaları geliştirme platformu** Bir hizmetin geliştirilmesi veya bir "uygulama" oluşturan hizmet koleksiyonu. Geliştirme platformu, kendi kodlarını paylaşılan bir kod deposuna dağıtmadan önce tüm iş geliştiricilerinin gerekli olmasını sağlar. Kapsayıcılar olarak dağıtılan hizmetlerin geliştirilmesi, Docker olmadan aynı uygulamaların veya hizmetlerin geliştirilmesine benzer. Tercih ettiğiniz dili (.NET, Node. js, Go, vs.) ve tercih edilen düzenleyiciyi veya Visual Studio veya Visual Studio Code gibi IDE 'yi kullanmaya devam edersiniz. Bununla birlikte, bir dağıtım hedefini Docker 'a göz önünde bulundurmanız yerine, hizmetlerinizi Docker ortamında geliştirirsiniz. Hedef ortamı geliştirme zamanında sağlayarak yerel olarak kapsayıcılardaki kodunuzu oluşturur, çalıştırır, test edin ve hatalarını ayıklayın. Hedef ortamı yerel olarak sağlayarak Docker kapsayıcıları, DevOps yaşam döngünüzü iyileştirmenize büyük ölçüde yardımcı olur. Visual Studio ve Visual Studio Code, geliştirme süreciniz dahilinde Docker kapsayıcılarını tümleştirme uzantılarına sahiptir.

- **Docker uygulamaları Için DevOps** Docker uygulamaları oluşturan geliştiriciler, kapsamlı bir otomatik uygulama yaşam döngüsü yönetimi (ALM) oluşturmak için Jenkins gibi [Azure DevOps Services](https://azure.microsoft.com/services/devops/) veya başka bir üçüncü taraf ürünü kullanabilir.

  Azure DevOps Services, geliştiriciler, kaynak kodu denetimini her yerden (Azure DevOps Services-git, GitHub, herhangi bir uzak Git deposu veya alt sürüm), sürekli tümleştirme (CI) içeren hızlı ve yinelemeli bir işlem için kapsayıcı odaklı DevOps oluşturabilir. , iç birim testleri, kapsayıcı/hizmet tümleştirme testleri, sürekli teslim (CD) ve Release Management (RM). Geliştiriciler ayrıca, Azure Kubernetes Service (AKS) ile Docker uygulama sürümlerini, geliştirmeden hazırlama ve üretim ortamlarına otomatik hale getirebilir.

- **Yönetim ve izleme** Üretim uygulamalarını ve hizmetlerini çeşitli yollarla yönetebilir ve izleyebilir ve her iki perspektifi birleştirilmiş bir deneyimde tümleştirirler.

  - **Azure portal** açık kaynaklı düzenleyiciler kullanıyorsanız, Azure Kubernetes hizmeti (aks), Service Fabric ve diğer düzenleyiciler, Docker ortamlarınızı ayarlamanıza ve bakımını yapmanıza yardımcı olur. Azure Service Fabric kullanıyorsanız, Service Fabric Explorer aracı kümenizi görselleştirmenize ve yapılandırmanıza olanak tanır.

  - **Docker Araçları** , tanıdık araçları kullanarak kapsayıcı uygulamalarınızı yönetebilir . Kapsayıcı iş yüklerini buluta taşımak için mevcut Docker yönetim uygulamalarınızı değiştirmeniz gerekmez. Zaten bildiğiniz uygulama yönetimi araçlarını kullanın ve seçtiğiniz Orchestrator için Standart API uç noktaları aracılığıyla bağlanın. Docker Datacenter veya hatta CLı Docker Araçları gibi Docker uygulamalarınızı yönetmek için diğer üçüncü taraf araçları da kullanabilirsiniz.

    Linux komutlarına alışkın olsanız bile, bu Linux alt sistemi özelliği üzerinde çalışan bir Linux alt sistemi komut satırı ve Products (Docker, Kubernetes...) istemcileri ile Microsoft Windows ve PowerShell 'i kullanarak kapsayıcı uygulamalarınızı yönetebilirsiniz. Bu kitabın devamındaki en sevdiğiniz Microsoft Windows işletim sistemini kullanarak Linux alt sistemi altında bu araçları kullanma hakkında daha fazla bilgi edineceksiniz.

  - **Açık kaynaklı araçlar** , aks, düzenleme ALTYAPıSıNıN Standart API uç noktalarını kullanıma sunduğundan, en popüler araçlar aks ile uyumludur ve çoğu durumda, Görselleştiriciler, izleme, komut satırı araçları dahil olmak üzere kutudan çıkar. ve hatta gelecekteki araçlar kullanılabilir hale gelir.

  - **Azure izleyici** , Azure 'un üretim ortamınızın her açısını izlemeye yönelik çözümüdür. Uygulamadan sistem tarafından oluşturulan günlük verilerini alabilmeniz için SDK 'sını hizmetlerinize ayarlayarak üretim Docker uygulamalarını izleyebilirsiniz.

Bu nedenle, Microsoft uçtan uca Kapsayıcılı Docker uygulaması yaşam döngüsü için tam bir temel sunar. Ancak, *isteğe bağlı olarak mevcut araçları ve süreçlerini seçip tümleştirmenize olanak tanıyan bir ürün ve teknoloji koleksiyonudur*. Becerinin derinlemesine bir yaklaşımla birlikte, Microsoft 'un Kapsayıcılı Docker uygulama geliştirme için güçlü bir konuma yerleştirilme esnekliği.

>[!div class="step-by-step"]
>[Önceki](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[İleri](../design-develop-containerized-apps/index.md)
