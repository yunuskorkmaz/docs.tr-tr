---
title: Anahtar paketleri
description: Mikro hizmet mimarisi, avantajları ve dezavantajları, tasarım DDD desenlerini gibi kullanırken ilgili üst düzey sorunları hızlı bir bakış için önemli dersler .NET mikro Hizmetleri mimariden kapsayıcılı .NET uygulamaları için Kılavuzu/e-kitabı edinin ve geliştirme, yanı sıra dayanıklılık, güvenlik ve düzenleyicileri kullanımı.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639695"
---
# <a name="key-takeaways"></a>Önemli dersler

Özeti ve önemli dersler bu kılavuzu en önemli sonuçlar aşağıda verilmiştir.

**Kapsayıcıları kullanmanın avantajları.** Üretim ortamlarında bağımlılıkları devrederek neden olduğu dağıtım sorunları azaltmaya yardımcı olduğundan kapsayıcı tabanlı çözümler önemli maliyet tasarrufları sunar. Kapsayıcılar, DevOps ve üretim işlemleri önemli ölçüde artırır.

**Kapsayıcıları bulunabilen olacaktır.** Docker tabanlı kapsayıcılar, Windows ve Linux eko, Microsoft, Amazon AWS, Google ve IBM gibi anahtar satıcılar tarafından desteklenen sektörde pratikte bir standart hale gelmektedir. Docker olacaktır Bulut ve şirket içi veri merkezlerinde bulunabilen yakında.

**Kapsayıcı dağıtım birimi olarak.** Bir Docker kapsayıcısı standart birim için herhangi bir sunucu tabanlı uygulama veya hizmet dağıtımının gelmektedir.

**Mikro hizmetler.** Çok sayıda bağımsız alt sistemlerin otonom bir hizmetler biçiminde karmaşık görev açısından kritik uygulamalar bağlı veya mikro hizmet mimarisini tercih edilen yaklaşım dağıtılmış ve büyük hale gelmektedir. Mikro hizmet tabanlı bir mimaride, uygulama, bağımsız olarak dağıtılabileceği ve geliştirilmiş, test edilmiş, tutulan, hizmetler koleksiyonu oluşturulmuştur. Her hizmet herhangi bir ilgili otonom veritabanı içerebilir.

**Etki alanı Odaklı Tasarım ve SOA.** Mikro hizmetler mimarisi desenleri hizmet odaklı mimari (SOA) ve etki alanı Odaklı Tasarım (DDD) türetilir. Tasarım ve işletme ihtiyaçlarını ve kuralları Gelişmekte olan ortamlar için mikro hizmet geliştirin, DDD yaklaşımlar ve desenleri göz önünde bulundurmanız önemlidir.

**Mikro hizmetler zorlukları.** Mikro hizmetler bağımsız olarak dağıtılmasını, sağlam alt sınırlarını ve teknoloji seviyelerine gibi çok sayıda güçlü özellik sunar. Ancak, bunlar da yükseltmek çok parçalanmış gibi dağıtılmış uygulama geliştirme'ile ilgili yeni zorluklar ve bağımsız veri modelleri, mikro hizmetler, nihai tutarlılığa kadar giden ve gelen sonuçları işletimsel karmaşıklığın arasında dayanıklı iletişim birden fazla mikro hizmetin günlüğe kaydetme ve izleme bilgilerini toplama. Bu görünüşler çok daha yüksek bir karmaşıklık düzeyi daha geleneksel tek parça bir uygulamayı tanıtır. Sonuç olarak, yalnızca belirli senaryoları mikro hizmet tabanlı uygulamalar için uygundur. Bunlar, gelişen birden çok alt sistemin büyük ve karmaşık uygulamalarla içerir. Daha iyi uzun dönemli çevikliği ve Uygulama Bakımı sağlayacağından bu gibi durumlarda, daha karmaşık bir yazılım mimarisi harcanmalıdır.

**Kapsayıcılar için herhangi bir uygulama.** Kapsayıcılar, mikro hizmetler için kullanışlıdır ancak aynı zamanda tek yapılı uygulamalar için kullanışlıdır geleneksel .NET Framework, Windows kapsayıcıları kullanırken temel alabilir. Docker, çok sayıda dağıtım üretim sorunlarını çözmek ve durumu resim geliştirme ve Test ortamlarını sağlama gibi kullanmanın avantajları, birçok farklı türde uygulamalar için geçerlidir.

**CLI IDE karşılaştırması.** Microsoft araçları ile tercih ettiğiniz yaklaşımı kullanarak kapsayıcılı .NET uygulamaları geliştirebilirsiniz. Visual Studio Code ve Docker CLI'yı kullanarak bir CLI ve düzenleyici tabanlı bir ortam ile geliştirebilirsiniz. Veya IDE odaklı bir yaklaşım ile Visual Studio ve benzersiz özellikleri için Docker, çok kapsayıcılı hata ayıklama gibi kullanabilirsiniz.

**Esnek bulut uygulamaları.** Bulut tabanlı sistemleri ve dağıtılmış sistemler genel olarak, her zaman sokması mümkündür kısmi hata. İstemcileri ve Hizmetleri ayrı işlemler (kapsayıcılar) olduğundan, hizmet istemci isteğini zamanında bir şekilde yanıt vermesi mümkün olmayabilir. Örneğin, bir hizmetin kapalı bakım ya da kısmi bir hata nedeniyle olabilir; Hizmet aşırı yüklenmiş olabilir ve çok yavaş yanıt ister; ya da ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir. Bu nedenle, bulut tabanlı bir uygulama, hataları benimseyin gerekir ve bu hatalara yanıt vermek için bir strateji sahip. Tekrarlanan isteklerin üstel önlemek için devre kesici desenleri uygulama yük ve bu stratejiler yeniden deneme ilkelerini (iletileri yeniden göndermeyi veya istekleri yeniden deneniyor) içerebilir. Temel olarak, bulut tabanlı uygulamalarda dayanıklı mekanizmalarına sahip olması gerekir; bulut altyapısı üzerinde temel veya özel olarak düzenleyiciler veya hizmet yolları tarafından sağlanan üst düzey dışındaki.

**Güvenlik.** Modern Dünyamızı kapsayıcıları ve mikro hizmetler, yeni güvenlik açıkları kullanıma sunabilirsiniz. Temel uygulama güvenliği, kimlik doğrulama ve yetkilendirme göre uygulamak için birkaç yolu vardır. Ancak, kapsayıcı güvenliği, doğal olarak daha güvenli uygulamalar neden ek anahtar bileşenler dikkate almanız gerekir. Diğer uygulamalarla iletişim kurmak için güvenli bir şekilde daha güvenli uygulamalar oluşturmanın önemli bir öğe var ve sistemleri, kimlik bilgileri, belirteçleri, parolalar ve benzeri, genellikle gerektiren bir sorun genellikle uygulama gizli dizilerini adlandırılır. Güvenli bir çözümdür, gizli aktarımda ve bekleme sırasında şifreleme ve parolaları son uygulama tarafından kullanılan zaman sızmasını önleme gibi güvenlik en iyi uygulamaları izlemelisiniz. Bu gizli dizileri depolanır ve güvenli olarak ne zaman tutulan gerek Azure Key Vault kullanma.

**Düzenleyiciler.** Azure Kubernetes hizmeti ve Azure Service Fabric gibi kapsayıcı tabanlı düzenleyiciler, herhangi bir önemli bir mikro hizmet ve kapsayıcı tabanlı uygulama anahtar parçasıdır. Bu uygulamalar bunları gerçekleştirmek yüksek karmaşıklık, ölçeklenebilirlik gereksinimlerini ve go sabit evrimi aracılığıyla. Bu kılavuz, düzenleyiciler ve mikro hizmet ve kapsayıcı tabanlı çözümler içindeki rollerine sundu. Uygulamanızın gereksinimlerine göre doğru karmaşık kapsayıcılı uygulamaları taşıyorsanız, Düzenleyicileri hakkında daha fazla bilgi için ek kaynaklar dışarı aramak yararlı bulabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
