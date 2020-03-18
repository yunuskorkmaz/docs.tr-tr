---
title: Docker nedir?
description: Docker anlayışınızı biraz daha derine alın, burada basit bir benzetme size yardımcı olabilir.
ms.date: 02/15/2019
ms.openlocfilehash: e3b3685f2fc6d5a9d33bb176d04ca910f0289344
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76919871"
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker,](https://www.docker.com/) uygulamaların bulutta veya şirket içinde çalıştırılabilen taşınabilir, kendi kendine yetebilen kapsayıcılar olarak dağıtımını otomatikleştirmek için açık kaynaklı bir [projedir.](https://github.com/docker/docker) Docker aynı zamanda bu teknolojiyi destekleyen ve geliştiren bir [şirkettir](https://www.docker.com/) ve Microsoft da dahil olmak üzere bulut, Linux ve Windows satıcılarıyla işbirliği içinde çalışmaktadır.

![Docker kapsayıcıların çalıştırabileceği yerleri gösteren diyagram.](./media/what-is-docker/docker-containers-run-anywhere.png)

**Şekil 1-2**. Docker, hibrit bulutun tüm katmanlarına konteyner dağıtıyor

Yukarıdaki diyagramda gösterildiği gibi, Docker kapsayıcıları azure'da müşteri veri merkezinde, harici bir hizmet sağlayıcısında veya bulutta her yerde, şirket içinde çalıştırılabilir. Docker görüntü kapsayıcıları linux ve Windows'da da yerel olarak çalıştırılabilir. Ancak, Windows görüntüleri yalnızca Windows ana bilgisayarlarında çalıştırılabilir ve Linux görüntüleri Linux ana bilgisayarlarında ve Windows ana bilgisayarlarında (şimdiye kadar Hyper-V Linux VM kullanarak) çalıştırılabilir ve ana bilgisayar sunucu bir sunucu veya VM anlamına gelir.

Geliştiriciler Windows, Linux veya macOS'ta geliştirme ortamlarını kullanabilir. Geliştirme bilgisayarında geliştirici, uygulama ve bağımlılıkları da dahil olmak üzere Docker görüntülerinin dağıtıldığı bir Docker ana bilgisayar çalıştırıyor. Linux veya Mac üzerinde çalışan geliştiriciler, Linux tabanlı bir Docker ana bilgisayar kullanır ve yalnızca Linux kapsayıcıları için resimler oluşturabilirler. (Mac'te çalışan geliştiriciler kodu kodlayabilir veya macOS'tan Docker CLI çalıştırabilir, ancak bu yazı itibariyle kapsayıcılar doğrudan macOS'ta çalışmaz.) Windows üzerinde çalışan geliştiriciler, Linux veya Windows Kapsayıcıları için resim oluşturabilir.

Geliştirme ortamlarında konteynerleri barındırmak ve ek geliştirici araçları sağlamak için Docker, Windows veya macOS için [Docker Community Edition (CE)](https://www.docker.com/community-edition) gemilerini iletir. Bu ürünler, konteynerleri barındırmak için gerekli VM'yi (Docker ana bilgisayar) yükler. Docker ayrıca, kurumsal geliştirme için tasarlanmış ve üretimde büyük iş açısından kritik uygulamalar inşa eden, gönderen ve çalıştıran BT ekipleri tarafından kullanılan [Docker Enterprise Edition 'ı (EE)](https://www.docker.com/enterprise-edition)de kullanıma sunmasıdır.

Windows [Kapsayıcılarını](/virtualization/windowscontainers/about/)çalıştırmak için iki tür çalışma alanı vardır:

- **Windows Server Kapsayıcıları,** işlem ve ad alanı yalıtım teknolojisi ile uygulama yalıtımı sağlar. Windows Server Kapsayıcısı, kapsayıcı ana bilgisayarla ve ana bilgisayarda çalışan tüm kapsayıcılarla bir çekirdek paylaşır.

- **Hyper-V Kapsayıcılar,** her kapsayıcıyı son derece optimize edilmiş bir sanal makinede çalıştırarak Windows Server Kapsayıcıları tarafından sağlanan yalıtımı genişletir. Bu yapılandırmada, kapsayıcı ana bilgisayarın çekirdeği Hyper-V Kapsayıcılarıyla paylaşılmaz ve daha iyi yalıtım sağlar.

Bu kapsayıcılar için görüntüler oluşturulur ve aynı şekilde çalışır. Aradaki fark, kapsayıcının görüntüden nasıl oluşturulduğudur— Hyper-V Konteyner içalıştırarak fazladan bir parametre gerektirir. Ayrıntılar için [Hyper-V Konteynerler'e](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)bakın.

## <a name="comparing-docker-containers-with-virtual-machines"></a>Docker konteynerlerini sanal makinelerle karşılaştırma

Şekil 1-3, VM'ler ve Docker kapları arasında bir karşılaştırma gösterir.

![VM ve kapsayıcı ortamlarının karşılaştırması gösteren diyagram.](./media/what-is-docker/comparison-vms-docker-conatiners.png)

**Şekil 1-3**. Geleneksel sanal makinelerin Docker kaplarla karşılaştırılması

Yukarıdaki diyagramda gösterildiği gibi, VM'ler için ana bilgisayar sunucusunda üç temel katman vardır. Aşağıdan yukarıya: Altyapı, Ana Bilgisayar İşletim Sistemi ve Bir Hypervisor. Tüm bunların yanı, her VM kendi işletim sistemi ve gerekli tüm kütüphaneler vardır. Öte yandan, Docker için, ana sunucu yalnızca Altyapı ve işletim sistemi vardır. Bunun üzerine, konteyner motoru kapsayıcıları izole tutar, ancak tek temel işletim sistemi hizmetlerini paylaşmalarını sağlar.

Kapsayıcılar çok daha az kaynağa ihtiyaç duyduğundan (örneğin, tam işletim sistemi gerekmez), dağıtmaları kolaydır ve hızlı başlarlar. Bu, daha yüksek yoğunluğa sahip olmanızı sağlar, bu da aynı donanım biriminde daha fazla hizmet çalıştırmanızı sağlayarak maliyetleri azaltmanızı sağlar.

Aynı çekirdek üzerinde çalışan bir yan etkisi olarak, VMs daha az izolasyon olsun.

Görüntünün temel amacı, farklı dağıtımlar arasında aynı ortamı (bağımlılıkları) sağlamaktır. Bu, makinenizde hata ayıklama ve sonra başka bir makineye dağıtmak anlamına gelir, aynı ortam garanti.

Kapsayıcı görüntüsü, bir uygulamayı veya hizmeti güvenli ve tekrarlanabilir bir şekilde dağıtmanın bir yoludur. Docker'ın sadece bir teknoloji değil, aynı zamanda bir felsefe ve bir süreç olduğunu söyleyebilirsiniz.

Docker'ı kullanırken, geliştiricilerin "Makinemde çalışıyor, neden üretimde değil?" demelerini duymayacaksınız. Paketlenmiş Docker uygulaması desteklenen docker ortamında yürütülebildiği ve tüm dağıtım hedeflerinde (Dev, QA, evreleme ve üretim gibi) amaçlandığı şekilde çalıştığı için sadece "Docker'da çalışır" diyebilirler.

## <a name="a-simple-analogy"></a>Basit bir benzetme

Belki basit bir benzetme Docker çekirdek kavramı kavramak yardımcı olabilir.

Bir an lığına 1950'lere geri dönelim. Hiçbir kelime işlemcileri vardı ve fotokopi her yerde (iyi, tür) kullanılmıştır.

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
