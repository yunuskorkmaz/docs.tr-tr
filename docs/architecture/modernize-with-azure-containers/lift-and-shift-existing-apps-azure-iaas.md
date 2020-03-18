---
title: Varolan .NET uygulamalarını Azure IaaS'a (Bulut Altyapısına Hazır) kaldırın ve kaydırın
description: Azure Bulut ve Windows Kapsayıcıları ile Varolan .NET Uygulamalarını Modernize Edin.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089629"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Varolan .NET uygulamalarını Azure IaaS'a (Bulut Altyapısına Hazır) kaldırın ve kaydırın

> Vizyon: Şirket içi yatırımınızı ve toplam donanım ve ağ bakımı maliyetinizi azaltmak için ilk adım olarak, buluttaki mevcut uygulamalarınızı yeniden barındırmanız yeterlidir.

Mevcut uygulamalarınızı hizmet (IaaS) platformu olarak Azure altyapısına *geçirmeden* önce, Azure'da doğrudan IaaS'a geçiş yapmak isteme *nedenleri* nizi çözümlemeniz önemlidir. Bu modernizasyon olgunluk düzeyindeki senaryo, mevcut şirket içi altyapınızı kullanmaya devam etmek yerine bulutta VM'ler kullanmaya başlamaktır.

Analiz etmek için başka bir nokta, *azure'da* daha gelişmiş yönetilen hizmetler eklemek yerine neden saf IaaS bulutuna geçiş yapmak isteyebileceğinizdir. İlk etapta hangi durumlarda IaaS gerektirebileceğini belirleyin.

Şekil 2-1 pozisyonları Bulut Altyapısı-Modernizasyon olgunluk düzeylerinde hazır uygulamalar:

![Bulut Altyapılarını Konumlandırma-Hazır uygulamaları](./media/image2-1.png)

**Şekil 2-1.** Bulut Altyapılarını Konumlandırma-Hazır uygulamaları

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Neden varolan .NET web uygulamalarını Azure IaaS'a geçirin?

Buluta geçişin temel nedeni, ilk IaaS düzeyinde bile, maliyet indirimleri elde etmektir. Kuruluşunuz daha yönetilen altyapı hizmetlerini kullanarak donanım bakımı, sunucu veya VM sağlama ve dağıtım ve altyapı yönetimine yaptığı yatırımı düşürebilir.

Uygulamalarınızı buluta taşıma kararı aldıktan sonra, PaaS gibi daha gelişmiş seçenekler yerine IaaS'i seçmenizin temel nedeni, IaaS ortamının daha tanıdık olmasıdır. Mevcut, şirket içi ortamınıza benzer bir ortama geçmek, onu buluta giden en hızlı yol yapan daha düşük bir öğrenme eğrisi sunar.

Ancak, buluta giden en hızlı yolu bulmak, uygulamalarınızın bulutta çalışmasını sağlamaktan en fazla faydayı sağlayacağınız anlamına gelmez. Herhangi bir kuruluş, daha önce tanıtılan Bulut Optimize edilmiş ve Bulut-Yerel olgunluk düzeylerinde bulut geçişinden en önemli avantajları elde eder.

Ayrıca, uygulamaların gelecekte iaas'ta bile bulutta çalışırken modernizasyonu ve yeniden mimarlığını daha kolay hale geldiği de ortaya çıkmıştır. Uygulama veri geçişi zaten elde edildi. Ayrıca, kuruluşunuz bulutta çalışmak için gerekli becerileri kazanmış ve bir "bulut kültüründe" çalışmaya geçiş yapmış olacaktır.

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>PaaS yerine IaaS'ye ne zaman göç edilebisisin

Sonraki bölümlerde çoğunlukla PaaS platformlarını ve hizmetlerini temel alan Bulut Tarafından Optimize Edilmiş uygulamalar tartışılır. Bu uygulamalar, buluta geçişten en çok faydayı sağlar.

Amacınız yalnızca varolan uygulamaları buluta taşımaksa, öncelikle Azure Uygulama Hizmeti'nde çalıştırılmak için önemli değişiklikler gerektirmeyen varolan uygulamaları tanımlayın. Bu uygulamalar, Bulut Için Optimize Edilmiş ilk adaylar olmalıdır.

Ardından, Uygulama Hizmeti gibi Windows Kapsayıcıları ve PaaS'a veya Azure Kubernetes Hizmeti gibi orkestratörlere hala taşınamayan uygulamalar için, bunları basit düz VM'lere (IaaS) geçirin.

Ancak, VM'leri doğru şekilde yapılandırmanın, güvence altına almanın ve korumanın, Azure'daki PaaS hizmetlerini kullanmaya kıyasla çok daha fazla zaman ve BT uzmanlığı gerektirdiğini unutmayın. Azure Sanal Makineleri düşünüyorsanız, VM ortamınızı yamamak, güncellemek ve yönetmek için gereken devam eden bakım çabasını dikkate aldığınızdan emin olun. Azure Sanal Makineler IaaS'dır.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Varolan uygulamalarınızı analiz etmek ve Azure'a geçirmek için Azure Geçiş'i kullanın

Buluta göç etmek zor olmak zorunda değildir. Ancak birçok kuruluş, çevreye ve uygulamalar, iş yükleri ve veriler arasındaki sıkı karşılıklı bağımlılıkları derinlemesine görmek için başlamak için mücadele eder. Bu görünürlük olmadan, ileriye doğru yol planlamak zor olabilir. Başarılı bir geçiş için nelerin gerekli olduğu hakkında ayrıntılı bilgi olmadan, kuruluşunuz içinde doğru konuşmaları yapamazsınız. Olası maliyet avantajları veya iş yüklerinin sadece kaldırma ve kaydırma veya başarılı bir şekilde geçiş yapmak için önemli bir yeniden çalışma gerektirip gerekmediği hakkında yeterli şey bilmiyorsunuz. Pek çok kuruluşun tereddüt etmemesine şaşmamalı.

[Azure Geçiş,](https://aka.ms/azuremigrate) Azure'a geçişte size yardımcı olmak için gereken yönergeleri, öngörüleri ve mekanizmaları sağlayan yeni bir hizmettir. Azure Geçiş sağlar:

- Şirket içi sanal makineler için keşif ve değerlendirme

- Çok katmanlı uygulamaların yüksek güven keşfi için dahili bağımlılık haritalama

- Azure sanal makinelerine akıllı sağ boyutlandırma

- Olası sorunları giderme yönergeleriile uyumluluk raporlaması

- Veritabanı bulma ve geçiş için Azure Veritabanı Yönetim Hizmeti ile tümleştirme

Azure Geçiş, iş yüklerinizin işletmeye en az etkiyle geçirebileceğine ve Azure'da beklendiği gibi çalıştırılayabildiği konusunda size güven verir. Doğru araçlar ve kılavuzla, kritik performans ve güvenilirlik gereksinimlerinin karşılandığına dair güvence verirken maksimum yatırım getirisi elde edebilirsiniz.

Şekil 2-2, Azure Geçiş tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşlemi gösterir.

![Bulut Altyapılarını Konumlandırma-Hazır uygulamaları](./media/image2-2.png)

**Şekil 2-2.** Bulut Altyapılarını Konumlandırma-Hazır uygulamaları

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Mevcut VM'lerinizi Azure VM'lerine geçirmek için Azure Site Kurtarma'yı kullanın

Uçtan uca [Azure Geçiş'in](https://aka.ms/azuremigrate)bir parçası olarak, [Azure Site Kurtarma,](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) web uygulamalarınızı Azure'daki VM'lere kolayca geçirmek için kullanabileceğiniz bir araçtır. Site Kurtarma'yı şirket içi VM'leri ve fiziksel sunucuları Azure'da çoğaltmak veya bunları ikincil bir şirket içi konuma çoğaltmak için kullanabilirsiniz. Desteklenen bir Azure VM'de, şirket içi *Hyper-V* VM'de, *VMware* VM'de veya Windows veya Linux fiziksel sunucusunda çalışan bir iş yükünü bile çoğaltabilirsiniz. Azure’a çoğaltma seçeneği, ikincil bir veri merkezi kullanmanın maliyetini ve karmaşıklığını ortadan kaldırır.

Site Kurtarma, kısmen şirket içi ve kısmen Azure'da olan karma ortamlar için de özel olarak hazırlanmıştır. Site Kurtarma, bir site çökerse, VM'lerde ve şirket içi fiziksel sunucularda çalışan uygulamalarınızı kullanılabilir durumda tutarak iş sürekliliğini sağlamaya yardımcı olur. Birincil site kullanılamıyorsa ikincil bir konumda kullanılabilir kalmaları için VM'lerde ve fiziksel sunucularda çalışan iş yüklerini çoğaltıyor. Birincil site yeniden çalışmaya başladığında birincil sitede iş yüklerini kurtarır.

Şekil 2-3, Azure Site Kurtarma'yı kullanarak birden çok VM geçişinin gerçekleştirilimi gösterir.

![Bulut Altyapılarını Konumlandırma-Hazır uygulamaları](./media/image2-3.png)

**Şekil 2-3.** Bulut Altyapılarını Konumlandırma-Hazır uygulamaları

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure Geçir Veri Sayfası**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Geçiş**

    <https://aka.ms/azuremigrate>

- **Azure geçiş merkezi**

    <https://azure.microsoft.com/migration/>

- **Site Recovery ile Azure’a Geçiş**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Azure Site Kurtarma hizmetine genel bakış**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **AWS'deki VM'leri Azure VM'lere geçirme**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
