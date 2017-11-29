---
title: Docker nedir?
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Docker nedir?"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa9cb379628fa91e5dc5b1b529f92db98fa59305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) olan bir [açık kaynaklı proje](https://github.com/docker/docker) uygulamalarının dağıtımını Bulut veya şirket içi çalıştırılabilir taşınabilir, sünece kapsayıcı olarak otomatikleştirmek için. Docker değil de bir [şirket](https://www.docker.com/) yükseltir ve bu teknolojisi geliştikçe. Bulut, Linux ve Windows satıcılar, dahil olmak üzere Microsoft ile işbirliğiyle docker çalışır.

![](./media/image2.png)

**Şekil 2-2**. Karma bulut tüm katmanlarını adresindeki kapsayıcıları docker dağıtır

Docker görüntü kapsayıcıları, Linux ve Windows'da yerel olarak çalıştırın. Yalnızca Windows ana bilgisayarlarında Windows görüntüsünü çalıştırın ve Linux görüntüleri yalnızca Linux ana bilgisayarda çalıştırın. Ana bilgisayar bir sunucu veya bir VM ' dir.

Windows, Linux veya macOS geliştirebilirsiniz. Geliştirme bilgisayar Docker görüntüleri, uygulamayı ve bağımlılıklarını dahil olmak üzere dağıtıldığı bir Docker ana çalıştırır. Linux veya macOS, Linux tabanlı ve Linux kapsayıcıları için yalnızca görüntüleri oluşturmak bir Docker ana bilgisayar kullanın. (MacOS üzerinde kod düzenleme veya Docker CLI çalıştırın, ancak bu yazma tarihinde kapsayıcıları doğrudan macOS üzerinde çalıştırmayın.) Windows'da Linux veya Windows kapsayıcıları için görüntüleri oluşturabilirsiniz.

Windows veya macOS, [Docker Community Edition (CE)](https://www.docker.com/community-edition) barındıran bir geliştirme ortamında kapsayıcıları ve ek geliştirici araçları sağlar. [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) oluşturmak, sevk ve büyük iş açısından kritik uygulamalar çalıştırmak BT ekipleri tarafından kullanılır. ~ Gerekli VM (kapsayıcıları barındırmak için Docker ana bilgisayarı) hem ürünlerini yükleyin. ~ 

[Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) çalışma zamanları iki tür ile çalışabilir:

-   Windows Server kapsayıcıları işlemi ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Bir Windows Server kapsayıcı bir çekirdek ana bilgisayarda çalışan tüm kapsayıcıları ve kapsayıcı ana bilgisayar ile paylaşır.

-   Windows Server kapsayıcıları tarafından her kapsayıcı yüksek oranda iyileştirilmiş bir sanal makinede çalışan tarafından sağlanan yalıtımı Hyper-V kapsayıcıları genişletin. Bu yapılandırmada, çekirdek kapsayıcı konağının Hyper-V daha iyi yalıtım sağlayan kapsayıcıları ile paylaşılmaz. Hyper-V kapsayıcıları izin güvenilmeyen ve *tehlikeli çok kiracılı* uygulamaları aynı ana bilgisayarda çalıştırmak için. Hyper-V kapsayıcıları başlangıç saatleri ve Windows Server kapsayıcıları daha yoğunluğu biraz daha az verimli olması.

Bu kapsayıcılar görüntülerde oluşturulur ve aynı şekilde işlev. Bunlar, kapsayıcı nasıl oluşturulacağını farklılık gösterir. Ayrıntılar için bkz [Hyper-V kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Docker kapsayıcıları sanal makinelerle karşılaştırma

Şekil 2-3 gösterir VM'ler ve Docker arasında bir karşılaştırma kapsayıcıları.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Sanal makineler****Docker kapsayıcıları** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  Sanal makineler, uygulama, gerekli kitaplıkları veya ikili dosyaları ve tam konuk işletim sistemi içerir. Tam sanallaştırma kapsayıcıyla taşıma daha fazla kaynak gerektirir. Kapsayıcılar, uygulama ve onun bağımlılıklarını içerir. Ancak, kapsayıcıları OS çekirdek ile diğer kapsayıcıları paylaşır. Kapsayıcıları kullanıcı alanı yalıtılmış işlemlerde olarak ana bilgisayar işletim sisteminde çalışır. Her kapsayıcı kapsayıcı başına özel bir sanal makine içinde çalıştığı Hyper-V kapsayıcılardaki dışında.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Şekil 2-3**. Docker kapsayıcıları için geleneksel sanal makineler karşılaştırması

Kapsayıcıları kadar daha az kaynak gerektirdiğinden (örneğin, bunlar tam işletim sisteminde gerekmez), Hızlı Başlat ve dağıtmak kolaydır. Düşük kaynak kullanımını daha yüksek yoğunluk sağlar. Daha fazla hizmet aynı donanım biriminde çalıştırabilir ve bu maliyetleri azaltır.

VM'ler sağlamak daha az yalıtım aynı çekirdek sonuçlarında çalışıyor.

Asıl amacı, görüntüyü, (bağımlılıklar) ortamında aynı farklı dağıtımlar arasında yapmasıdır. Bu, makinenizde hata ayıklama ve ardından garanti ortamıyla başka bir makineye dağıtma anlamına gelir.

Bir kapsayıcı görüntüsü, bir uygulama veya hizmet paketi ve güvenilir ve tekrarlanabilir bir şekilde dağıtmak için bir yoldur. Docker yalnızca bir teknoloji ancak aynı zamanda bir felsefesi ve bir işlem olduğunu diyebilirsiniz.

Docker geliştiriciler yok söyleyin, "Benim makinede neden üretimde çalıştığını?" Bunlar söyleyin, ", Docker üzerinde çalıştığı". Docker paketlenmiş uygulamalar tüm desteklenen Docker ortamda çalıştırılabilir. Docker paketlenmiş uygulamalar tutarlı bir şekilde tüm dağıtım hedeflerine (geliştirme, QA, hazırlama, üretim) çalıştırın.

>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (docker-terminology.md)
