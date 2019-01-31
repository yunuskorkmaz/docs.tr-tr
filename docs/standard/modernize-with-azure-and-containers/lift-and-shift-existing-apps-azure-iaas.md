---
title: Kaldırma ve var olan .NET uygulamalarını Azure Iaas (bulut altyapısını kullanıma hazır) için kaydırma
description: Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 2b987d43f476f261bfdbd1b2af6ca7f792178cf8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266630"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Kaldırma ve var olan .NET uygulamalarını Azure Iaas (bulut altyapısını kullanıma hazır) için kaydırma

> İşleme: Şirket içi yatırım ve donanım ve Bakım ağ toplam maliyetini azaltmak için ilk adım olarak, yalnızca mevcut uygulamalarınızı bulutta barındırma.

İçine alma önce *nasıl* mevcut uygulamalarınızı Azure altyapısı (ıaas) platformu olarak geçirmek için nedenlerini analiz önemlidir *neden* doğrudan Iaas'ye geçirin istiyorsunuz Azure'da. Bu modernizasyonu olgunluk düzeyinde temelde Vm'leri, şirket içi altyapınızı kullanmaya devam etme niyetiniz yerine bulutta kullanmaya başlamak için bir senaryodur.

Analiz etmek için başka bir nokta *neden* yalnızca Azure yönetilen Hizmetleri daha gelişmiş eklemek yerine, saf Iaas bulutuna geçirmek isteyebilirsiniz. Hangi durumlarda olabilir belirlemek Iaas ilk başta gerektirir.

Şekil 2-1, bulut altyapısını kullanıma hazır uygulamalar modernizasyonu olgunluk Düzeyler halinde yerleştirir:

![Bulut altyapısını kullanıma hazır uygulamalar konumlandırma](./media/image2-1.png)

> **Şekil 2-1.** Bulut altyapısını kullanıma hazır uygulamalar konumlandırma

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Neden Azure Iaas mevcut .NET web uygulamaları geçirme

Temel nedeni bile, ilk bir Iaas düzeyinde buluta geçirin, maliyet indirimleri elde etmektir. Daha fazla yönetilen altyapı Hizmetleri'ni kullanarak, kuruluşunuzun Donanım bakımı, sunucu veya VM sağlama ve dağıtım ve altyapı yönetimi, yatırım düşürebilirsiniz.

Uygulamalarınızı buluta geçmeye karar yaptıktan sonra neden, Iaas, PaaS yalnızca olduğu gibi daha gelişmiş seçenekler yerine Iaas ortamı tercih edebileceğiniz temel nedeni daha tanıdık gelecektir. Geçerli için benzer bir ortama taşıma, bir alt buluta giden en hızlı yol yapan öğrenme, şirket içi ortamı sunar.

Ancak, buluta giden en hızlı yol almak, bulutta çalışan uygulamalarınızın sahip gelen en çok faydayı elde anlamına gelmez. Herhangi bir kuruluştaki bir buluta geçiş zaten sunulan bulut için iyileştirilmiş hem de bulutta yerel olgunluk düzeylerinde sağladığı en önemli avantajları konusunda bilgi edineceksiniz.

Ayrıca dikkati uygulamaları modernize etme ve bulutta bile ıaas'de zaten çalışırken gelecekte yeniden oluşturma daha kolay olur. Uygulama veri geçişi zaten kazanmıştır. Ayrıca, kuruluşunuz bulutta çalışmak için gerekli becerileri kısalttılar ve bir "bulut kültürde." işletim için shift yapılan

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>PaaS için yerine Iaas geçirmek ne zaman

Sonraki bölümlerde, PaaS platformları ve Hizmetleri çoğunlukla göre bulut için iyileştirilmiş uygulamalar açıklanmaktadır. Bu uygulamaları buluta geçirme gelen birçok avantaj sağlar. 

Amacınız yalnızca mevcut uygulamalarınızı buluta taşımak için ise, ilk olarak, Azure App Service'te çalıştırılacak değişikliği gerektirmez, mevcut uygulamaları tanımlayın. Bu uygulamalar için ilk aday olmalıdır Bulutla optimize edilmiş. 

App Service veya Azure Service Fabric gibi düzenleyicilerle geçirme gibi bu basit düz vm'lere (Iaas) sonra uygulamalar için yine de Windows kapsayıcıları ve PaaS taşıyamazsınız. 

Ancak, doğru şekilde yapılandırma, güvenlik altına alma ve Vm'leri koruma çok daha fazla zaman ve IT uzmanlığı Azure PaaS hizmetleri kullanmaya kıyasla gerektirdiğini aklınızda bulundurun. Azure sanal makineleri düşünüyorsanız, düzeltme eki uygulama, güncelleştirme ve VM ortamınızı yönetmek için gereken sürekli bir bakım çabası hesaba katması emin olun. Azure sanal makineleri Iaas olur.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Analiz ve mevcut uygulamalarınızı azure'a geçirmek için Azure Geçişi'ı kullanın

Buluta geçmek zor olmak zorunda değildir. Ancak, çoğu kuruluş - ortam ve uygulamaları, iş yüklerini ve verileri birbirine sıkı derin görünürlük elde etmek için'da başlamak uğraşır. Bu görünürlük ileriye doğru yolu planlamak zor olabilir. Ne başarılı bir geçiş için gereken ilgili ayrıntılı bilgiler, kuruluşunuzdaki doğru konuşmalar sahip olamaz. Olası maliyet avantajları, hakkında yeterli bilmiyorsanız veya iş yükleri yalnızca lift-and-shift ile taşıma verebilir veya başarıyla geçirmek için önemli olması gerekir. Hiçbir elmas pek çok kuruluş istemeyebilir.

[Azure geçişi](https://aka.ms/azuremigrate) Kılavuzu, Öngörüler ve Azure'a geçiş ile yardımcı olmak için gereken mekanizmalar sağlayan yeni bir hizmettir. Azure geçişi sağlar:

- Keşif ve değerlendirme şirket içi sanal makineler için

- Yüksek güvenle bulma çok katmanlı uygulamaları için yerleşik bağımlılık eşlemesi

- Azure sanal makinelerine akıllı doğru boyutlandırma

- Uyumluluk kuralları düzelterek olası sorunlar için ile raporlama

- Veritabanı keşfi ve geçişi için Azure veritabanı yönetim hizmeti ile tümleştirme

Azure geçişi, iş yüklerinizi iş olabildiğince az etkileyerek geçirme ve Azure'da beklendiği gibi çalışmazsa olmanızı sağlar. Doğru Araçlar ve rehberlik ile en fazla kritik performans işlemlerini sırasında yatırım getirisini elde edebileceğiniz ve güvenilirlik ihtiyaçlarının karşılandığından.

Şekil 2-2, Azure geçişi tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşlemesi gösterir.

![Bulut altyapısını kullanıma hazır uygulamalar konumlandırma](./media/image2-2.png)

> **Şekil 2-2.** Bulut altyapısını kullanıma hazır uygulamalar konumlandırma

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Mevcut Vm'lerinizi Azure Vm'lerine geçirmek için Azure Site RECOVERY'yi kullanın.

Uçtan uca bir parçası olarak [Azure geçişi](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) kolayca web uygulamalarınızı Azure sanal makineleri geçirmek için kullanabileceğiniz bir araçtır. Şirket içi Vm'leri ve fiziksel sunucuları Azure'a çoğaltmak için veya bunları bir ikincil şirket içi konuma çoğaltmak için Site RECOVERY'yi kullanabilirsiniz. Bir şirket içi desteklenen bir Azure sanal makinesinde çalıştırılan bir iş yükü bile çoğaltabilirsiniz *Hyper-V* VM, bir *VMware* VM veya bir Windows veya Linux fiziksel sunucusu üzerinde. Azure'a çoğaltma, maliyet ve ikincil bir veri merkezi kullanmanın karmaşıklığını ortadan kaldırır.

Site kurtarma kısmen özellikle karma ortamlar için de yapılan şirket içinde ve kısmen üzerinde Azure. Site Recovery Vm'lerde çalışan uygulamalarınızı tutarak iş sürekliliği sağlamaya yardımcı olur ve şirket içi fiziksel sunucuları kullanılabilir bir site dışı kalırsa. Bu birincil site kullanılamıyorsa, ikincil bir konumda kullanılabilir kalmasını Vm'lerde ve fiziksel sunucularda çalışan iş yükleri çoğaltır. Bu, başladığında birincil site ile yeniden çalışan iş yüklerini kurtarır.

Şekil 2-3, Azure Site Recovery kullanarak birden çok sanal makine geçişi yürütülmesini gösterir.

![Bulut altyapısını kullanıma hazır uygulamalar konumlandırma](./media/image2-3.png)

> **Şekil 2-3.** Bulut altyapısını kullanıma hazır uygulamalar konumlandırma

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure veri geçişi**

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

- **Azure geçişi**

    [https://aka.ms/azuremigrate](https://aka.ms/azuremigrate)

- **Azure geçiş Merkezi**

    [https://azure.microsoft.com/migration/](https://azure.microsoft.com/migration/)

- **Site Recovery ile azure'a geçirme**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Azure Site Recovery hizmetine genel bakış**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **Azure VM'ler için AWS VM geçirme**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](migrate-your-relational-databases-to-azure.md)
