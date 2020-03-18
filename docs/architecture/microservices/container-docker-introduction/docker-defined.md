---
title: Docker nedir?
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Docker nedir?
ms.date: 08/31/2018
ms.openlocfilehash: a53845d3bbcf24f3eaeb98b9e08b6f35a023c30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337715"
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker,](https://www.docker.com/) uygulamaların bulutta veya şirket içinde çalıştırılabilen taşınabilir, kendi kendine yetebilen kapsayıcılar olarak dağıtımını otomatikleştirmek için açık kaynaklı bir [projedir.](https://github.com/docker/docker) Docker aynı zamanda bu teknolojiyi destekleyen ve geliştiren bir [şirkettir](https://www.docker.com/) ve Microsoft da dahil olmak üzere bulut, Linux ve Windows satıcılarıyla işbirliği içinde çalışmaktadır.

![Docker kapsayıcıların çalıştırabileceği yerleri gösteren diyagram.](./media/docker-defined/docker-containers-run-anywhere.png)

**Şekil 2-2**. Docker, hibrit bulutun tüm katmanlarına kapsayıcılar dağıtıyor.

Docker kapsayıcıları, müşteri veri merkezinde, harici bir hizmet sağlayıcısında veya bulutta Azure'da her yerde, şirket içinde çalıştırılabilir. Docker görüntü kapsayıcıları Linux ve Windows'da yerel olarak çalıştırılabilir. Ancak, Windows görüntüleri yalnızca Windows ana bilgisayarlarında çalıştırılabilir ve Linux görüntüleri Linux ana bilgisayarlarında ve Windows ana bilgisayarlarında (şimdiye kadar Hyper-V Linux VM kullanarak) çalıştırılabilir ve ana bilgisayar sunucu bir sunucu veya VM anlamına gelir.

Geliştiriciler Windows, Linux veya macOS'ta geliştirme ortamlarını kullanabilir. Geliştirme bilgisayarında geliştirici, uygulama ve bağımlılıkları da dahil olmak üzere Docker görüntülerinin dağıtıldığı bir Docker ana bilgisayar çalıştırıyor. Linux veya macOS üzerinde çalışan geliştiriciler, Linux tabanlı bir Docker ana bilgisayar kullanır ve yalnızca Linux kapsayıcıları için resim oluşturabilirler. (macOS üzerinde çalışan geliştiriciler kodu kodlayabilir veya macOS'tan Docker CLI çalıştırabilir, ancak bu yazının yazıldığı andan itibaren kapsayıcılar doğrudan macOS'ta çalışmaz.) Windows üzerinde çalışan geliştiriciler, Linux veya Windows Kapsayıcıları için resim oluşturabilir.

Geliştirme ortamlarında konteynerleri barındırmak ve ek geliştirici araçları sağlamak için Docker, Windows veya macOS için [Docker Community Edition (CE)](https://www.docker.com/community-edition) gemilerini iletir. Bu ürünler, konteynerleri barındırmak için gerekli VM'yi (Docker ana bilgisayar) yükler. Docker ayrıca, kurumsal geliştirme için tasarlanmış ve üretimde büyük iş açısından kritik uygulamalar inşa eden, gönderen ve çalıştıran BT ekipleri tarafından kullanılan [Docker Enterprise Edition 'ı (EE)](https://www.docker.com/enterprise-edition)de kullanıma sunmasıdır.

Windows [Kapsayıcılarını](/virtualization/windowscontainers/about/)çalıştırmak için iki tür çalışma alanı vardır:

- Windows Server Kapsayıcıları, işlem ve ad alanı yalıtım teknolojisi ile uygulama yalıtımı sağlar. Windows Server Kapsayıcısı, kapsayıcı ana bilgisayarla ve ana bilgisayarda çalışan tüm kapsayıcılarla bir çekirdek paylaşır.

- Hyper-V Kapsayıcılar, her kapsayıcıyı son derece optimize edilmiş bir sanal makinede çalıştırarak Windows Server Kapsayıcıları tarafından sağlanan yalıtımı genişletir. Bu yapılandırmada, kapsayıcı ana bilgisayarın çekirdeği Hyper-V Kapsayıcılarıyla paylaşılmaz ve daha iyi yalıtım sağlar.

Bu kapsayıcılar için görüntüler aynı şekilde oluşturulur ve aynı işlevi. Fark, hyper-v kapsayıcı çalıştıran görüntüden kapsayıcının nasıl oluşturulduğu için ekstra bir parametre gerektirir. Ayrıntılar için [Hyper-V Konteynerler'e](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)bakın.

## <a name="comparing-docker-containers-with-virtual-machines"></a>Docker konteynerlerini sanal makinelerle karşılaştırma

Şekil 2-3, VM'ler ve Docker kapları arasında bir karşılaştırma gösterir.

| Virtual Machines | Docker Konteynerler |
| -----------------| ------------------|
|![Geleneksel bir VM'nin donanım/yazılım yığınını gösteren diyagram.](./media/docker-defined/virtual-machine-hardware-software.png)|![Docker kapsayıcıları için donanım/yazılım yığınını gösteren diyagram.](./media/docker-defined/docker-container-hardware-software.png)|
|Sanal makineler uygulama, gerekli kitaplıklar veya ikililer ve tam bir konuk işletim sistemi içerir. Tam sanallaştırma kapsayıcılıkça daha fazla kaynak gerektirir. | Kapsayıcılar uygulama ve tüm bağımlılıkları içerir. Ancak, os çekirdeğini diğer kapsayıcılarla paylaşırlar ve ana bilgisayar işletim sisteminde kullanıcı alanında yalıtılmış işlemler olarak çalışır. (Her konteynerin konteyner başına özel bir sanal makinenin içinde çalıştığı Hyper-V kapları hariç.) |

**Şekil 2-3**. Geleneksel sanal makinelerin Docker kaplarla karşılaştırılması

VM'ler için, ana bilgisayar sunucusunda aşağıdan yukarıya doğru üç temel katman vardır: altyapı, Ana Bilgisayar İşletim Sistemi ve Bir Hypervisor ve her VM'nin kendi işletim sistemi ve gerekli tüm kitaplıklar olması. Docker için, ana bilgisayar sunucusu yalnızca altyapıya ve işletim sistemine sahiptir ve bunun üzerine, kapsayıcıyı izole eden ancak temel işletim sistemi hizmetlerini paylaşan konteyner motoru vardır.

Kapsayıcılar çok daha az kaynağa ihtiyaç duyduğundan (örneğin, tam işletim sistemi gerekmez), dağıtmaları kolaydır ve hızlı başlarlar. Bu, daha yüksek yoğunluğa sahip olmanızı sağlar, bu da aynı donanım biriminde daha fazla hizmet çalıştırmanızı sağlayarak maliyetleri azaltmanızı sağlar.

Aynı çekirdek üzerinde çalışan bir yan etkisi olarak, VMs daha az izolasyon olsun.

Bir görüntünün temel amacı, ortamı (bağımlılıkları) farklı dağıtımlar arasında aynı hale getirir. Bu, makinenizde hata ayıklama ve sonra aynı ortam garanti başka bir makineye dağıtmak anlamına gelir.

Kapsayıcı görüntüsü, bir uygulamayı veya hizmeti güvenli ve tekrarlanabilir bir şekilde dağıtmanın bir yoludur. Docker'ın sadece bir teknoloji değil, aynı zamanda bir felsefe ve bir süreç olduğunu söyleyebilirsiniz.

Docker'ı kullanırken, geliştiricilerin "Makinemde çalışıyor, neden üretimde değil?" demelerini duymayacaksınız. Paketlenmiş Docker uygulaması desteklenen docker ortamında yürütülebildiği ve tüm dağıtım hedeflerinde (Dev, QA, evreleme ve üretim gibi) amaçlandığı şekilde çalıştığı için basitçe "Docker'da çalışır" diyebilirler.

## <a name="a-simple-analogy"></a>Basit bir benzetme

Belki basit bir benzetme Docker çekirdek kavramı kavramak yardımcı olabilir.

Bir an lığına 1950'lere geri dönelim. Hiçbir kelime işlemcileri vardı ve fotokopi her yerde (tür) kullanılmıştır.

Gerektiğinde hızlı bir şekilde mektup toplu vermek, gerçek kağıt ve zarflar kullanarak müşterilere posta, her müşterinin adresine fiziksel olarak teslim edilecek (o zaman hiçbir e-posta vardı) sorumlu olduğunuzu düşünün.

Bir noktada, harflerin, mektubun amacına göre, gerektiği gibi seçilip düzenlenmiş büyük bir paragraf kümesinin bileşimi olduğunu fark esiniz, bu yüzden ağır bir zam almayı ummak için harfleri hızlı bir şekilde vermek için bir sistem tasarlarsınız.

Sistem basittir:

1. Her biri bir paragraf içeren saydam levhalardan oluşan bir deste ile başlarsınız.

2. Bir harf kümesi vermek için, sayfaları ihtiyacınız olan paragraflarla seçersiniz, sonra bunları istifler ve hizalarsınız, böylece güzel görünür ve okurlar.

3. Son olarak, seti fotokopi makinesine yerve istediğiniz kadar harf üretmeye başlayın.

Yani, basitleştirmek, Docker'ın temel fikri bu.

Docker'da her katman, bir programı yükleme gibi bir komutu çalıştırdıktan sonra dosya sisteminin başına gelen değişiklikler kümesidir.

Bu nedenle, katman kopyalandıktan sonra dosya sistemine "baktığınızda" program yüklendiğinde katmandahil olan tüm dosyaları görürsünüz.

Görüntüyü, işletim sisteminin zaten yüklü olduğu bir "bilgisayara" yüklenmeye hazır yardımcı salt okunur sabit disk olarak düşünebilirsiniz.

Benzer şekilde, bir kapsayıcıyı sabit disk yüklü görüntüyle "bilgisayar" olarak düşünebilirsiniz. Kapsayıcı, tıpkı bir bilgisayar gibi, açık veya kapalı güç olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](docker-terminology.md)
