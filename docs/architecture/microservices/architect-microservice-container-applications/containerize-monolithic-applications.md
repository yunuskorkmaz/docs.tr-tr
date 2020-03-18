---
title: Tek Yapılı Uygulamaları Kapsayıcıya Alma
description: Monolitik uygulamaları konteynerleme, mikro hizmetler mimarisinden tüm avantajları elde etmese de, hemen teslim edilebilen önemli dağıtım avantajlarına sahiptir.
ms.date: 01/30/2020
ms.openlocfilehash: 0e6f7504a91d2b1a89193471746168fc34f50956
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503275"
---
# <a name="containerizing-monolithic-applications"></a>Tek Yapılı Uygulamaları Kapsayıcıya Alma

Tek, tek bir, monolitik olarak dağıtılan bir web uygulaması veya hizmeti oluşturmak ve bunu bir kapsayıcı olarak dağıtmak isteyebilirsiniz. Uygulamanın kendisi dahili olarak yekpare olmayabilir, ancak çeşitli kitaplıklar, bileşenler ve hatta katmanlar (uygulama katmanı, etki alanı katmanı, veri erişim katmanı, vb.) olarak yapılandırılmıştır. Ancak, harici olarak, tek bir kapsayıcı- tek bir işlem, tek bir web uygulaması veya tek bir hizmet.

Bu modeli yönetmek için, uygulamayı temsil etmek için tek bir kapsayıcı dağıtın. Kapasiteyi artırmak için, ölçeklendirin, yani önünde bir yük dengeleyicisi ile daha fazla kopya ekleyin. Basitlik, tek bir kapsayıcıda veya VM'de tek bir dağıtımın yönetilmesinden gelir.

![Yekpare kapsayıcı uygulamanın bileşenlerini gösteren diyagram.](./media/containerize-monolithic-applications/monolithic-containerized-application.png)

**Şekil 4-1**. Konteynerleştirilmiş yekpare bir uygulamanın mimarisiörneği

Şekil 4-1'de gösterildiği gibi, her kapsayıcıya birden çok bileşen, kitaplık veya dahili katman ekleyebilirsiniz. Yekpare kapsayıcılı bir uygulama, işlevselliğinin çoğunu dahili katmanları veya kitaplıkları olan tek bir kapsayıcı içinde kullanır ve kapsayıcıyı birden çok sunucu/VM'de klonlayarak ölçeklendirebilir. Ancak, bu yekpare desen kapsayıcı ilkesi ile çakışabilir "bir kapsayıcı bir şey yapar ve tek bir işlemde yapar", ancak bazı durumlarda tamam olabilir.

Uygulama büyürse, ölçeklendirmeyi gerektiren bu yaklaşımın dezavantajı belirgin hale gelir. Tüm uygulama ölçeklendirebiliyorsa, bu gerçekten bir sorun değildir. Ancak, çoğu durumda, uygulamanın sadece birkaç bölümü ölçekleme gerektiren boğma noktalarıdır, diğer bileşenler ise daha az kullanılır.

Örneğin, tipik bir e-ticaret uygulamasında, ürün bilgileri alt sistemini ölçeklendirmeniz gerekir, çünkü çok daha fazla müşteri ürünleri satın almaktan daha fazla sınar. Sepetlerini ödeme ardışık hattını kullanmaktan daha fazla müşteri kullanır. Daha az müşteri yorum ekler veya satın alma geçmişini görüntüleyin. Ayrıca, içeriği ve pazarlama kampanyalarını yönetmesi gereken yalnızca bir avuç çalışanA sahip olabilirsiniz. Yekpare tasarımı ölçeklendirin, bu farklı görevlerin tüm kodu birden çok kez dağıtılır ve aynı sınıfta ölçeklendirilir.

Uygulama yatay yinelemesini ölçeklendirmenin, uygulamanın farklı alanlarını bölmenin ve benzer iş kavramlarını veya verilerin bölümlenmesini ölçeklendirmenin birden çok yolu vardır. Ancak, tüm bileşenleri ölçekleme sorununa ek olarak, tek bir bileşendeki değişiklikler tüm uygulamanın tam olarak yeniden test edilmesini ve tüm örneklerin tam olarak yeniden dağıtılmasını gerektirir.

Ancak, uygulamanın geliştirilmesi başlangıçta mikro hizmetler yaklaşımları için daha kolay olduğundan, monolitik yaklaşım yaygındır. Böylece birçok kuruluş bu mimari yaklaşımı kullanarak gelişir. Bazı kuruluşlar yeterince iyi sonuçlar elde ederken, diğerleri sınırları vuruyor. Araçlar ve altyapı yıllar önce hizmet odaklı mimariler (SOA) oluşturmayı çok zorlaştırdığı ve uygulama büyüyene kadar ihtiyacı görmedikleri için birçok kuruluş uygulamalarını bu modeli kullanarak tasarladı.

Altyapı açısından bakıldığında, her sunucu aynı ana bilgisayar içinde birçok uygulama çalıştırabilir ve Şekil 4-2'de gösterildiği gibi kaynak kullanımında kabul edilebilir bir verimlilik oranına sahiptir.

![Bir ana bilgisayarın kaplarda birçok uygulama çalıştırdiğini gösteren diyagram.](./media/containerize-monolithic-applications/host-multiple-apps-containers.png)

**Şekil 4-2**. Monolitik yaklaşım: Birden çok uygulamayı çalıştıran ana bilgisayar, her uygulama kapsayıcı olarak çalışıyor

Microsoft Azure'daki monolitik uygulamalar her örnek için özel VM'ler kullanılarak dağıtılabilir. Ayrıca, [Azure sanal makine ölçek kümelerini](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/)kullanarak Sanal Makineler'i kolayca ölçeklendirebilirsiniz. [Azure Uygulama Hizmeti,](https://azure.microsoft.com/services/app-service/) VM'leri yönetmenize gerek kalmadan yekpare uygulamalar ve kolayca ölçeklendirilebilir. Azure Uygulama Hizmetleri, 2016 yılından bu yana tek sayıda Docker kapsayıcısı örneğini çalıştırarak dağıtımı basitleştirebilir.

QA ortamı veya sınırlı bir üretim ortamı olarak, şekil 4-3'te gösterildiği gibi birden çok Docker ana bilgisayar VM'si dağıtabilir ve Azure dengeleyicisini kullanarak bunları dengeleyebilirsiniz. Bu, tüm uygulama tek bir kapsayıcı içinde yaşadığından, ölçeklemeyi kaba bir gren yaklaşımıyla yönetmenize olanak tanır.

![Yekpare uygulama kaplarını çalıştıran birkaç ana bilgisayar ını gösteren diyagram.](./media/containerize-monolithic-applications/docker-infrastructure-monolithic-application.png)

**Şekil 4-3**. Tek bir kapsayıcı uygulamasını ölçekleme birden çok ana bilgisayar örneği

Çeşitli ana bilgisayarlara dağıtım geleneksel dağıtım teknikleri ile yönetilebilir. Docker ana bilgisayarları gibi `docker run` komutlarla veya `docker-compose` el ile gerçekleştirilen komutlarla veya sürekli teslimat (CD) ardışık hatları gibi otomasyonla yönetilebilir.

## <a name="deploying-a-monolithic-application-as-a-container"></a>Yekpare bir uygulamayı kapsayıcı olarak dağıtma

Yekpare uygulama dağıtımlarını yönetmek için kapsayıcıkullanmanın yararları vardır. Kapsayıcı örneklerini ölçekleme, ek VM'leri dağıtmaktan çok daha hızlı ve kolaydır. Sanal makine ölçek kümeleri kullansanız bile, VM'lerin başlaması zaman alır. Kapsayıcılar yerine geleneksel uygulama örnekleri olarak dağıtıldığında, uygulamanın yapılandırması ideal olmayan VM'nin bir parçası olarak yönetilir.

Docker görüntüleri olarak güncellemeleri dağıtmak çok daha hızlı ve ağ verimlidir. Docker görüntüleri genellikle saniyeler içinde başlar ve bu da piyasaya çıkma hızlarını hızlandırR. Docker görüntü örneğini yıkmak komut vermek `docker stop` kadar kolaydır ve genellikle bir saniyeden kısa sürede tamamlanır.

Kapsayıcılar tasarım gereği değişmez olduğundan, bozuk VM'ler hakkında endişelenmenize gerek yoktur. Buna karşılık, bir VM için güncelleştirme komut dosyaları diskte bırakılan belirli bir yapılandırma veya dosya için hesap unutabilir.

Monolitik uygulamalar Docker'dan fayda lanabilirken, sadece avantajlara değiniyoruz. Kapsayıcıları yönetmenin ek avantajları, her konteyner örneğinin çeşitli örneklerini ve yaşam döngüsünü yöneten konteyner orkestratörleri ile dağıtımdan gelir. Monolitik uygulamayı tek tek ölçeklendirilebilen, geliştirilebilen ve dağıtılabilen alt sistemlere dönüştürmek, mikro hizmetler alanına giriş noktanızdır.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Azure Uygulama Hizmetinde tek kapsayıcı tabanlı bir uygulama yayımlama

Azure'a dağıtılan bir kapsayıcının doğrulanmasını almak ister bir uygulama yalnızca tek kapsayıcı lı bir uygulama olduğunda, Azure Uygulama Hizmeti ölçeklenebilir tek kapsayıcı tabanlı hizmetler sağlamak için harika bir yol sağlar. Azure Uygulama Hizmeti'ni kullanmak kolaydır. Kodunuzu almayı, Visual Studio'da oluşturmayı ve doğrudan Azure'a dağıtmayı kolaylaştırmak için Git ile harika entegrasyon sağlar.

![Kapsayıcı Kayıt Defteri'ni gösteren Uygulama Hizmeti Oluştur iletişim kutusunun ekran görüntüsü.](./media/containerize-monolithic-applications/publish-azure-app-service-container.png)

**Şekil 4-4**. Visual Studio 2019'dan Azure Uygulama Hizmetine tek konteyner li bir uygulama yayınlama

Docker olmadan, Azure Uygulama Hizmeti'nde desteklenmeyen diğer özelliklere, çerçevelere veya bağımlılıklara ihtiyacınız varsa, Azure ekibinin Uygulama Hizmeti'ndeki bağımlılıkları güncelleştirmesini beklemeniz gerekir. Veya azure bulut hizmetleri veya VM'ler gibi diğer hizmetlere geçmeniz gerekir, burada daha fazla denetiminiz vardır ve uygulamanız için gerekli bir bileşeni veya çerçeveyi yükleyebilirsiniz.

Visual Studio 2017'de konteyner desteği ve daha sonra Şekil 4-4'te gösterildiği gibi, uygulama ortamınıza istediğiniz her şeyi dahil edebilme nizi sağlar. Bir kapsayıcıda çalıştırdığınıza göre, uygulamanız için bir bağımlılık eklerseniz, dockerfile veya Docker resminize bağımlılık ekleyebilirsiniz.

Şekil 4-4'te de gösterildiği gibi, yayımlama akışı bir görüntüyü konteyner kayıt defterine iter. Bu, Azure Konteyner Kayıt Defteri (Azure'daki dağıtımlarınıza yakın ve Azure Etkin Dizin grupları ve hesapları tarafından güvenli hale alınmış bir kayıt defteri) veya Docker Hub veya şirket içi kayıt defteri gibi diğer Docker kayıt defteri olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](docker-application-state-data.md)
