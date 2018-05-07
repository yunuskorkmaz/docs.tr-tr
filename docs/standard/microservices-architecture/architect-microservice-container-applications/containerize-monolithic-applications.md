---
title: Containerizing tek yapılı uygulamaları
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Containerizing tek yapılı uygulamaları
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f5d00c6ce4c965d66937dae3f8e5453883afb4b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="containerizing-monolithic-applications"></a>Containerizing tek yapılı uygulamaları

Bir tek, monolithically dağıtılan web uygulaması veya hizmeti geliştirmek ve kapsayıcı olarak dağıtmak isteyebilirsiniz. Uygulama dahili olarak tek yapılı olmayabilir ancak gibi birkaç kitaplıkları, bileşenler veya hatta Katmanlar (uygulama katmanı, etki alanı katman, veri erişim katmanı, vb.) yapılandırılmış. Harici olarak ancak, tek bir kapsayıcı değildir — tek bir işlem, bir tek bir web uygulaması veya bir hizmettir.

Bu model yönetmek için uygulamayı temsil etmek için tek bir kapsayıcı dağıtın. Ölçeği için yalnızca bir yük dengeleyici önde ile daha fazla kopyası ekleyin. Basitlik, tek bir dağıtım bir tek kapsayıcı veya VM yönetme gelir.

![](./media/image1.png)

**Şekil 4-1**. Örnek kapsayıcılı tek yapılı uygulama mimarisi

Şekil 4-1'de gösterildiği gibi her kapsayıcısında birden çok bileşenleri, kitaplıkları veya iç Katmanlar içerebilir. Ancak, bu tek yapılı deseni "bir kapsayıcı bir şeyi yapar ve tek bir işlemde mu", ancak olabilir kapsayıcı İlkesi ile çakışabilir için bazı durumlarda Tamam olabilir.

Bu yaklaşımın bir dezavantajı uygulama büyürse ölçeklendirmek için gerektiren korumalı hale gelir. Tüm uygulama ölçeklendirme yapabilir, onu gerçekten bir sorun değildir. Bununla birlikte, çoğu durumda, yalnızca birkaç uygulama ölçeklendirme, diğer bileşenler durumdayken gerektiren daha az kullanılan sıkıştırma noktaları bölümlerdir.

Bunları satın daha birçok daha fazla müşteri ürünleri gözatmak için örneğin, bir tipik e-ticaret uygulaması ürün bilgi alt ölçeklendirmek gerekmesi muhtemeldir. Daha fazla müşteriler kendi Sepeti ödeme işlem hattını kullanma daha kullanın. Daha az müşteriler, yorum eklemek veya satın alma geçmişlerini görüntüleyin. Ve içerik ve pazarlama kampanyaları yönetmeniz gereken çalışanlar, sayıda olabilir. Tek yapılı tasarım ölçeği, bu farklı görevler için tüm kod birden çok kez dağıtılır ve aynı düzeyde ölçeklendirilmiş.

Uygulama ölçeklendirme birden çok yolu vardır: uygulama ve bölümleme benzer iş kavramları ve verileri işleminin farklı alanları bölünmesinde yatay çoğaltma. Ancak, tüm uygulama ve tüm örnekleri tam çözümünüzün yeniden dağıtımını tam retesting tüm bileşenleri ölçeklendirme sorun ek olarak, tek bir bileşen değişiklikler gerektirir.

Ancak, bir uygulamanın geliştirilmesi mikro yaklaşımlar için başlangıçta daha kolay olduğundan tek yapılı bir yaklaşım ortak değildir. Bu nedenle, birçok kuruluş mimari bu yaklaşımı kullanarak geliştirin. Bazı kuruluşlar iyi yeterli sonuçları olmuş olsa da, diğerlerinin sınırları devreyi. Birçok kuruluş araçları ve altyapı hizmeti oluşturmak için yıl önce mimarileri (SOA) yönelik ve gereken listelenmiyor çok zor yapıldığı için bu modeli kullanarak uygulamalarını tasarlanmış — uygulama büyüdü kadar.

Her sunucu altyapısı açısından bakıldığında, aynı ana içinde birçok uygulama çalıştırın ve Şekil 4-2'de gösterildiği gibi kaynak kullanımı kabul edilebilir bir oran verimlilik sahip.

![](./media/image2.png)

**Şekil 4-2**. Tek yapılı bir yaklaşım: ana bilgisayar birden fazla uygulama çalıştıran bir kapsayıcı olarak çalışan her uygulama

Microsoft Azure tek yapılı uygulamalarda özel VM'ler için her bir örneği kullanılarak dağıtılabilir. Ayrıca, kullanarak [Azure VM ölçek kümesi](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), sanal makineleri kolayca ölçeklendirebilirsiniz. [Azure uygulama hizmeti](https://azure.microsoft.com/services/app-service/) ayrıca tek yapılı uygulamaları çalıştırabilir ve sanal makineleri yönetmek gerek kalmadan örnekleri kolayca ölçeklendirin. 2016, Azure App Services Dağıtımı basitleştirme Docker kapsayıcıları de, tek tek örneklerini çalıştırabilirsiniz.

QA ortamında veya sınırlı üretim ortamında olarak, birden çok Docker ana bilgisayar sanal makineleri dağıtmak ve bunları Şekil 4-3'te gösterildiği gibi Azure dengeleyicisi kullanarak Dengeleme. Tüm uygulama tek bir kapsayıcıda durur çünkü bu, bir birimi kaba yaklaşımda ölçeklendirme yönetmenizi sağlar.

![](./media/image3.png)

**Şekil 4-3**. Bir tek kapsayıcı uygulamasını ölçeklendirme birden çok ana bilgisayar örneği

Çeşitli konaklarına dağıtım geleneksel dağıtım teknikleri ile yönetilebilir. Docker ana bilgisayarları gibi komutlarla yönetilebilir `docker run` veya `docker-compose` el ile veya kesintisiz teslim (CD) ardışık düzen gibi automation aracılığıyla gerçekleştirilir.

## <a name="deploying-a-monolithic-application-as-a-container"></a>Tek yapılı bir uygulama bir kapsayıcı olarak dağıtma

Tek yapılı uygulama dağıtımlarını yönetmek için kapsayıcıları kullanmanın avantajları vardır. Kapsayıcı örnekleri ölçeklendirme çok daha hızlı ve ek sanal makineleri dağıtma daha kolay olur. VM ölçek kümesi kullansanız bile, sanal makineleri başlatmak için zaman ayırın. Geleneksel uygulama örnekleri kapsayıcıları yerine olarak dağıtıldığında, uygulama yapılandırmasını ideal olmayan VM bir parçası olarak yönetilir.

Şu ana kadar daha hızlı Docker görüntüleri olarak güncelleştirmeleri dağıtmak ve ağ verimli. Docker görüntüleri hangi piyasa sürümlerini hızlandırır saniye cinsinden genellikle başlatın. Docker görüntü örneği hattının kaldırılması veren olarak kadar kolay bir `docker stop` komut ve genellikle değerinden bir saniyede tamamlar.

Kapsayıcıları tasarım gereği değişmez olduğundan, hiçbir zaman bozuk VM'ler hakkında endişelenmeniz gerekir. Buna karşılık, bir VM için güncelleştirme kodları bazı belirli yapılandırma veya diskte dosya için hesap unuttunuz.

Tek yapılı uygulamalar Docker yararlanabilir olsa da, biz yalnızca faydaları üzerine temas. Kapsayıcıları yönetme ek avantajları çeşitli örnekleri ve her bir kapsayıcı örnek ömrünü yönetmek kapsayıcı orchestrators ile dağıtma gelir. Ölçeği, geliştirilmiş ve tek tek dağıttığınız alt sistemleri tek yapılı uygulamasına parçalamak, giriş bölgesi içine mikro noktasıdır.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Azure App Service'e tek kapsayıcı tabanlı bir uygulama yayımlama

Azure'a dağıtılan bir kapsayıcı doğrulanması almak istediğinizi veya bir uygulamayı yalnızca bir tek kapsayıcısı uygulamasına olduğunda, Azure uygulama hizmeti ölçeklenebilir tek kapsayıcı tabanlı hizmetler için harika bir yolu sağlar. Azure uygulama hizmeti kullanarak basit bir işlemdir. Kodunuzu almak, Visual Studio'da derleme ve doğrudan Azure dağıtma kolaylaştırmak için Git ile iyi tümleştirme sağlar.

![](./media/image4.png)

**Şekil 4-4**. Visual Studio'da Azure App Service'e bir tek kapsayıcı uygulama yayımlama

Docker diğer özellikleri, çerçeveleri veya Azure App Service'te desteklenmeyen bağımlılıkları gerekirse bu bağımlılıkların App Service'teki Azure ekibi güncelleştirilmiş kadar bekleyin vardı. Veya Azure Service Fabric, Azure bulut Hizmetleri veya burada daha fazla denetimi kaldı ve uygulamanız için gerekli bir bileşen veya framework yükleyebilir VM'ler bile, gibi diğer hizmetlere geçiş gerekiyordu.

Visual Studio 2017 kapsayıcı desteği Şekil 4-4'te gösterildiği gibi uygulama ortamınızda istediğiniz ekleme yeteneği verir. Uygulamanıza bir bağımlılık eklerseniz, bir kapsayıcıda çalıştırılan olmadığından, bağımlılık Dockerfile veya Docker yansımanıza içerebilir.

Yayımla akış de gösterildiği gibi Şekil 4-4'te, görüntüyü bir kapsayıcı kayıt defteri iter. Bu, (kayıt defteri dağıtımlarınızda Azure kapatın ve Azure Active Directory grupları ve hesaplarını tarafından güvenliği sağlanan) Azure kapsayıcı kayıt defteri ya da, Docker hub'a veya bir şirket içi kayıt defteri gibi diğer Docker kayıt olabilir.


>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (docker-uygulama-durumu-data.md)
