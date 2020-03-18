---
title: Anahtar paketleri
description: Kapsayıcı .NET Uygulamaları kılavuzu/e-kitap için .NET Microservices Architecture'dan önemli paketleri alın, avantajlar ve dezavantajlar, tasarım ve geliştirme için DDD desenleri gibi bir mikrohizmet mimarisi ni kullanırken ilgili üst düzey sorunlara hızlı bir şekilde göz atın, esneklik, güvenlik ve orkestratörlerin kullanımı.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296027"
---
# <a name="key-takeaways"></a>Anahtar Paketler

Özet ve anahtar paket olarak, bu kılavuzdan elde edilen en önemli sonuçlar şunlardır.

**Konteyner kullanmanın faydaları.** Kapsayıcı tabanlı çözümler, üretim ortamlarında başarısız bağımlılıkların neden olduğu dağıtım sorunlarını azaltmaya yardımcı olduğundan önemli maliyet tasarrufu sağlar. Kapsayıcılar DevOps'leri ve üretim operasyonlarını önemli ölçüde iyileştirir.

**Konteynerler her yerde olacak.** Docker tabanlı kapsayıcılar, Microsoft, Amazon AWS, Google ve IBM gibi Windows ve Linux ekosistemlerinin önemli satıcıları tarafından desteklenen, sektördeki fiili standart haline gelmektedir. Docker muhtemelen yakında hem bulut hem de şirket içi veri merkezlerinde her yerde bulunacaktır.

**Dağıtım birimi olarak kapsayıcılar.** Docker kapsayıcısı, sunucu tabanlı herhangi bir uygulama veya hizmet için standart dağıtım birimi haline gelmektedir.

**Mikro hizmetler.** Mikro hizmetler mimarisi, otonom hizmetler biçiminde birçok bağımsız alt sistemden yola çıkarak dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen bir yaklaşım haline gelmektedir. Mikro hizmet tabanlı bir mimaride uygulama, bağımsız olarak geliştirilen, sınanan, sürümlenmiş, dağıtılan ve ölçeklenen hizmetler topluluğu olarak oluşturulur. Her hizmet, ilgili herhangi bir özerk veritabanı içerebilir.

**Etki alanı odaklı tasarım ve SOA.** Microservices mimari desenleri hizmet odaklı mimari (SOA) ve etki alanına dayalı tasarımdan (DDD) kaynaklanır. Değişen iş ihtiyaçları ve kuralları olan ortamlar için mikro hizmetler tasarlarken ve geliştirdiğinizde, DDD yaklaşımlarını ve desenlerini göz önünde bulundurmanız önemlidir.

**Mikro hizmetler zorlukları.** Microservices, bağımsız dağıtım, güçlü alt sistem sınırları ve teknoloji çeşitliliği gibi birçok güçlü özellik sunar. Bununla birlikte, parçalanmış ve bağımsız veri modelleri, mikro hizmetler arasındaki esnek iletişim, nihai tutarlılık ve operasyonel karmaşıklık gibi dağıtılmış uygulama geliştirme ile ilgili birçok yeni zorluk da birden fazla mikro hizmetten günlük ve izleme bilgilerini toplama. Bu yönleri geleneksel monolitik uygulama çok daha yüksek bir karmaşıklık düzeyi tanıtmak. Sonuç olarak, yalnızca belirli senaryolar mikro hizmet tabanlı uygulamalar için uygundur. Bunlar, birden çok değişen alt sistemlere sahip büyük ve karmaşık uygulamaları içerir. Bu gibi durumlarda, daha iyi uzun vadeli çeviklik ve uygulama bakımı sağlayacak, çünkü daha karmaşık bir yazılım mimarisi ne kadar yatırım yapmaya değer.

**Herhangi bir uygulama için konteynerler.** Kapsayıcılar mikro hizmetler için uygundur, ancak Windows Kapsayıcıları kullanırken geleneksel .NET Framework'e dayalı yekpare uygulamalar için de yararlı olabilir. Docker'ı kullanmanın birçok dağıtımdan üretime sorunları çözme ve en gelişmiş Geliştirme ve Test ortamları sağlama gibi avantajları birçok farklı uygulama türü için geçerlidir.

**CLI, IDE'ye karşı.** Microsoft araçları yla, tercih ettiğiniz yaklaşımı kullanarak kapsayıcı .NET uygulamaları geliştirebilirsiniz. Docker CLI ve Visual Studio Code'u kullanarak CLI ve editör tabanlı bir ortam geliştirebilirsiniz. Ya da Visual Studio ile IDE odaklı bir yaklaşım ve Docker için çok konteyner hata ayıklama gibi benzersiz özellikleri kullanabilirsiniz.

**Esnek bulut uygulamaları.** Genel olarak bulut tabanlı sistemlerde ve dağıtılmış sistemlerde kısmi arıza riski her zaman vardır. İstemler ve hizmetler ayrı işlemler (kapsayıcılar) olduğundan, bir hizmet istemcinin isteğine zamanında yanıt veremeyebilir. Örneğin, kısmi bir arıza veya bakım nedeniyle bir hizmet kapalı olabilir; hizmet aşırı yüklenmiş ve isteklere yavaş yanıt verebilir; veya ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir. Bu nedenle, bulut tabanlı bir uygulama bu hataları benimsemeli ve bu hatalara yanıt vermek için bir stratejiye sahip olmalıdır. Bu stratejiler, yinelenen isteklerin üstel yükünü önlemek için ilkeleri yeniden denemeyi (iletileri yeniden göndermeyi veya istekleri yeniden denemeyi) ve devre kesici desenleri uygulamayı içerebilir. Temel olarak, bulut tabanlı uygulamaların, orkestratörler veya servis otobüsleri tarafından sağlanan üst düzey uygulamalar gibi bulut altyapısına veya özele dayalı esnek mekanizmalara sahip olması gerekir.

**Güvenlik.** Konteyner ler ve mikro hizmetlerden oluşan modern dünyamız yeni güvenlik açıklarını ortaya çıkarabilir. Kimlik doğrulama ve yetkilendirmeye dayalı temel uygulama güvenliğini uygulamanın çeşitli yolları vardır. Ancak, kapsayıcı güvenliği, doğal olarak daha güvenli uygulamalarla sonuçlanan ek anahtar bileşenleri göz önünde bulundurmalıdır. Daha güvenli uygulamalar oluşturmanın kritik bir unsuru, genellikle kimlik bilgileri, belirteçler, parolalar ve benzeri ve genellikle uygulama sırları olarak adlandırılan diğer uygulamalar ve sistemlerle güvenli bir iletişim biçimine sahip olmaktır. Herhangi bir güvenli çözüm, geçiş sırasında ve istirahatte sırları şifrelemek ve son uygulama tarafından tüketildiğinde sırların sızmasını önlemek gibi güvenlik en iyi uygulamalarını izlemelidir. Bu sırların Azure Key Vault'u kullanırken olduğu gibi güvenli bir şekilde saklanması ve saklanması gerekir.

**Orkestratörler.** Azure Kubernetes Hizmeti ve Azure Hizmet Kumaşı gibi konteyner tabanlı orkestratörler, önemli mikro hizmet ve konteyner tabanlı uygulamaların önemli bir parçasıdır. Bu uygulamalar yüksek karmaşıklık, ölçeklenebilirlik ihtiyaçlarını da yanlarında taşır ve sürekli evrim geçirir. Bu kılavuz, orkestratörleri ve mikrohizmet tabanlı ve konteyner tabanlı çözümlerdeki rollerini tanıtmıştır. Uygulama gereksinimleriniz sizi karmaşık kapsayıcı uygulamalara doğru taşıyorsa, orkestratörler hakkında daha fazla bilgi edinmek için ek kaynaklar aramayı yararlı bulacaksınız.

>[!div class="step-by-step"]
>[Önceki](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
