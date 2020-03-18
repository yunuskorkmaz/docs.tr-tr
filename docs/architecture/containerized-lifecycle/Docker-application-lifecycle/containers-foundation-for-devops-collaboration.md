---
title: DevOps işbirliğinin temeli olarak kapsayıcılar
description: DevOps'leri kolaylaştırmak için kapsayıcıların kilit rolünü anlayın.
ms.date: 02/15/2019
ms.openlocfilehash: 8258f4331212d92376d64fef318adcdff492f61f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73094494"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>DevOps işbirliğinin temeli olarak kapsayıcılar

Kapsayıcılar ve Docker teknolojisidoğası gereği, geliştiriciler tipik "benim makine üzerinde çalışır" bahane ortadan kaldırırken BT işlemleri ve üretim ortamları ile kolayca kendi yazılım ve bağımlılıkları paylaşabilirsiniz. Kapsayıcılar farklı ortamlar arasındaki uygulama çakışmalarını çözer. Dolaylı olarak, kapsayıcılar ve Docker geliştiricileri ve BT işlemlerini birbirine yaklaştırarak etkili bir şekilde işbirliği yapmalarını kolaylaştırır. Konteyner iş akışının benimsenmesi, birçok müşteriye aradıkları ancak daha önce serbest bırakma ve boru hatları oluşturmak için daha karmaşık yapılandırma yoluyla uygulamak zorunda kaldıkları DevOps sürekliliğini sağlar. Kapsayıcılar DevOps'taki yapı/test/dağıtım boru hatlarını basitleştirir.

![Docker uygulamasının yaşam döngüsünün sahipliğini gösteren diyagram.](./media/containers-foundation-for-devops-collaboration/persona-workloads-docker-container-lifecycle.png)

**Şekil 2-1.** Konteynerleştirilmiş Docker uygulamaları için yaşam döngüsünde "kişilikler" başına temel iş yükleri

Docker kapsayıcıları ile geliştiriciler kapsayıcının içindekilere (uygulama ve hizmet ve çerçevelere ve bileşenlere bağımlılıklar) ve kapsayıcıların ve hizmetlerin bir hizmet koleksiyonundan oluşan bir uygulama olarak birlikte nasıl birlikte nasıl birlikte nasıl oluştuğuna sahiptir. Birden çok kapsayıcının karşılıklı bağımlılıkları `docker-compose.yml` bir dosyada tanımlanır veya *dağıtım bildirimi*olarak adlandırılabilir. Bu arada, BT operasyon ekipleri (BT uzmanları ve yönetimi) üretim ortamlarının yönetimine odaklanabilir; altyapı; ölçeklenebilirlik; izlenmesi; ve sonuç olarak, çeşitli kapların içeriğini bilmek zorunda kalmadan, uygulamaların son kullanıcılar için doğru şekilde sunulmasını sağlamak. Bu nedenle, adı "konteyner," gerçek dünya nakliye konteyner ler için benzetme hatırlatarak. Bu nedenle, bir konteynerin içeriğinin sahipleri, konteynerin nasıl sevk edileceği konusunda kendilerini ilgilendirmezler ve nakliye şirketi bir konteyneri, içeriğini bilmeden veya umursamadan varış noktasına taşır. Benzer bir şekilde, geliştiriciler "taşıma" mekanizmaları ile kendilerini endişe gerek kalmadan bir Docker konteyner içinde içeriğini oluşturabilir ve kendi.

Şekil 2-1'in sol tarafındaki sütunda, geliştiriciler Docker kapsayıcılarına Windows veya Mac için Docker'ı kullanarak yerel olarak kod yazar ve çalıştırın. Kod için çalışma ortamını, temel işletim sisteminin çalışmasını belirten bir Dockerfile'ı ve kodlarını Docker görüntüsüne oluşturmak için yapı adımlarını kullanarak tanımlarlar. Geliştiriciler, yukarıda belirtilen `docker-compose.yml` dosya dağıtım bildirimini kullanarak bir veya daha fazla görüntünün nasıl birlikte çalışacağını tanımlar. Yerel geliştirmelerini tamamladıklarında, uygulama kodlarını ve Docker yapılandırma dosyalarını seçtikleri kod deposuna (diğer bir şekilde Git deposu) iterler.

DevOps sütunu, kod deposunda sağlanan Dockerfile'yi kullanarak yapı-Sürekli Tümleştirme (CI) ardışık hatlarını tanımlar. CI sistemi, seçilen Docker kayıt defterinden temel kapsayıcı görüntülerini çeker ve uygulama için özel Docker görüntülerini oluşturur. Görüntüler daha sonra doğrulanır ve birden çok ortama dağıtımlar için kullanılan Docker kayıt defterine itilir.

Sağdaki sütunda, operasyon ekipleri, uygulamanın nasıl olabileceği hakkında geliştirme ekibine geri bildirim ve öngörüler sağlamak için, çevre ve uygulamaları izlerken, dağıtım uygulamaları ve altyapıyı üretimde yönetirler. Geliştirilmiş. Konteyner uygulamaları genellikle konteyner orkestratörleri kullanılarak üretimde çalıştırılır.

İki takım, bir sözleşme olarak endişelerin ayrılmasını sağlayan temel bir platform (Docker konteynerleri) aracılığıyla işbirliği yaparken, iki takımın uygulama yaşam döngüsündeki işbirliğini büyük ölçüde geliştiriyor. Geliştiriciler kapsayıcı içeriğine, çalışma ortamına ve kapsayıcı karşılıklı bağımlılıklarına sahipken, operasyon ekipleri yerleşik görüntüleri manifestoyla birlikte alır ve bunları orkestrasyon sisteminde çalıştırın.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Docker kullanırken uygulama yaşam döngüsünde zorluklar.

Önümüzdeki yıllarda konteyner uygulamalarının sayısını artıracak birçok neden vardır ve bu nedenlerden biri de mikro hizmetlere dayalı uygulamaların oluşturulmasıdır.

Son 15 yıl içinde, web hizmetlerinin kullanımı binlerce uygulamanın temelini olmuştur ve muhtemelen birkaç yıl sonra, Docker konteynerleri üzerinde çalışan mikro hizmet tabanlı uygulamalarda da aynı durumu bulacağız.

Ayrıca, tek tek uygulamalar için Docker kapları kullanabilirsiniz ve hala Docker yararları en almak bahsetmeye değer. Konteynerler sadece mikro hizmetleri hedeflemiyor.

Docker konteynerizasyon ve mikro hizmetlerin kullanımı, kuruluşlarınızın geliştirme sürecinde yeni zorluklara neden olur ve bu nedenle, üretim sistemlerinde çalışan birçok konteyner ve mikro hizmeti korumak için sağlam bir stratejiye ihtiyacınız vardır. Sonuç olarak, kurumsal uygulamalarda üretimde çalışan yüzlerce veya binlerce kapsayıcı/örnek bulunur.

Bu zorluklar DevOps araçlarını kullanırken yeni talepler oluşturur, böylece DevOps etkinliklerinizde yeni süreçler tanımlamanız ve bu tür soruların yanıtlarını bulmanız gerekir:

- Geliştirme, CI/CD, yönetim ve operasyonlar için hangi araçları kullanabilirim?

- Şirketim üretimde çalışırken konteynerdeki hataları nasıl yönetebilir?

- Üretimde yazılımlarımızın parçalarını minimum kapalı kalma süresiyle nasıl değiştirebiliriz?

- Üretim sistemimizi nasıl ölçeklendirebiliriz ve nasıl izleyebiliriz?

- Sürüm boru hattımızda kapsayıcıların test edilmesi ve konuşlandırılması nasıl dahil edebiliriz?

- Microsoft Azure'daki kapsayıcılar için Açık Kaynak araçlarını/platformlarını nasıl kullanabiliriz?

Tüm bu soruları yanıtlayabilirseniz, uygulamalarınızı (mevcut veya yeni uygulamalar) Docker konteynerlerine taşımaya daha hazırlıklı sınız.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Genel uçtan uca Docker uygulaması yaşam döngüsü iş akışına giriş

Şekil 2-2, bu örnekte belirli DevOps etkinliklerine ve varlıklarına odaklanarak Docker uygulama yaşam döngüsü için daha ayrıntılı bir iş akışı sunar.

![Docker uygulamasının genel uçtan uca yaşam döngüsünü gösteren diyagram.](./media/containers-foundation-for-devops-collaboration/generic-end-to-enddpcker-app-life-cycle.png)

**Şekil 2-2.** Docker konteyneruygulaması yaşam döngüsü için üst düzey iş akışı

Her şey, iç döngü iş akışında kod yazmaya başlayan geliştiriciyle başlar. İç döngü aşaması, geliştiricilerin kodu kod deposuna itmeden önce gerçekleşen her şeyi tanımladığı yerdir (örneğin, Git gibi bir kaynak denetim sistemi). Depo, işlendikten sonra Sürekli Tümleştirme (CI) ve iş akışının geri kalanını tetikler.

İç döngü temelde "kod", "çalıştır", "test" ve "hata ayıklama" gibi tipik adımların yanı sıra uygulamayı yerel olarak çalıştırmadan hemen önce gereken ek adımlardan oluşur. Bu, geliştiricinin uygulamayı Docker kapsayıcısı olarak çalıştırma ve test etme işlemidir. İç döngü iş akışı izleyen bölümlerde açıklanacaktır.

Sondan uca iş akışına bakmak için bir adım geri giderek, DevOps iş akışı bir teknoloji den veya bir araç kümesinden daha fazlasıdır: kültürel evrim gerektiren bir zihniyettir. Uygulama yaşam döngüsünüzün daha hızlı ve daha öngörülebilir olmasını sağlamak için kişiler, süreçler ve uygun araçlardır. Kapsayıcılaştırılmış iş akışını benimseyen işletmeler genellikle kuruluşlarını, kapsayıcılaştırılmış iş akışıyla eşleşen kişileri ve işlemleri temsil edecek şekilde yeniden yapılandırın.

DevOps pratik gelişmiş izlenebilirlik ve tekrarlanabilir iş akışları ile sonuçlanır otomasyon ile hataya açık manuel süreçleri değiştirerek ekiplerin rekabet baskılarına birlikte daha hızlı yanıt yardımcı olabilir. Kuruluşlar ayrıca, şirket içi ve bulut kaynaklarının yanı sıra sıkı bir şekilde entegre edilmiş takım larla ortamları daha verimli yönetebilir ve maliyet tasarrufu gerçekleştirebilir.

Docker uygulamaları için DevOps iş akışınızı uygularken, docker teknolojilerinin iş akışının hemen hemen her aşamasında, geliştirme kutunuzdan iç döngü (kod, çalıştırma, hata ayıklama), yapı testi-CI aşamasında ve son olarak, bu kapsayıcıların evreleme ve üretim ortamlarına konuşlandırılması.

Kalite uygulamalarının iyileştirilmesi, hataların geliştirme döngüsünün başlarında belirlenmesine yardımcı olur ve bu da hataların giderilmesinin maliyetini azaltır. Ortam ve bağımlılıkları görüntüye ekleyerek ve aynı görüntüyü birden çok ortama dağıtma felsefesini benimseyerek, dağıtımları daha güvenilir hale getiren ortama özel yapılandırmaları ayıklama disiplinini teşvik eleştirirsiniz.

Etkili enstrümantasyon (izleme ve tanılama) yoluyla elde edilen zengin veriler, gelecekteki öncelikleri ve yatırımları yönlendirmek için performans sorunları ve kullanıcı davranışı hakkında bilgi sağlar.

DevOps bir yolculuk değil, bir hedef olarak kabul edilmelidir. Başarı gösterebileceğiniz, öğrenebileceğiniz ve gelişebileceğiniz uygun kapsamlı projeler aracılığıyla kademeli olarak uygulanmalıdır.

## <a name="benefits-of-devops-for-containerized-applications"></a>DevOps'lerin konteyner uygulamaları için faydaları

Burada katı bir DevOps iş akışı tarafından sağlanan en önemli faydalarından bazıları şunlardır:

- Daha kaliteli, daha hızlı ve daha iyi uyumlulukla yazılım sunun.

- Sürekli iyileştirme ve ayarlamaları daha erken ve daha ekonomik bir şekilde geliştirin.

- Yazılım teslimi ve işletiminde yer alan paydaşlar arasında şeffaflığı ve işbirliğini artırın.

- Güvenlik risklerini en aza indirirken maliyetleri kontrol edin ve sağlanan kaynakları daha etkin bir şekilde kullanın.

- Açık kaynak yatırımları da dahil olmak üzere mevcut DevOps yatırımlarınızın çoğunu takın ve iyi oynayın.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](../Microsoft-platform-tools-containerized-apps/index.md)
