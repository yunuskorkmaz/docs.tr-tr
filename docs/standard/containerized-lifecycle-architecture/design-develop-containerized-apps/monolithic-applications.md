---
title: Tek yapılı uygulamaları
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: fe25fa8772c60625c5564d5e7194957366a6010a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572755"
---
# <a name="monolithic-applications"></a>Tek yapılı uygulamaları

Bu senaryoda, bir tek ve tek yapılı bir web uygulaması veya hizmeti oluşturma ve bir kapsayıcı olarak dağıtma. Uygulama içinde yapısı tek yapılı olmayabilir; birkaç kitaplıkları, bileşenler veya hatta Katmanlar (uygulama katmanı, etki alanı katman, veri erişim katmanı, vb.) oluşturan. Harici olarak tek bir işlem, tek bir web uygulaması veya tek bir hizmet gibi tek bir kapsayıcı değil.

Bu model yönetmek için uygulamayı temsil etmek için tek bir kapsayıcı dağıtın. Ölçeklemek için birkaç daha fazla yük dengeleyici önde kopyalarla eklemeniz yeterlidir. Basitlik, tek bir dağıtım bir tek kapsayıcı veya sanal makine (VM) yönetme gelir.

Bir kapsayıcı yalnızca bir şeyi yapar ve tek bir işlemde mu asıl, tek yapılı düzeni çakışma ' dir. Şekil 4-1'de gösterildiği gibi birden çok bileşenleri/kitaplıklarına veya her kapsayıcı içindeki iç katmanları içerebilir.

![](./media/image1.png)

Şekil 4-1: örneği tek yapılı uygulama mimarisi

Bu yaklaşımın dezavantajı, veya uygulama büyürken ölçeklendirmek için gerektiren gelir. Tüm uygulama ölçeklendirilmiş, onu gerçekten bir sorun değildir. Daha az kullanılan diğer bileşenleri ancak bununla birlikte, çoğu durumda, birkaç uygulama bölümlerinin sıkıştırma ölçeklendirme, gerektiren noktalarıdır.

Tipik e-ticaret örnek, büyük olasılıkla gerekenler ürün bilgi bileşeni ölçeklendirmek için kullanmaktır. Birçok daha fazla müşteri ürünleri bunları satın daha göz atın. Daha fazla müşteriler kendi Sepeti ödeme işlem hattını kullanma daha kullanın. Daha az müşteriler, yorum eklemek veya satın alma geçmişlerini görüntüleyin. Ve büyük olasılıkla, içerik ve pazarlama kampanyaları yönetmek için gerekli olan tek bir bölgedeki çalışanlar sayıda vardır. Tek yapılı tasarım ölçeklendirme tarafından tüm kod dağıtıldığı birden çok kez.

Ek olarak "ölçek-her şeyi" sorun, tek bir bileşen değişiklik gerektiren tüm örnekleri tam çözümünüzün yeniden dağıtımını yanı sıra tüm uygulama tam retesting.

Tek yapılı bir yaklaşım yaygındır ve birçok kuruluş bu mimari yöntemi ile geliştirdiğiniz. Başkalarının sınırları karşılaştığınız ancak birçok iyi yeterli sonuçları keyfini çıkarın. Birçok uygulamalarını bu modelde araçları ve altyapısı SOAs oluşturmak çok zor ve gereken görmek istemediğiniz için tasarlanmış — uygulama büyüdü kadar.

Her sunucu altyapı açısından bakıldığında, aynı ana içinde birçok uygulamayı çalıştırın ve Şekil 4-2'de gösterildiği gibi kaynakları kullanımınızı verimlilik kabul edilebilir bir oran olması.

![](./media/image2.png)

Şekil 4-2: birden çok apps/kapsayıcı çalıştıran bir ana bilgisayar

Her bir örneği için özel VM'ler kullanarak azure'da tek yapılı uygulamaları dağıtabilirsiniz. Kullanarak [Azure VM ölçek kümesi](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), sanal makineleri kolayca ölçeklendirebilirsiniz. [Azure App Services](https://azure.microsoft.com/en-us/services/app-service/) tek yapılı uygulamaları çalıştırabilir ve sanal makineleri yönetmek zorunda kalmadan örnekleri kolayca ölçeklendirin. 2016, Azure App Services Dağıtımı basitleştirme Docker kapsayıcıları, de, tek tek örneklerini çalıştırabilirsiniz. Ve Docker kullanarak, Docker ana bilgisayar olarak tek bir VM'yi dağıtmak ve birden çok örneği çalıştırın. Şekil 4-3'te gösterildiği gibi Azure dengeleyici kullanarak ölçeklendirme yönetebilirsiniz.

![](./media/image3.png)

Şekil 4-3: bir tek Docker uygulama apps/kapsayıcıları ölçeklendirme birden çok ana bilgisayar

Geleneksel dağıtım teknikleri aracılığıyla çeşitli konakları dağıtımına yönetebilirsiniz. Docker ana bilgisayarları gibi komutları kullanarak yönetebileceğiniz `docker run` biz daha sonra bu e-kitap içinde açıklayan sürekli teslim (CD) ardışık düzen gibi automation aracılığıyla el ile.

## <a name="monolithic-application-deployed-as-a-container"></a>Bir kapsayıcı olarak dağıtılan tek yapılı uygulaması

Tek yapılı dağıtımları yönetmek için kapsayıcıları kullanmanın avantajları vardır. Kapsayıcıları örneklerini ölçeklendirme çok daha hızlı ve ek sanal makineleri dağıtma daha kolay olur. VM ölçek kümesi, Docker kapsayıcıları barındırmak için gerekli olan sanal makineleri ölçeklendirmek için harika bir özellik olsa da bunlar ayarlamak için zaman ayırın. Uygulama örnekleri dağıtıldığında, uygulama yapılandırmasını VM bir parçası olarak yönetilir.

Şu ana kadar daha hızlı Docker görüntüleri olarak güncelleştirmeleri dağıtmak ve ağ verimli. Vn örnekleri ek Vm'lerden kaynaklanan eklenen maliyetlerini ortadan Vn 1 örneklerinizi aynı ana bilgisayar üzerinde ayarlanabilir. Docker görüntüleri genellikle piyasa sürümlerini hızlandırma saniye cinsinden başlatın. Docker örneği hattının kaldırılması çağırma olarak kadar kolay `docker stop` genellikle değerinden bir saniyede Tamamlanıyor komutu.

Kapsayıcıları tasarım gereği, kendiliğinden değişmez olduğundan, hiçbir zaman bazı belirli yapılandırma veya diskte dosya için hesap bir güncelleştirme betiğini unuttunuz çünkü bozuk VM'ler hakkında endişelenmeniz gerekir.

Tek yapılı uygulamaları Docker yararlı olabilir ancak biz avantajlarından yalnızca ipuçları temas. Kapsayıcıları yönetme büyük avantajları gelir çeşitli örnekleri ve her bir kapsayıcı örnek yaşam döngüsünü yönetme kapsayıcı orchestrators ile dağıtma. Ölçeği, geliştirilmiş ve tek tek dağıttığınız alt sistemleri tek yapılı uygulamasına parçalamak, giriş bölgesi içine mikro noktasıdır.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Azure App Service'e tek bir Docker kapsayıcısı uygulamayı yayımlama

Ya da Azure'a dağıtılan bir kapsayıcı hızlı doğrulanması almak istediğiniz olduğundan veya bir uygulama olduğundan yalnızca bir tek kapsayıcı uygulaması, Azure App Services ölçeklenebilir tek kapsayıcı hizmetlerini sağlamak için harika bir yol sağlar.

Azure uygulama hizmeti ile sezgisel ve alma ve harika Git sağladığından hızla tümleştirme, kodunuzu almak için Microsoft Visual Studio derleme çalıştırıp doğrudan Azure'a dağıtma. Ancak, geleneksel olarak (docker'la yok), diğer özellikleri, çerçeveleri veya uygulama Hizmetleri'nde desteklenmeyen bağımlılıkları gerekirse bu bağımlılıkların App Service'teki Azure ekibi güncelleştirmeleri kadar bekleyin için gereken veya gibi diğer hizmetlerine geçti Service Fabric, bulut Hizmetleri veya bile düz VM'ler, kendisi için daha fazla denetime sahip ve uygulamanız için gerekli bir bileşen veya framework yükleyebilirsiniz.

Şimdi, ancak (Kasım 2016 ' Microsoft Connect 2016 duyurdu) ve kapsayıcı desteği Azure App Service'de Visual Studio 2017 kullanırken Şekil 4‑4 gösterildiği gibi uygulama ortamınızda istediğiniz dahil etme yeteneği verir. Bir kapsayıcıda çalıştığından, uygulamanıza bir bağımlılık eklediyseniz, bu bağımlılıkların Dockerfile veya Docker görüntünüzü de dahil olmak üzere özelliği alın.

![](./media/image4.png)

Şekil 4-4: Azure App Service'e bir kapsayıcı, Visual Studio apps/kapsayıcılardan yayımlama.

Şekil 4-4, aynı zamanda Yayımla akış görüntüyü Azure kapsayıcı (bir kayıt defteri dağıtımlarınızda Azure yakınında ve Azure Active Directory grupları ve hesaplarını tarafından güvenliği sağlanan) kayıt defteri olabilen bir kapsayıcı kayıt defteri veya başka bir Docker kayıt aracılığıyla iter gösterir Docker hub'a veya şirket içi kayıt defterleri gibi.


>[!div class="step-by-step"]
[Önceki] (ortak-kapsayıcı-design-principles.md) [sonraki] (state-and-data-in-docker-applications.md)
