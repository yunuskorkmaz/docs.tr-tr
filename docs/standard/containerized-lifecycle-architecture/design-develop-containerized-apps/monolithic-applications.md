---
title: Tek yapılı uygulamalar
description: Tek yapılı uygulamaları kapsayıcıya alma için temel kavramları anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e7454100b09f602e1e103c38685609e1dab62fe9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644987"
---
# <a name="monolithic-applications"></a>Tek yapılı uygulamalar

Bu senaryoda, tek ve tek parça bir web uygulaması veya hizmeti oluşturma ve kapsayıcı olarak dağıtma. Uygulama içinde yapısı tek parça olmayabilir; birkaç kitaplıklar, bileşenler veya hatta katmanları (uygulama katmanı, etki alanı katmanı, veri erişim katmanı, vb.) oluşturan. Harici olarak tek bir işlem, tek bir web uygulaması veya tek bir hizmet gibi tek bir kapsayıcı olduğundan.

Bu model yönetmek için uygulamayı temsil etmek için tek bir kapsayıcı dağıtırsınız. Ölçeklendirme için önde gelen bir yük dengeleyici ile birkaç kopya eklemeniz yeterlidir. Basitlik, bir çoklu kapsayıcı veya sanal makine (VM) tek bir dağıtım yönetmesini gelir.

Kapsayıcı yalnızca bir şeyi yapar ve tek bir işlemde çalıştığı asıl, tek parçalı çakışma modelidir. Şekil 4-1'de gösterildiği gibi birden çok bileşenleri/kitaplıkları veya her bir kapsayıcı içindeki iç Katmanlar içerebilir.

![Monolitik bir uygulamayı tüm veya çoğu işlevlerini tek bir işlem veya kapsayıcı içinde vardır ve bu iç katmanları veya kitaplıkları bileşenlerden.](./media/image1.png)

**Şekil 4-1.** Tek parçalı uygulama mimarisi örneği

Bu yaklaşımın bir dezavantajı, varsa veya uygulama büyürken, ölçeklendirme gerektiren gelir. Uygulamanın tamamı ölçeği, gerçekten bir sorun değildir. Diğer bileşenleri daha az kullanılır ancak çoğu durumda, uygulamanın bazı bölümlerini sıkıştırma ölçeklendirme gerektiren noktalarıdır.

Tipik bir e-ticaret örneği kullanarak, büyük olasılıkla gerekenler ürün bilgi bileşeni ölçeklendirmektir. Pek çok daha fazla müşteriye satın çok ürünlerin göz atın. Daha fazla müşteriye kendi Sepeti ödeme işlem hattını kullanma daha kullanın. Daha az müşteriler, yorum eklemek veya satın alma geçmişlerini görüntüleyin. Ve büyük olasılıkla çalışanlar, içerik ve pazarlama kampanyaları yönetmek için gereken tek bir bölgede olması gerekir. Tek yapılı tasarım ölçeğini genişleterek tüm kodlar dağıtılan birden çok kez.

Ek olarak "ölçek-her şeyi" sorun, tek bir bileşen için bir değişiklik yapılması tam yeniden dağıtma işlemi tüm örneklerin yanı sıra uygulamanın tamamı tam çözülüp.

Tek parçalı bir yaklaşım için ortaktır ve birçok kuruluşun mimari bu yöntemi ile geliştirdiğiniz. Başkalarının sınırları karşılaştığınız oysa birçok iyi yeterli sonuçları keyfini çıkarın. Çoğu araçları ve altyapı SOAs derleme çok zor ve bunlar gereken görmediniz çünkü bu modeli uygulamalarında tasarlanmış — kadar uygulamayı büyüdü.

Altyapı açısından bakıldığında, her sunucu aynı konak içindeki birçok uygulama çalıştırabilir ve Şekil 4-2'de gösterildiği gibi kaynakları kullanımınızı verimliliği kabul edilebilir bir oran olması.

![Tek bir ana bilgisayara birden fazla uygulama ayrı kapsayıcılarda çalıştırabilirsiniz.](./media/image2.png)

**Şekil 4-2.** Birden çok uygulama/kapsayıcı çalıştıran bir konağa

Son olarak, bir kullanılabilirlik açısından, tek parçalı uygulamalarla bir bütün olarak dağıtılmalıdır; diğer bir deyişle, şunları yapmalısınız durumunda *durdurup*, tüm işlevlere ve tüm kullanıcılar dağıtım penceresi sırasında etkilenecek. Belirli durumlarda, Azure ve kapsayıcılar bunlardan en aza indirmek ve Şekil 4-3'te görüldüğü gibi uygulamanızın kapalı kalma süresi olasılığını.

Her örneği için özel VM'ler kullanarak azure'da tek yapılı uygulamalar dağıtabilirsiniz. Kullanarak [Azure VM ölçek kümeleri](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), Vm'leri bir kolayca ölçeklendirebilirsiniz.

Ayrıca [Azure uygulama hizmetleri](https://azure.microsoft.com/services/app-service/) tek yapılı uygulamaları çalıştırma ve Vm'leri yönetmek zorunda kalmadan örneklerini kolayca ölçeklendirin. Azure uygulama hizmetleri, dağıtımını basitleştirme amacıyla da Docker kapsayıcıları tek örneğini çalıştırabilirsiniz.

Docker ana bilgisayarları olarak birden çok VM dağıtın ve kapsayıcıları VM başına herhangi bir sayıda çalıştırın. Ardından, Azure Load Balancer'ı kullanarak, Şekil 4-3'te, gösterildiği gibi ölçeklendirme yönetebilirsiniz.

![Monolitik bir uygulamayı kapsayıcılarda her bir uygulamanın çalıştığı farklı Konaklara genişletilmiş.](./media/image3.png)

**Şekil 4-3**. Bir tek Docker uygulama uygulamalar/kapsayıcıları ölçeklendirme-giden birden çok konak

Geleneksel dağıtım teknikleri aracılığıyla konakları kendilerini dağıtımını yönetebilirsiniz.

Docker kapsayıcıları gibi komutları kullanarak komut satırından yönetebilmeniz için `docker run` ve `docker-compose up`, ve ayrıca sürekli teslim (CD) işlem hatlarını otomatikleştirin ve Docker konakları Azure DevOps hizmetlerinden örneği için dağıtın.

## <a name="monolithic-application-deployed-as-a-container"></a>Bir kapsayıcı dağıtılan tek parçalı uygulama

Tek parça dağıtımlarını yönetmek için kapsayıcılar'ı kullanmanın avantajları vardır. Kapsayıcı örnekleri ölçeklendirme, çok daha hızlı ve ek sanal makineleri dağıtma kolaydır.

Docker görüntülerini çok daha hızlı olduğundan, güncelleştirmeleri dağıtmak ve etkili ağ. Docker kapsayıcıları, genellikle piyasaya çıkarma hızlandırma saniyeler içinde başlayın. Bir Docker kapsayıcısı bozmadan çağırma olarak kolayca `docker stop` komutu, genellikle kısa bir saniye içinde tamamlanıyor.

Kapsayıcılar tasarım gereği, doğası gereği sabit olduğundan, hiçbir zaman bazı belirli bir yapılandırma veya dosya diskte hesap bir güncelleştirme betiğini unuttum çünkü bozuk VM'ler hakkında endişelenmeniz gerekmiyor.

Tek yapılı uygulamaları Docker yararlı olabilir ancak biz avantajlardan yalnızca ipuçları temas. Kapsayıcıları yönetme büyük avantajlar, çeşitli örnekleri ve her kapsayıcı örneği yaşam döngüsünü yönetme kapsayıcı düzenleyicileri ile dağıtması gelir. Ölçeği, geliştirilen ve dağıtılan ayrı ayrı alt sistemler tek parça uygulamasına'kurmak bozucu, mikro hizmetlerin bölge içinde giriş noktası niteliğindedir.

Kapsayıcılar "kaldırma ve kaydırma" tek parçalı uygulamalarla ve uygulamalarınızı nasıl modernleştirmelisiniz hakkında bilgi edinmek için bu ek Microsoft Kılavuzu okuyabilirsiniz [Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını Modernleştirme ](../../modernize-with-azure-and-containers/index.md), PDF olarak karşıdan yükleyebileceğiniz <https://aka.ms/LiftAndShiftWithContainersEbook>.

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Tek bir Docker kapsayıcı uygulamasını Azure App Service'e yayımlama

Ya da hızlı bir doğrulama Azure'a dağıtılan bir kapsayıcının almak istediğiniz veya uygulamayı olduğundan yalnızca bir tek kapsayıcı uygulaması, Azure App Services ölçeklenebilir tek kapsayıcı hizmetleri sağlamak için harika bir yol sağlar.

Azure App Service'i kullanarak, kullanımı kolay olan ve başlayabilirsiniz ve harika Git sağladığından hızlıca çalışmaya tümleştirme, kodunuzu almak için Microsoft Visual Studio'da derleyin ve doğrudan Azure'a dağıtın. Ancak, geleneksel olarak (hiçbir Docker ile), diğer özellikleri, çerçeveleri veya uygulama hizmetleri, desteklenmeyen bağımlılıkları gerekirse bu bağımlılıkların App Service'te Azure ekibi güncelleştirmeleri için beklemeniz gerektiği veya gibi diğer hizmetlere geçiş Service Fabric, bulut Hizmetleri veya bile düz VM'ler, daha fazla denetime sahip olursunuz ve uygulamanız için gerekli bileşen veya framework yükleyebilirsiniz.

Şimdi, Şekil 4-4'te gösterildiği gibi Visual Studio 2017'yi kullanarak, kapsayıcı desteği Azure App Service, uygulama ortamınızda istediğiniz dahil etme yeteneği sağlar. Bir kapsayıcıda çalıştırdığınız olduğundan, uygulamanıza bir bağımlılık eklediyseniz, bu bağımlılıkların Dockerfile ya da Docker görüntünüzü dahil olmak üzere özelliğine sahip olursunuz.

![Kapsayıcı kayıt defteri Seçicisi vurgulama, bir Azure app Service'e yayımlama için Visual Studio Sihirbazı'nı görüntüleyin.](./media/image4.png)

**Şekil 4-4**. Bir kapsayıcı, Visual Studio uygulamalar/kapsayıcılardan Azure App Service'te yayımlama

Şekil 4-4, aynı zamanda yayımlama akışı görüntüyü Azure Container Registry (bir kayıt defteri Azure dağıtımlarınız için neredeyse ve Azure Active Directory'de gruplar ve hesaplar tarafından güvenliği sağlanan) olabilecek bir kapsayıcı kayıt defteri veya başka bir Docker kayıt aracılığıyla gönderim gösterir Docker Hub veya şirket içi kayıt defterleri gibi.

>[!div class="step-by-step"]
>[Önceki](common-container-design-principles.md)
>[İleri](state-and-data-in-docker-applications.md)
