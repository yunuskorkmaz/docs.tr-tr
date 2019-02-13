---
title: Docker nedir?
description: Docker'ın Anlayışınızı içinde daha ayrıntılı alın, burada basit benzerleme yardımcı olabilir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: c8300c964dfce0cc8e39478cc10ed7589dbca2c9
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218560"
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) olduğu bir [açık kaynaklı proje](https://github.com/docker/docker) bulutta veya şirket içinde çalışan taşınabilir, kendi kendine yeterli kapsayıcı uygulamalarının dağıtımını otomatikleştirmek için (bkz: Şekil 1 - 2). Docker, ayrıca bir [şirket](https://www.docker.com/) yükseltir ve bulut, Linux ve Windows sağlayıcılar dahil olmak üzere Microsoft ile işbirliği içinde çalışan bu teknolojiyi geliştirir.

![](./media/image2.png)

Şekil 1-2: Docker kapsayıcıları tüm katmanlarda karma bulutun dağıtır.

Docker görüntüsü kapsayıcılar, Linux ve Windows üzerinde yerel olarak çalıştırabilirsiniz. Ancak, Windows görüntülerini yalnızca Windows konaklarda çalışabilir ve Linux görüntüleri, bir konak sunucusu veya bir VM yani yalnızca Linux konaklarda çalışabilir.

Geliştiriciler, Windows, Linux veya macOS geliştirme ortamları kullanabilirsiniz. Geliştirme bilgisayarında geliştirici için hangi Docker görüntüleri, uygulamayı ve bağımlılıkları da dahil olmak üzere dağıtılan bir Docker konağı olarak çalışır. Linux veya Mac üzerinde çalışan geliştiriciler, Linux tabanlı bir Docker konağı kullanın ve bunlar görüntülerini yalnızca Linux kapsayıcıları oluşturabilirsiniz. (Mac üzerinde çalışan geliştiriciler kodu düzenleyebilir ya da Docker komut satırı arabirimini \[CLI\] macOS, ancak, şu andan itibaren kapsayıcıları doğrudan macOS üzerinde çalıştırmayın.) Windows üzerinde çalışan geliştiriciler, Linux veya Windows kapsayıcıları için görüntü oluşturabilirsiniz.

Docker kapsayıcıları geliştirme ortamlarında barındırmak ve diğer geliştirici araçlarını sağlamak için gelen [Docker Community Edition'ı (CE)](https://www.docker.com/community-edition) macOS veya Windows için. Bu ürünler gerekli VM (ana kapsayıcı barındırmak için Docker) yükleyin. Docker da kullanımınıza [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), Kurumsal geliştirme için tasarlanan ve yapı BT ekipleri tarafından kullanılan, gönderin ve büyük iş açısından kritik uygulamalar üretimde çalışır.

Çalıştırılacak [Windows kapsayıcıları](/virtualization/windowscontainers/about/), çalışma zamanları iki tür vardır:

-   **Windows Server kapsayıcı** bu çalışma zamanı işlemi ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Bir Windows Server kapsayıcı bir çekirdek ana bilgisayarda çalışan tüm kapsayıcılar ve kapsayıcı konağı ile paylaşır.

-   **Hyper-V kapsayıcı** bu her kapsayıcı yüksek oranda iyileştirilmiş bir VM'de çalıştıran Windows Server kapsayıcıları tarafından sağlanan yalıtımı genişletir. Bu yapılandırmada, daha iyi yalıtım sağlayan Hyper-V kapsayıcıları ile kapsayıcı konağı çekirdeğini paylaşılmıyor.

Bu kapsayıcılar için görüntüler ve aynı işlevi aynı şekilde oluşturulur. Kapsayıcı görüntüsünü nasıl oluşturulduğunu fark — bir Hyper-V kapsayıcı çalıştırma, ek bir parametresi gerektirir. Ayrıntılar için bkz [Hyper-V kapsayıcıları](/virtualization/windowscontainers/about/).

## <a name="comparing-docker-containers-with-vms"></a>Docker kapsayıcıları Vm'leri ile karşılaştırma

Şekil 1-3 gösterir bir karşılaştırmasını VM'ler ve Docker kapsayıcıları.

Kapsayıcılar çok daha az kaynak gerektirdiğinden (örneğin, bunlar tam bir işletim sistemi gerekmez), bunlar kolayca ve Hızlı Başlat. Bu, böylece maliyetleri azaltırken aynı donanım biriminde daha fazla hizmet çalıştırabileceğiniz anlamına gelir, yüksek yoğunluklu olmasını mümkün kılar.

Bir yan aynı çekirdeği üzerinde çalıştırma etkisi, Vm'lere göre daha az Yalıtımın elde edin.

Asıl amacı, görüntü, ortamın (bağımlılıklar) aynı farklı dağıtımlar arasında yapmasıdır. Bu, makinenizde hata ayıklayın ve ardından garanti ortamıyla başka bir makineye dağıtma anlamına gelir.

Bir kapsayıcı görüntüsü, bir uygulama veya hizmet paketini ve güvenilir ve tekrarlanabilir bir şekilde dağıtmak için bir yoldur. Bu bakımdan, Docker, yalnızca bir teknoloji değil, bir felsefesi ve bir işlem de uygulanır.

Docker'ı kullanırken, geliştiricilerin söyleyin duyacak değil, "Benim makinemde neden üretimde çalışır?" Bunlar yalnızca, "Docker'ın üzerinde çalıştığı" çünkü paket Docker uygulama desteklenen bir Docker ortamında çalıştırabilirsiniz ve onu tüm dağıtım hedeflerine (hazırlama, üretim, vs. Dev, QA.) istendiği şekilde çalışacaktır söyleyebilirsiniz.

![](./media/image3.png)

Şekil 1-3: Docker kapsayıcıları için geleneksel VM'lerin karşılaştırması

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](docker-terminology.md)
