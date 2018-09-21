---
title: Docker nedir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker nedir?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 1b0cae037371666f2f1cd2ccb8c509a5618e7397
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540430"
---
# <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) olduğu bir [açık kaynaklı proje](https://github.com/docker/docker) Bulut veya şirket içinde çalışan taşınabilir, kendi kendine yeterli kapsayıcı uygulamalarının dağıtımını otomatikleştirmek için. Docker, ayrıca bir [şirket](https://www.docker.com/) bulut, Linux ve Windows sağlayıcılar dahil olmak üzere Microsoft ile işbirliği içinde çalışan, bu teknoloji geliştikçe ve yükseltir.

![Docker kapsayıcıları, Azure'da şirket içi müşteri veri merkezi, bir dış hizmet sağlayıcısı veya Bulut her yerden çalıştırabilirsiniz.](./media/image2.png)

**Şekil 2-2**. Docker kapsayıcıları tüm katmanlarda karma bulutun dağıtır.

Docker görüntüsü kapsayıcılar, Linux ve Windows üzerinde yerel olarak çalıştırabilirsiniz. Ancak, Windows görüntülerini yalnızca Windows konaklarda çalışabilir ve Linux görüntüleri Linux ve Windows konakları (bir Hyper-V Linux VM şimdiye kullanarak), üzerinde ana bilgisayar bir sunucu veya VM olduğu anlamına gelir çalıştırabilirsiniz.

Geliştiriciler, Windows, Linux veya macOS geliştirme ortamları kullanabilirsiniz. Geliştirme bilgisayarında, Docker görüntülerini, uygulamayı ve bağımlılıklarını dağıtıldığı bir Docker konağı Geliştirici çalıştırır. Linux veya Mac üzerinde çalışan geliştiriciler, Linux tabanlı bir Docker konağı kullanın ve bunlar görüntülerini yalnızca Linux kapsayıcıları oluşturabilirsiniz. (Mac üzerinde çalışan geliştiriciler kodu düzenleyebilir ya da Docker CLI'yı macOS çalıştırın, ancak bu makalenin yazıldığı zaman itibariyle, kapsayıcılar, doğrudan macOS üzerinde çalıştırmayın.) Windows üzerinde çalışan geliştiriciler, Linux veya Windows kapsayıcıları için görüntü oluşturabilirsiniz.

Docker kapsayıcıları geliştirme ortamlarında barındırmak ve diğer geliştirici araçlarını sağlamak için gelen [Docker Community Edition'ı (CE)](https://www.docker.com/community-edition) macOS veya Windows için. Bu ürünler gerekli VM (ana kapsayıcı barındırmak için Docker) yükleyin. Docker da kullanımınıza [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), Kurumsal geliştirme için tasarlanan ve yapı BT ekipleri tarafından kullanılan, gönderin ve büyük iş açısından kritik uygulamalar üretimde çalışır.

Çalıştırılacak [Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), çalışma zamanları iki tür vardır:

-   Windows Server kapsayıcıları, işlem ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Bir Windows Server kapsayıcı bir çekirdek ana bilgisayarda çalışan tüm kapsayıcılar ve kapsayıcı konağı ile paylaşır.

-   Yüksek oranda iyileştirilmiş bir sanal makinede her kapsayıcı çalıştırarak Windows Server kapsayıcıları tarafından sağlanan yalıtım üzerinde Hyper-V kapsayıcıları genişletin. Bu yapılandırmada, daha iyi yalıtım sağlayan Hyper-V kapsayıcıları ile kapsayıcı konağı çekirdeğini paylaşılmıyor.

Bu kapsayıcılar için görüntüler ve aynı işlevi aynı şekilde oluşturulur. Kapsayıcının nasıl oluşturulacağını fark görüntüsünü Hyper-V kapsayıcı çalıştırma ek bir parametre gerektiriyor. Ayrıntılar için bkz [Hyper-V kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Docker kapsayıcıları sanal makinelerle karşılaştırma

Şekil 2-3 gösterir bir karşılaştırmasını VM'ler ve Docker kapsayıcıları.

<table>
<tbody>
<tr>
<td style="width:50%"><p><strong>Sanal makineler</strong></p>
<p><img src="media/image3.png" style="width:100%; vertical-align:top;" alt="For VMs, there are three base layers in the host server, from the bottom-up: infrastructure, Host Operating System and a Hypervisor and on top of all that each VM has its own OS and all necessary libraries"/></p>
<p>Sanal makineler, uygulama, gerekli kitaplıkları veya ikili dosyaları ve tam konuk işletim sistemi içerir. Tam sanallaştırma kapsayıcı daha fazla kaynak gerektirir.</p></td>
<td style="width:50%"><p><strong>Docker kapsayıcıları</strong></p>
<p><img src="media/image4.png" style="width:100%; vertical-align:top;" alt="For Docker, the host server only has the infrastructure and the OS and on top of that, the container engine, that keeps container isolated but sharing the base OS services."/></p>
<p>Kapsayıcılar, uygulama ve tüm bağımlılıkları içerir. Ancak, bunlar diğer kapsayıcılarla yalıtılmış işlemlerde kullanıcı alanı konak işletim sisteminde çalışan işletim sistemi çekirdeğini paylaşır. (Hyper-V kapsayıcıları her kapsayıcıyı kapsayıcı başına özel bir sanal makinenin içinde çalıştığı içinde hariç.)</p></td>
</tr>
</tbody>
</table>

**Şekil 2-3**. Docker kapsayıcıları için geleneksel sanal makineler karşılaştırması

Kapsayıcılar çok daha az kaynak gerektirdiğinden (örneğin, bunlar tam bir işletim sistemi gerekmez), bunlar kolayca ve Hızlı Başlat. Bu, daha yüksek yoğunluk, böylece maliyetleri azaltırken aynı donanım biriminde daha fazla hizmet çalıştırmanıza olanak tanır, yani olmasını sağlar.

Bir yan aynı çekirdeği üzerinde çalıştırma etkisi, Vm'lere göre daha az Yalıtımın alın.

Asıl amacı, görüntü, ortamın (bağımlılıklar) aynı farklı dağıtımlar arasında yapmasıdır. Bu, makinenizde hata ayıklayın ve ardından garanti ortamıyla başka bir makineye dağıtma anlamına gelir.

Bir kapsayıcı görüntüsü, bir uygulama veya hizmet paketini ve güvenilir ve tekrarlanabilir bir şekilde dağıtmak için bir yoldur. Docker yalnızca bir teknoloji ancak aynı zamanda bir felsefesi ve bir işlem olduğunu diyebilirsiniz.

Docker'ı kullanırken, geliştiricilerin söyleyin duyacak değil, "Benim makinemde neden üretimde çalışır?" Bunlar yalnızca diyebilirsiniz, "Docker üzerinde çalıştığı", çünkü paket Docker uygulama herhangi bir desteklenen Docker ortamda yürütülebilir ve bu şekilde çalışır, tüm dağıtım hedefleri üzerinde (hazırlama, üretim, vs. Dev, QA.) kullanılması.

## <a name="a-simple-analogy"></a>Basit benzerleme

Belki de basit benzerleme kavrayın, Docker'ın temel kavramı alma yardımcı olabilir.

Kısa bir süre için 50's süre içinde geri dönelim. Herhangi bir sözcük işlemcisi vardı ve fotokopi her yerde kullanıldı (tür).

Toplu harf gerçek kağıt ve zarflar, fiziksel olarak (oluştu hiç e-posta geri sonra) her bir müşterinin adrese teslim edilecek kullanan müşteriler, postalanmak üzere gerektiği gibi hızlı bir şekilde vermekten sorumlu düşünün.

Belirli bir noktada yalnızca çok sayıda çekilmiş ve harf çok hızlı bir şekilde vermek için bir sistem oluşturmak için harf, amacı göre gerektiği gibi düzenlenen zaman paragraflar, oluşumunu yüklü bir miktar olursa almak istediği harflerdir farkında olun.

Sistem çok basittir:

1.  Saydam sayfaları bir paragraf içeren bir deste başlayın

2.  Bir dizi harf sorun için ihtiyacınız paragrafları sayfalarıyla seçin, ardından yığını ve arayın ve ince okuma hizalamadan ve

3.  Son olarak, gerektiği kadar harf üretmek için Fokotopi ve ENTER tuşuna Başlangıç kümesi yerleştirin.

Bu nedenle, basitleştirme, Docker'ın temel fikri olan,

Docker, her katman için dosya sistemi örneğin bir program yükledikten, bir komut yürütüldükten sonra gerçekleşen değişikliklerin elde edilen kümesidir.

"Katman kopyalandıktan sonra dosya sistemi baktığınızda" tüm dosyaları görmek için program yüklendiğinde katman dahil.

Görüntüsü, işletim sistemi zaten yüklü olduğu bir ikincil salt okunur sabit disk "bilgisayar" yüklenmek için hazır olarak düşünebilirsiniz.

Similary, bir kapsayıcının "yüklü bilgisayar" resim sabit diski düşünebilirsiniz. Bir bilgisayar gibi kapsayıcı açılıp kapatılabilir.

>[!div class="step-by-step"]
[Önceki](index.md)
[İleri](docker-terminology.md)
