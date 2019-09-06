---
title: Anahtar paketleri
description: .NET mikro hizmetleri mimarisinden Kapsayıcılı .NET uygulamaları kılavuzu/e-kitabı için en önemli sorunları hızlı bir şekilde görmek için, bir mikro hizmet mimarisi kullanılırken, avantaj ve dezavantajları, örneğin tasarım için DDD desenlerine göz atın ve geliştirme, dayanıklılık, güvenlik ve düzenleyicilerinin kullanımı.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296027"
---
# <a name="key-takeaways"></a>Anahtar koymalar

Özet ve anahtar, en önemli ekibinizle bu kılavuzdan aşağıda verilmiştir.

**Kapsayıcıları kullanmanın avantajları.** Kapsayıcı tabanlı çözümler, üretim ortamlarındaki başarısız bağımlılıklardan kaynaklanan dağıtım sorunlarını azaltmaya yardımcı olduklarından önemli maliyet tasarrufu sağlar. Kapsayıcılar DevOps ve üretim işlemlerini önemli ölçüde geliştirir.

**Kapsayıcılar ubititous olacaktır.** Docker tabanlı kapsayıcılar, Microsoft, Amazon AWS, Google ve IBM gibi Windows ve Linux ekosistemlerindeki temel satıcılar tarafından desteklenen sektördeki standart bir standart haline geliyor. Docker, büyük olasılıkla hem bulutta hem de şirket içi veri merkezlerinde bizde olacak.

**Dağıtım birimi olarak kapsayıcılar.** Bir Docker kapsayıcısı, herhangi bir sunucu tabanlı uygulama veya hizmet için standart dağıtım birimidir.

**Mikro hizmetler.** Mikro hizmetler mimarisi, özerk hizmetler biçimindeki birçok bağımsız alt sistemi temel alan dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen yaklaşım haline geliyor. Mikro hizmet tabanlı bir mimaride, uygulama geliştirilmiş, test edilmiş, sürümlü, dağıtılan ve bağımsız olarak ölçeklenen bir hizmetler koleksiyonu olarak oluşturulur. Her hizmet, ilgili tüm otonom veritabanlarını içerebilir.

**Etki alanı odaklı tasarım ve SOA.** Mikro hizmet mimarisi desenleri, hizmet odaklı mimari (SOA) ve etki alanı denetimli tasarımdan (DDD) türetilir. Gelişen iş ihtiyaçları ve kuralları olan ortamlar için mikro hizmetler tasarladığınızda ve geliştirirken, DDD yaklaşımlarının ve desenlerinin dikkate alınması önemlidir.

**Mikro hizmet sorunları.** Mikro hizmetler bağımsız dağıtım, güçlü alt sistem sınırları ve teknoloji çeşitlemesi gibi birçok güçlü özellik sunar. Bununla birlikte, parçalanmış ve bağımsız veri modelleri, mikro hizmetler arasındaki dayanıklı iletişim, nihai tutarlılık ve bu işlemin sonucu olan işlemsel karmaşıklık gibi dağıtılmış uygulama geliştirmeyle ilgili birçok yeni zorluk da yükseltir. birden çok mikro hizmetten günlüğe kaydetme ve izleme bilgilerini toplama. Bu yönleri geleneksel tek parçalı bir uygulamadan çok daha yüksek bir karmaşıklık düzeyi sağlar. Sonuç olarak, mikro hizmet tabanlı uygulamalar için yalnızca belirli senaryolar uygundur. Bunlar, birden fazla gelişen alt sistemi olan büyük ve karmaşık uygulamaları içerir. Bu durumlarda, daha uzun süreli çeviklik ve uygulama Bakımı sağlayacağından daha karmaşık bir yazılım mimarisine yatırım harcamıştır.

**Tüm uygulamalar için kapsayıcılar.** Kapsayıcılar, mikro hizmetler için uygundur, ancak Windows kapsayıcıları kullanılırken geleneksel .NET Framework temel alan tek parçalı uygulamalar için de kullanışlı olabilir. Birçok dağıtım-üretim sorununu çözme ve son teknoloji geliştirme ve test ortamları sağlama gibi Docker kullanmanın avantajları, birçok farklı uygulama türü için geçerlidir.

**CLı ve IDE.** Microsoft araçları ile, tercih ettiğiniz yaklaşımı kullanarak Kapsayıcılı .NET uygulamaları geliştirebilirsiniz. Docker CLı ve Visual Studio Code kullanarak bir CLı ve düzenleyici tabanlı ortamla geliştirebilirsiniz. Ya da Visual Studio ile IDE odaklı bir yaklaşım ve çok Kapsayıcılı hata ayıklama gibi Docker için benzersiz özellikleri kullanabilirsiniz.

**Dayanıklı bulut uygulamaları.** Bulut tabanlı sistemler ve dağıtılmış sistemlerde, genel olarak her zaman kısmi hata riski vardır. İstemciler ve hizmetler ayrı süreçler (kapsayıcılar) olduğundan, bir hizmet istemcinin isteğine zamanında yanıt veremeyebilir. Örneğin, bir hizmet kısmi bir hata veya bakım için kapatılmış olabilir; hizmet aşırı yüklenmiş ve isteklere yavaş yanıt veriyor olabilir; ya da ağ sorunları nedeniyle kısa bir süredir erişilebilir olmayabilir. Bu nedenle, bulut tabanlı bir uygulamanın bu hatalara yanıt vermesi ve bu hatalara yanıt vermek için bir strateji olması gerekir. Bu stratejiler, tekrarlanmış isteklerin üstel yükünün önüne geçmek için yeniden deneme ilkelerini (iletileri yeniden göndermeyi veya istekleri yeniden göndermeyi) ve devre kesici düzenlerini uygulamayı içerebilir. Temel olarak, bulut tabanlı uygulamaların, düzenleme yöneticileri veya hizmet veri yolları tarafından sağlananlara göre, bulut altyapısına veya özel tabanlı olarak dayanıklı mekanizmalarına sahip olması gerekir.

**Güven.** Modern bir kapsayıcı dünyamız ve mikro hizmetler yeni güvenlik açıklarını açığa çıkarır. Kimlik doğrulama ve yetkilendirme temel alınarak temel uygulama güvenliği uygulamak için birkaç yol vardır. Ancak, kapsayıcı güvenliği, doğal olarak daha güvenli uygulamalarla sonuçlanan ek anahtar bileşenleri dikkate almalıdır. Daha güvenli uygulamalar oluşturmaya yönelik kritik bir öğe, genellikle kimlik bilgileri, belirteçler, parolalar ve benzer şekilde uygulama gizli dizileri olarak adlandırılan gibi, diğer uygulama ve sistemlerle iletişim kurmak için güvenli bir yoldur. Her türlü güvenli çözüm, aktarım sırasında ve REST sırasında gizli dizileri şifrelemek ve parolaların son uygulama tarafından tüketilirken sızmasını önlemek gibi en iyi güvenlik uygulamalarını izlemelidir. Azure Key Vault kullanırken olduğu gibi, bu parolaların güvenli bir şekilde depolanması ve güvenli tutulması gerekir.

**Düzenleyicileri.** Azure Kubernetes hizmeti ve Azure Service Fabric gibi kapsayıcı tabanlı düzenleyiciler, önemli mikro hizmet ve kapsayıcı tabanlı uygulamaların önemli bir parçasıdır. Bu uygulamalar, yüksek karmaşıklığa, ölçeklenebilirlik ihtiyaçlarına sahip ve sabit bir evrimle gider. Bu kılavuz, mikro hizmet tabanlı ve kapsayıcı tabanlı çözümlerde yöneticileri ve bunların rollerini sunmuştur. Uygulamanızın ihtiyacı olan karmaşık Kapsayıcılı uygulamalara yaklaşmayı düşünüyorsanız, düzenlemeler hakkında daha fazla bilgi edinmek için ek kaynaklar aramak yararlı olacaktır.

>[!div class="step-by-step"]
>[Önceki](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
