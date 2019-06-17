---
title: DevOps işbirliğinin temeli olarak kapsayıcılar
description: Kapsayıcılar, DevOps kolaylaştırmak için önemli bir rol anlayın.
ms.date: 02/15/2019
ms.openlocfilehash: 37faf00f270414df363f36894317f31f81a2937e
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641304"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>DevOps işbirliğinin temeli olarak kapsayıcılar

Kapsayıcıları ve Docker teknolojisini çok gereği, geliştiriciler kendi yazılım ve bağımlılıkları kolayca ile BT işlemleri ve üretim ortamları tipik "Benim makinemde çalışıyor" excuse sorununu ortadan kaldırırken paylaşabilir. Kapsayıcılar, farklı ortamlar arasında uygulama çakışmaları çözün. Dolaylı olarak kapsayıcıları ve Docker geliştiriciler ve BT işlemleri daha yakın bir araya, bunları etkin bir biçimde işbirliği kolaylaştırmaya getirin. Birçok müşteri, kapsayıcı iş akışı'ı benimsemeyi DevOps sürekliliği Aranan ancak daha karmaşık yayın yapılandırması aracılığıyla uygulama ve komut zincirleri oluşturmak vardı sağlar. Kapsayıcılar, DevOps derleme/test/dağıtma hatlarında basitleştirin.

![Docker çalıştırma/izleme/yönetme iş yükünü BT işlemleri ve geliştirme/tasarım iş yükü Geliştirici ve mimarlara arasında köprü oluşturmaya yardımcı olur.](./media/image1.png)

**Şekil 2-1.** Kapsayıcılı Docker uygulamaları için yaşam döngüsü "Kişiler" başına ana iş yükleri

Kapsayıcı (uygulama ve hizmeti ve bağımlılıklarını çerçeveleri ve bileşenleri) ve kapsayıcılar ve hizmetler hizmetler topluluğu tarafından oluşturulmuş bir uygulama olarak birlikte nasıl davranacağını nedir ile Docker kapsayıcılarında, geliştiricilerin kendi. Birden çok kapsayıcı bağımlılıkları tanımlanan bir `docker-compose.yml` dosya veya ne çağrılabilir bir *dağıtım bildirimi*. Bu arada, BT işlem ekipleri (BT uzmanları ve yönetim), üretim ortamları yönetimine odaklanabilir; Altyapı; ölçeklenebilirlik; İzleme; ve sonuç olarak, uygulamaların düzgün bir şekilde, son kullanıcılar için çeşitli kapsayıcıları içeriğini bilmek zorunda kalmadan sunduğunuzdan kullandığınızdan emin olun. Bu nedenle, "geri çağırma gerçek nakliye benzerliği ad kapsayıcısı,". Bu nedenle, bir kapsayıcının içerik sahipleri kendilerini nasıl kapsayıcıya gönderilecek ve kargo şirketi taşımalar kaynaklandığı noktaya kapsayıcıdan hedefine bilerek veya içeriği hakkında caring olmadan endişe. Benzer şekilde, geliştiricilerin oluşturabilir ve kendi kendilerini "taşıma" mekanizmaları ile uğraşmak zorunda kalmadan bir Docker kapsayıcısı içinde içeriği.

Şekil 2-1'in sol tarafındaki pillar, geliştiriciler, yazma ve yerel kod için Docker Windows veya Mac kullanarak Docker kapsayıcılarında çalıştırın Bir Docker görüntüsü halinde kodlarını oluşturmaya yönelik derleme adımları yanı sıra çalıştırmak için temel işletim sistemi belirten bir Dockerfile'ı kullanarak kod işletim ortamını tanımlarlar. Geliştiricilerin nasıl bir veya daha fazla görüntü tanımlamak yukarıda sözü edilen kullanarak çalışmak `docker-compose.yml` dosya dağıtım bildirimi. Kendi yerel geliştirme tamamlandıkça bunlar kendi uygulama kodunu ve Docker yapılandırma dosyalarını kod depoya seçtikleri (diğer bir deyişle, Git deposu) gönderin.

DevOps sütununu kullanarak kod deposunda sağlanan Dockerfile derleme – sürekli tümleştirme (CI) işlem hatları tanımlar. CI sistemi seçilen Docker kayıt defterinden temel kapsayıcı görüntülerini çeker ve uygulaması için özel Docker görüntülerini oluşturur. Görüntüleri ardından doğrulandı ve birden çok ortama dağıtımları için kullanılan Docker kayıt defterine gönderildi.

Sağ sütun takımları yönetme işlemleri uygulamalarınızın ve altyapınızın geri bildirim ve geliştirme ekibi, uygulamanın nasıl olabileceği hakkında içgörüler sağlayabilir bir ortam ve uygulamaların izleme sırasında üretimde dağıtılan geliştirildi. Kapsayıcı uygulamalar genellikle kapsayıcı düzenleyicileri kullanarak üretim ortamında çalıştırılır.

Büyük ölçüde uygulama yaşam döngüsü içinde iki takımların işbirliği geliştirme sırasında bir görev ayrımı nettir bir sözleşme sağlayan bir temel platform (Docker kapsayıcıları) üzerinden iki takımların işbirliği. Operasyon ekibi bildiriminin yanı sıra yerleşik görüntüleri alın ve bunları kendi düzenleme sistemi içinde çalışan geliştiricilerin kapsayıcı içeriğini, kendi işletim ortamını ve kapsayıcı bağımlılıklarını aittir.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Docker'ı kullanırken zorluklardan uygulama yaşam döngüsü.

Gelecek yıl içinde kapsayıcılı uygulamaların sayısını artıracak birçok neden vardır ve bu nedenlerden biri üzerinde mikro hizmet tabanlı uygulamaları oluşturmayı.

Son 15 yıl sırasında web Hizmetleri kullanımı, temel uygulamaları binlerce olmuştur ve büyük olasılıkla, birkaç yıl sonra biz de aynı durum ile Docker kapsayıcılarında çalıştırılan mikro hizmet tabanlı uygulamalar bulabilirsiniz.

Ayrıca değerinde tek yapılı uygulamalar için Docker kapsayıcıları da kullanabilirsiniz ve Docker avantajları çoğunu almaya devam ediyorsanız bahsetmek için bir hizmettir. Kapsayıcılar mikro hizmetler yalnızca hedefleyen değil.

Docker kapsayıcı ve mikro hizmetler neden yeni zorluklar, kuruluşların ve bu nedenle, geliştirme sürecinde kullanımını birçok kapsayıcıları ve mikro hizmetler üretim sistemleri üzerinde çalışan korumak için sağlam bir strateji gerekir. Sonuç olarak, kurumsal uygulamalar, yüzlerce veya binlerce üretimde çalışan kapsayıcılar/örnek sahip olur.

Bu zorluklar, DevOps araçları, DevOps etkinliklerinizde yeni işlemleri tanımlayın ve bu türden sorular için yanıtlar bulmak zorunda kalırsınız şekilde kullanırken yeni talepleri oluşturun:

- Geliştirme, CI/CD, yönetim ve işlemler için hangi araçları kullanabilirim?

- Nasıl Şirketim hataları kapsayıcıları üretimde çalışırken yönetebilir miyim?

- En düşük kapalı kalma süresi'yla üretimde yazılımımızı parçalarını nasıl Değiştirebiliriz?

- Biz nasıl ölçeklendirebilirsiniz ve biz üretim sistemimiz nasıl izleyebilir miyim?

- Nasıl biz test ve kapsayıcıların dağıtımını bizim yayın işlem hattında ekleyebilir miyim?

- Microsoft azure'da kapsayıcılar için açık kaynak araçları/platformları nasıl kullanabileceğimizi?

Tüm bu soruları yanıtlayabilir, daha iyi Docker kapsayıcıları, uygulamalarınızı (mevcut veya yeni uygulamalar) taşımak hazırlanmış olacaksınız. 

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Bir genel uçtan uca Docker uygulaması yaşam döngüsü iş giriş

Şekil 2-2, bu örnekte belirli DevOps etkinlikleri ve varlıklar üzerinde odaklanarak bir Docker uygulaması yaşam döngüsü için daha ayrıntılı bir iş akışı sunar.

![Bu diyagramda devops'un "dış döngü" gösterilmektedir. Kod depoya gönderildiğinde bir CI işlem hattı başlatıldıktan sonra uygulamanın dağıtılacağı CD işlem hattı başlar. Geliştirme ekipleri için kullanıcı ve iş gereksinimlerinizi yanıt vermek için gerçek böylece "İç döngü" gerçekleştiği geri geliştirme iş yükü olarak, dağıtılmış uygulamalardan toplanan ölçümleri beslenir.](./media/image2.png)

**Şekil 2-2.** Docker kapsayıcı uygulama yaşam döngüsü için üst düzey iş akışı

Her şeyi Geliştirici iç döngü akışında kod yazmaya başlar ile başlar. Geliştiriciler kodu depoya (örneğin, bir kaynak denetim sistemi Git gibi) kod göndermeden önce gerçekleşen her şeyi burada tanımlarsınız iç döngü aşamadır. Bundan sonra taahhüt, depo Tetikleyiciler sürekli tümleştirme (CI) ve iş akışının geri kalanı.

İç döngü temelde "code"Çalıştır""test"ve"debug"yanı sıra doğrudan uygulamayı yerel olarak çalıştırmadan önce gereken ek adımlar" gibi tipik adımları içerir. Bu çalıştırmak ve uygulamayı bir Docker kapsayıcısı olarak test etmek için geliştirici işlemidir. İzleyen bölümlerde iç döngü iş akışı açıklanacaktır.

Bir adım sonuna kadar son iş akışı sırasında bakmak için geri alma, DevOps iş akışı bir teknoloji veya bir araç kümesi büyük: kültürel evrimi gerektiren bir yaklaşımdır. Kişiler, işlemler ve uygun araçları, uygulama yaşam döngüsü daha hızlı ve daha öngörülebilir hale getirmek için. Kapsayıcıya alınmış bir iş akışı genellikle benimseyen kuruluşlar, kuruluşlarının, insanları ve kapsayıcılı iş akışıyla eşleşecek işlemleri temsil etmek için yeniden yapılandırabilirsiniz.

DevOps uygulayan daha hızlı birlikte için rekabet baskılarına sonuçları geliştirilmiş izlenebilirlik ve yinelenebilir iş akışları Otomasyon, hata yapmaya açık ve el ile gerçekleştirilen işlemleri değiştirerek yanıt ekipleri yardımcı olabilir. Kuruluşlar da ortamları daha verimli bir şekilde yönetebilir ve şirket içi ve bulut kaynakları ile maliyet tasarrufu yanı sıra sıkıca tümleşik Araçlar farkında olun.

Docker uygulamaları için DevOps iş akışınızın uygularken, Docker teknolojileri iç döngü (çalışma kodu, hata ayıklama), derleme test CI aşaması çalışırken, geliştirme kutusundan mevcut iş akışı, neredeyse her aşamasında olduğunu görürsünüz ve Son olarak, hazırlama ve üretim ortamlarına kapsayıcıların dağıtımını.

Kalite uygulamalarının geliştirme düzeltme maliyeti azaltır Geliştirme döngüsünün başlarında, kusurlarını tanımlamaya yardımcı olur. Görüntüde ortam ve bağımlılıklar dahil olmak üzere ve birden çok ortamda aynı görüntüsü dağıtma bir felsefesi benimseme ayıklama dağıtımları daha güvenilir hale ortama özgü yapılandırmaları olan bir uzmanlık alanı tanıtın.

Etkili Araçları (izleme ve tanılama) alınan zengin veriler, performans sorunlarını ve gelecekteki öncelikleri ve Yatırımlar için rehberlik için kullanıcı davranışını hakkında Öngörüler sağlar.

DevOps yolculuğu, bir hedef kabul edilmelidir. Artımlı olarak kendisinden, başarı göstermek, öğrenin ve evrim Geçiren uygun kapsamlı projelerini aracılığıyla uygulanmalıdır.

## <a name="benefits-of-devops-for-containerized-applications"></a>Kapsayıcılı uygulamalar için DevOps avantajları

Düz bir DevOps iş akışı tarafından sağlanan en önemli avantajlarından bazıları şunlardır:

- Daha hızlı ve daha iyi uyumluluk daha kaliteli yazılım sunun.

- Sürekli gelişim ve ayarlamaları önceden ve daha ekonomik bir şekilde yönlendirir.

- Saydamlık ve hissedarlar sunmaya ve yazılım işletim arasında işbirliğini artırın.

- Güvenlik riski en aza indirerek sağlanan kaynakları daha etkili bir şekilde yazılımınız ve maliyetleri denetim.

- Tak ve açık kaynak yatırımları dahil olmak üzere, var olan DevOps yatırımlarınızı birçoğu ile iyi kullan.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](../Microsoft-platform-tools-containerized-apps/index.md)
