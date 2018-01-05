---
title: "Kaldırın ve mevcut uygulamalar Azure Iaas kaydırma"
description: "Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize."
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eed17ad06c138c3a4eb85f5e023427b681488784
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="lift-and-shift-existing-apps-azure-iaas"></a>Kaldırın ve mevcut uygulamalar Azure Iaas kaydırma

> Görme: şirket içi yatırım ve toplam maliyeti donanım azaltın ve yeniden barındırma bakım, ağ yalnızca mevcut uygulamalarınızı bulutta bir ilk adım.

İçine alma önce *nasıl* mevcut uygulamalarınızı Azure altyapı (ıaas) platformu olarak geçirmek için nedenleri çözümlemek önemli olduğunu *neden* doğrudan Iaas geçirmek istediğiniz Azure'da. Bu modernization olgunluk düzeyde aslında geçerli, şirket içi altyapınızı kullanmaya devam edebilirsiniz yerine bulutta VM'ler kullanmaya başlamak için senaryodur.

Analiz etmek için başka bir nokta *neden* saf Iaas bulutuna daha gelişmiş yönetilen Azure hizmetlerinde yalnızca eklemek yerine geçirmek isteyebilirsiniz. Hangi durumlarda olabilir belirlemek gereken Iaas ilk başta gerektirir.

Şekil 2-1'de modernization olgunluk düzeyleri bulut altyapısı çapında kullanılmaya hazır uygulamalar yerleştirir:

![Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma](./media/image2-1.png)

> **Şekil 2-1.** Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Neden Azure Iaas varolan .NET web uygulamalarını geçirme 

Maliyet azaltması elde etmek için bile, ilk bir Iaas düzeyinde buluta geçirmek için ana nedeni olmasıdır. Daha fazla yönetilen altyapı hizmetleri kullanarak, kuruluşunuz kendi donanım bakım, sunucu veya VM sağlama ve dağıtım ve altyapı Yönetimi yatırım düşürebilirsiniz.

Buluta uygulamalarınızı geçmeye karar yaptıktan sonra neden, Iaas yerine PaaS basitçe, olduğu gibi daha gelişmiş seçenekler Iaas ortam tercih edebileceğiniz ana nedeni daha tanıdık gelecektir. Geçerli için benzer bir ortama taşıma, bir alt öğrenme olmasını sağlayan en hızlı yolu buluta eğrisi, şirket içi ortamı sunar.

Ancak, en hızlı yolu buluta alma, uygulamalarınızı bulutta çalışan sahip gelen çoğu avantajı elde anlamına gelmez. Herhangi bir kuruluştaki zaten sunulan bulut DevOps hazır ve PaaS (bulut Hızlandırılmış) olgunluk düzeyleri bulut taşınan en önemli avantajlarını elde edersiniz.

Ayrıca korumalı uygulamaları modernize ve gelecekte zaten bulutta bile Iaas üzerinde çalışırken yeniden düzenlenmesine daha kolay olur. Uygulama veri geçişi zaten elde kısmen doğru olmasıdır. Ayrıca, kuruluşunuz bulutta çalışmak için gerekli niteliklere kazanılan ve bir "bulut kültürün." işletim için shift yapılan

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Ne zaman yerine bir Iaas PaaS için geçirmek için

Sonraki bölümlerde, çoğunlukla PaaS platformları ve Hizmetleri göre bulut DevOps çapında kullanılmaya hazır uygulamalar tartışın. Bu uygulamaları buluta geçiş çoğu avantajları verin.

Amacınız yalnızca uygulamalarınız buluta taşımak için ilk olarak, Azure App Service'te çalıştırmak için önemli değişiklik gerektiren uygulamalarınız belirlemek. Bu uygulamaları ilk adayları olmalıdır.

İstemiyorsanız veya hala Windows kapsayıcıları ve/veya Azure Service Fabric veya Kubernetes gibi orchestrators taşıyamazsınız, düz VM'ler (Iaas) kullanırsınız sonra henüz, ardından durumdur.

Ancak, doğru yapılandırma, güvenliği ve VM'ler koruyarak daha fazla zaman ve Azure'da PaaS hizmetleri kullanmaya kıyasla BT uzmanlık gerektirdiğini unutmayın. Azure sanal makineleri düşünüyorsanız, düzeltme eki, güncelleştirme ve VM ortamınızı yönetmek için gerekli devam eden bakım çaba dikkate almanız emin olun. Azure sanal makinelerin Iaas şeklindedir.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Azure geçirmek çözümlemek ve mevcut uygulamalarınızı azure'a geçirmek için kullanın

Buluta geçiş zor sahip değil. Ancak, çoğu kuruluş - ortam ve uygulamaların, iş yükleri ve verileri arasında sıkı bağımlılıklarını derin bir görünürlük aktarıp kullanmaya başlama güçlük. Bu görünürlük yolun İleri plana zor olabilir. Başarılı bir geçiş için gerekli ilgili ayrıntılı bilgi, kuruluşunuz içinde sağ görüşmeleri sahip olamaz. Yeterli olası faydaları, maliyet hakkında tanımadığınız veya iş yükleri yalnızca yükseltme-ve-shift verebilir veya başarıyla geçirmek için önemli yeniden çalışma gerektirir. Wonder birçok kuruluş istemeyebilir.

[Azure geçirme](https://aka.ms/azuremigrate) , Kılavuzu, Öngörüler ve Azure'a geçirme yardımcı olmak için gereken mekanizmaları sağlayan yeni bir hizmettir. Azure geçirme sağlar:

-   Bulma ve şirket içi sanal makineler için değerlendirme

-   Çok katmanlı uygulamaları Yüksek Güvenilirlikli bulma için yerleşik bağımlılık eşleme

-   Azure sanal makineler için akıllı sağa boyutlandırma

-   Uyumluluk kuralları düzelterek olası sorunlar için raporlama

-   Veritabanı bulma ve geçiş için Azure veritabanı yönetim hizmeti ile tümleştirme

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

-   **Azure veri geçirme**

    [https://aka.MS/azuremigration\_veri sayfası](https://aka.ms/azuremigration\_datasheet)

-   **Azure geçirme**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

-   **Site Recovery ile azure'a geçirme**

    [https://docs.microsoft.com/Azure/Site-Recovery/Site-Recovery-Migrate-to-Azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

-   **Azure Site Recovery hizmetine genel bakış**

    [https://docs.microsoft.com/Azure/Site-Recovery/Site-Recovery-Overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

-   **Azure VM'ler için aws'deki geçirme VM'ler**

    [https://docs.microsoft.com/Azure/Site-Recovery/Site-Recovery-Migrate-aws-to-Azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[Önceki](index.md)
[sonraki](migrate-your-relational-databases-to-azure.md)
