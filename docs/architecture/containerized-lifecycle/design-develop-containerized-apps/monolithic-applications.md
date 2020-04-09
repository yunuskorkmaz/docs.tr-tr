---
title: Tek yapılı uygulamalar
description: Yekpare uygulamaları kapsayıcılaştırmak için temel kavramları anlayın.
ms.date: 02/15/2019
ms.openlocfilehash: 3c186f6a300588816916886927f93e0c06ebd6bc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988992"
---
# <a name="monolithic-applications"></a>Tek yapılı uygulamalar

Bu senaryoda, tek ve yekpare bir web uygulaması veya hizmeti oluşturuyor ve kapsayıcı olarak dağıtıyorsunuz. Uygulama içinde, yapı yekpare olmayabilir; birkaç kitaplık, bileşen ve hatta katmandan (uygulama katmanı, etki alanı katmanı, veri erişim katmanı, vb.) oluşabilir. Harici olarak, tek bir işlem, tek bir web uygulaması veya tek bir hizmet gibi tek bir kapsayıcıdır.

Bu modeli yönetmek için, uygulamayı temsil etmek için tek bir kapsayıcı dağıtın. Ölçeklendirmek için, sadece önünde bir yük dengeleyici ile birkaç kopya daha ekleyin. Basitlik, tek bir kapsayıcıda veya sanal makinede (VM) tek bir dağıtımın yönetilmesinden gelir.

Bir kapsayıcının yalnızca tek bir şey yaptığı ve bunu tek bir işlemde yaptığı prensibitaki tek bir işlemde, yekpare desen çakışıyor. Şekil 4-1'de gösterildiği gibi, her kapsayıcıya birden çok bileşen/kitaplık veya dahili katman ekleyebilirsiniz.

![Uygulamayı klonlayarak ölçeklenen yekpare bir uygulamayı gösteren diyagram.](./media/monolithic-applications/monolithic-application-architecture-example.png)

**Şekil 4-1.** Yekpare uygulama mimarisiörneği

Yekpare bir uygulama işlevselliğinin tümünü veya çoğunu tek bir işlem veya kapsayıcı içinde kullanır ve dahili katmanlarda veya kitaplıklarda bileşenlenir. Bu yaklaşımın dezavantajı, uygulama büyürse veya büyüyünce ölçeklendirilmesi ne zaman gerçekleşirse ortaya çıkar. Tüm uygulama ölçekli ise, gerçekten bir sorun değil. Ancak, çoğu durumda, uygulamanın birkaç bölümü ölçekleme gerektiren boğma noktalarıdır, diğer bileşenler ise daha az kullanılır.

Tipik e-ticaret örneğini kullanarak, büyük olasılıkla ihtiyacınız olan ürün bilgileri bileşenini ölçeklendirmektir. Çok daha fazla müşteri satın almaktan çok ürünlere göz atar. Sepetlerini ödeme ardışık hattını kullanmaktan daha fazla müşteri kullanır. Daha az müşteri yorum ekler veya satın alma geçmişini görüntüleyin. Ve büyük olasılıkla, tek bir bölgede, içerik ve pazarlama kampanyaları yönetmek için gereken çalışan sadece bir avuç var. Monolitik tasarımı ölçeklendirerek, kodun tümü birden çok kez dağıtılır.

"Her şeyi ölçeklendir" sorununa ek olarak, tek bir bileşendeki değişiklikler, tüm uygulamanın tam olarak yeniden test edilmesini ve tüm örneklerin yeniden dağıtılmasını gerektirir.

Yekpare yaklaşım yaygındır ve birçok kuruluş bu mimari yöntemle gelişmektedir. Pek çoğu yeterince iyi sonuçlara sahipken, diğerleri sınırla karşılaşır. Araçlar ve altyapı SOA'lar oluşturmak çok zor olduğu için birçok kişi bu modelde uygulamalarını tasarladı ve uygulama büyüyene kadar bu ihtiyacı görmediler.

Altyapı açısından bakıldığında, her sunucu aynı ana bilgisayar içinde birçok uygulama çalıştırabilir ve Şekil 4-2'de gösterildiği gibi kaynak kullanımınızda kabul edilebilir bir verimlilik oranına sahiptir.

![Ayrı kaplarda birden fazla uygulama içeren bir ana bilgisayarı gösteren bir diyagram.](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**Şekil 4-2.** Birden çok uygulama/kapsayıcı çalıştıran bir ana bilgisayar

Son olarak, kullanılabilirlik açısından, yekpare uygulamalar bir bütün olarak dağıtılmalıdır; bu, *durdurmanız ve başlatmanız*gerektiğinde, tüm işlevlerin ve tüm kullanıcıların dağıtım penceresi sırasında etkileneceği anlamına gelir. Bazı durumlarda, Azure ve kapsayıcıların kullanımı bu durumları en aza indirebilir ve Şekil 4-3'te görebileceğiniz gibi uygulamanızın kapalı kalma süresini azaltabilir.

Her örnek için özel VM'ler kullanarak Azure'da yekpare uygulamaları dağıtabilirsiniz. [Azure VM Ölçek Kümelerini](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)kullanarak VM'leri kolayca ölçeklendirebilirsiniz.

Azure Uygulama [Hizmetlerini,](https://azure.microsoft.com/services/app-service/) VM'leri yönetmek zorunda kalmadan yekpare uygulamaları çalıştırmak ve örnekleri kolayca ölçeklendirmek için de kullanabilirsiniz. Azure Uygulama Hizmetleri, dağıtımı basitleştirerek docker kapsayıcılarının tek örneklerini de çalıştırabilir.

Docker ana bilgisayar olarak birden çok VM dağıtabilir ve VM başına herhangi bir sayıda kapsayıcı çalıştırabilirsiniz. Daha sonra, Şekil 4-3'te gösterildiği gibi bir Azure Yük Dengeleyicisi kullanarak ölçeklemeyi yönetebilirsiniz.

![Farklı ana bilgisayarlara ölçeklenen yekpare bir uygulamayı gösteren bir diyagram.](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**Şekil 4-3**. Tek bir Docker uygulamasını ölçekleme birden çok ana bilgisayar

Geleneksel dağıtım teknikleri ile ev sahiplerinin dağıtımını yönetebilirsiniz.

Docker kapsayıcılarını komut satırından, sürekli `docker run` `docker-compose up`teslim (CD) ardışık hatlarında otomatikleştirerek ve örneğin Azure DevOps Hizmetleri'nden Docker ana bilgisayarlarına dağıtarak yönetebilirsiniz.

## <a name="monolithic-application-deployed-as-a-container"></a>Konteyner olarak dağıtılan monolitik uygulama

Yekpare dağıtımları yönetmek için kapsayıcıları kullanmanın yararları vardır. Kapsayıcı örneklerini ölçekleme, ek VM'leri dağıtmaktan çok daha hızlı ve kolaydır.

Docker görüntüleri olarak güncellemeleri dağıtmak çok daha hızlı ve ağ verimlidir. Docker konteynerleri genellikle saniyeler içinde başlar ve hızlı kullanıma alınır. Docker konteynerini yıkmak `docker stop` komutu çağırmak kadar kolaydır ve genellikle bir saniyeden kısa sürede tamamlanır.

Kapsayıcılar doğuştan değişmez olduğundan, tasarım gereği bozuk VM'ler hakkında endişelenmenize gerek yoktur, çünkü bir güncelleştirme komut dosyası diskte bırakılan belirli bir yapılandırma yı veya dosyayı hesaba kaçmayı unuttu.

Monolitik uygulamalar Docker'dan fayda sağlasa da, sadece avantajların ipuçlarına değiniyoruz. Kapsayıcıları yönetmenin daha büyük yararları, her konteyner örneğinin çeşitli örneklerini ve yaşam döngüsünü yöneten konteyner orkestratörleri ile dağıtımdan gelir. Monolitik uygulamayı tek tek ölçeklendirilebilen, geliştirilebilen ve dağıtılabilen alt sistemlere dönüştürmek, mikro hizmetler alanına giriş noktanızdır.

Kapsayıcılarla yekpare uygulamaları nasıl "kaldırAbileceğiniz ve kaydırabileceğiniz" hakkında bilgi edinmek ve uygulamalarınızı nasıl modernize edebilirsiniz, bu ek Microsoft kılavuzunu okuyabilirsiniz, [Mevcut .NET uygulamalarını Azure bulutu ve Windows Kapsayıcıları ile modernize](../../modernize-with-azure-containers/index.md)edin , ayrıca PDF olarak da <https://aka.ms/LiftAndShiftWithContainersEbook>indirebilirsiniz.

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Azure Uygulama Hizmetinde tek bir Docker kapsayıcı uygulaması yayınlama

Azure'a dağıtılan bir kapsayıcının hızlı bir şekilde doğrulanmasını istediğinizden veya uygulama yalnızca tek konteyner uygulaması olduğundan, Azure Uygulama Hizmetleri ölçeklenebilir tek kapsayıcı hizmetleri sağlamak için harika bir yol sağlar.

Azure Uygulama Hizmeti'ni kullanmak sezgiseldir ve kodunuzu almak, Microsoft Visual Studio'da oluşturmak ve doğrudan Azure'a dağıtmak için harika Git tümleştirmesi sağladığı ndan hızlı bir şekilde çalışmaya devam edebilirsiniz. Ancak, geleneksel olarak (Docker olmadan) Uygulama Hizmetlerinde desteklenmeyen diğer özelliklere, çerçevelere veya bağımlılıklara ihtiyacınız varsa, Azure ekibinin App Hizmetindeki bağımlılıkları güncelleştirdiğiveya Daha fazla denetiminiz olan ve uygulamanız için gerekli bir bileşen veya çerçeve yükleyebileceğiniz Hizmet Kumaşı, Bulut Hizmetleri ve hatta düz VM'ler gibi diğer hizmetlere geçene kadar bunu beklemeniz gerekir.

Şimdi, Şekil 4-4'te gösterildiği gibi, Visual Studio 2017'yi kullanırken, Azure Uygulama Hizmeti'ndeki konteyner desteği, uygulama ortamınıza istediğiniz her şeyi ekleme olanağı sağlar. Uygulamanıza bir bağımlılık eklediyseniz, bir kapsayıcıda çalıştırdığınız için Dockerfile veya Docker resminize bu bağımlılıkları ekleme özelliğine sahip olabilirsiniz.

![Kapsayıcı Kayıt Defteri'ni gösteren Uygulama Hizmeti Oluştur iletişim kutusunun ekran görüntüsü.](./media/monolithic-applications/publish-azure-app-service-container.png)

**Şekil 4-4**. Visual Studio uygulamalarından/kapsayıcılarından Azure Uygulama Hizmetine kapsayıcı yayınlama

Şekil 4-4 ayrıca, yayımlama akışının bir görüntüyü, Azure Konteyner Kayıt Defteri (Azure'daki dağıtımlarınıza yakın ve Azure Etkin Dizin grupları ve hesapları tarafından güvence altına alınmış bir kayıt defteri) veya Docker Hub veya şirket içi kayıt şirketleri gibi diğer Docker Registry'si olabilecek bir Kapsayıcı Kayıt Defteri'ne iter.

>[!div class="step-by-step"]
>[Önceki](common-container-design-principles.md)
>[Sonraki](state-and-data-in-docker-applications.md)
