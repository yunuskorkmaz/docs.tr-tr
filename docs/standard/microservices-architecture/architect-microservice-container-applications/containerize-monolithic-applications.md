---
title: Tek yapılı uygulamaları kapsayıcıya alma
description: Tek yapılı uygulamaları rağmen kapsayıcılı hale getirmek, mikro hizmetler mimarisi tüm avantajlarını elde edemez, hemen dağıtılabilecek dağıtım önemli faydası vardır.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: d1de4c4beb8c60aa543e5c71243d93b83fe52072
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130928"
---
# <a name="containerizing-monolithic-applications"></a>Tek yapılı uygulamaları kapsayıcıya alma

Tek ve monolithically dağıtılan web uygulaması veya hizmeti oluşturma ve kapsayıcı olarak dağıtmak isteyebilirsiniz. Uygulama dahili olarak tek parça olmayabilir, ancak birkaç kitaplıklar, bileşenler veya hatta katmanları (uygulama katmanı, etki alanı katmanı, veri erişim katmanı, vb.) yapılandırılmış. Dışarıdan, ancak tek bir kapsayıcıya olur — tek bir işlem, tek bir web uygulaması veya tek bir hizmet.

Bu model yönetmek için uygulamayı temsil etmek için tek bir kapsayıcı dağıtırsınız. Kapasiteyi artırmak için ölçek genişletme, diğer bir deyişle, eklemeniz yeterlidir önde gelen bir yük dengeleyici ile daha fazla kopyalar. Basitlik, tek bir dağıtım bir çoklu kapsayıcı veya VM yönetmesini gelir.

![Tek parça kapsayıcılı bir uygulama işlevselliğini iç katmanları veya kitaplıkları, birden çok VM'de sunucuları/kapsayıcı kopyalayarak ans ölçekler kullanıma sahip tek bir kapsayıcı içinde çoğu sahip](./media/image1.png)

**Şekil 4-1**. Tek parça bir uygulamayı kapsayıcılı mimarisi örneği

Şekil 4-1'de gösterildiği gibi her bir kapsayıcı içinde birden çok bileşenleri, kitaplıkları veya iç Katmanlar içerebilir. Bu tek parçalı bir düzen "kapsayıcı bir şeyi yapar ve tek bir işlemde yok" olabilir, ancak kapsayıcı ilke çakışması ancak bazı durumlarda için Tamam'ı olabilir.

Bu yaklaşımın bir dezavantajı, ölçeklendirme gerektiren uygulama büyürse değiştirmeye karşı korumalı hale gelir. Uygulamanın tamamı ölçeklendirilebilir, gerçekten bir sorun değildir. Ancak, çoğu durumda, uygulamanın yalnızca birkaç parçaları sıkıştırma diğer bileşenleri çalışırken ölçeklendirme gerektiren daha az kullanılan noktalarıdır.

Çok daha fazla müşteriye ürünleri satın daha Gözat çünkü Örneğin, bir normal e-ticaret uygulamasında, büyük olasılıkla ürün bilgi alt ölçeklendirmeniz mi gerekiyor. Daha fazla müşteriye kendi Sepeti ödeme işlem hattını kullanma daha kullanın. Daha az müşteriler, yorum eklemek veya satın alma geçmişlerini görüntüleyin. Ve içeriği ve pazarlama kampanyaları yönetmesi gereken çalışanlar, olması olabilir. Tek yapılı tasarım ölçeklendirirseniz, bu farklı görevler için tüm kod birden çok kez dağıtılan ve aynı düzeyde ölçeklendirilebilir.

Bir uygulama yatay bölme farklı alanlarını uygulama ve bölümleme benzer iş kavramlarını veya veri çoğaltma, ölçeği birden çok yolu vardır. Ancak, tüm bileşenlerini ölçeklendirirken sorununu ek olarak, tüm uygulama ve tam yeniden dağıtma işlemi tüm örneklerin tam çözülüp değişiklikleri tek bir bileşene gerektirir.

Ancak, uygulama geliştirme mikro hizmetler yaklaşım için başlangıçta daha kolay olduğundan tek parçalı bir yaklaşım ortak değildir. Bu nedenle, birçok kuruluş bu mimari yaklaşım kullanarak geliştirin. Bazı kuruluşların iyi yeterli sonuçları alırken, diğerleri sınırları karşılaşırsınız. Birçok kuruluş uygulamalarına araçları ve altyapı yaptığı çok zor yıl önce hizmet odaklı mimarilerin (SOA) oluşturun ve gereken listelenmiyor çünkü bu modeli kullanarak tasarlanmış-kadar uygulama büyüdü.

Altyapı açısından bakıldığında, her sunucu aynı konak içindeki birçok uygulama çalıştırabilir ve Şekil 4-2'de gösterildiği gibi kaynak kullanımı verimliliği kabul edilebilir bir oranı sahip.

![Bir konak, birkaç tek yapılı uygulamalar, her biri ayrı bir kapsayıcı üzerinde çalıştırabilirsiniz.](./media/image2.png)

**Şekil 4-2**. Tek parçalı bir yaklaşım: Bir kapsayıcı olarak çalışan her bir uygulamada birden fazla uygulama çalıştıran konak

Microsoft azure'da tek yapılı uygulamalar her örneği için özel VM'ler kullanılarak dağıtılabilir. Ayrıca, kullanarak [Azure sanal makine ölçek kümeleri](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/), sanal makineleri kolayca ölçeklendirebilirsiniz. [Azure App Service](https://azure.microsoft.com/services/app-service/) ayrıca tek yapılı uygulamaları çalıştırabilir ve sanal makineleri yönetmenize gerek kalmadan örneklerini kolayca ölçeklendirin. 2016 tarihinden beri Azure uygulama hizmetleri dağıtımını basitleştirme amacıyla da Docker kapsayıcıları'nın tek örneklerine çalıştırabilirsiniz.

QA ortamında veya sınırlı üretim ortamında olarak birden fazla Docker konağı Vm'leri dağıtma ve Şekil 4-3'te gösterilen şekilde Azure dengeleyicisi kullanarak Dengeleme. Tüm uygulama tek bir kapsayıcıda yer alan çünkü bu, bir dilimi kaba yaklaşım ile ölçeklendirme yönetmenizi sağlar.

![Birden çok ana bilgisayar, her biri tek parçalı uygulama ile kapsayıcı çalıştırma.](./media/image3.png)

**Şekil 4-3**. Bir çoklu kapsayıcı uygulaması ölçeklendirme birden çok konak örneği

Çeşitli konaklarına dağıtım geleneksel dağıtım teknikleri ile yönetilebilir. Docker ana bilgisayarları gibi komutlarla yönetilebilir `docker run` veya `docker-compose` el ile veya sürekli teslim (CD) işlem hatlarından gibi Otomasyon aracılığıyla gerçekleştirilir.

## <a name="deploying-a-monolithic-application-as-a-container"></a>Bir kapsayıcı olarak tek parça bir uygulamayı dağıtma

Tek parçalı uygulama dağıtımlarını yönetmek için kapsayıcılar'ı kullanmanın avantajları vardır. Container Instances ölçeklendirme, çok daha hızlı ve ek sanal makineleri dağıtma kolaydır. Sanal makine ölçek kümeleri kullansanız bile VM başlatmak için zaman ayırın. Geleneksel uygulama örnekleri kapsayıcılar yerine olarak dağıtıldığında, uygulama yapılandırmasını, ideal olmayan VM bir parçası olarak yönetilir.

Docker görüntülerini çok daha hızlı olduğundan, güncelleştirmeleri dağıtmak ve etkili ağ. Docker görüntülerini genellikle piyasaya çıkarma hızlandırır, saniyeler içinde çalışmaya başlayın. Bir Docker görüntüsü örneğini bozmadan verme olarak kadar kolay bir `docker stop` komutunu ve genellikle bir saniye içinde tamamlanır.

Kapsayıcılar, tasarımı gereği sabit olduğundan, hiçbir zaman bozuk VM'ler hakkında endişelenmeniz gerekmiyor. Buna karşılık, bir VM için güncelleştirme betikleri bazı belirli bir yapılandırma veya dosya diskte hesabı Unut.

Tek yapılı uygulamalar Docker yararlanabilir, ancak biz yalnızca avantajlarına temas. Kapsayıcıları yönetme ek avantajlar, çeşitli örnekleri ve her kapsayıcı örneği ömrünü yönetmek kapsayıcı düzenleyicileri ile dağıtması gelir. Ölçeği, geliştirilen ve dağıtılan ayrı ayrı alt sistemler tek parça uygulamasına'kurmak bozucu, mikro hizmetlerin bölge içinde giriş noktası niteliğindedir.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Tek kapsayıcı tabanlı bir uygulamayı Azure App Service'e yayımlama

Azure'a dağıtılan bir kapsayıcının doğrulama almak isteyip istemediğinizi veya uygulamanın yalnızca bir tek kapsayıcı uygulama olduğunda, Azure App Service ölçeklenebilir tek kapsayıcı tabanlı hizmetleri sağlamak için harika bir yol sağlar. Azure App Service kullanarak basit bir işlemdir. Bu, kodunuzu alın, Visual Studio'da derleyin ve doğrudan Azure'a dağıtmak kolay hale getirmek için Git ile harika tümleştirme sağlar.

![Visual Studio'dan Azure App Service için bir çoklu kapsayıcı uygulaması Yayımlama Sihirbazı](./media/image4.png)

**Şekil 4-4**. Bir tek kapsayıcı uygulamasını Azure App Service'e Visual Studio'dan yayımlama

Docker, diğer özellikleri, çerçeveleri veya Azure App Service'te desteklenmeyen bağımlılıkları gerekirse bu bağımlılıkların App Service'te Azure ekibi güncelleştirilmiş bekleyin gerekiyordu. Veya Azure Service Fabric, Azure bulut Hizmetleri veya burada daha fazla denetim sahipti ve uygulamanız için gerekli bileşen veya framework yükleyebilir Vm'leri bile, gibi diğer hizmetlere geçiş gerekiyordu.

Kapsayıcı desteği Visual Studio 2017'de, Şekil 4-4'te gösterildiği gibi uygulama ortamınızda istediğiniz ekleme olanağı sağlar. Uygulamanıza bir bağımlılık eklerseniz, bir kapsayıcıdaki çalıştırıyorsanız bu yana Dockerfile ya da Docker görüntünüzü bağımlılık içerebilir.

Yayımlama akışı da görüldüğü gibi Şekil 4-4'te, görüntüyü bir kapsayıcı kayıt defteri iter. Bu, Azure Container Registry (bir kayıt defteri için Azure dağıtımlarınızda kapatın ve Azure Active Directory'de gruplar ve hesaplar tarafından güvenli) veya tüm diğer Docker kayıt defteri, Docker Hub veya bir şirket içi kayıt defteri gibi olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](docker-application-state-data.md)