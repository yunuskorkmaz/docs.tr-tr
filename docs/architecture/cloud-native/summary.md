---
title: Özet
description: Azure Kılavuzu/e-kitabı için bulutta yerel .NET uygulamalarını tasarlayarak Key ekibinizle 'in Özeti.
ms.date: 04/29/2020
ms.openlocfilehash: 97f20771aae73ed88d2dadefa7ba89d64eb62fcd
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82899698"
---
# <a name="summary"></a>Özet

Özet bölümünde, bu kılavuzun önemli ekibinizle şunlardır:

- **Bulutta yerel** , genel değişiklik, büyük ölçek ve esnekliği gibi modern uygulamaların, genel, özel ve karma bulutlar gibi dinamik ortamlarda tasarlanmasıyla ilgili modern uygulamalar tasarlamaya yönelik olarak tasarlanmıştır.

- ** [Bulut Yerel bilgi işlem altyapısı](https://www.cncf.io/) (cncf)** , 300 ana şirketlerin üzerinde etkili bir açık kaynaklı konsorsiyum. Bulut Yerel bilgi işlemin teknoloji ve bulut yığınları arasında benimsenmesini sağlamaktan sorumludur.

- **Cncf yönergeleri** ,, Şekil 12-1 ' de gösterildiği gibi, bulutta yerel uygulamaların altı önemli ve daha fazla sayıda süslü bir değer ayraçlarını

  ![Bulutta yerel temel sütunlar](./media/cloud-native-foundational-pillars.png)

  **Şekil 12-1**. Bulutta yerel temel sütunlar

- Bu bulut Yerel paragraf örnekleri şunları içerir:
  - Bulut ve temel aldığı hizmet modeli
  - Modern tasarım ilkeleri
  - Mikro hizmetler
  - Kapsayıcılama ve kapsayıcı düzenlemesi
  - Veritabanları ve ileti aracıları gibi bulut tabanlı yedekleme hizmetleri
  - Kod ve kod dağıtımı gibi altyapı dahil Otomasyon

- **Kubernetes** , bulutta yerel çoğu uygulama için tercih edilen barındırma ortamıdır. Daha küçük, basit hizmetler bazen Azure Işlevleri gibi sunucusuz platformlarda barındırılır. Birçok temel Otomasyon özelliği arasında her iki ortam de iş yükü birimlerinin dalgalanmayı işlemek için otomatik ölçeklendirme sağlar.

- **Hizmet iletişimi** , bulutta yerel bir uygulama oluştururken önemli bir tasarım kararı haline gelir. Uygulamalar genellikle ön uç istemci iletişimini yönetmek için bir API ağ geçidi sunar. Ardından arka uç mikro hizmetleri, mümkün olduğunda zaman uyumsuz iletişim desenleri uygulayan birbirleriyle iletişim kurmayı de sağlar.

- **GRPC** , yaş-eski uzak yordam ÇAĞRıSı (RPC) protokolünü gelişten modern ve yüksek performanslı bir çerçevedir. Bulut-yerel uygulamalar, arka uç hizmetleri arasında ileti gönderimi kolaylaştırmak için genellikle gRPC 'yi çok fazla kaya. gRPC, Aktarım Protokolü için HTTP/2 kullanır. İleti boyutları% 60-80 daha küçük olan JSON Serileştirmeden daha hızlı olabilir. gRPC açık kaynak ve bulut Yerel Bilgi Işlem altyapısı (CNCF) tarafından yönetiliyor.

- **Dağıtılmış veriler** , genellikle bulutta yerel uygulamalar tarafından uygulanan bir modeldir. Uygulamalar, iş işlevlerini küçük, bağımsız mikro hizmetlere ayırır. Her mikro hizmet kendi bağımlılıklarını, verilerini ve durumunu kapsüller. Klasik paylaşılan veritabanı modeli, her biri bir mikro hizmetle hizalanan birçok küçük veritabanından birine gelişir. Duman temizlediğinde, bir `database-per-microservice` modeli kullanıma sunan bir tasarımla karşılaştık.

- **Hayır-SQL veritabanları** , yüksek performanslı, ilişkisel olmayan veri depolarına başvurur. Bu kişiler, kullanım kolaylığı, ölçeklenebilirlik, esnekliği ve kullanılabilirlik özellikleriyle Excel. Alt saniye yanıt süresi gerektiren yüksek hacimli hizmetler NoSQL veri depolarını kabul etmek. Dağıtılmış bulut Yerel sistemlerine yönelik NoSQL teknolojilerinin uzaması aşırı belirtilemez.

- **Newsql** , NoSQL 'in dağıtılmış ölçeklenebilirliğini ve ilişkisel bir veritabanının ACID garantisini birleştiren, gelişmekte olan bir veritabanı teknolojisidir. NewSQL veritabanları, tam işlem/ACID uyumluluğu ile dağıtılmış ortamlarda yüksek hacimlerde veri işlemesi gereken iş sistemlerini hedefler. Cloud Native Computing Foundation (CNCF), çeşitli NewSQL veritabanı projelerini sunar.

- **Dayanıklılık** , sisteminizin hataya tepki verme ve hala işlevsel olmaya devam etme yeteneğidir. Bulutta yerel sistemler, hata olduğu yerde dağıtılan bir mimariye sahiptir. Uygulamalar, hataya sorunsuz bir şekilde yanıt vermek ve tamamen işlevsel bir duruma dönmek için oluşturulmalıdır.

- **Hizmet kafesleri** , hizmet iletişimini ve diğer çapraz kesme sorunlarını ele almak için yerleşik yeteneklere sahip yapılandırılabilir bir altyapı katmanıdır. Bunlar, iş kodınızdan çapraz kesme sorumlulukları ayırır. Bu sorumluluklar bir hizmet proxy 'sine taşınır. Denir `Sidecar pattern`, iş kodunuzda yalıtım sağlamak için proxy ayrı bir işleme dağıtılır.

- **Observability** , bulutta yerel uygulamalar için önemli bir tasarım konusudur. Hizmetler bir düğüm kümesine dağıtıldığında, Merkezi günlük, izleme ve uyarılar zorunlu hale gelir. Azure Izleyici, sisteminizin durumuna ilişkin görünürlük sağlamak için tasarlanan bulut tabanlı araçların bir koleksiyonudur.

- **Kod olarak altyapı** , platform sağlamayı otomatikleştiren yaygın olarak kabul edilen bir uygulamadır. Altyapınız ve dağıtımlarınız otomatik, tutarlı ve yinelenebilir. Azure Resource Manager, Teraform ve Azure CLı gibi araçlar, ihtiyacınız olan bulut altyapısını bildirimli olarak betiğe olanak sağlar.

- **Kod Otomasyonu** , bulutta yerel uygulamalar için bir gereksinimdir. Modern CI/CD sistemleri bu ilkeyi karşılamanın sağlanmasına yardımcı olur. Tutarlı ve kaliteli kodların sağlanmasına yardımcı olacak ayrı derleme ve dağıtım adımları sağlar. Derleme aşaması, kodu bir ikili yapıta dönüştürür. Yayın aşaması ikili yapıtı seçer, dış ortam yapılandırmasını uygular ve belirtilen bir ortama dağıtır. Azure DevOps ve GitHub, tam özellikli DevOps ortamlardır.

>[!div class="step-by-step"]
>[Önceki](application-bundles.md)
