---
title: Tek yapılı uygulamalar
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 17dabb143a1948cbcfa748b4c3bbcff5a57d2c24
ms.sourcegitcommit: 82a3f7882bc03ed733af91fc2a0b113195bf5dc7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2018
ms.locfileid: "52743275"
---
# <a name="monolithic-applications"></a>Tek yapılı uygulamalar

Bu senaryoda, bir tek ve tek parça bir web uygulaması veya hizmeti oluşturma ve kapsayıcı olarak dağıtma. Uygulama içinde yapısı tek parça olmayabilir; birkaç kitaplıklar, bileşenler veya hatta katmanları (uygulama katmanı, etki alanı katmanı, veri erişim katmanı, vb.) oluşturan. Harici olarak tek bir işlem, tek bir web uygulaması veya tek bir hizmet gibi tek bir kapsayıcı olduğundan.

Bu model yönetmek için uygulamayı temsil etmek için tek bir kapsayıcı dağıtırsınız. Ölçeklendirme için önde gelen bir yük dengeleyici ile birkaç kopya eklemeniz yeterlidir. Basitlik, bir çoklu kapsayıcı veya sanal makine (VM) tek bir dağıtım yönetmesini gelir.

Kapsayıcı yalnızca bir şeyi yapar ve tek bir işlemde çalıştığı asıl, tek parçalı çakışma modelidir. Şekil 4-1'de gösterildiği gibi birden çok bileşenleri/kitaplıkları veya her bir kapsayıcı içindeki iç Katmanlar içerebilir.

![](./media/image1.png)

Şekil 4-1: örnek olarak tek parça uygulama mimarisi

Bu yaklaşımın bir dezavantajı, varsa veya uygulama büyürken, ölçeklendirme gerektiren gelir. Uygulamanın tamamı ölçeği, gerçekten bir sorun değildir. Diğer bileşenleri daha az kullanılır ancak çoğu durumda, uygulamanın bazı bölümlerini sıkıştırma ölçeklendirme gerektiren noktalarıdır.

Tipik bir e-ticaret örneği kullanarak, büyük olasılıkla gerekenler ürün bilgi bileşeni ölçeklendirmektir. Pek çok daha fazla müşteriye satın çok ürünlerin göz atın. Daha fazla müşteriye kendi Sepeti ödeme işlem hattını kullanma daha kullanın. Daha az müşteriler, yorum eklemek veya satın alma geçmişlerini görüntüleyin. Ve büyük olasılıkla çalışanlar, içerik ve pazarlama kampanyaları yönetmek için gereken tek bir bölgede olması gerekir. Tek yapılı tasarım ölçeğini genişleterek tüm kodlar dağıtılan birden çok kez.

Ek olarak "ölçek-her şeyi" sorun, tek bir bileşen için bir değişiklik yapılması tam yeniden dağıtma işlemi tüm örneklerin yanı sıra uygulamanın tamamı tam çözülüp.

Tek parçalı bir yaklaşım için ortaktır ve birçok kuruluşun mimari bu yöntemi ile geliştirdiğiniz. Başkalarının sınırları karşılaştığınız oysa birçok iyi yeterli sonuçları keyfini çıkarın. Çoğu araçları ve altyapı SOAs derleme çok zor ve bunlar gereken görmediniz çünkü bu modeli uygulamalarında tasarlanmış — kadar uygulamayı büyüdü.

Altyapı açısından bakıldığında, her sunucu aynı konak içindeki birçok uygulama çalıştırabilir ve Şekil 4-2'de gösterildiği gibi kaynakları kullanımınızı verimliliği kabul edilebilir bir oran olması.

![](./media/image2.png)

Şekil 4-2: birden çok uygulama/kapsayıcı çalıştıran bir konağa

Her örneği için özel VM'ler kullanarak azure'da tek yapılı uygulamalar dağıtabilirsiniz. Kullanarak [Azure VM ölçek kümeleri](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), Vm'leri bir kolayca ölçeklendirebilirsiniz. [Azure uygulama hizmetleri](https://azure.microsoft.com/services/app-service/) tek yapılı uygulamaları çalıştırabilir ve Vm'leri yönetmek zorunda kalmadan örneklerini kolayca ölçeklendirin. 2016 tarihinden beri Azure uygulama hizmetleri dağıtımını basitleştirme amacıyla da Docker kapsayıcılar'ın tek örneklerine çalıştırabilirsiniz. Ve Docker kullanarak Docker konağı olarak tek bir VM dağıtma ve birden çok örneğini çalıştırmak. Azure, Şekil 4-3'te gösterildiği gibi kullanarak ölçeklendirme yönetebilirsiniz.

![](./media/image3.png)

Şekil 4-3: bir tek Docker uygulama uygulamalar/kapsayıcıları ölçeklendirme-giden birden çok konak

Dağıtım çeşitli Konaklara geleneksel dağıtım teknikleri aracılığıyla yönetebilirsiniz. Docker ana bilgisayarları gibi komutları kullanarak yönetebileceğiniz `docker run` biz daha sonra bu e-kitap açıklayan sürekli teslim (CD) işlem hatları gibi Otomasyon aracılığıyla el ile.

## <a name="monolithic-application-deployed-as-a-container"></a>Bir kapsayıcı dağıtılan tek parçalı uygulama

Tek parça dağıtımlarını yönetmek için kapsayıcılar'ı kullanmanın avantajları vardır. Kapsayıcı örnekleri ölçeklendirme, çok daha hızlı ve ek sanal makineleri dağıtma kolaydır. VM ölçek kümeleri, Docker kapsayıcılarınız barındırmak için gerekli olan, Vm'leri ölçeklendirmek için harika bir özellik olsa da bunlar ayarlamak için zaman ayırın. Uygulama örnekleri olarak dağıtıldığında, uygulama yapılandırmasını VM bir parçası olarak yönetilir.

Docker görüntülerini çok daha hızlı olduğundan, güncelleştirmeleri dağıtmak ve etkili ağ. Vn örnekleri ek Vm'lerden kaynaklanan ek maliyetleri ortadan Vn 1 örneklerinizin aynı ana bilgisayar üzerinde ayarlanabilir. Docker görüntülerini genellikle piyasaya çıkarma hızlandırma saniyeler içinde başlayın. Bir Docker örneğini bozmadan çağırma olarak kolayca `docker stop` komutu, genellikle kısa bir saniye içinde tamamlanıyor.

Kapsayıcılar tasarım gereği, doğası gereği sabit olduğundan, hiçbir zaman bazı belirli bir yapılandırma veya dosya diskte hesap bir güncelleştirme betiğini unuttum çünkü bozuk VM'ler hakkında endişelenmeniz gerekmiyor.

Tek yapılı uygulamaları Docker yararlı olabilir ancak biz avantajlardan yalnızca ipuçları temas. Kapsayıcıları yönetme büyük avantajlar çeşitli örnekleri ve her kapsayıcı örneği yaşam döngüsünü yönetme kapsayıcı düzenleyicileri ile dağıtması gelir. Ölçeği, geliştirilen ve dağıtılan ayrı ayrı alt sistemler tek parça uygulamasına'kurmak bozucu, mikro hizmetlerin bölge içinde giriş noktası niteliğindedir.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Tek bir Docker kapsayıcı uygulamasını Azure App Service'te yayımlama

Ya da hızlı bir doğrulama Azure'a dağıtılan bir kapsayıcının almak istediğiniz veya uygulamayı olduğundan yalnızca bir tek kapsayıcı uygulaması, Azure App Services ölçeklenebilir tek kapsayıcı hizmetleri sağlamak için harika bir yol sağlar.

Azure App Service'i kullanarak, kullanımı kolay olan ve başlayabilirsiniz ve harika Git sağladığından hızlıca çalışmaya tümleştirme, kodunuzu almak için Microsoft Visual Studio'da derleyin ve doğrudan Azure'a dağıtın. Ancak, geleneksel olarak (hiçbir Docker ile), diğer özellikleri, çerçeveleri veya uygulama hizmetleri, desteklenmeyen bağımlılıkları gerekirse bu bağımlılıkların App Service'te Azure ekibi güncelleştirmeleri için beklemeniz gerektiği veya gibi diğer hizmetlere geçiş Service Fabric, bulut Hizmetleri veya bile düz VM'ler, daha fazla denetime sahip olursunuz ve uygulamanız için gerekli bileşen veya framework yükleyebilirsiniz.

Şimdi, Bununla birlikte, (Microsoft Connect 2016'da, Kasım 2016'da açıkladığımız) ve Azure App Service kapsayıcı desteği Visual Studio 2017 kullanırken Şekil 4‑4 ' gösterildiği gibi uygulama ortamınızda istediğiniz dahil etme yeteneği verir. Bir kapsayıcıda çalıştığından uygulamanıza bir bağımlılık eklediyseniz, bu bağımlılıkların Dockerfile ya da Docker görüntünüzü dahil olmak üzere özelliğine sahip olursunuz.

![](./media/image4.png)

Şekil 4-4: bir kapsayıcı Visual Studio uygulamalar/kapsayıcılardan Azure App Service'e yayımlama

Şekil 4-4, aynı zamanda yayımlama akışı görüntüyü Azure Container Registry (bir kayıt defteri Azure dağıtımlarınız için neredeyse ve Azure Active Directory'de gruplar ve hesaplar tarafından güvenliği sağlanan) olabilecek bir kapsayıcı kayıt defteri veya başka bir Docker kayıt aracılığıyla gönderim gösterir Docker Hub veya şirket içi kayıt defterleri gibi.

>[!div class="step-by-step"]
>[Önceki](common-container-design-principles.md)
>[İleri](state-and-data-in-docker-applications.md)