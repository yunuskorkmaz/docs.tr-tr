---
title: Docker nedir?
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c75b2fa87e5aad93693c76c3bbd135044b36525f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) olan bir [açık kaynaklı proje](https://github.com/docker/docker) uygulamalarının dağıtımını Bulut veya şirket içi çalıştırabilirsiniz taşınabilir, sünece kapsayıcı olarak otomatikleştirmek için (bkz. Şekil 1 - 2). Docker değil de bir [şirket](https://www.docker.com/) yükseltir ve bulut, Linux ve Windows satıcılar, dahil olmak üzere Microsoft ile işbirliğiyle çalışma bu teknolojiyi geliştirir.

![](./media/image2.png)

Şekil 1-2: karma bulut tüm katmanlarını adresindeki kapsayıcıları Docker dağıtır

Docker görüntü kapsayıcıları, Linux ve Windows'da yerel olarak çalıştırabilirsiniz. Ancak, Windows görüntülerini yalnızca Windows konaklarda çalıştırabilirsiniz ve Linux görüntüleri bir konak sunucusu veya bir VM yani yalnızca Linux konaklarda çalıştırabilirsiniz.

Geliştiriciler, geliştirme ortamları Windows, Linux veya macOS kullanabilir. Geliştirme bilgisayarınızda hangi Docker görüntüleri, uygulama ve onun bağımlılıklarını dahil olmak üzere dağıtılan bir Docker ana Geliştirici çalışır. Linux tabanlı olan bir Docker ana bilgisayar Mac veya Linux üzerinde çalışan geliştiricilere kullanmak ve görüntülerini yalnızca Linux kapsayıcı oluşturabilirsiniz. (Mac üzerinde çalışan geliştiricilere kod düzenleme veya Docker komut satırı arabirimini çalıştırmasına \[CLI\] macOS, ancak bu, bu yazma itibariyle, kapsayıcıları doğrudan macOS üzerinde çalıştırmayın.) Windows üzerinde çalışan geliştiriciler, Linux veya Windows kapsayıcıları için görüntülerini oluşturabilirsiniz.

Geliştirme ortamlarında kapsayıcıları barındırmak ve ek geliştirici araçları sağlamak için Docker gelir [Docker Community Edition (CE)](https://www.docker.com/community-edition) macOS veya Windows için. Bu ürünler gerekli VM (kapsayıcıları barındırmak için Docker ana bilgisayarı) yükleyin. Docker de kullanılabilir hale getirir [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), Kurumsal geliştirme için tasarlanmıştır ve yapı BT ekipleri tarafından kullanılan, sevk ve büyük iş açısından kritik uygulamalar üretimde çalıştırın.

Çalıştırmak için [Windows kapsayıcıları](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview), çalışma zamanları iki tür vardır:

-   **Windows Server kapsayıcı** bu çalışma zamanı işlemi ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Bir Windows Server kapsayıcı bir çekirdek ana bilgisayarda çalışan tüm kapsayıcıları ve kapsayıcı ana bilgisayar ile paylaşır.

-   **Hyper-V kapsayıcı** bu her kapsayıcı yüksek oranda iyileştirilmiş bir VM'de çalıştıran Windows Server kapsayıcıları tarafından sağlanan yalıtımı genişletir. Bu yapılandırmada, çekirdek kapsayıcı konağının Hyper-V daha iyi yalıtım sağlayan kapsayıcıları ile paylaşılmaz.

Bu kapsayıcılar görüntülerinin aynı şekilde oluşturulur ve aynı işlevi. Kapsayıcı görüntüden nasıl oluşturulduğunu farktır — bir Hyper-V kapsayıcı çalıştıran ek bir parametre gerektirir. Ayrıntılar için bkz [Hyper-V kapsayıcıları](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-vms"></a>Docker kapsayıcılarını VM'ler ile karşılaştırma

Şekil 1-3 gösterir VM'ler ve Docker arasında bir karşılaştırma kapsayıcıları.

Kapsayıcıları kadar daha az kaynak gerektirdiğinden (örneğin, bunlar tam işletim sisteminde gerekmez), dağıtmak kolay ve Hızlı Başlat. Bu, daha yüksek yoğunluk, böylece maliyetlerini azaltma aynı donanım biriminde daha fazla hizmet çalışabilir anlamına sahip mümkün kılar.

Bir yan aynı çekirdeği üzerinde çalışan sonucu olarak, sanal makineleri daha az yalıtımı elde.

Asıl amacı, görüntüyü, (bağımlılıklar) ortamında aynı farklı dağıtımlar arasında yapmasıdır. Bu, makinenizde hata ayıklama ve ardından garanti ortamıyla başka bir makineye dağıtma anlamına gelir.

Bir kapsayıcı görüntüsü, bir uygulama veya hizmet paketi ve güvenilir ve tekrarlanabilir bir şekilde dağıtmak için bir yoldur. Bu noktada Docker yalnızca bir teknoloji değil, bir felsefesi ve işlem de olabilir.

Docker kullanırken, geliştiriciler söyleyin duyacak değil, "Benim makinede neden üretimde çalıştığını?" Bunlar yalnızca, ", Docker üzerinde çalıştığı" paketlenmiş Docker uygulama tüm desteklenen Docker ortamda çalıştırabilir ve onu tüm dağıtım hedeflerini (hazırlama, üretim, vb. geliştirme, QA.) üzerinde istendiği şekilde çalışır olduğundan söyleyebilirsiniz.

![](./media/image3.png)

Şekil 1-3: Docker kapsayıcıları için geleneksel VM'ler karşılaştırması


>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (docker-terminology.md)
