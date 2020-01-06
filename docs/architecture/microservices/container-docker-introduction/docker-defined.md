---
title: Docker nedir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker nedir?
ms.date: 08/31/2018
ms.openlocfilehash: a53845d3bbcf24f3eaeb98b9e08b6f35a023c30e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337715"
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) , uygulamaların bulutta veya şirket içinde çalışabilen, taşınabilir, kendi kendine yeterli kapsayıcı olarak dağıtımını otomatik hale getirmeye yönelik [Açık kaynaklı bir projem](https://github.com/docker/docker) . Docker Ayrıca, Microsoft dahil olmak üzere bulut, Linux ve Windows satıcılarıyla birlikte çalışarak bu teknolojiyi tanıtan ve geliştikçe bir [şirkettir](https://www.docker.com/) .

![Docker kapsayıcısının çalışacağı yerleri gösteren diyagram.](./media/docker-defined/docker-containers-run-anywhere.png)

**Şekil 2-2**. Docker, kapsayıcıyı karma bulutun tüm katmanlarında dağıtır.

Docker kapsayıcıları, müşteri veri merkezinde her yerde, şirket içi bir hizmet sağlayıcısında veya bulutta, Azure 'da her yerde çalışabilir. Docker görüntü kapsayıcıları, Linux ve Windows üzerinde yerel olarak çalışabilir. Ancak, Windows yansımaları yalnızca Windows konakları üzerinde çalışabilir ve Linux görüntüleri Linux konakları ve Windows konakları üzerinde çalıştırılabilir (Bu nedenle, ana bilgisayar bir sunucu veya VM anlamına gelir).

Geliştiriciler Windows, Linux veya macOS 'ta geliştirme ortamlarını kullanabilir. Geliştirme bilgisayarında, geliştirici, uygulama ve bağımlılıkları dahil olmak üzere Docker görüntülerinin dağıtıldığı bir Docker ana bilgisayarı çalıştırır. Linux veya macOS üzerinde çalışan geliştiriciler, Linux tabanlı bir Docker Konağı kullanır ve yalnızca Linux kapsayıcıları için görüntü oluşturabilirler. (MacOS 'ta çalışan geliştiriciler, macOS 'tan kod düzenleyebilir veya Docker CLı 'yi çalıştırabilir, ancak bu yazma sırasında kapsayıcılar doğrudan macOS üzerinde çalışmaz.) Windows üzerinde çalışan geliştiriciler, Linux ya da Windows kapsayıcıları için görüntü oluşturabilir.

Geliştirme ortamlarında kapsayıcıları barındırmak ve ek geliştirici araçları sağlamak için Docker, Windows veya macOS için [Docker Community Edition (CE)](https://www.docker.com/community-edition) ile birlikte gelir. Bu ürünler, kapsayıcıları barındırmak için gerekli VM 'yi (Docker ana bilgisayarı) yükler. Docker Ayrıca Kurumsal Geliştirme için tasarlanan kullanılabilir [Docker Enterprise Edition 'ı (ee)](https://www.docker.com/enterprise-edition)de sunar ve üretimde büyük işletme açısından kritik uygulamalar oluşturan, gönderen ve çalıştıran BT ekipleri tarafından kullanılır.

[Windows kapsayıcıları](/virtualization/windowscontainers/about/)çalıştırmak için iki tür çalışma zamanı vardır:

- Windows Server kapsayıcıları, işlem ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Windows Server kapsayıcısı, bir çekirdeği kapsayıcı Konakla ve konakta çalışan tüm kapsayıcılarla paylaşır.

- Hyper-V kapsayıcıları, her kapsayıcıyı yüksek oranda iyileştirilmiş bir sanal makinede çalıştırarak Windows Server kapsayıcıları tarafından sunulan yalıtımın üzerine genişletilir. Bu yapılandırmada, kapsayıcı konağın çekirdeği, daha iyi yalıtım sağlayan Hyper-V kapsayıcılarıyla paylaşılmaz.

Bu kapsayıcıların görüntüleri aynı şekilde oluşturulur ve aynı işlevi görür. Fark, bir Hyper-V kapsayıcısını çalıştıran görüntüden kapsayıcının oluşturulma biçiminde ek bir parametre olması gerekir. Ayrıntılar için bkz. [Hyper-V kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Docker kapsayıcılarını sanal makinelerle karşılaştırma

Şekil 2-3, VM 'Ler ve Docker Kapsayıcıları arasında bir karşılaştırma gösterir.

| Sanal Makineler | Docker Kapsayıcıları |
| -----------------| ------------------|
|![Geleneksel bir sanal makinenin donanım/yazılım yığınını gösteren diyagram.](./media/docker-defined/virtual-machine-hardware-software.png)|![Docker kapsayıcıları için donanım/yazılım yığınını gösteren diyagram.](./media/docker-defined/docker-container-hardware-software.png)|
|Sanal makineler, uygulamayı, gerekli kitaplıkları veya ikili dosyaları ve tam Konuk işletim sistemini içerir. Tam sanallaştırma kapsayıcıdan daha fazla kaynak gerektirir. | Kapsayıcılar, uygulamayı ve tüm bağımlılıklarını içerir. Ancak, IŞLETIM sistemi çekirdeğini konak işletim sistemindeki kullanıcı alanında yalıtılmış süreçler olarak çalışan diğer kapsayıcılarla paylaşır. (Hyper-V kapsayıcıları dışında, her kapsayıcının kapsayıcı başına özel bir sanal makine içinde çalıştığı yer.) |

**Şekil 2-3**. Geleneksel sanal makinelerin Docker kapsayıcılarına karşılaştırması

VM 'Ler için, aşağıdan yukarıya ana bilgisayar sunucusunda üç temel katman vardır: altyapı, ana bilgisayar Işletim sistemi ve hiper yönetici ve her VM 'nin kendi işletim sistemi ve tüm gerekli kitaplıklar vardır. Docker için, konak sunucusu yalnızca altyapıyı ve işletim sistemini, kapsayıcıyı yalıtılmış ancak temel işletim sistemi hizmetlerini paylaşan kapsayıcı altyapısını barındırır.

Kapsayıcılar çok daha az kaynak gerektirdiğinden (örneğin, tam bir işletim sistemine gerek kalmaz), kolayca dağıtılır ve hızlı bir başlangıç yapabilirsiniz. Bu, daha yüksek yoğunluklu hale gelir, yani aynı donanım biriminde daha fazla hizmet çalıştırmanıza olanak tanır ve böylece maliyetleri azaltır.

Aynı çekirdekte çalıştırmanın yan etkisi olarak VM 'lerden daha az yalıtımdan yararlanın.

Bir görüntünün ana amacı, ortamın (bağımlılıklar) farklı dağıtımlarda aynı olmasını sağlamaktır. Bu, makinenizde Hata ayıklayabilmeniz ve aynı ortamı garanti eden başka bir makineye dağıtabileceğiniz anlamına gelir.

Bir kapsayıcı görüntüsü, bir uygulamayı veya hizmeti paketlemeyi ve güvenilir ve tekrarlanabilir bir şekilde dağıtmayı bir yoldur. Docker 'ın yalnızca bir teknoloji ve ayrıca bir FIN ve bir işlem olmadığını söyleyebilirsiniz.

Docker kullanırken, "BT makinelerimde çalışıyor, neden üretimde çalışmıyor?" konusunda geliştiricilere söylendirilmezsiniz. Paketlenmiş Docker uygulaması desteklenen herhangi bir Docker ortamında yürütülebildiğinden ve tüm dağıtım hedeflerine (geliştirme, QA, hazırlama ve üretim gibi) tasarlandığı şekilde çalıştığından, "Docker üzerinde çalışıyor" gibi bir şey olabilir.

## <a name="a-simple-analogy"></a>Basit bir benzerleme vurguladı

Belki de basit bir benzerleme vurguladı, Docker 'ın temel kavramının attık 'sini elde etmenize yardımcı olabilir.

Yine de 1950s bir süre sonra geri gidelim. Hiçbir sözcük işlemcisi yoktu ve photocopers her yerde (türü) kullanılmıştı.

Her bir müşterinin adresine fiziksel olarak teslim edilecek şekilde, gerçek kağıtların ve zarfların kullanılması için gerektiğinde her bir kişinin, her bir müşterinin adresine (e-posta yoktu

Belli bir noktada, harflerin amacına göre, gerektiğinde çekilen ve düzenlenmiş büyük bir paragraf kümesinin bir kompozisyonunun bir bileşim olduğunu fark etmiş olursunuz. böylece, bir sistem, her zaman hızlı bir şekilde mektuplar vermesini ve bu sayede bir en iyi şekilde bir geliştirme almayı ister.

Sistem basittir:

1. Her biri bir paragraf içeren bir saydam sayfa destesi ile başlarsınız.

2. Bir harf kümesi vermek için, ihtiyacınız olan paragrafları içeren sayfaları seçer, daha sonra bunları bulup daha iyi okuyabilmeleri için yığırsınız ve hizalayın.

3. Son olarak, kümeyi photofotokopi ' a yerleştirip başlangıç ' a basarak gereken sayıda harf oluşturabilirsiniz.

Böylece, Docker 'ın temel fikri basitleştiriliyor.

Docker 'da, her katman, bir program yükleme gibi bir komut yürütüldükten sonra dosya sisteminde gerçekleşen değişiklikler kümesidir.

Bu nedenle, katman kopyalandıktan sonra dosya sistemine "baktığınızda", programın yüklendiği zaman katmana dahil edilen tüm dosyaları görürsünüz.

Bir görüntüyü, işletim sisteminin zaten yüklü olduğu bir "bilgisayara" yüklenmeye hazırlamış bir yardımcı salt okunurdur sabit disk olarak düşünebilirsiniz.

Benzer şekilde, bir kapsayıcıyı görüntü sabit diski yüklü "bilgisayar" olarak düşünebilirsiniz. Kapsayıcı, tıpkı bir bilgisayar gibi, açık veya kapalı olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](docker-terminology.md)
