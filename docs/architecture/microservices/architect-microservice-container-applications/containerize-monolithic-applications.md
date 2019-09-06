---
title: Tek Yapılı Uygulamaları Kapsayıcıya Alma
description: Tek parçalı uygulamaların kapsayıcılarından yararlanın, mikro hizmetler mimarisinin tüm avantajlarını almamakla birlikte, hemen teslim edilebilir önemli dağıtım avantajları vardır.
ms.date: 09/20/2018
ms.openlocfilehash: 9e457fba56c8fdf946618fca10285f4c0a343af4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295544"
---
# <a name="containerizing-monolithic-applications"></a>Tek Yapılı Uygulamaları Kapsayıcıya Alma

Tek, tek parçalı olarak dağıtılan bir Web uygulaması veya hizmeti oluşturmak ve bunu bir kapsayıcı olarak dağıtmak isteyebilirsiniz. Uygulamanın kendisi dahili olarak tek parçalı olabilir, ancak birkaç kitaplık, bileşen veya hatta Katmanlar (uygulama katmanı, etki alanı katmanı, veri erişim katmanı, vb.) olarak yapılandırılmıştır. Dışarıdan, ancak tek bir işlem, tek bir Web uygulaması veya tek bir hizmet olan tek bir kapsayıcıdır.

Bu modeli yönetmek için, uygulamayı temsil etmek üzere tek bir kapsayıcı dağıtırsınız. Kapasiteyi artırmak için ölçeği ölçeklendirebilirsiniz, diğer bir deyişle, yalnızca bir yük dengeleyiciye sahip daha fazla kopya eklersiniz. Kolaylık, tek bir kapsayıcıda veya VM 'de tek bir dağıtımı yönetmekten gelir.

![Tek parçalı kapsayıcılı bir uygulama, iç katmanlar ya da kitaplıklar ile tek bir kapsayıcı içindeki işlevselliğinin çoğunu içerir, bu da kapsayıcıyı birden çok sunucu/VM 'de klonlayarak ölçeklendirir](./media/image1.png)

**Şekil 4-1**. Kapsayıcılı tek parçalı uygulama mimarisine örnek

Şekil 4-1 ' de gösterildiği gibi, her bir kapsayıcıya birden çok bileşen, kitaplık veya iç katman ekleyebilirsiniz. Ancak, bu tek parçalı bir model, "kapsayıcı tek bir işlem" ve bu işlemi bir işlemde yapar "kapsayıcı ilkesiyle çakışabilir, ancak bazı durumlarda tamam olabilir.

Uygulamanın büyümesi durumunda bu yaklaşımın aşağı kısmı, ölçeklendirilmesi gerekir. Uygulamanın tamamı ölçeklenebiliyorsanız, aslında bir sorun değildir. Ancak çoğu durumda, uygulamanın yalnızca birkaç bölümü ölçeklendirmeyi gerektiren sıkıştırma noktalarından, diğer bileşenler daha az kullanılır.

Örneğin, tipik bir e-ticaret uygulamasında, büyük olasılıkla ürün bilgileri alt sistemini ölçeklendirmeniz gerekir, çünkü pek çok müşteri satın alma işleminden farklı ürünlere gözatacağından. Daha fazla müşteri, kendi sepetini ödeme işlem hattını kullanmından kullanıyor. Daha az müşteri, yorum ekler veya satın alma geçmişini görüntüler. Böylece içerik ve pazarlama kampanyalarını yönetmesi gereken yalnızca birkaç çalışanın olması gerekebilir. Tek parçalı tasarımı ölçeklendirirseniz, bu farklı görevlere yönelik tüm kodlar birden çok kez dağıtılır ve aynı şekilde ölçeklendirilir.

Uygulama yatay tekrarlarının ölçeklendirilmesi, uygulamanın farklı bölgelerini bölmek ve benzer iş kavramlarını veya verileri bölümlemek için birden çok yol vardır. Ancak, tüm bileşenlerin ölçeklendirilmesi sorununa ek olarak, tek bir bileşendeki değişiklikler tüm uygulamanın tam yeniden test edilmesini ve tüm örneklerin tam yeniden dağıtılması gerektirir.

Ancak, tek parçalı yaklaşım yaygın bir uygulamadır çünkü uygulamanın geliştirilmesi, mikro hizmetler yaklaşımlarından önce daha kolay. Bu nedenle, birçok kuruluş bu mimari yaklaşımı kullanarak geliştirir. Bazı kuruluşların yeterince iyi sonuçları olsa da, diğerleri sınırlara ulaşırlar. Birçok kuruluş, bu modeli kullanarak uygulamalarını tasarlamış çünkü araçlar ve altyapı, hizmet yönelimli mimariler (SOA) yıl önce oluşturmayı çok zorlaştırıyordu ve uygulama grew 'a kadar gerek olmadığını görmemelidir.

Altyapı açısından, her sunucu aynı ana bilgisayar içinde birçok uygulama çalıştırabilir ve Şekil 4-2 ' de gösterildiği gibi, kaynakların kullanımı için kabul edilebilir bir verimlilik içerebilir.

![Bir konak, her biri ayrı bir kapsayıcıda olmak üzere çeşitli tek parçalı uygulamalar çalıştırabilir.](./media/image2.png)

**Şekil 4-2**. Tek parçalı yaklaşım: Her uygulama bir kapsayıcı olarak çalışan birden çok uygulama çalıştıran konak

Microsoft Azure tek parçalı uygulamalar, her örnek için adanmış VM 'Ler kullanılarak dağıtılabilir. Ayrıca, [Azure sanal makine ölçek kümelerini](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/)kullanarak VM 'leri kolayca ölçeklendirebilirsiniz. [Azure App Service](https://azure.microsoft.com/services/app-service/) , tek parçalı uygulamalar çalıştırabilir ve VM 'leri yönetmeniz gerekmeden örnekleri kolayca ölçeklendirebilir. 2016 ' den itibaren, Azure App Services, her Docker kapsayıcısının tek bir örneğini çalıştırabilir ve dağıtımı basitleştirecek.

Soru-cevap ortamında veya sınırlı bir üretim ortamında, Şekil 4-3 ' de gösterildiği gibi birden çok Docker Konağı sanal makinesi dağıtabilir ve bunları Azure dengeleyicisi kullanarak dengeleyebilirsiniz. Bu, tüm uygulamanın tek bir kapsayıcı içinde bulunduğu için ölçeği kaba bir yaklaşım ile yönetmenizi sağlar.

![Her biri tek parçalı uygulamayla bir kapsayıcı çalıştıran birçok ana bilgisayar.](./media/image3.png)

**Şekil 4-3**. Tek bir kapsayıcı uygulamasını ölçeklendirerek birden çok ana bilgisayar örneği

Çeşitli konaklara dağıtım, geleneksel dağıtım teknikleri ile yönetilebilir. Docker konakları el ile veya elle `docker run` `docker-compose` gerçekleştirilen komutlarla veya sürekli teslim (CD) işlem hatları gibi Otomasyon aracılığıyla yönetilebilir.

## <a name="deploying-a-monolithic-application-as-a-container"></a>Tek parçalı uygulamayı kapsayıcı olarak dağıtma

Tek parçalı uygulama dağıtımlarını yönetmek için kapsayıcıları kullanmanın avantajları vardır. Kapsayıcı örneklerinin ölçeklendirilmesi, ek VM 'Leri dağıtmaktan çok daha hızlı ve daha kolaydır. Sanal Makine Ölçek Kümeleri kullanıyor olsanız da VM 'Lerin başlaması zaman alır. Kapsayıcılar yerine geleneksel uygulama örnekleri olarak dağıtıldığında, uygulamanın yapılandırması VM 'nin bir parçası olarak yönetilir ve bu ideal değildir.

Docker görüntüsü olarak güncelleştirmelerin dağıtımı, çok daha hızlı ve daha verimlidir. Docker görüntüleri genellikle Saniyeler içinde başlar ve piyasaya çıkarma hızlanır. Docker görüntü örneğini aşağı doğru artırma, bir `docker stop` komutu vermek kadar kolay ve genellikle bir saniyeden daha az tamamlanır.

Kapsayıcılar tasarıma göre sabit olduğundan, bozulan VM 'Ler hakkında endişelenmeniz gerekmez. Buna karşılık, bir VM için güncelleştirme betikleri, diskte kalan belirli bir yapılandırma veya dosya için hesap almayı unutabilirler.

Tek parçalı uygulamalar Docker 'tan faydalanabilir, ancak avantajlara dokunuyoruz. Kapsayıcıları yönetmenin ek avantajları, her bir kapsayıcı örneğinin çeşitli örneklerini ve yaşam döngüsünü yöneten kapsayıcı düzenleyicilerinin dağıtımıyla gelir. Tek parçalı uygulamayı, ölçeklendirilebilir, geliştirilmiş ve dağıtılan alt sistemlere bölmek, mikro hizmetler bölgesine giriş noktanşa noktasıdır.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Azure App Service için tek Kapsayıcılı tabanlı bir uygulama yayımlama

Azure 'a dağıtılan bir kapsayıcının doğrulanmasını mi yoksa bir uygulamanın yalnızca tek kapsayıcılı bir uygulama olduğu durumlarda Azure App Service, ölçeklenebilir tek kapsayıcı tabanlı hizmetler sağlamak için harika bir yol sağlar. Azure App Service kullanmak basittir. Kodunuzu almak, Visual Studio 'da derlemek ve doğrudan Azure 'a dağıtmak için git ile harika bir tümleştirme sağlar.

![Visual Studio 'dan Azure App Service için tek bir kapsayıcı uygulamayı yayımlamaya yönelik sihirbaz](./media/image4.png)

**Şekil 4-4**. Visual Studio 'dan Azure App Service için tek kapsayıcılı bir uygulama yayımlama

Docker olmadan, Azure App Service desteklenmeyen diğer yetenekler, çerçeveler veya bağımlılıklara ihtiyaç duymanız durumunda, Azure ekibi App Service bu bağımlılıkları güncelleştirene kadar beklemeniz gerekiyordu. Ya da daha fazla denetiminiz olan Azure Cloud Services veya VM 'Ler gibi diğer hizmetlere geçmeniz gerekiyordu ve uygulamanız için gerekli bir bileşeni veya çerçeveyi yükleyebilirsiniz.

Visual Studio 2017 ve üzeri sürümlerde kapsayıcı desteği, Şekil 4-4 ' de gösterildiği gibi, uygulama ortamınıza istediğiniz şeyi dahil etmenizi sağlar. Bir kapsayıcıda çalıştırdığınız için, uygulamanıza bir bağımlılık eklerseniz, bu bağımlılığı Dockerfile veya Docker yansımanıza dahil edebilirsiniz.

Şekil 4-4 ' de de gösterildiği gibi, yayımlama akışı bir görüntüyü kapsayıcı kayıt defteri aracılığıyla iter. Bu, Azure Container Registry (Azure 'daki dağıtımlarınıza bir kayıt defteri yakın ve Azure Active Directory gruplar ve hesaplar ile güvenliği sağlanmış) veya Docker Hub veya şirket içi kayıt defteri gibi başka bir Docker kayıt defteri olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)İleri
>[](docker-application-state-data.md)
