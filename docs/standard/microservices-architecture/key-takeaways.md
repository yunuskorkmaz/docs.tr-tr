---
title: Önemli dersler
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | önemli dersler
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d6e09b9856396e99c9b03d595c1896e2451724fe
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152272"
---
# <a name="key-takeaways"></a>Önemli dersler

Özeti ve önemli dersler bu kılavuzu en önemli sonuçlar aşağıda verilmiştir.

**Kapsayıcıları kullanmanın avantajları.** Kapsayıcılar, üretim ortamlarında bağımlılıkları eksikliği nedeniyle dağıtım sorunları için bir çözüm olduğundan kapsayıcı tabanlı çözümler maliyet tasarrufu önemli avantajı sağlar. Kapsayıcılar, DevOps ve üretim işlemleri önemli ölçüde artırır.

**Kapsayıcıları bulunabilen olacaktır.** Docker tabanlı kapsayıcılar, kapsayıcı sektördeki en önemli Windows ve Linux eko satıcılar tarafından desteklenen, pratikte bir standart hale gelmektedir. Bu, Microsoft, Amazon AWS, Google ve IBM içerir. Yakın gelecekte, Docker büyük olasılıkla hem buluttaki hem de şirket içi veri merkezlerinde bulunabilen olacaktır.

**Kapsayıcı dağıtım birimi olarak.** Bir Docker kapsayıcısı standart birim için herhangi bir sunucu tabanlı uygulama veya hizmet dağıtımının gelmektedir.

**Mikro hizmetler.** Mikro hizmet mimarisi, birden çok bağımsız alt sistemlerin otonom bir hizmetler biçiminde göre dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen yaklaşım gelmektedir. Mikro hizmet tabanlı bir mimaride, uygulama, bağımsız olarak dağıtılabileceği ve geliştirilmiş, test edilmiş, tutulan, olabilecek hizmetler koleksiyonu yerleşik olarak bulunur; Bu ilgili herhangi bir otonom veritabanı içerebilir.

**Etki alanı Odaklı Tasarım ve SOA.** Mikro hizmetler mimarisi desenleri hizmet odaklı mimari (SOA) ve etki alanı Odaklı Tasarım (DDD) türetilir. Tasarım ve gelişen iş kuralları belirli bir etki alanı şekillendirme ile ortamlar için mikro hizmet geliştirin, hesap DDD yaklaşımlar ve desenleri almak önemlidir.

**Mikro hizmetler zorlukları.** Mikro hizmetler bağımsız olarak dağıtılmasını, sağlam alt sınırlarını ve teknoloji seviyelerine gibi çok sayıda güçlü özellik sunar. Ancak, bunlar da yükseltmek çok parçalanmış gibi dağıtılmış uygulama geliştirme'ile ilgili yeni zorluklar ve bağımsız veri modelleri, mikro hizmetler, nihai tutarlılığa kadar giden ve gelen sonuçları işletimsel karmaşıklığın arasında dayanıklı iletişim birden fazla mikro hizmetin günlüğe kaydetme ve izleme bilgilerini toplama. Bu görünüşler daha yüksek bir karmaşıklık düzeyi daha geleneksel tek parça bir uygulamayı tanıtır. Sonuç olarak, yalnızca belirli senaryoları mikro hizmet tabanlı uygulamalar için uygundur. Bunlar, gelişen birden çok alt sistemin büyük ve karmaşık uygulamalarla içerir; daha iyi uzun dönemli çevikliği ve Uygulama Bakımı sağlayacağından bu gibi durumlarda, daha karmaşık bir yazılım mimarisi harcanmalıdır.

**Kapsayıcılar için herhangi bir uygulama.** Kapsayıcılar, mikro hizmetler için kullanışlıdır, ancak bunlar için özel değildir. Kapsayıcılar, geleneksel .NET Framework tabanlı ve Windows kapsayıcıları ile modernleştirdiğini eski uygulamalar dahil olmak üzere tek parçalı uygulamalarla birlikte de kullanılabilir. Docker, çok sayıda dağıtım üretim sorunlarını çözmek ve teknoloji geliştirme ve Test ortamlarını sağlama gibi kullanmanın avantajları, birçok farklı türde uygulamalar için geçerlidir.

**CLI IDE karşılaştırması.** Microsoft araçları ile tercih ettiğiniz yaklaşımı kullanarak kapsayıcılı .NET uygulamaları geliştirebilirsiniz. Visual Studio Code ve Docker CLI'yı kullanarak bir CLI ve düzenleyici tabanlı bir ortam ile geliştirebilirsiniz. Veya Visual Studio ile birlikte benzersiz özellikleri IDE odaklı bir yaklaşım için Docker, gibi çoklu kapsayıcı uygulamalarının hata ayıklamanız mümkün olan gibi kullanabilirsiniz.

**Esnek bulut uygulamaları.** Bulut tabanlı sistemleri ve dağıtılmış sistemler genel olarak, her zaman sokması mümkündür kısmi hata. İstemcileri ve Hizmetleri ayrı işlemler (kapsayıcılar) olduğundan, hizmet istemci isteğini zamanında bir şekilde yanıt vermesi mümkün olmayabilir. Örneğin, bir hizmetin kapalı bakım ya da kısmi bir hata nedeniyle olabilir; Hizmet aşırı yüklenmiş olabilir ve istekleri için çok yavaş yanıt; veya, yalnızca ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir. Bu nedenle, bulut tabanlı bir uygulama, hataları benimseyin gerekir ve bu hatalara yanıt vermek için bir strateji sahip. Tekrarlanan isteklerin üstel önlemek için devre kesici desenleri uygulama yük ve bu stratejiler yeniden deneme ilkelerini (iletileri yeniden göndermeyi veya istekleri yeniden deneniyor) içerebilir. Temel olarak, bulut tabanlı uygulamalarda dayanıklı mekanizmalarına sahip olması gerekir; özel olanları ya da olanları tabanlı düzenleyiciler veya hizmet yollarına üst düzey çerçeveleri gibi bulut altyapısı üzerinde.

**Güvenlik.** Modern Dünyamızı kapsayıcıları ve mikro hizmetler, yeni güvenlik açıkları kullanıma sunabilirsiniz. Temel uygulama güvenliği, kimlik doğrulama ve yetkilendirme dayanır; Bu uygulama için birden çok yol yok. Ancak, kapsayıcı güvenliği doğal olarak daha güvenli uygulamalar neden ek anahtar bileşenleri içerir. Diğer uygulamalar ve sistemler ile iletişim kurmak için güvenli bir şekilde güvenli uygulamalar oluşturmanın önemli bir öğe yaşıyor, sorun genellikle kimlik bilgileri, belirteçleri, parolalar ve diğer gizli bilgi türleri gerektirir — genellikle uygulama gizli dizilerini adlandırılır. Güvenli bir çözümdür, gizli dizileri aktarım sırasında şifreleme gibi güvenlik en iyi uygulamaları izlemelisiniz; bekleme sırasında şifreleme parolaları; ve parolaları son uygulama tarafından kullanılan zaman yanlışlıkla sızmasını önleme. Bu gizli dizileri depolanır ve bir yere nedensiz gerekir. Güvenliğin sağlanmasına yardımcı olmak için seçtiğiniz düzenleyicinin altyapısının ya da Azure Key Vault ve bunu kullanmak uygulama kodu için sağladığı yolları gibi bulut altyapısının yararlanabilirsiniz.

**Düzenleyiciler.** Kapsayıcı tabanlı düzenleyiciler Azure Service Fabric ve Azure Container Service (Kubernetes, Mesos DC/OS ve Docker Swarm) ile sağlanan olanlar gibi herhangi bir çok kapsayıcılı ve mikro hizmet tabanlı herhangi bir üretime hazır uygulama için vazgeçilmez Sabit evrimi önemli karmaşıklığı ve ölçeklenebilirliği gereksinimlerine sahip uygulama. Bu kılavuz, düzenleyiciler ve mikro hizmet ve kapsayıcı tabanlı çözümler içindeki rollerine sundu. Uygulamanızın gereksinimlerine göre doğru karmaşık kapsayıcılı uygulamaları taşıyorsanız, Düzenleyicileri hakkında daha fazla bilgi için ek kaynaklar dışarı aramak faydalı

>[!div class="step-by-step"]
>[Önceki](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)