---
title: Mevcut .NET uygulamalarını Azure IaaS 'ye yükseltme ve kaydırma (bulut altyapısına hazırlanın)
description: Azure bulut ve Windows kapsayıcıları Ile mevcut .NET uygulamalarını modernleştirin.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089629"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Mevcut .NET uygulamalarını Azure IaaS 'ye yükseltme ve kaydırma (bulut altyapısına hazırlanın)

> Vizyon: ilk adım olarak, şirket içi yatırımınızdan ve donanım ve ağ bakımının toplam maliyetinizi azaltmak için, mevcut uygulamalarınızı bulutta yeniden barındırmanız yeterlidir.

Mevcut uygulamalarınızı Azure hizmet olarak altyapı (IaaS) platformuna geçirme işlemine geçmeden önce, Azure 'Da IaaS 'ye doğrudan geçiş *yapmak istediğiniz nedenleri analiz etmeniz önemlidir* . Bu modernon vade düzeyindeki senaryo temelde, geçerli şirket içi altyapınızı kullanmaya devam etmek yerine buluttaki VM 'Leri kullanmaya başlamadır.

Analiz etmek için başka bir *nokta de yalnızca* Azure 'da daha gelişmiş yönetilen hizmetler eklemek yerine saf IaaS bulutuna geçiş yapmak isteyebilirsiniz. İlk yerde IaaS için hangi durumların gerekli olabileceğini belirleme.

Şekil 2-1, bulut altyapısına uygun olan uygulamaları modernleştirme vade düzeylerinde konumlandırır:

![Bulut altyapısına yönelik özellikli uygulamaları konumlandırma](./media/image2-1.png)

**Şekil 2-1.** Bulut altyapısına yönelik özellikli uygulamaları konumlandırma

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Mevcut .NET Web uygulamaları neden Azure IaaS 'ye geçirilir?

İlk IaaS düzeyinde bile buluta geçiş yapmanın ana nedeni, maliyet azaltmaları elde etmelidir. Kuruluşunuz, daha fazla yönetilen altyapı hizmeti kullanarak, donanım bakımı, sunucu veya VM sağlama ve dağıtım ve altyapı yönetimi için yatırımınızı düşürür.

Uygulamalarınızı buluta taşıma kararı verdikten sonra, PaaS gibi daha gelişmiş seçenekler yerine IaaS ' ı seçip IaaS ortamının daha tanıdık olması gerekir. Geçerli, şirket içi ortamınıza benzer bir ortama geçiş yapmak, daha düşük bir öğrenme eğrisi sunarak buluta en hızlı yol açar.

Ancak, bulut için en hızlı yolu almak, uygulamalarınızın bulutta çalışmasını sağlamak için en avantajdan yararlanabileceğinizi ifade etmez. Herhangi bir kuruluş, bulut geçişinizden en önemli avantajlara sahip olacak, zaten buluta Iyileştirilmiş ve bulut Yerel vade seviyelerine sahip olur.

Ayrıca, uygulamaların bulutta zaten çalışmakta olduğu durumlarda (IaaS 'de bile) modernleştirin ve yeniden mimarilerde daha kolay hale geldiğini de unutmayın. Uygulama verileri geçişi zaten elde edildi. Ayrıca, kuruluşunuz bulutta çalışmak için gereken becerileri elde etmiş ve bir "bulut kültürüne" kaydırma yapacaktır.

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>PaaS yerine IaaS 'e geçiş yapma

Sonraki bölümlerde, genellikle PaaS platformları ve hizmetlerine bağlı olan buluta Iyileştirilmiş uygulamalar ele alınmaktadır. Bu uygulamalar, buluta geçiş işleminden en iyi avantajları sağlar.

Amacınız var olan uygulamaları buluta taşımak için ilk olarak, Azure App Service içinde çalışması gereken önemli değişiklikleri gerektirmeyen mevcut uygulamaları belirlersiniz. Bu uygulamalar, buluta En Iyi duruma getirilmiş ilk aday olmalıdır.

Daha sonra, Azure Kubernetes hizmeti gibi App Service veya düzenleyicilerle Windows kapsayıcılarına ve PaaS 'ye geçemeyen uygulamalar için, bunları basit düz VM 'lere (IaaS) geçirin.

Ancak, VM 'Lerin yapılandırılması, güvenliğinin sağlanması ve sürdürülmesi, Azure 'da PaaS hizmetlerini kullanmaya kıyasla çok daha fazla zaman ve BT uzmanlığı gerektirdiğini unutmayın. Azure sanal makinelerini düşünüyorsanız, VM ortamınızı düzeltme eki uygulamak, güncelleştirmek ve yönetmek için gereken devam eden bakım çabalarını göz önünde bulundurduğunuzdan emin olun. Azure sanal makineleri IaaS 'dir.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Azure geçişi 'ni kullanarak mevcut uygulamalarınızı çözümleyin ve Azure 'a geçirin

Buluta geçiş yapmak zor değildir. Ancak birçok kuruluş, ortama ve uygulamalar, iş yükleri ve veriler arasındaki sıkı bağımlılıklar hakkında ayrıntılı görünürlük almak için kullanmaya başlamıştır. Bu görünürlük olmadan yolun ileri planlanılması zor olabilir. Başarılı bir geçiş için nelerin gerekli olduğuna ilişkin ayrıntılı bilgiler olmadan, kuruluşunuzda doğru konuşmaları olamaz. Olası maliyet avantajları hakkında yeterince bilginiz yok ya da iş yüklerinin yalnızca kaldırıp kaldıramayacağını veya başarıyla geçiş yapmak için önemli bir yeniden çalışma gerektirebilir. Çok sayıda kuruluş yoktur.

[Azure geçişi](https://aka.ms/azuremigrate) , Azure 'a geçiş yaparken size yardımcı olmak için gereken kılavuz, Öngörüler ve mekanizmaları sağlayan yeni bir hizmettir. Azure geçişi şunları sağlar:

- Şirket içi sanal makineler için bulma ve değerlendirme

- Çok katmanlı uygulamaların yüksek güvenilirlikli keşfi için yerleşik bağımlılık eşlemesi

- Azure sanal makinelerine akıllı doğru boyutlandırma

- Olası sorunları giderme yönergeleriyle uyumluluk raporlaması

- Veritabanı bulma ve geçiş için Azure veritabanı yönetim hizmeti ile tümleştirme

Azure geçişi, iş yüklerinizin işletmeye en az etkiyle geçiş yapma ve Azure 'da beklendiği gibi çalıştırma konusunda size güvendiğinden emin olmanızı sağlar. Doğru araçlar ve kılavuzla, kritik performans ve güvenilirlik ihtiyaçlarını karşıladıktan sonra yatırımdaki maksimum iadeyi elde edebilirsiniz.

Şekil 2-2, Azure geçişi tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşlemesini gösterir.

![Bulut altyapısına yönelik özellikli uygulamaları konumlandırma](./media/image2-2.png)

**Şekil 2-2.** Bulut altyapısına yönelik özellikli uygulamaları konumlandırma

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Mevcut VM 'lerinizi Azure VM 'lerine geçirmek için Azure Site Recovery kullanın

Uçtan uca [Azure geçişi](https://aka.ms/azuremigrate)kapsamında, [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) Web uygulamalarınızı Azure 'daki VM 'lere kolayca geçirmek için kullanabileceğiniz bir araçtır. Şirket içi VM 'Leri ve fiziksel sunucuları Azure 'a çoğaltmak veya ikincil bir şirket içi konuma çoğaltmak için Site Recovery kullanabilirsiniz. Hatta, desteklenen bir Azure VM 'de çalışan bir iş yükünü şirket içi *Hyper-V* VM 'Sinde, *VMware* VM 'de veya Windows ya da Linux fiziksel sunucusunda çoğaltabilirsiniz. Azure 'a çoğaltma, ikincil bir veri merkezinin korunmasının maliyetini ve karmaşıklığını ortadan kaldırır.

Site Recovery Ayrıca, kısmen şirket içinde ve kısmen Azure 'da olan karma ortamlar için de yapılır. Site Recovery, VM 'lerde çalışan uygulamalarınızı ve şirket içi fiziksel sunucuları bir site daha sonra kullanılabilir durumda tutarak iş sürekliliği sağlamaya yardımcı olur. Birincil site kullanılabilir değilse ikincil bir konumda kullanılabilir kalması için VM 'lerde ve fiziksel sunucularda çalışan iş yüklerini çoğaltır. Çalışır duruma geldiğinde birincil siteye iş yüklerini kurtarır.

Şekil 2-3 Azure Site Recovery kullanarak birden çok VM geçişlerinin yürütülmesini gösterir.

![Bulut altyapısına yönelik özellikli uygulamaları konumlandırma](./media/image2-3.png)

**Şekil 2-3.** Bulut altyapısına yönelik özellikli uygulamaları konumlandırma

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure veri sayfasını geçirme**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure geçişi**

    <https://aka.ms/azuremigrate>

- **Azure'a geçiş merkezi**

    <https://azure.microsoft.com/migration/>

- **Site Recovery ile Azure 'a geçiş**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Azure Site Recovery hizmete genel bakış**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **AWS 'de VM 'Leri Azure VM 'lerine geçirme**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
