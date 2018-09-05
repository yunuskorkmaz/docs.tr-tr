---
title: Docker nedir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker nedir?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 36a153ca636adbfe7a335d71cc1baef4e213f4c9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534695"
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) olduğu bir [açık kaynaklı proje](https://github.com/docker/docker) Bulut veya şirket içinde çalışan taşınabilir, kendi kendine yeterli kapsayıcı uygulamalarının dağıtımını otomatikleştirmek için. Docker, ayrıca bir [şirket](https://www.docker.com/) yükseltir ve bu teknoloji geliştikçe. Docker, bulut, Linux ve Windows sağlayıcılar dahil olmak üzere Microsoft ile işbirliği içinde çalışır.

![](./media/image2.png)

**Şekil 2-2**. Docker kapsayıcıları tüm katmanlarda karma bulutun dağıtır.

Docker görüntüsü kapsayıcılar, Linux ve Windows üzerinde yerel olarak çalıştırın. Windows konaklarda Windows görüntülerini çalıştırmak ve yalnızca Linux ana bilgisayarlarında Linux görüntüleri çalıştırın. Bir sunucu veya bir sanal ana bilgisayardır.

Windows, Linux veya Macos'ta geliştirebilirsiniz. Geliştirme bilgisayarında, Docker görüntülerini, uygulamayı ve bağımlılıklarını dağıtıldığı bir Docker konağı çalıştırır. Linux veya macOS, Linux tabanlı ve Linux kapsayıcı görüntülerini yalnızca oluşturabilmeniz için bir Docker konağı kullanın. (MacOS üzerinde kod düzenleyin veya Docker CLI'yı çalıştırın, ancak bu makalenin yazıldığı zaman itibariyle, kapsayıcılar, doğrudan macOS üzerinde çalıştırmayın.) Windows üzerinde Linux veya Windows kapsayıcıları için görüntü oluşturabilirsiniz.

Windows veya macOS, [Docker Community Edition'ı (CE)](https://www.docker.com/community-edition) barındıran bir geliştirme ortamında kapsayıcılar ve diğer geliştirici araçları sağlar. [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) oluşturun, gönderin ve büyük iş açısından kritik uygulamalar çalıştırmak BT ekipleri tarafından kullanılır. Her iki ürün gerekli VM (ana kapsayıcı barındırmak için Docker) yükleyin.

[Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) çalışma zamanları iki tür ile çalışır:

-   Windows Server kapsayıcıları, işlem ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Bir Windows Server kapsayıcı bir çekirdek ana bilgisayarda çalışan tüm kapsayıcılar ve kapsayıcı konağı ile paylaşır.

-   Yüksek oranda iyileştirilmiş bir sanal makinede her kapsayıcı çalıştırarak Windows Server kapsayıcıları tarafından sağlanan yalıtım üzerinde Hyper-V kapsayıcıları genişletin. Bu yapılandırmada, daha iyi yalıtım sağlayan Hyper-V kapsayıcıları ile kapsayıcı konağı çekirdeğini paylaşılmıyor. Hyper-V kapsayıcıları izin güvenilmeyen ve *tehlikeli çok kiracılı* aynı ana bilgisayarda çalıştırılacak uygulamalar. Hyper-V kapsayıcıları başlatma sürelerine ve Windows Server kapsayıcıları daha yoğunluklu biraz daha az verimli olması.

Bu kapsayıcı görüntülerinin oluşturulur ve aynı şekilde işlev. Bunlar, kapsayıcının nasıl oluşturulacağını farklılık gösterir. Ayrıntılar için bkz [Hyper-V kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Docker kapsayıcıları sanal makinelerle karşılaştırma

Şekil 2-3 gösterir bir karşılaştırmasını VM'ler ve Docker kapsayıcıları.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Sanal makineler****Docker kapsayıcıları** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  Sanal makineler, uygulama, gerekli kitaplıkları veya ikili dosyaları ve tam konuk işletim sistemi içerir. Tam sanallaştırma kapsayıcı daha fazla kaynak gerektirir. Kapsayıcılar, uygulama ve tüm bağımlılıkları içerir. Ancak, kapsayıcılar, işletim sistemi çekirdek diğer kapsayıcılar ile paylaşır. Kapsayıcıları, konak işletim sisteminde yalıtılmış işlemlerde kullanıcı alanı olarak çalıştırın. Hyper-V kapsayıcıları her kapsayıcıyı kapsayıcı başına özel bir sanal makinenin içinde çalıştığı içinde hariç.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Şekil 2-3**. Docker kapsayıcıları için geleneksel sanal makineler karşılaştırması

Kapsayıcılar çok daha az kaynak gerektirdiğinden (örneğin, bunlar tam bir işletim sistemi gerekmez), Hızlı Başlat ve kolayca dağıtılır. Düşük kaynak kullanımını daha yüksek yoğunluklu sağlar. Daha fazla hizmeti aynı donanım birim üzerinde çalıştırın ve maliyetleri azaltabilirsiniz.

VM'ler daha az yalıtım aynı çekirdek sonuçları üzerinde çalışıyor.

Asıl amacı, görüntü, ortamın (bağımlılıklar) aynı farklı dağıtımlar arasında yapmasıdır. Bu, makinenizde hata ayıklayın ve ardından garanti ortamıyla başka bir makineye dağıtma anlamına gelir.

Bir kapsayıcı görüntüsü, bir uygulama veya hizmet paketini ve güvenilir ve tekrarlanabilir bir şekilde dağıtmak için bir yoldur. Docker yalnızca bir teknoloji ancak aynı zamanda bir felsefesi ve bir işlem olduğunu diyebilirsiniz.

Docker geliştiriciler olmayan örneğin "Benim makinemde neden üretimde çalışır?" Söyledikleri, "Docker üzerinde çalıştığı". Docker-paketlenmiş uygulamalar tüm desteklenen Docker ortamda çalıştırılabilir. Docker paketlenmiş uygulamaları tutarlı bir şekilde tüm dağıtım hedefleri (geliştirme, QA, hazırlama, üretim) üzerinde çalıştırın.

>[!div class="step-by-step"]
[Önceki](index.md)
[İleri](docker-terminology.md)
