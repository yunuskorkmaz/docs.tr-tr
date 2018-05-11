---
title: Kaldırın ve mevcut .NET uygulamalarını Azure Iaas (bulut altyapı hazır) kaydırma
description: Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 458b1bd1fc9fc24ce43d0926655fe0767aabc43c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Kaldırın ve mevcut .NET uygulamalarını Azure Iaas (bulut altyapı hazır) kaydırma

> Görme: şirket içi yatırım ve toplam maliyeti donanım azaltın ve yeniden barındırma bakım, ağ yalnızca mevcut uygulamalarınızı bulutta bir ilk adım.

İçine alma önce *nasıl* mevcut uygulamalarınızı Azure altyapı (ıaas) platformu olarak geçirmek için nedenleri çözümlemek önemli olduğunu *neden* doğrudan Iaas geçirmek istediğiniz Azure'da. Bu modernization olgunluk düzeyde aslında geçerli, şirket içi altyapınızı kullanmaya devam edebilirsiniz yerine bulutta VM'ler kullanmaya başlamak için senaryodur.

Analiz etmek için başka bir nokta *neden* saf Iaas bulutuna daha gelişmiş yönetilen Azure hizmetlerinde yalnızca eklemek yerine geçirmek isteyebilirsiniz. Hangi durumlarda olabilir belirlemek Iaas ilk başta gerektirir.

Şekil 2-1'de modernization olgunluk düzeyleri bulut altyapısı çapında kullanılmaya hazır uygulamalar yerleştirir:

![Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma](./media/image2-1.png)

> **Şekil 2-1.** Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Neden Azure Iaas varolan .NET web uygulamalarını geçirme

Maliyet azaltması elde etmek için bile, ilk bir Iaas düzeyinde buluta geçirmek için ana nedeni olmasıdır. Daha fazla yönetilen altyapı hizmetleri kullanarak, kuruluşunuz kendi donanım bakım, sunucu veya VM sağlama ve dağıtım ve altyapı Yönetimi yatırım düşürebilirsiniz.

Buluta uygulamalarınızı geçmeye karar yaptıktan sonra neden, Iaas yerine PaaS basitçe, olduğu gibi daha gelişmiş seçenekler Iaas ortam tercih edebileceğiniz ana nedeni daha tanıdık gelecektir. Geçerli için benzer bir ortama taşıma, bir alt öğrenme olmasını sağlayan en hızlı yolu buluta eğrisi, şirket içi ortamı sunar.

Ancak, en hızlı yolu buluta alma, uygulamalarınızı bulutta çalışan sahip gelen çoğu avantajı elde anlamına gelmez. Herhangi bir kuruluştaki önceden sunulan bulut optimize ve bulut-yerel olgunluk düzeylerinde bulut taşınan en önemli avantajlarını elde edersiniz.

Ayrıca korumalı uygulamaları modernize ve bunlar zaten bulutta bile Iaas üzerinde çalışırken gelecekte rearchitect daha kolay olur. Uygulama veri geçişi zaten kazanmıştır. Ayrıca, kuruluşunuz bulutta çalışmak için gerekli niteliklere kazanılan ve bir "bulut kültürün." işletim için shift yapılan

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Ne zaman yerine bir Iaas PaaS için geçirmek için

Sonraki bölümlerde PaaS platformları ve Hizmetleri çoğunlukla göre bulut iyileştirilmiş uygulamalar açıklanmaktadır. Bu uygulamaları buluta geçiş çoğu avantajları verin. 

Amacınız yalnızca uygulamalarınız buluta taşımak için ilk olarak, Azure App Service'te çalıştırmak için önemli değişiklik gerek duymaz mevcut uygulamaları belirlemek. Bu uygulamalar için ilk aday olmalıdır Bulutla optimize edilmiş. 

Uygulama hizmeti veya Azure Service Fabric gibi orchestrators geçirmek gibi basit düz VM'ler (Iaas) için daha sonra uygulamalar için hala Windows kapsayıcıları ve PaaS taşınamıyor. 

Ancak, doğru yapılandırma, güvenliği ve VM'ler koruyarak daha fazla zaman ve Azure'da PaaS hizmetleri kullanmaya kıyasla BT uzmanlık gerektirdiğini unutmayın. Azure sanal makineleri düşünüyorsanız, düzeltme eki, güncelleştirme ve VM ortamınızı yönetmek için gerekli devam eden bakım çaba dikkate almanız emin olun. Azure sanal makinelerin Iaas şeklindedir.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Azure geçirmek çözümlemek ve mevcut uygulamalarınızı azure'a geçirmek için kullanın

Buluta geçiş zor sahip değil. Ancak, çoğu kuruluş - ortam ve uygulamaların, iş yükleri ve verileri arasında sıkı bağımlılıklarını derin bir görünürlük aktarıp kullanmaya başlama güçlük. Bu görünürlük yolun İleri plana zor olabilir. Başarılı bir geçiş için gerekli ilgili ayrıntılı bilgi, kuruluşunuz içinde sağ görüşmeleri sahip olamaz. Yeterli olası faydaları, maliyet hakkında tanımadığınız veya iş yükleri yalnızca yükseltme-ve-shift verebilir veya başarıyla geçirmek için önemli yeniden çalışma gerektirir. Wonder birçok kuruluş istemeyebilir.

[Azure geçirme](https://aka.ms/azuremigrate) , Kılavuzu, Öngörüler ve Azure'a geçirme yardımcı olmak için gereken mekanizmaları sağlayan yeni bir hizmettir. Azure geçirme sağlar:

- Bulma ve şirket içi sanal makineler için değerlendirme

- Çok katmanlı uygulamaları Yüksek Güvenilirlikli bulma için yerleşik bağımlılık eşleme

- Azure sanal makineler için akıllı sağa boyutlandırma

- Uyumluluk kuralları düzelterek olası sorunlar için raporlama

- Veritabanı bulma ve geçiş için Azure veritabanı yönetim hizmeti ile tümleştirme

Azure geçirme iş yüklerinizi iş için en az etkiyle geçirmek ve Azure'da beklendiği gibi çalışmazsa güven verir. Doğru Araçlar ve Kılavuzu, en çok önemli performans modemlerin sırasında yatırım getirisi elde edebilirsiniz ve güvenilirlik gereksinimlerini karşılıyor.

Şekil 2-2 Azure geçirmek tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşleme gösterir.

![Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma](./media/image2-2.png)

> **Şekil 2-2.** Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Azure VM'ler için var olan sanal makineleri geçirmek için Azure Site Recovery kullanın

Uçtan uca bir parçası olarak [Azure geçirmek](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) kolayca web uygulamalarınızı Azure sanal makineleri geçirmek için kullanabileceğiniz bir araçtır. Site Recovery, şirket içi sanal makineleri ve fiziksel sunucuları azure'a veya ikincil şirket içi konumuna çoğaltmak için kullanabilirsiniz. Bile bir şirket içi üzerinde desteklenen bir Azure VM üzerinde çalışan bir iş yükünü çoğaltabilir *Hyper-V* VM üzerindeki bir *VMware* VM veya Windows veya Linux fiziksel sunucuda. Azure'a çoğaltma için ikincil veri merkezine sürdürme karmaşıklığı ve maliyeti ortadan kaldırır.

Kısmen özellikle karma ortamlar için Site Recovery yapılan ayrıca şirket içi ve kısmen üzerinde Azure. Site Recovery iş sürekliliği VM'ler üzerinde çalıştırılan uygulamalarınızı tutarak sağlamaya yardımcı olur ve fiziksel sunucular kullanılabilir bir site kullanılamaz hale gelirse şirket. Böylece birincil site kullanılamıyorsa, ikincil bir konumda kullanılabilir kalır, sanal makineleri ve fiziksel sunucularda çalışan iş yükleri çoğaltır. Bu olduğunda, birincil site ve yeniden çalıştırmayı iş yükleri kurtarır.

Şekil 2-3, Azure Site Recovery kullanarak birden çok VM geçiş yürütülmesi gösterir.

![Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma](./media/image2-3.png)

> **Şekil 2-3.** Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure veri geçirme**

    [https://aka.ms/azuremigration\_Veri sayfası](https://aka.ms/azuremigration\_datasheet)

- **Azure geçirme**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- **Site Recovery ile azure'a geçirme**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Azure Site Recovery hizmetine genel bakış**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **Azure VM'ler için aws'deki geçirme VM'ler**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[Önceki](index.md)
[sonraki](migrate-your-relational-databases-to-azure.md)
