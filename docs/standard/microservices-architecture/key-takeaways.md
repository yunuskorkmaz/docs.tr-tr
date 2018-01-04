---
title: Anahtar paketler
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | anahtar paketler"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2dbcfbe28f5461b7a40e8b0b49dbcf5e31490d70
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="key-takeaways"></a>Anahtar paketler

Bir Özet ve anahtar paketler en önemli bir sonuca bu Guide'daki verilmiştir.

**Kapsayıcıları kullanmanın yararları.** Kapsayıcıları üretim ortamlarında bağımlılıkları eksikliği nedeniyle dağıtım sorunları için bir çözüm olduğundan kapsayıcı tabanlı çözümler önemli faydası maliyet tasarrufu sağlar. Kapsayıcıları DevOps ve üretim işlemlerinin önemli ölçüde artırır.

**Kapsayıcıları bulunabilen olacaktır.** Docker tabanlı kapsayıcıları, Windows ve Linux ekosistemlerini en önemli satıcılar tarafından desteklenen kapsayıcı endüstri gerçek standart hale gelmektedir. Bu, Microsoft, Amazon AWS, Google ve IBM içerir. Yakın gelecekte Docker büyük olasılıkla Bulut ve şirket içi veri merkezlerinde bulunabilen olacaktır.

**Kapsayıcılar olarak dağıtım birimidir.** Docker kapsayıcısı için herhangi bir sunucu tabanlı bir uygulama veya hizmet dağıtımının standart birim durumundadır.

**Mikro.** Mikro mimarisi birden çok bağımsız alt sistemleri otonom Hizmetleri biçiminde temel dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen yaklaşım durumundadır. Mikro hizmet tabanlı bir mimaride uygulama dağıtılır ve bağımsız olarak ölçeklendirilmiş geliştirilmiş, test edilmiş, sürümlü, olabilir hizmetler koleksiyonu yerleşik olarak bulunur; Bu, tüm ilgili otonom veritabanı içerebilir.

**Etki alanı Odaklı Tasarım ve SOA.** Mikro mimarisi desenleri hizmet odaklı mimari (SOA) ve etki alanı Odaklı Tasarım (DDD) türetilir. İş kuralları belirli bir etki alanı şekillendirme gelişen ile ortamlar için mikro tasarlayıp, hesap DDD yaklaşımlar ve desenler almanız önemlidir.

**Mikro zorluklar.** Mikro bağımsız dağıtım, güçlü alt sınırlarını ve teknoloji seviyelerine gibi pek çok güçlü özellikleri sunar. Ancak, bunlar ayrıca Yükselt birçok yeni zorluklar parçalanmış gibi dağıtılmış uygulama geliştirme için ilgili ve bağımsız veri modelleri, esnek arasındaki iletişimi mikro, nihai tutarlılık, gelen sonuçları işletim karmaşıklığını birden çok mikro oturum açma ve izleme bilgilerini toplama. Bu yönlerinin daha yüksek bir karmaşıklık düzeyi daha geleneksel tek yapılı uygulama tanıtır. Sonuç olarak, yalnızca belirli senaryolar mikro hizmet tabanlı uygulamalar için uygundur. Bunlar, birden çok gelişen alt sistemleri ile büyük ve karmaşık uygulamaları içerir; daha iyi uzun vadeli çeviklik ve uygulama bakım sağlayacak bu durumlarda, daha karmaşık bir yazılım mimaride yatırım değerinde demektir.

**Herhangi bir uygulama için kapsayıcı.** Kapsayıcıları için mikro kullanışlıdır ancak bunlar için özel değildir. Kapsayıcılar ayrıca tek yapılı uygulamalarla geleneksel .NET Framework temel alınarak ve Windows kapsayıcıları modernized eski uygulamalar dahil olmak üzere kullanılabilir. Çoğu dağıtım üretim sorunu çözme ve harikası geliştirme ve Test ortamları sağlama gibi Docker kullanmanın avantajları farklı türlerde uygulamalar için geçerlidir.

**CLI IDE karşılaştırması.** Microsoft araçları ile tercih edilen yaklaşım kullanarak kapsayıcılı .NET uygulamaları geliştirebilirsiniz. Visual Studio Code ve Docker CLI kullanarak bir CLI ve düzenleyici tabanlı ortam geliştirebilirsiniz. Veya Visual Studio ve benzersiz özellikleri ile IDE odaklı bir yaklaşım Docker için gibi birden çok kapsayıcı uygulamalarda hata ayıklama yapamamasına gibi kullanabilirsiniz.

**Dayanıklı bulut uygulamaları.** Bulut tabanlı sistemleri ve dağıtılmış sistemleri içinde genel olarak, her zaman riski yoktur kısmi hata. Bir hizmet, istemciler ve hizmetler ayrı işlemler (kapsayıcı) olduğundan, bir istemcinin isteğini zamanında bir şekilde yanıt verebilir olmayabilir. Örneğin, bir hizmet aşağı bakım için veya kısmi bir hatası nedeniyle olabilir; Hizmet aşırı yüklenmiş olabilir ve son derece yavaş çok yanıt ister; veya, yalnızca ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir. Bu nedenle, bulut tabanlı bir uygulama bu hataları çekirdeğin ve bu bu hataları yanıt yerinde bir strateji olması gerekir. Yinelenen isteklerinin yük üstel önlemek için uygulama devre kesici desenleri ve bu stratejileri (iletileri göndermeden veya istekleri yeniden deneniyor) yeniden deneme ilkelerini içerebilir. Temel olarak, bulut tabanlı uygulamalar dayanıklı mekanizmaları olması gerekir; özel olanları ya da olanları orchestrators veya hizmet yollarına üst düzey çerçeveler gibi bulut altyapısı göre.

**Güvenlik.** Bizim modern world kapsayıcıları ve mikro yeni güvenlik açıkları getirebilir. Temel uygulama güvenliği kimlik doğrulama ve yetkilendirme temel alır; Bu uygulama için birden çok yolu yok. Ancak, kapsayıcı güvenlik doğası gereği güvenli uygulamaların neden ek anahtar bileşenleri içerir. Daha güvenli uygulamalar oluşturmanın önemli bir öğe diğer uygulamalar ve sistemler ile iletişim için güvenli bir yol olması, bir şey kimlik bilgileri, belirteçleri, parolalar ve diğer gizli bilgi türleri aynı sıklıkta gerektirir — genellikle uygulama gizlilikleri olarak adlandırılır. Güvenli bir çözümdür gizli aktarım sırasında şifreleme gibi güvenlik en iyi uygulamaları izlemelisiniz; Şifreleme parolaları REST; ve parolaları son uygulama tarafından tüketilen zaman istemeden sızmasını engelliyor. Bu gizli depolanır ve güvenli bir yerde tutulması gerekir. Güvenliğin sağlanmasına yardımcı olmak için seçilen orchestrator'ın altyapısının ya da Azure anahtar kasası ve uygulama kodu kullanmak sağladığı yolları gibi bulut altyapısının avantajından yararlanabilirsiniz.

**Orchestrators.** Azure kapsayıcı hizmeti (Kubernetes, Mesos DC/OS ve Docker Swarm) ve Azure Service Fabric sağlanan herhangi bir çok kapsayıcısına ve herhangi bir üretime hazır mikro hizmet tabanlı uygulama için vazgeçilmez olanlardır gibi kapsayıcı tabanlı orchestrators Uygulama önemli karmaşıklık, ölçeklenebilirlik gereksinimlerini ve sabit evrimi. Bu kılavuz orchestrators ve rolleri mikro hizmet ve kapsayıcı tabanlı çözümlerinde anlatılmıştır. Uygulamanızın gereksinimlerine karmaşık kapsayıcılı uygulamaları taşıyorsanız, orchestrators hakkında daha fazla bilgi için ek kaynaklar çıkışı aramak yararlı

>[!div class="step-by-step"]
[Önceki] (secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
